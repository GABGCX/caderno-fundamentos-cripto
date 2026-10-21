# Capítulo 85: Slashing por Dentro, Penalidade Inicial, Correlação e o Prêmio do Denunciante

O Capítulo 2 apresentou o slashing em poucas linhas, e o Capítulo 63 mostrou quais votos conflitantes dão dentes à finalidade. Falta olhar para o outro lado da regra: o que acontece, passo a passo e em números, com o saldo de quem é cortado. A função da especificação que faz isso é curta, mas esconde três peças de desenho bem diferentes: um golpe inicial pequeno, uma punição que depende de quantos outros validadores falharam junto e um prêmio para quem denuncia. Este capítulo percorre as três, com as constantes atuais da camada de consenso.

**Quem pode ser cortado.** Um validador só é cortável enquanto não foi cortado antes e enquanto estiver entre a época de ativação e a época em que fica sacável. Na prática isso significa que a janela de risco continua aberta mesmo depois que o validador pede para sair (Capítulo 84): enquanto o saldo não é liberado, uma prova de conduta antiga ainda pode ser apresentada. A prova chega dentro de um bloco, de dois jeitos. A denúncia de proponente traz dois cabeçalhos de bloco assinados para o mesmo slot, e cada bloco comporta até 16 delas. A denúncia de atestador traz duas atestações em conflito, e a Electra limita a uma por bloco, mas ela pode atingir todos os validadores que aparecem nas duas listas ao mesmo tempo. As condições de conflito (voto duplo e voto envolvente) foram detalhadas no Capítulo 63.

**O que a função faz, em ordem.** A função `slash_validator` executa cinco ações. Primeiro, inicia a saída do validador (a fila é a do Capítulo 49). Segundo, marca o validador como cortado. Terceiro, empurra a data em que o saldo ficará sacável para pelo menos 8.192 épocas à frente, valor de `EPOCHS_PER_SLASHINGS_VECTOR`. Quarto, registra o saldo efetivo dele num vetor circular de totais cortados. Quinto, desconta a penalidade inicial e paga as recompensas. Como cada época dura 384 segundos, 8.192 épocas equivalem a cerca de 36 dias, contra os 256 épocas (pouco mais de um dia) de uma saída comum. Esse é o motivo de o cortado ficar tanto tempo preso: o protocolo precisa de uma janela longa para somar tudo o que foi cortado ao redor.

**Penalidade inicial, o golpe pequeno.** O desconto imediato é o saldo efetivo dividido por uma constante, e essa constante já mudou várias vezes ao longo das versões da especificação, como mostra a tabela.

| Versão | Divisor da penalidade inicial | Sobre 32 ETH | Multiplicador proporcional | Divisor do prêmio |
| --- | --- | --- | --- | --- |
| Fase 0 (lançamento) | 128 | 0,25 ETH | 1 | 512 |
| Altair | 64 | 0,5 ETH | 2 | 512 |
| Bellatrix (The Merge) | 32 | 1 ETH | 3 | 512 |
| Electra (Pectra) | 4.096 | 0,0078125 ETH | 3 | 4.096 |

*A tabela mostra que o protocolo endureceu a punição proporcional de 1 para 3 e, ao mesmo tempo, quase zerou o golpe inicial com a Pectra.*

A razão da queda está na própria EIP-7251 (Capítulo 40). Como a penalidade inicial cresce linearmente com o saldo efetivo, um validador de 2.048 ETH pagaria 64 ETH com o divisor 32 por um erro isolado, e esse risco desencorajava a consolidação. Com o divisor 4.096, o mesmo validador paga 0,5 ETH. O texto da proposta chama isso de tornar a penalidade inicial desprezível. A dissuasão de verdade foi deslocada para a segunda peça.

**Penalidade de correlação, o golpe que depende dos outros.** A cada época, a função `process_slashings` olha para os validadores cortados cuja data de saldo sacável está exatamente 4.096 épocas à frente (metade do vetor), ou seja, os que estão no meio da quarentena, perto do 18º dia. Para eles, calcula-se a soma de todos os saldos efetivos registrados no vetor nas últimas 8.192 épocas, multiplica-se por 3 e limita-se ao total ativo da rede. A fração resultante é aplicada ao saldo efetivo de cada cortado.

```latex
S = soma dos saldos efetivos cortados na janela de 8192 epocas
T = saldo total ativo
fracao = min(3 x S, T) / T
penalidade = saldo_efetivo x fracao
```

Isso produz uma curva simples: um corte isolado, com S minúsculo diante de T, tira uma fração ínfima do saldo, enquanto um ataque que corte um terço do total ativo leva a fração a 1, e o validador perde tudo. A tabela abaixo usa só proporções, sem números de mercado.

| Fração do total ativo cortada na janela | Fração do saldo perdida na correlação |
| --- | --- |
| 0,1% | 0,3% |
| 1% | 3% |
| 10% | 30% |
| 33,3% ou mais | 100% |

*A tabela mostra o efeito do multiplicador 3: o custo cresce em linha reta até que cortar um terço da rede custe tudo a todos os envolvidos.*

Esse limiar não é arbitrário. É o mesmo um terço do Capítulo 63: quem quebra a finalidade precisa de pelo menos um terço do stake para ter votado de forma conflitante, e por isso perde, no mínimo, esse terço inteiro. A regra faz o custo de um ataque ser medido pela fração do stake envolvida, e não por um valor fixo por validador.

**Por que esperar 18 dias.** A espera de metade do vetor tem um motivo de informação. Se a penalidade fosse aplicada na hora, ela só enxergaria os cortes já ocorridos, e um validador cortado cedo escaparia com punição leve mesmo que o ataque se espalhasse depois. Esperar 4.096 épocas dá tempo de a soma S refletir os cortes vizinhos, anteriores e posteriores, dentro de uma janela total de 8.192. Como o vetor é circular, entradas antigas são zeradas conforme a janela avança.

```mermaid
flowchart LR
    A[Época 0<br/>prova incluída] --> B[Golpe inicial<br/>saldo efetivo / 4096]
    B --> C[Saída iniciada<br/>marcado como cortado]
    C --> D[Época 4096<br/>penalidade de correlação]
    D --> E[Época 8192<br/>saldo sacável]
    E --> F[Varrimento devolve<br/>o saldo restante]
```

*O desenho mostra a linha do tempo de um validador cortado: golpe inicial no dia zero, correlação por volta do 18º dia e liberação do que sobrar por volta do 36º.*

**O prêmio do denunciante.** O dinheiro retirado não é todo queimado. A função calcula um prêmio igual ao saldo efetivo dividido por uma constante (512 antes da Electra, 4.096 depois). Uma parte de 8/64 (um oitavo) vai para o proponente do bloco que incluiu a prova, e o resto vai para o denunciante. Como a prova no bloco não informa quem a descobriu, na prática o denunciante vem vazio e o proponente do bloco fica com o prêmio inteiro. Com 32 ETH e o divisor atual, o prêmio é de 0,0078125 ETH, do qual o proponente leva 0,0009765625 ETH pela parte fixa. Observe que o prêmio é igual à penalidade inicial: na Electra, o corte inicial financia exatamente o prêmio, e o resto da punição (a correlação e os efeitos da saída) sai de circulação como queima.

**O que o cortado continua perdendo.** Além dos dois golpes, o validador cortado já saiu da lista ativa: deixa de receber recompensas de atestação e de proposição (Capítulo 48), segue sujeito às penalidades por omissão enquanto a saída não se completa e, se a rede estiver em vazamento por inatividade (Capítulo 61), ainda sofre os descontos adicionais. Soma-se a isso o custo de oportunidade de ficar com o saldo preso por cerca de 36 dias.

**O que isso muda na prática.** Primeiro, o risco do staking individual por erro de configuração é pequeno em termos de punição imediata, desde que o incidente não atinja muitos validadores ao mesmo tempo. Segundo, o risco real está na correlação: operadores, serviços de staking e clientes que concentram muitos validadores (Capítulos 3, 28 e 57) transformam um erro local em um evento correlacionado, e a fração S cresce de acordo. É por isso que diversidade de clientes e distribuição de chaves, como a DVT, aparecem como defesa econômica, e não só técnica. Terceiro, o casamento de duas chaves de assinatura no mesmo validador em máquinas diferentes é a causa clássica de voto duplo acidental, e o desenho acima explica por que a prática comum é nunca ligar um validador de reserva com a mesma chave ao mesmo tempo. O material é educacional e não recomenda comprar, vender ou fazer staking.

**Glossário do capítulo.**

- **Slashing**: punição aplicada a um validador que assinou mensagens em conflito, com perda de saldo e saída forçada.
- **Denúncia de proponente (proposer slashing)**: prova de que o mesmo validador assinou dois blocos diferentes para o mesmo slot.
- **Denúncia de atestador (attester slashing)**: prova de duas atestações em conflito (voto duplo ou envolvente), que pode atingir vários validadores de uma vez.
- **EPOCHS_PER_SLASHINGS_VECTOR**: constante igual a 8.192 épocas (cerca de 36 dias), que define o tamanho do vetor circular de cortes e o tempo de quarentena.
- **Penalidade inicial**: desconto imediato do saldo efetivo dividido por uma constante, hoje 4.096 para o prefixo da Electra.
- **Penalidade de correlação**: desconto aplicado na metade da quarentena, proporcional à fração do stake cortada na janela, com multiplicador 3 e limite no total ativo.
- **Prêmio do denunciante (whistleblower reward)**: recompensa paga a quem inclui a prova, dividida entre o proponente do bloco e o denunciante.
- **Saldo efetivo**: saldo arredondado em múltiplos de 1 ETH usado como base de todas as contas de penalidade.
- **Quarentena do cortado**: período em que o validador já saiu da lista ativa, mas só poderá sacar o que sobrar após 8.192 épocas.

**Fontes.**

- Especificação da fase 0 (consenso), constantes de slashing e `slash_validator`: https://raw.githubusercontent.com/ethereum/consensus-specs/master/specs/phase0/beacon-chain.md
- Especificação do Altair, constantes e `process_slashings` revisados: https://raw.githubusercontent.com/ethereum/consensus-specs/master/specs/altair/beacon-chain.md
- Especificação do Bellatrix, divisor 32 e multiplicador 3: https://raw.githubusercontent.com/ethereum/consensus-specs/master/specs/bellatrix/beacon-chain.md
- Especificação da Electra, divisores de 4.096 e `process_slashings` atual: https://raw.githubusercontent.com/ethereum/consensus-specs/master/specs/electra/beacon-chain.md
- EIP-7251, racional sobre tornar a penalidade inicial desprezível: https://raw.githubusercontent.com/ethereum/EIPs/master/EIPS/eip-7251.md
