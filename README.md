Esse experimento consiste na certificação SSL de domínio de servidor backend em nodejs. Toda aplicação rodara em Docker.
Para realizar a certificação de um domínio, primeiro devera possuir um domínio e seguir os seguintes passos:
1. Realizar as substituições de ''{domain}'' pelo domínio e ''{email}'' pelo email nos arquivos `./docker-compose-certbot.yml`, `./nginx/conf/default.conf` e `./nginx/conf/prod`.

2. Execute o seguinte comando para o start dos serviços (nginx e backend):
```bash
docker-compose up -d
```
3. Execute o seguinte comando para gerar os certificados SSL do domínio:
```bash
docker-compose -f docker-compose-certbot.yml up
```
4. Gere o ssl_dhparam usando o seguinte comando na pasta `./certbot/letsencrypt/`:
```bash
sudo openssl dhparam -out dhparam.pem 2048
```
5. Modifique o arquivo de configuração na pasta `./nginx/conf/`:
```bash
mv default.conf test && mv prod default.conf
```
6. Realize o restart do nginx para pegar a nova configuração:
```bash
docker-compose restart nginx
```

Pronto, agora pode utilizar o https.
