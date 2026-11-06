# CT02 — Obrigatórios ausentes no cadastro

**Autoria:** Carlos Gabriel Dos Santos Rodrigues  
**Objetivo:** verificar que o cadastro recusa a ausência dos campos obrigatórios, indica as pendências e permite concluir um ciclo válido após corrigi-las.  
**Requisitos relacionados:** Inclusão #24265 (CA #24532, #24533); Consulta #24268 (CA #24548); Atualização #24269 (CA #24563, #24566); Exclusão #24270 (CA #24574, #24575).  
**Ator:** usuário autorizado às quatro operações.  
**Pré-condições:** categoria `Câmera` ativa, usina `Usina Alfa` disponível; série `CT02-CAM-001` livre; ativo criado neste caso sem registros operacionais ou históricos.

## Dados de teste

Cadastro válido: série `CT02-CAM-001`, nome `Câmera do portão`, categoria `Câmera`, usina `Usina Alfa`, situação `Ativo`. Atualização válida: nome `Câmera do acesso`.

## [FP] Fluxo principal — criar, consultar, atualizar e excluir

1. O ator abre o cadastro e tenta confirmar os dados válidos, exceto que deixa **Nome** vazio. **Esperado:** nenhum ativo é criado; o sistema informa que o Nome está pendente. O ator preenche `Câmera do portão` e confirma. **Esperado:** o cadastro é aceito.
2. O ator consulta pela série `CT02-CAM-001`. **Esperado:** encontra um único registro com nome, categoria, usina e situação informados.
3. O ator atualiza o nome para `Câmera do acesso`. **Esperado:** a consulta ao mesmo registro apresenta o novo nome; continua existindo um único ativo dessa série.
4. O ator solicita a exclusão. **Esperado:** recebe pedido de confirmação. Após confirmar, o ativo é excluído e não aparece na consulta de ativos disponíveis.

## [A1] Cada outro obrigatório ausente

Antes da inclusão válida do passo 1, repetir tentativas independentes deixando vazio **um** dos seguintes campos por vez: identificação (sem série nem patrimônio), categoria, usina e situação. Em cada tentativa, manter os demais dados válidos. **Esperado em todas:** inclusão recusada, campo pendente indicado e nenhum cadastro adicional. O cenário não decide como patrimônio sem série deve ser representado; somente exercita ausência total de identificação.

## Regras de negócio

- **[RN1]** Os cinco grupos obrigatórios são identificação, nome, categoria, localização em usina e situação (#24532).
- **[RN2]** A recusa por vazio precisa indicar os campos pendentes (#24533); o CA não fixa a redação completa da mensagem.
