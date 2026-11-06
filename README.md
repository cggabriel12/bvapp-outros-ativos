# Lab 06 — Cenários de teste de Outros Ativos

Mini projeto individual de **Carlos Gabriel Dos Santos Rodrigues** para a EPIC 2.1.3 — Gestão de Outros Ativos do BVapp. A entrega é documental: os cenários descrevem comportamentos esperados; não foram executados nem automatizados.

## Como ler

Cada arquivo em `functional_tests/` usa a forma do exemplo `UC001 — Manter produtos` da Aula 06: objetivo, requisitos, ator, fluxo principal `[FP]`, fluxos alternativos `[A]` e regras de negócio `[RN]`. Também registra pré-condições, dados e resultados esperados. Em todos os dez cenários, o fluxo principal inclui **criar, consultar, atualizar e excluir**. Os fluxos alternativos verificam o foco particular de cada caso.

| Cenário | Foco |
| --- | --- |
| [CT01](functional_tests/CT01-ciclo-basico.md) | Ciclo básico, mensagens e auditoria |
| [CT02](functional_tests/CT02-campos-obrigatorios.md) | Obrigatórios ausentes |
| [CT03](functional_tests/CT03-campos-complementares.md) | Campos complementares opcionais |
| [CT04](functional_tests/CT04-categoria-e-usina.md) | Categorias ativas e usina |
| [CT05](functional_tests/CT05-situacao.md) | Opções de situação |
| [CT06](functional_tests/CT06-serie-duplicada.md) | Série duplicada |
| [CT07](functional_tests/CT07-listagem-e-detalhe.md) | Listagem e detalhe |
| [CT08](functional_tests/CT08-filtros-serie-categoria.md) | Filtros por série e categoria |
| [CT09](functional_tests/CT09-filtros-localizacao-situacao.md) | Filtros por localização e situação; resultado vazio |
| [CT10](functional_tests/CT10-atualizacao-e-exclusao.md) | Validação da atualização e confirmação da exclusão |

O [plano de ação](PLANO_DE_ACAO.md) registra a seleção e os limites do recorte.

## Fontes

- Enunciado da atividade: `lab06.md`, na pasta de trabalho de origem.
- Exemplo de formato: `raw.md`, na pasta de trabalho de origem.
- [Requisitos da EPIC 2.1.3](https://github.com/DiogoBAguiar/bvapp-ativos-requisitos/tree/5f3072939bb7ce5f90b64bf0faa5483bbb0d3260), commit `5f3072939bb7ce5f90b64bf0faa5483bbb0d3260`.
- Os IDs `#24532` a `#24578` indicados nos cenários são os critérios de aceitação de origem do OpenProject. A [revisão de Outros Ativos](https://github.com/DiogoBAguiar/bvapp-ativos-requisitos/blob/5f3072939bb7ce5f90b64bf0faa5483bbb0d3260/evidencias/revisao-outros-ativos-walkthrough-2026-11-05.md) distingue esses critérios dos complementos locais e registra as pendências.

Os dados `CTxx-...`, nomes de exemplo, categorias e usinas indicados nas pré-condições são **dados de teste**, não cadastros reais nem regras novas do produto. Onde a fonte não define texto de erro, ordem exata ou formato de valor, o cenário não inventa esse detalhe.

## Apresentação de cinco minutos

1. Contextualizar o recorte e as fontes (1 minuto).
2. Mostrar a organização dos arquivos e a rastreabilidade (1 minuto).
3. Apresentar o CT10, percorrendo FP, alternativas, dados e resultados (2 minutos).
4. Explicar os limites documentados e concluir (1 minuto).
