# CT07 — Campos da listagem e detalhe selecionado

**Autoria:** Carlos Gabriel Dos Santos Rodrigues  
**Objetivo:** verificar os campos exigidos na listagem e a abertura do detalhe do ativo escolhido, antes e depois da edição.  
**Requisitos relacionados:** Inclusão #24265 (CA #24532); Consulta #24268 (CA #24548, #24549, #24554); Atualização #24269 (CA #24563, #24566); Exclusão #24270 (CA #24574, #24575).  
**Ator:** usuário autorizado às quatro operações.  
**Pré-condições:** categoria `Cisterna` ativa; usina `Usina Sul` disponível; série `CT07-CIS-001` livre. Há outro ativo previamente cadastrado com série `CT07-OUTRO`, nome `Outro equipamento`, para distinguir as fichas. O ativo criado não terá registros operacionais ou históricos.

## Dados de teste

Novo ativo: série `CT07-CIS-001`, nome `Cisterna secundária`, categoria `Cisterna`, localização `Usina Sul`, situação `Ativo`. Atualização: nome `Cisterna secundária revisada`.

## [FP] Fluxo principal — criar, consultar, atualizar e excluir

1. O ator cadastra o novo ativo com os dados acima. **Esperado:** a inclusão é concluída.
2. O ator abre a consulta de Outros Ativos. **Esperado:** a listagem apresenta para o registro `CT07-CIS-001` identificação, nome, categoria, localização e situação. O ator seleciona esse registro. **Esperado:** o detalhe corresponde a `CT07-CIS-001`, com seus dados cadastrados; não mostra os dados de `CT07-OUTRO` como se fossem do selecionado.
3. O ator edita o nome do registro selecionado para `Cisterna secundária revisada` e confirma. **Esperado:** a listagem e o detalhe do mesmo ativo apresentam o novo nome e mantêm série, categoria, localização e situação.
4. O ator solicita exclusão desse registro, confirma quando solicitado e consulta novamente. **Esperado:** `CT07-CIS-001` não consta entre os disponíveis; `CT07-OUTRO` continua disponível.

## [A1] Seleção do outro registro

No passo 2, se o ator escolher `CT07-OUTRO`, o detalhe deve corresponder a esse segundo registro. O teste volta a selecionar `CT07-CIS-001` antes da edição. Este alternativo verifica a associação entre linha escolhida e detalhe, sem especificar campos que a fonte não enumerou.

## Regras de negócio

- **[RN1]** A listagem contém os cinco campos enumerados em #24549.
- **[RN2]** O ativo selecionado na listagem pode ter seus detalhes completos visualizados (#24554). A completude é avaliada conforme os dados previstos no cadastro; o cenário não cria campos adicionais.
