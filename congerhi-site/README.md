# Site CONGERHI 2027

Landing page de vendas do CONGERHI 2027 — "Sem Máscaras: dos bastidores ao palco".
Arquivo único (`index.html`) + pasta `assets/`. Basta abrir no navegador ou subir em qualquer hospedagem estática.

## O que configurar antes de publicar
No final do `index.html`, no bloco `CONFIG`:
- `links.presencial`: link de pagamento Asaas do Passaporte (vazio = botão abre o WhatsApp (14) 99665-8272 com o lote atual)
- Lotes: editar o array `LOTES` (valores e datas de fim); o site troca o lote sozinho
- `links.premio`: formulário de indicação do Prêmio Ser Gente
- `links.patrocinio`, `links.whatsapp`, `links.instagram`, `links.email`
- `leadEndpoint`: URL que recebe os cadastros da lista do 1º lote (Google Apps Script, RD Station, n8n...)

Enquanto um link estiver vazio, o botão leva para o formulário da lista.

## Fontes usadas
- Identidade visual CONGERHI 2027 (azul petróleo #002F4E, azul profundo #00004C, cinza #939393, branco; Unispace/Montserrat).
- Mídia Kit 2027 (tema, 4 atos, 5 pilares, ingressos, Prêmio Ser Gente).
- Drive do evento: fotos reais do CONGERHI 2026, contatos, endereço, lotes de 2026 e depoimentos em vídeo.
- Vídeo de abertura: reel do Instagram embutido no topo.

## Pendências de conteúdo
- Data: usamos 19 e 20/03/2027 (Mídia Kit 2027). O Mapa do Evento diz 20 e 21/03, que foram as datas de 2026.
- Nomes e fotos dos palestrantes (hoje são cards "Em breve").
- Depoimentos e fotos reais de edições anteriores.
