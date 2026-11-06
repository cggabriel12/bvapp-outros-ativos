# CT06 — Número de série duplicado

**Autoria:** Carlos Gabriel Dos Santos Rodrigues  
**Objetivo:** verificar que uma segunda inclusão com o mesmo número de série é recusada e que uma série livre permite concluir o ciclo.  
**Requisitos relacionados:** Inclusão #24265 (CA #24532, #24538); Consulta #24268 (CA #24548); Atualização #24269 (CA #24563, #24566); Exclusão #24270 (CA #24574, #24575).  
**Ator:** usuário autorizado às quatro operações.  
**Pré-condições:** existe outro ativo com série `CT06-EXISTENTE`, sem exclusão solicitada neste caso; categoria `Equipamento de rede` ativa e usina `Usina Norte` disponíveis; série `CT06-LIVRE` ainda não usada; o novo ativo não terá registros operacionais ou históricos.

## Dados de teste

Primeira tentativa: série `CT06-EXISTENTE`, nome `Roteador duplicado`. Cadastro corrigido: série `CT06-LIVRE`, nome `Roteador adicional`, categoria `Equipamento de rede`, usina `Usina Norte`, situação `Ativo`. Atualização: nome `Roteador adicional revisado`.

## [FP] Fluxo principal — criar, consultar, atualizar e excluir

1. O ator tenta cadastrar `Roteador duplicado` com a série `CT06-EXISTENTE`, mantendo os demais obrigatórios válidos. **Esperado:** a inclusão é recusada; não surge um segundo ativo com essa série. O ator informa `CT06-LIVRE`, muda o nome para `Roteador adicional` e confirma. **Esperado:** o novo cadastro é aceito.
2. O ator consulta `CT06-LIVRE` e `CT06-EXISTENTE` separadamente. **Esperado:** a primeira consulta encontra o ativo novo; a segunda continua encontrando somente o registro que já existia.
3. O ator altera o nome do ativo `CT06-LIVRE` para `Roteador adicional revisado` e confirma. **Esperado:** o mesmo cadastro exibe o nome atualizado; o registro preexistente não muda.
4. O ator solicita a exclusão do ativo `CT06-LIVRE`, recebe confirmação e a aceita. **Esperado:** o novo ativo deixa de aparecer entre os disponíveis; `CT06-EXISTENTE` continua consultável.

## [A1] Tentativa duplicada sem correção

Se o ator não substituir a série repetida no passo 1, nenhum segundo cadastro é efetivado. O CA #24538 não define a frase literal da recusa, portanto o cenário não exige uma mensagem específica.

## Regras de negócio

- **[RN1]** Dois ativos não podem ser incluídos com o mesmo número de série (#24538).
- **[RN2]** Este caso compara a mesma série, no mesmo tipo de ativo, sem presumir regras de normalização, patrimônio ou unicidade entre tipos.
