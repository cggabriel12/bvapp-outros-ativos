# Plano de ação — Lab 06: Outros Ativos

**Autor:** Carlos Gabriel Dos Santos Rodrigues  
**Data:** 06/11/2026  
**Entrega:** documentação individual de cenários de teste.

## 1. Base e recorte

- Enunciado local: `../lab06.md`.
- Exemplo de formato: `../raw.md` (`UC001 — Manter produtos`).
- Requisitos: EPIC 2.1.3 — Gestão de Outros Ativos, no repositório de consulta `../bvapp-ativos-requisitos/`.
- Versão consultada dos requisitos: commit `5f3072939bb7ce5f90b64bf0faa5483bbb0d3260`.
- Fonte normativa: 26 critérios originais das Features #24265, #24268, #24269 e #24270 do OpenProject. Os critérios locais derivados ajudam na leitura, mas não substituem a origem.

Os exemplos usarão identificação por **número de série informado**, categoria e usina cadastradas, e ativos sem registros operacionais ou históricos para a exclusão bem-sucedida. Dados de exemplo são condições do cenário, não novas regras de negócio. O resultado esperado será o descrito no requisito, mesmo quando a revisão documental registrar divergência da implementação atual.

## 2. Dez cenários a produzir

| Arquivo | Foco principal | Critérios de origem em destaque |
| --- | --- | --- |
| CT01 | Ciclo básico de um outro ativo, com mensagens e auditoria | #24532, #24539, #24540, #24548, #24563, #24566, #24568, #24574, #24575, #24576, #24577 |
| CT02 | Recusa de inclusão com obrigatórios ausentes; correção e ciclo completo | #24532, #24533 |
| CT03 | Campos complementares disponíveis e opcionais | #24534 |
| CT04 | Categorias ativas em ordem alfabética e seleção de usina | #24535, #24536 |
| CT05 | Quatro opções da situação no cadastro | #24537 |
| CT06 | Recusa de número de série já cadastrado | #24538 |
| CT07 | Campos da listagem e detalhe do ativo selecionado | #24548, #24549, #24554 |
| CT08 | Filtros por série e categoria | #24550 |
| CT09 | Filtros por localização e situação; resultado vazio | #24550, #24552 |
| CT10 | Validação, persistência e auditoria da atualização; confirmação e auditoria da exclusão | #24563, #24565, #24566, #24567, #24568, #24574, #24575, #24576, #24577 |

Cada arquivo terá um fluxo completo de **criar, consultar, atualizar e excluir** para respeitar a regra de CRUD do enunciado. O foco principal acrescentará verificações próprias, sem contar dez repetições idênticas como trabalho distinto. Usaremos as seções do UC001: objetivo, requisitos, ator, fluxo principal, fluxos alternativos e regras de negócio. Acrescentaremos pré-condições, dados e resultados esperados, autoria e rastreabilidade por ID.

## 3. Pontos que não serão presumidos

- Patrimônio sem série e regras de comparação entre tipos de ativo.
- Qual campo é o identificador único imutável na atualização.
- Quais vínculos e históricos, em detalhe, impedem a exclusão.
- Ordem exata da tabela (o critério original não define coluna nem direção).
- Contrato do arquivo de exportação, paginação e formatos.
- Detalhes de perfis de autorização, concorrência, reenvio e falhas de rede.

Esses assuntos ficam registrados como limites do recorte. Não serão usados como resultados esperados dos dez cenários.

## 4. Execução

1. Criar o mini projeto local independente do repositório de requisitos, com `README.md`, este plano e `functional_tests/`.
2. Redigir dez arquivos Markdown com dados distintos e quatro operações em cada cenário.
3. Conferir IDs, mensagens literais, campos obrigatórios, autoria e consistência dos fluxos.
4. Iniciar um repositório Git local próprio e deixar a entrega pronta para publicação no GitHub.
5. Publicar no GitHub de Carlos e enviar o link no Classroom quando houver acesso à conta e ao serviço; conferir que o professor pode abrir o repositório.

## 5. Critério de pronto

Dez cenários documentados e rastreados, sem regras inventadas, cada um contendo criar, consultar, atualizar e excluir; arquivos legíveis em um repositório individual; README com índice e instruções de apresentação. Publicação e envio são etapas separadas, verificadas por URL acessível.

## 6. Andamento

- [x] Mini projeto local independente e plano documentado.
- [x] Dez cenários redigidos em `functional_tests/`.
- [x] Revisão estrutural dos dez arquivos e do índice.
- [x] Repositório Git local iniciado e primeiro commit preparado.
- [ ] Repositório GitHub de Carlos criado e conteúdo publicado.
- [ ] Link público ou acessível ao professor conferido e enviado no Classroom.
- [ ] Apresentação individual realizada.
