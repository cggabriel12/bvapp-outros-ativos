# CT05 — Quatro opções de situação

**Autoria:** Carlos Gabriel Dos Santos Rodrigues  
**Objetivo:** verificar que o cadastro oferece as quatro situações especificadas e preserva a opção escolhida durante a consulta e a edição de outro campo.  
**Requisitos relacionados:** Inclusão #24265 (CA #24532, #24537); Consulta #24268 (CA #24548, #24549); Atualização #24269 (CA #24563, #24566); Exclusão #24270 (CA #24574, #24575).  
**Ator:** usuário autorizado às quatro operações.  
**Pré-condições:** categoria `Câmera` ativa, usina `Usina Norte` selecionável; série `CT05-CAM-001` livre; ativo sem registros operacionais ou históricos.

## Dados de teste

Série `CT05-CAM-001`, nome `Câmera em revisão`, categoria `Câmera`, usina `Usina Norte`, situação escolhida `Em manutenção`. Atualização: nome `Câmera revisada`, sem pedir mudança de situação.

## [FP] Fluxo principal — criar, consultar, atualizar e excluir

1. O ator abre o cadastro e examina o campo Situação. **Esperado:** as opções são `Ativo`, `Inativo`, `Em manutenção` e `Descartado`. Seleciona `Em manutenção`, informa os demais obrigatórios e confirma. **Esperado:** o cadastro registra essa situação.
2. O ator consulta `CT05-CAM-001`. **Esperado:** a listagem identifica sua situação como `Em manutenção`.
3. O ator altera apenas o nome para `Câmera revisada` e confirma. **Esperado:** a consulta apresenta o novo nome para o mesmo ativo e conserva `Em manutenção`.
4. O ator solicita a exclusão e a confirma. **Esperado:** o ativo não aparece mais na consulta de disponíveis.

## [A1] Inspeção das alternativas

No passo 1, antes da escolha, o ator percorre as quatro opções sem confirmar outros cadastros. **Esperado:** todas estão disponíveis. O cenário não afirma transições automáticas, efeitos operacionais ou significado de cada estado, pois esses detalhes não estão definidos neste critério.

## Regras de negócio

- **[RN1]** Situação é campo obrigatório (#24532).
- **[RN2]** As quatro opções enumeradas em #24537 devem estar disponíveis. Este caso não deriva uma política de mudança de situação da história #29050, que possui apenas título na fonte.
