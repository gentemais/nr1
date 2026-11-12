# Site CONGERHI 2027

Landing page de vendas do CONGERHI 2027 — "Sem Máscaras: dos bastidores ao palco".
Arquivo único (`index.html`) + pasta `assets/`. Basta abrir no navegador ou subir em qualquer hospedagem estática.

## O que configurar antes de publicar
No final do `index.html`, no bloco `CONFIG`:
- `links.presencial`, `links.vip`, `links.digital`: links de checkout de cada ingresso
- `links.premio`: formulário de indicação do Prêmio Ser Gente
- `links.patrocinio`, `links.whatsapp`, `links.instagram`, `links.email`
- `leadEndpoint`: URL que recebe os cadastros da lista do 1º lote (Google Apps Script, RD Station, n8n...)

Enquanto um link estiver vazio, o botão leva para o formulário da lista.

## Pendências de conteúdo
- Confirmar a data: o Mídia Kit diz 19 e 20/03/2027; o Mapa do Evento diz 20 e 21/03.
- Valores e lotes dos ingressos (hoje aparecem como "Em breve").
- Nomes e fotos dos palestrantes (hoje são cards "Em breve").
- Depoimentos e fotos reais de edições anteriores.
