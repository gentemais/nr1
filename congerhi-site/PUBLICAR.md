# Como publicar o site do CONGERHI 2027

O site é estático: só arquivos HTML, imagens e CSS/JS embutidos. Não precisa de Node, banco de dados nem build.

## O que subir
- `index.html`
- `patrocinio.html`
- pasta `assets/`

(Não precisa subir `README.md`, `PUBLICAR.md` nem `preview.png`.)

## Atenção ao domínio
Hoje `congerhi.com.br` já mostra a home nova. Antes de publicar, decidir se este site **substitui** a home atual ou entra num subdomínio (ex.: `2027.congerhi.com.br`). Se for subdomínio, trocar o `server_name` e o certbot abaixo.

## Alternativa: puxar direto do GitHub (dentro da VPS)
```bash
cd /var/www && git clone -b claude/beautiful-faraday-dgwefp https://github.com/gentemais/nr1.git congerhi-src
ln -sfn /var/www/congerhi-src/congerhi-site /var/www/congerhi
```
Para atualizar depois: `cd /var/www/congerhi-src && git pull`.
(Se o repositório for privado, usar uma chave de deploy do GitHub.)

## Passo a passo na VPS 1 (Contabo, onde ficam os sites do grupo)

1. Copiar os arquivos para o servidor (do computador de quem tem o acesso):
   ```bash
   scp -r index.html patrocinio.html assets root@169.58.209.206:/var/www/congerhi/
   ```
2. Criar o site no Nginx (`/etc/nginx/sites-available/congerhi`):
   ```nginx
   server {
       listen 80;
       server_name 2027.congerhi.com.br;
       root /var/www/congerhi;
       index index.html;
       location / { try_files $uri $uri/ /index.html; }
       location /assets/ { expires 30d; add_header Cache-Control "public"; }
   }
   ```
3. Ativar e recarregar:
   ```bash
   ln -s /etc/nginx/sites-available/congerhi /etc/nginx/sites-enabled/
   nginx -t && systemctl reload nginx
   ```
4. No Registro.br, apontar o domínio (registro A `2027`) para `169.58.209.206`.
5. Gerar o HTTPS:
   ```bash
   certbot --nginx -d 2027.congerhi.com.br
   ```

Se o domínio escolhido for outro (ex.: eventocongerhi.com.br), é só trocar o `server_name` e o certbot.

## Depois de publicado
- Conferir no celular: vídeo de abertura, botão "Garantir meu passaporte" (abre o WhatsApp), formulário.
- Para trocar links (Asaas, Google Forms), editar o bloco `CONFIG` no fim do `index.html` e subir de novo só esse arquivo.
