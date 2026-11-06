# CT08 — Filtros por identificação e categoria

**Autoria:** Carlos Gabriel Dos Santos Rodrigues  
**Objetivo:** verificar que a consulta pode restringir os registros por identificação do ativo e por categoria.  
**Requisitos relacionados:** Inclusão #24265 (CA #24532); Consulta #24268 (CA #24548, #24550); Atualização #24269 (CA #24563, #24566); Exclusão #24270 (CA #24574, #24575).  
**Ator:** usuário autorizado às quatro operações.  
**Pré-condições:** categorias ativas `Câmera` e `Equipamento de rede`, usina `Usina Alfa` disponível; existe o ativo `CT08-REDE-OUTRO` da categoria `Equipamento de rede`; série `CT08-CAM-001` livre. O ativo criado não terá registros operacionais ou históricos.

## Dados de teste

Série `CT08-CAM-001`, nome `Câmera lateral`, categoria `Câmera`, usina `Usina Alfa`, situação `Ativo`. Atualização: nome `Câmera lateral revisada`.

## [FP] Fluxo principal — criar, consultar, atualizar e excluir

1. O ator cadastra `Câmera lateral` com todos os dados indicados. **Esperado:** um novo ativo é criado com série `CT08-CAM-001`.
2. O ator consulta por identificação `CT08-CAM-001`. **Esperado:** o resultado contém o ativo criado e não contém `CT08-REDE-OUTRO`. O ator aplica o filtro de categoria `Câmera`. **Esperado:** o ativo criado continua no resultado e o equipamento de rede não aparece. O ator abre seu detalhe para confirmar a série.
3. O ator altera o nome do ativo filtrado para `Câmera lateral revisada` e confirma. **Esperado:** a consulta pelos mesmos filtros encontra o mesmo cadastro com o novo nome.
4. O ator solicita a exclusão desse ativo e a confirma. **Esperado:** ele deixa de aparecer na consulta de disponíveis; o ativo da categoria `Equipamento de rede` permanece.

## [A1] Filtro somente por categoria

No passo 2, retirar o filtro de identificação e manter apenas `Câmera`. **Esperado:** os resultados pertencem à categoria `Câmera`. O cenário volta a informar a série antes da edição para selecionar o alvo exato.

## Regras de negócio

- **[RN1]** Identificação e Categoria são filtros previstos em #24550.
- **[RN2]** Neste caso, a identificação usada é a série informada no cadastro. O teste não decide a representação de patrimônio sem série, nem exige busca parcial ou normalização não definida no CA de origem.
