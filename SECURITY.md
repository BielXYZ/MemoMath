# Segurança e Privacidade

## Em poucas palavras

O **MemoMath** executa inteiramente no navegador e não possui backend, login, banco de dados remoto ou rastreamento de dados pessoais. Não há cookies de rastreamento, anúncios ou envio de respostas para servidores externos.

O progresso das fases, preferências de tema e áudio permanecem exclusivamente no armazenamento local do navegador (`localStorage`).

## Dados e armazenamento

O projeto utiliza:

- `localStorage` para salvar o progresso das fases de cada módulo e as preferências de tema/som;
- `Cache Storage` e `Service Worker` para funcionamento offline instantâneo (PWA).

Esses dados pertencem à origem do site. O navegador pode limpá-los caso o usuário limpe os dados de navegação ou utilize o modo anônimo. Para reiniciar todo o progresso, basta limpar os dados do site nas configurações do navegador ou usar a opção correspondente.

## Síntese de áudio local

Os efeitos sonoros (acertos, erros, transições de fase) são sintetizados em tempo real através da **Web Audio API** do próprio navegador, dispensando o download de arquivos de áudio externos pesados e garantindo que o aplicativo funcione com latência zero e 100% offline. O áudio é opcional e pode ser desativado pelo botão correspondente na interface.

## Reporte responsável

Caso encontre algum problema de segurança ou comportamento inesperado, você pode abrir uma issue no repositório oficial ou entrar em contato através do GitHub.
