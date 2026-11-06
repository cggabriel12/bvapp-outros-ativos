# CT03 — Campos complementares opcionais

**Autoria:** Carlos Gabriel Dos Santos Rodrigues  
**Objetivo:** verificar a disponibilidade dos campos complementares e que sua ausência não impede o ciclo de um ativo com obrigatórios preenchidos.  
**Requisitos relacionados:** Inclusão #24265 (CA #24532, #24534); Consulta #24268 (CA #24548, #24554); Atualização #24269 (CA #24563, #24566); Exclusão #24270 (CA #24574, #24575).  
**Ator:** usuário autorizado às quatro operações.  
**Pré-condições:** categoria `Cisterna` ativa, usina `Usina Alfa` disponível; série `CT03-CIS-001` livre; não haverá vínculo operacional ou histórico para o ativo criado.

## Dados de teste

Obrigatórios: série `CT03-CIS-001`, nome `Cisterna principal`, categoria `Cisterna`, usina `Usina Alfa`, situação `Ativo`. Fabricante, Modelo, Data de Aquisição, Vida Útil Estimada e Observações Gerais ficam sem valor. Na atualização, o nome passa a `Cisterna de apoio`.

## [FP] Fluxo principal — criar, consultar, atualizar e excluir

1. O ator abre o cadastro. **Esperado:** os cinco campos complementares estão disponíveis. Informa os obrigatórios, deixa os complementares vazios e confirma. **Esperado:** a inclusão é aceita; os complementares não são tratados como pendências.
2. O ator consulta `CT03-CIS-001` e abre o detalhe. **Esperado:** encontra o ativo selecionado e seus dados preenchidos; os campos complementares sem informação não são apresentados como valores fornecidos.
3. O ator edita o nome para `Cisterna de apoio`, mantém os complementares vazios e confirma. **Esperado:** a atualização é aceita e a consulta mostra o novo nome no mesmo ativo.
4. O ator solicita exclusão, recebe a confirmação e a aceita. **Esperado:** o ativo deixa de constar na consulta de disponíveis.

## [A1] Complementos disponíveis sem preenchimento

No passo 1, observar individualmente Fabricante, Modelo, Data de Aquisição, Vida Útil Estimada e Observações Gerais. **Esperado:** cada campo pode ficar sem valor e nenhum deles é apontado como obrigatório. Este caso não atribui formato ou unidade à vida útil nem inventa texto para campos sem valor.

## Regras de negócio

- **[RN1]** Os complementares enumerados em #24534 são opcionais.
- **[RN2]** A ausência desses campos não dispensa os obrigatórios de #24532.
