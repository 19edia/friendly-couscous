# Validação — atualização de inicialização e assistente

## 27/09/2026 — botões, Sub líder, tutorial e High member

- Suíte completa executada com processos isolados: `node --test --test-concurrency=2`, **162 testes aprovados, zero falhas**.
- Nove regressões dos botões: abertura imediata dos modais, confirmação/cancelamento na mensagem original, intervalos independentes por divisão/token, ticket preservado se a resposta expira, recuperação da mensagem e botão após rollback, ID de fechamento inválido, autorização de administrador Discord e fechamento sem duplicar jobs.
- Startup identifica um Interactions Endpoint URL que desvia cliques do Gateway. Logs registram chegada de interação, estado do bot e reconexões, sem token ou conteúdo enviado no formulário.
- Nove testes da patente Sub líder: acesso completo, IFJs de terceiros, gestão de equipe, `/warn`, tribunal, migração e tutorial persistente com autenticação e CSRF. Treze testes da interface para Meu Discord, navegação, tutorial por patente e acesso completo do Sub líder.
- High member recebe Equipe nas duas divisões; testadas remoção por rebaixamento/revogação e preservação de cargos não gerenciados.
- Edge headless real com API simulada: tutorial Sub líder no desktop, dez categorias administrativas, seletor de nova patente, tutorial concluído sem reaparecer no reload; tutorial e vínculo obrigatório de moderador/recrutador em tela de 390 px. Sem erros JavaScript ou transbordamento horizontal.
- Capturas com contas fictícias: `../EXEMPLOS/boas-vindas-sublider.png` e `../EXEMPLOS/boas-vindas-moderador-mobile.png`.

Não foi fornecido endereço ou acesso à instância Render. O timeout geral relatado não foi reproduzido no servidor publicado; os defeitos locais foram corrigidos e foram adicionadas verificações e registros para identificar se os cliques chegam ao bot. Nenhum deploy, clique em bot de produção ou mudança em contas Discord reais foi realizado.

---

## 27/09/2026 — tribunal, Meu Discord e embeds

- Suíte completa: `node --test --test-concurrency=2`, **135 testes aprovados, zero falhas**.
- Sintaxe dos módulos de tribunal, API, bot e painel aprovada.
- Tribunal: 16 testes do módulo e 7 de integração API/bot com PGlite e Discord simulado. Validados autenticação, patente, CSRF, vínculo confirmado, identidade original, migração repetida, criação única, permissões privadas, convites, erros e nova tentativa, recuperação após falha, encerramento e preservação do canal.
- Fechamento bloqueia mensagens, threads, gerenciamento de mensagens e webhooks dos participantes comuns. Administradores nativos do Discord mantêm suas permissões.
- Meu Discord: seis testes de regressão para estado confirmado, troca opcional, navegação, primeiro vínculo obrigatório e respostas atrasadas.
- Embeds: serialização, campos de até 1.024 caracteres, orçamento total de 6.000 caracteres, preservação do texto integral em anexo, identidade e atualização dos painéis existentes.
- Navegador Edge real em modo headless, com API simulada: fluxo de abrir/concluir tribunal; Discord confirmado; troca opcional; navegação por categorias; confirmação inicial do moderador. Desktop 1440 px e celular 390 px, sem erros JavaScript e sem transbordamento horizontal.
- Capturas locais em `../EXEMPLOS/tribunal-painel.png`, `../EXEMPLOS/tribunal-mobile.png` e `../EXEMPLOS/discord-confirmado.png`, com dados fictícios.

Não houve implantação nem envio para servidores Discord reais. A migração e a atualização dos painéis permanentes serão executadas ao iniciar esta versão no ambiente configurado.

---

Verificado em 20/09/2026.

- `npm test`: 25 testes aprovados, sem falhas.
- `npm run check`: sintaxe dos módulos de entrada, bot e painel aprovada.
- Processo real com configuração inválida: encerrou com código 1, sem anunciar servidor pronto e sem imprimir o segredo usado no teste.
- Testes de falha em sistema, conexão PostgreSQL, esquema, escrita/leitura, login Discord e permissões: nenhum abriu o listener HTTP; recursos criados foram encerrados.
- Sucesso: listener aberto somente após os testes, fila ativada por último.
- BOT_ENABLED=false: Discord explicitamente dispensado, apenas painel iniciado.
- PostgreSQL embarcado (PGlite): leitura/escrita com rollback deixou zero registros de teste.
- Checks Discord usam simulação: hierarquia e tipo incorreto de canal foram rejeitados sem publicar mensagens.
- Chromium: assistente percorreu 29 etapas, validou URL inválida, realizou 30 gravações por um handle de arquivo simulado, gerou download com conteúdo compatível com o parser .env do Node e importou os valores novamente.
- Assistente: falha de escrita e navegador sem seletor de arquivos tratados sem alegar salvamento. Layout móvel conferido sem transbordamento horizontal.
- O nome do download pode ser ajustado pelo navegador (ex.: env.txt); o aplicativo orienta renomear para .env. A gravação direta depende do seletor e da permissão do navegador real.

Os 10 testes anteriores de autenticação, permissões, IFJ, denúncias, filas e tickets continuam aprovados.

Não executado: conexão aos servidores Discord reais do usuário, implantação Render/Supabase ou diálogo nativo de gravação do sistema operacional. São necessários seus tokens, banco e IDs para essas verificações. O preflight real roda automaticamente quando você iniciar o projeto configurado.


Atualização Caçados/Guerras/carteiras: 84 testes automatizados aprovados. Navegador: upload real de arquivo local, prévia, criação de quatro jobs (dois caçados e duas guerras), viewport de 390 pixels sem overflow e sem erros JavaScript. PNGs dos dois tipos renderizados e inspecionados. Discord e banco de produção não acessados.
