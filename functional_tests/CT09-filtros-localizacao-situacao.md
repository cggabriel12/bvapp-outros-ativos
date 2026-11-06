# CT09 — Filtros por localização e situação; resultado vazio

**Autoria:** Carlos Gabriel Dos Santos Rodrigues  
**Objetivo:** verificar os filtros por usina e situação e a mensagem definida para uma combinação sem correspondência.  
**Requisitos relacionados:** Inclusão #24265 (CA #24532, #24537); Consulta #24268 (CA #24548, #24550, #24552); Atualização #24269 (CA #24563, #24566); Exclusão #24270 (CA #24574, #24575).  
**Ator:** usuário autorizado às quatro operações.  
**Pré-condições:** categoria `Equipamento de rede` ativa; usinas `Usina Norte` e `Usina Sul` disponíveis; há um ativo preexistente `CT09-SUL-ATIVO` em `Usina Sul` com situação `Ativo`, e nenhum ativo `Em manutenção` em `Usina Sul`; série `CT09-NORTE-001` livre. O ativo criado não terá registros operacionais ou históricos.

## Dados de teste

Série `CT09-NORTE-001`, nome `Switch em manutenção`, categoria `Equipamento de rede`, usina `Usina Norte`, situação `Em manutenção`. Atualização: nome `Switch de apoio em manutenção`.

## [FP] Fluxo principal — criar, consultar, atualizar e excluir

1. O ator cadastra o switch com os dados indicados. **Esperado:** a inclusão é aceita com localização `Usina Norte` e situação `Em manutenção`.
2. O ator filtra a consulta por `Usina Norte` e `Em manutenção`. **Esperado:** encontra `CT09-NORTE-001`. Depois filtra por `Usina Sul` e `Em manutenção`. **Esperado:** nenhum ativo corresponde e é mostrada a frase `Nenhum ativo encontrado para os critérios informados`. O ator restaura os primeiros filtros e seleciona `CT09-NORTE-001`.
3. O ator altera apenas o nome para `Switch de apoio em manutenção` e confirma. **Esperado:** os filtros `Usina Norte` e `Em manutenção` continuam encontrando o mesmo ativo com o novo nome.
4. O ator solicita a exclusão do switch, confirma e repete esses filtros. **Esperado:** o ativo excluído não aparece entre os disponíveis. O ativo `CT09-SUL-ATIVO` permanece disponível em sua própria combinação de filtros.

## [A1] Filtros isolados

No passo 2, aplicar Localização `Usina Norte` sem Situação e depois Situação `Em manutenção` sem Localização. **Esperado:** cada filtro restringe o resultado pelo respectivo atributo. Voltar à combinação dos dois filtros antes da edição.

## Regras de negócio

- **[RN1]** Localização e Situação são filtros previstos em #24550.
- **[RN2]** Quando nenhum registro satisfaz os filtros, a mensagem literal é a de #24552. O cenário não define o comportamento de falha de rede ou carregamento, que não faz parte desse CA.
