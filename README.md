# Caderno de Fundamentos Cripto (ETH em foco)

Caderno de estudo que cresce sozinho: três vezes por dia uma tarefa agendada do Claude escreve um capítulo novo sobre fundamentos de cripto, tecnologia, história e economia, com o ecossistema Ethereum como fio condutor. A ideia é decidir com entendimento, não só olhando gráfico.

Cada capítulo é pesquisado em fontes primárias (ethereum.org, documentação oficial dos protocolos, material técnico reconhecido), cita as fontes no final e fecha com um glossário dos termos que apareceram no texto. Os capítulos também trazem diagramas em Mermaid, tabelas comparativas e fórmulas, que o GitHub renderiza direto na página.

## Índice

| # | Capítulo | Tema |
| --- | --- | --- |
| 1 | [Ethereum, por que ele existe](capitulos/01-ethereum-por-que-ele-existe.md) | Origem, The Merge, tokenomics do ETH |
| 2 | [Proof-of-Stake por dentro](capitulos/02-proof-of-stake-por-dentro.md) | Validadores, slots, epochs, comitês, slashing |
| 3 | [Staking líquido e Lido](capitulos/03-staking-liquido-e-lido.md) | stETH, rebase, saques, riscos e concentração |
| 4 | [Restaking e EigenLayer](capitulos/04-restaking-e-eigenlayer.md) | AVSs, operator sets, stake único, LRTs e seus riscos |
| 5 | [Rollups e Layer 2, o conceito geral](capitulos/05-rollups-e-layer-2.md) | Sequenciador, prova de fraude vs. prova de validade, EIP-4844, framework Stages |
| 6 | [Arbitrum em detalhe](capitulos/06-arbitrum-em-detalhe.md) | Nitro, jogo da bisseção, BoLD, AnyTrust e Nova, ARB DAO, Stylus |
| 7 | [Optimism e o Superchain](capitulos/07-optimism-e-o-superchain.md) | OP Stack, Bedrock, Cannon, Lei das Chains, RetroPGF, saída da Base em 2026 |
| 8 | [Base em detalhe](capitulos/08-base-em-detalhe.md) | Origem na Coinbase, Smart Wallet, Flashblocks, saída do OP Stack, Azul, Base App |
| 9 | [zk-Rollups vs. Rollups Otimistas](capitulos/09-zk-rollups-vs-rollups-otimistas.md) | Provas de validade, SNARK vs. STARK, tipos de zkEVM, panorama de 2026 |
| 10 | [Glamsterdam, o próximo grande salto do Ethereum](capitulos/10-glamsterdam-proximo-salto-ethereum.md) | ePBS, Block-Level Access Lists, caminho para 200M de gas, cronograma de testnets |
| 11 | [DeFi, AMMs e Pools de Liquidez](capitulos/11-defi-amms-pools-de-liquidez.md) | Uniswap V1 a V4, fórmula do produto constante, liquidez concentrada, perda impermanente, Curve StableSwap |
| 12 | [DeFi, Protocolos de Empréstimo (Aave e Compound)](capitulos/12-defi-protocolos-emprestimo-aave-compound.md) | Pools de empréstimo, aToken/cToken, health factor, liquidação, flash loans, Compound III (Comet) |
| 13 | [ETFs de ETH e a entrada institucional](capitulos/13-etfs-de-eth-e-a-entrada-institucional.md) | ETFs spot, criação/resgate in-kind, ETFs com staking, fila de validadores, tesourarias corporativas (DAT) |
| 14 | [Stablecoins, USDC e o lastro em dólar](capitulos/14-stablecoins-usdc-e-o-lastro-em-dolar.md) | Circle, Centre Consortium, Circle Reserve Fund, depeg do SVB, blacklist, GENIUS Act |
| 15 | [Stablecoins, DAI e a colateralização cripto](capitulos/15-dai-e-colateralizacao-cripto.md) | Vaults, razão de colateralização, Black Thursday, Peg Stability Module, rebranding para Sky (SKY, USDS) |
| 16 | [EIP-1559 em profundidade, Base Fee e Priority Fee](capitulos/16-eip-1559-base-fee-priority-fee.md) | Leilão de primeiro preço, ajuste algorítmico da base fee, multiplicador de elasticidade, queima vs. emissão, manipulação teórica do base fee |
| 17 | [MEV, o que é e como a rede tenta domar](capitulos/17-mev-o-que-e-como-a-rede-tenta-domar.md) | Flash Boys 2.0, Dark Forest, ataques sandwich, MEV-Boost, censura de relays, rumo ao ePBS e ao FOCIL |
| 18 | [Tokenomics Avançada, Emissão, Vesting e Distribuição](capitulos/18-tokenomics-avancada-emissao-vesting-distribuicao.md) | Fair launch vs. premine, premine do ETH em 2015, cliff e vesting linear, UNI e ARB, token streaming com Sablier e Hedgey |
| 19 | [Governança e DAOs, Como Funciona Votar On-Chain](capitulos/19-governanca-e-daos-votar-on-chain.md) | Contrato Governor, quorum e timelock, delegação, Snapshot, a UNIfication da Uniswap, Token House e Citizens' House, Security Council da Arbitrum |
| 20 | [A História da The DAO e o Hard Fork de 2016](capitulos/20-a-historia-da-dao-e-o-hard-fork-de-2016.md) | Reentrância no contrato da The DAO, Robin Hood Group, soft fork abandonado, Carbonvote, hard fork no bloco 1.920.000, nascimento do Ethereum Classic, relatório da SEC |
| 21 | [Contratos Inteligentes e a EVM, Como o Código Roda de Fato](capitulos/21-contratos-inteligentes-e-a-evm.md) | Yellow Paper, compilação Solidity para bytecode, stack/memory/storage/calldata, gás por opcode, EIP-2929, EOA vs. conta de contrato, ciclo de vida de uma transação, EOF |
| 22 | [Padrões de Token, ERC-20 e ERC-721 na Prática](capitulos/22-padroes-de-token-erc-20-erc-721-na-pratica.md) | Padrões como acordos públicos, approve e transferFrom, decimals, permit (ERC-2612), safeTransferFrom no ERC-721, metadados, ERC-1155 e ERC-4626 |
| 23 | [Interoperabilidade, Pontes entre Chains e seus Riscos](capitulos/23-interoperabilidade-pontes-entre-chains-e-seus-riscos.md) | Lock-and-mint e burn-and-mint, confiança e verificação, Wormhole, Ronin, Nomad, perguntas para avaliar uma ponte |
| 24 | [Contas Abstratas e a ERC-4337](capitulos/24-contas-abstratas-e-erc-4337.md) | EOA vs. conta de contrato, UserOperation, bundler, EntryPoint, paymaster, EIP-7702 e a Pectra, riscos de delegação |
| 25 | [Oráculos e o Chainlink, Como o Mundo de Fora Entra no Contrato](capitulos/25-oraculos-e-chainlink.md) | Problema do oráculo, Data Feeds, limite de desvio e heartbeat, TWAP do Uniswap V3, manipulação no Mango Markets |
| 26 | [Carteiras, Chaves, Seed Phrase e Custódia](capitulos/26-carteiras-chaves-seed-phrase-e-custodia.md) | Chave privada, endereço e EIP-55, BIP-39 e BIP-32, carteiras HD, modelos de custódia, multisig e ERC-1271 |
| 27 | [Golpes Comuns e Como Reconhecer](capitulos/27-golpes-comuns-e-como-reconhecer.md) | Personificação, aprovações enganosas e Permit2, envenenamento de endereço, pig butchering, hack da Bybit, hábitos de defesa |
| 28 | [Clientes de Execução e Consenso, o Valor da Diversidade](capitulos/28-clientes-de-execucao-e-consenso-diversidade.md) | Engine API, limiares de 1/3 e 2/3, bugs do Prysm (2023 e Fusaka) e do Nethermind, dominância do Geth |
| 29 | [Privacidade no Ethereum, Entre a Transparência e o Sigilo](capitulos/29-privacidade-no-ethereum.md) | Pseudonimato vs. anonimato, mixers e provas de conhecimento zero, linha do tempo jurídica do Tornado Cash, Privacy Pools, endereços furtivos (ERC-5564), Kohaku |
| 30 | [Tokenização de Ativos do Mundo Real, Quando o Título Vira Token](capitulos/30-tokenizacao-de-ativos-do-mundo-real.md) | RWAs, fundo BUIDL e BENJI, ERC-3643 e conformidade no contrato, tokens permissionados, riscos jurídicos e de custódia |
| 31 | [NFTs além da Especulação, Identidade, Aluguel e Contas](capitulos/31-nfts-alem-da-especulacao.md) | ENS e Name Wrapper, royalties (ERC-2981) e o fim do Operator Filter, soulbound (ERC-5192), aluguel (ERC-4907), contas vinculadas a tokens (ERC-6551) |
| 32 | [Ethereum e Solana, uma Comparação Estrutural](capitulos/32-ethereum-e-solana-comparacao-estrutural.md) | Camada base enxuta vs. rápida, Proof of History e Alpenglow (Votor), modelo de contas, isenção de aluguel, taxa de prioridade, Firedancer |
| 33 | [Incidentes de Segurança Marcantes, Parity, Beanstalk e Euler](capitulos/33-incidentes-de-seguranca-marcantes-parity-beanstalk-euler.md) | Biblioteca compartilhada da Parity e o congelamento de 2017, voto emprestado na Beanstalk, função sem checagem de liquidez no Euler, práticas de defesa |
| 34 | [Disponibilidade de Dados, Blobs e PeerDAS](capitulos/34-disponibilidade-de-dados-blobs-e-peerdas.md) | Blobs do EIP-4844, erasure coding, colunas e custódia, amostragem, forks BPO após a Fusaka |
| 35 | [Taxas de Gás na Prática, Como Ler e Como Economizar](capitulos/35-taxas-de-gas-na-pratica.md) | Gás usado vs. preço por unidade, limite e teto na carteira, custos por operação, piso de calldata (EIP-7623), reembolsos (EIP-3529), como reduzir a conta, EIP-2780 |
| 36 | [Bitcoin e Ethereum, uma Comparação Estrutural](capitulos/36-bitcoin-e-ethereum-comparacao-estrutural.md) | UTXO vs. contas, Script e Taproot vs. EVM, proof-of-work vs. proof-of-stake, halving e política monetária, SegWit, cultura de mudança |
| 37 | [Estado, Statelessness e Expiração de Histórico](capitulos/37-estado-statelessness-e-expiracao-de-historico.md) | Estado vs. histórico, testemunhas, Verkle (EIP-6800) e árvore binária (EIP-7864), expiração de estado, EIP-4444, Portal Network |
| 38 | [ePBS por Dentro, Lance do Builder e Comitê de Payload](capitulos/38-epbs-por-dentro-lance-builder-e-comite-de-payload.md) | EIP-7732, builders com stake, lance assinado, envelope de payload, PTC, validação adiada, slot cheio/vazio/ignorado |
| 39 | [Block-Level Access Lists, o Mapa que Permite Executar em Paralelo](capitulos/39-block-level-access-lists-e-execucao-paralela.md) | EIP-7928, hash no cabeçalho, BlockAccessIndex, leitura de disco e execução em paralelo, limite atrelado ao gás, custo de propagação |
| 40 | [Pectra e o Staking, MaxEB, Consolidação e Saídas pela Camada de Execução](capitulos/40-pectra-e-o-staking-maxeb-consolidacao-e-saidas.md) | EIP-7251 (teto de 2.048 ETH, credencial 0x02, consolidação), EIP-7002 (saída via contrato), EIP-6110 (depósitos no bloco), limites de churn por peso |
| 41 | [Fusaka por Dentro, o Pacote que Foi Além do PeerDAS](capitulos/41-fusaka-por-dentro-o-pacote-alem-do-peerdas.md) | Limite de gás por transação (EIP-7825), bloco de 8 MiB, MODEXP, piso do blob (EIP-7918), CLZ, secp256r1 e passkeys, proponentes previsíveis |
| 42 | [FOCIL e a Hegotá, Listas de Inclusão contra a Censura](capitulos/42-focil-e-a-hegota-listas-de-inclusao-contra-a-censura.md) | EIP-7805, comitê de 16 membros, listas de 8 KiB, relógio do slot, inclusão condicional, equivocação, escopo da Hegotá |
| 43 | [Glamsterdam além das Manchetes, Quanto Custa Criar e Ler Estado](capitulos/43-glamsterdam-alem-das-manchetes-precificacao-de-estado.md) | Escopo da EIP-7773, CPSB e gás de estado (EIP-8037), custo de acesso (EIP-8038), reembolsos fora do bloco (EIP-7778), churn de saída (EIP-8061) |
| 44 | [Computação Quântica e o Futuro Pós-Quântico do Ethereum](capitulos/44-computacao-quantica-e-o-futuro-pos-quantico-do-ethereum.md) | Shor e Grover, exposição de ECDSA, BLS e KZG, leanXMSS e leanVM, ML-DSA (EIP-8355), transação de quadros (EIP-8141), cronograma até 2029, hard fork de recuperação |
| 45 | [Intenções entre Chains, ERC-7683 e a Corrida pela Interoperabilidade Padronizada](capitulos/45-intencoes-entre-chains-erc-7683-e-interoperabilidade-padronizada.md) | Intents e solvers, resolvedores, ERC-7683, endereços interoperáveis (ERC-7930), mensagens entre chains (ERC-7786), onde o risco se desloca |

## Como funciona

- Documento vivo original: Claude Docs, atualizado a cada capítulo.
- Este repositório recebe uma cópia em Markdown de cada capítulo novo, um arquivo por capítulo em `capitulos/`.
- O índice acima é atualizado junto.

## Licença

Conteúdo de estudo pessoal de Gabriel Costa. As fontes citadas pertencem aos seus respectivos autores.
