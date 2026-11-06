# CT10 — Validação da atualização e confirmação da exclusão

**Autoria:** Carlos Gabriel Dos Santos Rodrigues  
**Objetivo:** verificar a revalidação de obrigatório na edição, a persistência e o log da atualização, e a confirmação, mensagem e log da exclusão.  
**Requisitos relacionados:** Inclusão #24265 (CA #24532); Consulta #24268 (CA #24548); Atualização #24269 (CA #24563, #24565, #24566, #24567, #24568); Exclusão #24270 (CA #24574, #24575, #24576, #24577).  
**Ator:** usuário autorizado às quatro operações, identificado como `carlos.teste`.  
**Pré-condições:** categoria `Câmera` ativa, usina `Usina Alfa` disponível; série `CT10-CAM-001` livre; ativo deste cenário sem registros operacionais ou históricos.

## Dados de teste

Série `CT10-CAM-001`, nome inicial `Câmera leste`, categoria `Câmera`, usina `Usina Alfa`, situação `Ativo`. Tentativa de edição: Nome vazio. Edição válida: Nome `Câmera leste revisada`.

## [FP] Fluxo principal — criar, consultar, atualizar e excluir

1. O ator cadastra o ativo com os dados iniciais. **Esperado:** o registro é criado.
2. O ator consulta `CT10-CAM-001` e abre o registro. **Esperado:** encontra `Câmera leste` e os demais dados iniciais.
3. O ator abre a edição, apaga o Nome e tenta confirmar. **Esperado:** a atualização é recusada porque Nome é obrigatório; a consulta ainda mostra `Câmera leste`. O ator informa `Câmera leste revisada` e confirma. **Esperado:** a alteração fica registrada no mesmo ativo, a consulta mostra o novo nome, aparece `Ativo atualizado com sucesso` e o log contém `carlos.teste`, data e hora da modificação.
4. O ator solicita excluir `CT10-CAM-001`. **Esperado:** o sistema solicita confirmação antes de excluir. O ator cancela. **Esperado:** o ativo permanece consultável. O ator solicita novamente e confirma. **Esperado:** a exclusão é concluída, aparece `Ativo excluído com sucesso`, e o log registra a operação de exclusão com `carlos.teste`, data e hora.
5. O ator repete a consulta pela série. **Esperado:** o ativo excluído não é apresentado entre os disponíveis.

## [A1] Edição inválida mantida

Se o ator não corrigir o Nome vazio no passo 3, não há atualização bem-sucedida nem mensagem de sucesso. O cadastro anterior permanece para consulta. O CA #24565 não fixa a frase exata do erro; este cenário exige a recusa por Nome obrigatório, sem prescrever a redação da mensagem.

## [A2] Exclusão sem confirmação

Se o ator cancelar no passo 4 e encerrar o fluxo, a exclusão não é concluída. A consulta ainda encontra `CT10-CAM-001`. A continuação do fluxo principal demonstra a confirmação efetiva em uma segunda solicitação.

## Regras de negócio

- **[RN1]** Os obrigatórios do cadastro continuam validados na atualização (#24532, #24565).
- **[RN2]** Alterações válidas são registradas e a atualização exibe a mensagem literal de #24568; o log exige usuário, data e hora (#24566, #24567).
- **[RN3]** A exclusão depende de confirmação (#24575), mostra a mensagem literal de #24577 e registra operação, usuário, data e hora (#24576).
- **[RN4]** Este cenário não testa qual é o identificador imutável nem quais históricos bloqueiam exclusão; usa um ativo sem essas dependências.
