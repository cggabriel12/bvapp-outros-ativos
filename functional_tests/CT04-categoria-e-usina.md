# CT04 — Categorias ativas e seleção da usina

**Autoria:** Carlos Gabriel Dos Santos Rodrigues  
**Objetivo:** verificar a lista de categorias e a associação do ativo à usina escolhida.  
**Requisitos relacionados:** Inclusão #24265 (CA #24532, #24535, #24536); Consulta #24268 (CA #24548, #24549); Atualização #24269 (CA #24563, #24566); Exclusão #24270 (CA #24574, #24575).  
**Ator:** usuário autorizado às quatro operações.  
**Pré-condições:** categorias `Alfa` e `Beta` cadastradas e ativas; categoria `Gama` cadastrada e inativa; usinas `Usina Norte` e `Usina Sul` cadastradas e selecionáveis; série `CT04-001` livre. O ativo deste caso não recebe registros operacionais ou históricos.

## Dados de teste

Série `CT04-001`, nome `Equipamento de apoio`, categoria `Beta`, usina `Usina Sul`, situação `Ativo`. Atualização: nome `Equipamento de apoio sul`.

## [FP] Fluxo principal — criar, consultar, atualizar e excluir

1. O ator abre o cadastro e observa as categorias. **Esperado:** `Alfa` aparece antes de `Beta`; `Gama` não é oferecida, pois está inativa. O ator seleciona `Beta` e `Usina Sul`, preenche os demais obrigatórios e confirma. **Esperado:** o ativo é cadastrado associado a `Usina Sul`.
2. O ator consulta pela série `CT04-001`. **Esperado:** a listagem identifica `Beta` como categoria e `Usina Sul` como localização do ativo.
3. O ator atualiza apenas o nome. **Esperado:** a consulta apresenta `Equipamento de apoio sul` e mantém `Beta` e `Usina Sul` no mesmo cadastro.
4. O ator solicita a exclusão, confirma quando solicitado e consulta novamente. **Esperado:** o ativo excluído não aparece entre os disponíveis.

## [A1] Outra usina selecionável

No passo 1, antes de confirmar, o ator observa também `Usina Norte` como alternativa de localização, mas mantém `Usina Sul` selecionada. **Esperado:** a escolha de usina é possível; o cenário verifica somente o vínculo efetivamente escolhido.

## Regras de negócio

- **[RN1]** A lista de categorias contém as previamente cadastradas e ativas em ordem alfabética (#24535).
- **[RN2]** O campo Localização permite selecionar a usina à qual o ativo ficará vinculado (#24536); usina é obrigatória no cadastro (#24532).
