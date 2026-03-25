# Pitch do Pre-Projeto

## 1. Visao do produto
O Dashboard de Comunicacao Interna concentra perfis, postagens e comentarios em uma unica interface. O ganho para o usuario final e reduzir dispersao de informacao e facilitar acompanhamento rapido da atividade de cada colaborador.

## 2. Viabilidade tecnica e economica
- O prototipo usa `JSONPlaceholder` para validar a experiencia sem custo de back-end proprio.
- O desenvolvimento foi acelerado com consumo REST via `fetch`.
- O foco inicial ficou na experiencia, no fluxo de dados e nos riscos de integracao.

## 3. Arquitetura adotada
- Cliente-Servidor: o navegador atua como cliente e a API publica como fornecedora de dados.
- MVC no cliente:
  - Model: entidades e adaptadores de contrato.
  - View: renderizacao de usuarios, posts, comentarios, loading e erros.
  - Controller: estado global, eventos e orquestracao do fluxo.

## 4. Principais riscos e mitigacoes
- Lentidao da API:
  - timeout de 8 segundos com `AbortController`
  - retry automatico para falhas transientes
- Indisponibilidade:
  - captura de erro de rede com mensagem amigavel
- Erros HTTP:
  - tratamento especifico para `404` e `5xx`
- Mudanca no formato do JSON:
  - validacao de payload
  - adaptadores `fromApi()` para campos obrigatorios
  - bloqueio de renderizacao inconsistente

## 5. Roteiro sugerido de apresentacao
1. Problema: comunicacao interna dispersa em varias ferramentas.
2. Solucao: dashboard unico para explorar usuarios, posts e comentarios.
3. Demonstracao: selecionar usuario, abrir posts, abrir comentarios.
4. Arquitetura: explicar Cliente-Servidor e MVC.
5. Riscos: mostrar como timeout, retry e validacao de contrato protegem a experiencia.
6. Proximo passo: trocar API fake por back-end real e autenticar usuarios.