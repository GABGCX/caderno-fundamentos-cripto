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

## Como funciona

- Documento vivo original: Claude Docs, atualizado a cada capítulo.
- Este repositório recebe uma cópia em Markdown de cada capítulo novo, um arquivo por capítulo em `capitulos/`.
- O índice acima é atualizado junto.

## Licença

Conteúdo de estudo pessoal de Gabriel Costa. As fontes citadas pertencem aos seus respectivos autores.
