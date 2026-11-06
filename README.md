# Laboratório 06 — Cenários de teste de Outros Ativos

**Autor:** Carlos Gabriel Dos Santos Rodrigues

**Projeto:** BVapp · EPIC 2.1.3 — Gestão de Outros Ativos

Este repositório apresenta **dez cenários de teste documentados** para equipamentos de rede, câmeras, cisternas e outros ativos da mesma gestão. Cada cenário tem objetivo, requisitos relacionados, ator, pré-condições, dados, fluxo principal, alternativas, regras de negócio e resultados esperados. A atividade é de especificação: os cenários não foram executados nem automatizados.

Como pede o Laboratório 06, **cada arquivo descreve criar, consultar, atualizar e excluir no mesmo fluxo**. Os cenários usam a organização do exemplo `UC001 — Manter produtos` da aula: fluxo principal `[FP]`, fluxos alternativos `[A]` e regras `[RN]`.

## Cenários

### 1. [CT01 — Ciclo básico de outro ativo](functional_tests/CT01-ciclo-basico.md)

Um roteador é cadastrado, localizado na consulta, tem o nome atualizado e é excluído após confirmação. O cenário verifica as mensagens literais de sucesso e os registros de auditoria previstos para inclusão e exclusão. **Critérios em destaque:** #24532, #24539, #24540, #24548, #24563, #24574–#24577.

### 2. [CT02 — Obrigatórios ausentes no cadastro](functional_tests/CT02-campos-obrigatorios.md)

O cadastro é tentado sem nome e, em alternativas independentes, sem identificação, categoria, usina ou situação. Cada tentativa deve ser recusada com indicação do campo pendente. Depois de preencher os obrigatórios, o ativo segue pelo ciclo completo. **Critérios em destaque:** #24532–#24533.

### 3. [CT03 — Campos complementares opcionais](functional_tests/CT03-campos-complementares.md)

Uma cisterna é cadastrada sem Fabricante, Modelo, Data de Aquisição, Vida Útil Estimada e Observações Gerais. O cenário verifica que os campos existem, mas sua ausência não impede o cadastro quando os obrigatórios estão preenchidos. **Critério em destaque:** #24534.

### 4. [CT04 — Categorias ativas e seleção da usina](functional_tests/CT04-categoria-e-usina.md)

O cadastro apresenta categorias ativas em ordem alfabética, omite a categoria inativa e permite escolher a usina. A consulta deve mostrar a categoria e a localização efetivamente selecionadas. **Critérios em destaque:** #24535–#24536 e #24549.

### 5. [CT05 — Quatro opções de situação](functional_tests/CT05-situacao.md)

O campo Situação deve oferecer `Ativo`, `Inativo`, `Em manutenção` e `Descartado`. O cenário cadastra uma câmera `Em manutenção`, consulta o estado e verifica que editar apenas o nome não altera a situação escolhida. **Critério em destaque:** #24537.

### 6. [CT06 — Número de série duplicado](functional_tests/CT06-serie-duplicada.md)

Uma tentativa de cadastrar outro ativo com a mesma série de um registro existente deve ser recusada, sem produzir um segundo cadastro. Com uma série livre, o novo ativo pode percorrer o ciclo completo; o preexistente permanece inalterado. **Critério em destaque:** #24538.

### 7. [CT07 — Campos da listagem e detalhe selecionado](functional_tests/CT07-listagem-e-detalhe.md)

A listagem deve mostrar identificação, nome, categoria, localização e situação. Ao abrir um registro, o detalhe deve corresponder ao ativo escolhido, inclusive após a atualização do nome. **Critérios em destaque:** #24548–#24549 e #24554.

### 8. [CT08 — Filtros por identificação e categoria](functional_tests/CT08-filtros-serie-categoria.md)

A consulta usa o número de série informado como identificação e depois aplica a categoria `Câmera`. O resultado deve conter o ativo compatível e excluir da seleção um equipamento de outra categoria. **Critério em destaque:** #24550.

### 9. [CT09 — Filtros por localização e situação](functional_tests/CT09-filtros-localizacao-situacao.md)

O cenário filtra ativos por usina e por situação, isoladamente e em conjunto. Uma combinação sem correspondência deve apresentar `Nenhum ativo encontrado para os critérios informados`. **Critérios em destaque:** #24550 e #24552.

### 10. [CT10 — Atualização validada e exclusão confirmada](functional_tests/CT10-atualizacao-e-exclusao.md)

Uma edição com Nome vazio deve ser recusada; a edição válida deve persistir, exibir a mensagem de sucesso e gerar log. A exclusão é primeiro cancelada e depois confirmada, com mensagem e auditoria próprias. **Critérios em destaque:** #24563, #24565–#24568 e #24574–#24577.

## Organização e rastreabilidade

```text
bvapp-outros-ativos/
├── README.md
└── functional_tests/
    ├── CT01-ciclo-basico.md
    ├── ...
    └── CT10-atualizacao-e-exclusao.md
```

Os IDs dos critérios remetem às quatro Features de origem da EPIC 2.1.3: **Inclusão #24265**, **Consulta #24268**, **Atualização #24269** e **Exclusão #24270**. A base consultada foi o [repositório de requisitos do BVapp no commit `5f30729`](https://github.com/DiogoBAguiar/bvapp-ativos-requisitos/tree/5f3072939bb7ce5f90b64bf0faa5483bbb0d3260). A [revisão de Outros Ativos](https://github.com/DiogoBAguiar/bvapp-ativos-requisitos/blob/5f3072939bb7ce5f90b64bf0faa5483bbb0d3260/evidencias/revisao-outros-ativos-walkthrough-2026-11-05.md) registra as decisões ainda pendentes.

Os nomes, séries, categorias e usinas `CTxx` são **dados de teste**. Para manter resultados esperados claros, estes dez cenários usam série informada e ativos sem histórico operacional. Não presumem regras para patrimônio sem série, identificador imutável, tipos de histórico que bloqueiam exclusão ou contrato de exportação.
