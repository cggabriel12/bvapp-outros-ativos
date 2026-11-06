# CT01 — Ciclo básico de outro ativo

**Autoria:** Carlos Gabriel Dos Santos Rodrigues  
**Objetivo:** verificar que um ativo pode ser cadastrado, consultado, atualizado e excluído, com mensagens e registros de auditoria exigidos.  
**Requisitos relacionados:** EPIC 2.1.3; Inclusão #24265 (CA #24532, #24539, #24540); Consulta #24268 (CA #24548); Atualização #24269 (CA #24563, #24566, #24568); Exclusão #24270 (CA #24574, #24575, #24576, #24577).  
**Ator:** usuário autorizado a executar as quatro operações; seu identificador é `carlos.teste` neste caso.  
**Pré-condições:** categoria `Equipamento de rede` ativa, usina `Usina Alfa` selecionável; número de série `CT01-REDE-001` ainda não cadastrado; ativo sem registros operacionais ou históricos associados.

## Dados de teste

| Campo | Inclusão | Atualização |
| --- | --- | --- |
| Número de série | `CT01-REDE-001` | preservado |
| Nome | `Roteador principal` | `Roteador reserva` |
| Categoria | `Equipamento de rede` | preservada |
| Localização | `Usina Alfa` | preservada |
| Situação | `Ativo` | preservada |

## [FP] Fluxo principal — criar, consultar, atualizar e excluir

1. O ator abre o cadastro de Outros Ativos, informa os dados de inclusão e confirma. **Esperado:** o sistema cria um ativo com ID próprio, mostra `Ativo cadastrado com sucesso` e registra no log o ID criado, `carlos.teste`, data e hora da inclusão.
2. O ator consulta Outros Ativos pela série `CT01-REDE-001` e abre o registro encontrado. **Esperado:** a consulta apresenta o mesmo ativo e os dados cadastrados.
3. O ator edita somente o nome para `Roteador reserva` e confirma. **Esperado:** o mesmo ativo passa a apresentar o novo nome, sem criar outro cadastro, e o sistema mostra `Ativo atualizado com sucesso`.
4. O ator solicita a exclusão desse ativo. **Esperado:** o sistema pede confirmação antes de excluir. O ator confirma. **Esperado:** o sistema conclui a exclusão, mostra `Ativo excluído com sucesso` e grava no log a operação, `carlos.teste`, data e hora.
5. O ator repete a consulta pela série. **Esperado:** o ativo excluído não é apresentado entre os ativos disponíveis.

## [A1] Confirmação não dada

No passo 4, enquanto não houver confirmação, o sistema não conclui a exclusão. A consulta ainda apresenta o ativo. Este alternativo explicita a condição do CA #24575; o ciclo principal segue quando o ator confirma.

## Regras de negócio

- **[RN1]** Identificação por série, nome, categoria, usina e situação compõem os obrigatórios deste caso (#24532).
- **[RN2]** As três mensagens de sucesso são as frases literais dos respectivos CAs (#24539, #24568, #24577).
- **[RN3]** A inclusão e a exclusão possuem os campos mínimos de log definidos em #24540 e #24576. Este caso não presume um formato de tela ou arquivo para o log.
