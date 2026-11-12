# Como publicar o site do CONGERHI 2027

O site é estático: só arquivos HTML, imagens e CSS/JS embutidos. Não precisa de Node, banco de dados nem build.

## O que subir
- `index.html`
- pasta `assets/`

(Não precisa subir `README.md`, `PUBLICAR.md` nem `preview.png`.)

## Passo a passo na VPS 1 (Contabo, onde ficam os sites do grupo)

1. Copiar os arquivos para o servidor (do computador de quem tem o acesso):
   ```bash
   scp -r index.html assets root@169.58.209.206:/var/www/congerhi/
   ```
2. Criar o site no Nginx (`/etc/nginx/sites-available/congerhi`):
   ```nginx
   server {
       listen 80;
       server_name congerhi.com.br www.congerhi.com.br;
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
4. No Registro.br, apontar o domínio (registro A de `congerhi.com.br` e `www`) para `169.58.209.206`.
5. Gerar o HTTPS:
   ```bash
   certbot --nginx -d congerhi.com.br -d www.congerhi.com.br
   ```

Se o domínio escolhido for outro (ex.: eventocongerhi.com.br), é só trocar o `server_name` e o certbot.

## Depois de publicado
- Conferir no celular: vídeo de abertura, botão "Garantir meu passaporte" (abre o WhatsApp), formulário.
- Para trocar links (Asaas, Google Forms), editar o bloco `CONFIG` no fim do `index.html` e subir de novo só esse arquivo.
