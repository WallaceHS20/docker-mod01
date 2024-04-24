docker build -t app .

# Arquivo DockerFile

#### DEFININDO A PLATAFORMA E IMAGEM
~~~~dockerFILE
FROM node:12-alpine 
~~~~

#### CRIANDO E DEFININDO DIRETÓRIO PADRÃO PARA IMAGEM
~~~~dockerFILE
WORKDIR /app
~~~~

#### OTIMIZANDO A CONSTRUÇÃO DA IMAGEM ANALISANDO AS DEPEDÊNCIAS 
~~~~dockerFILE
COPY package.json .
~~~~

#### ADICIONAR USUÁRIO NA IMAGEM
~~~~dockerFILE
RUN addgroup dev && adduser -S -G wallace dev
~~~~

#### DEFININDO USUÁRIO PADRÃO PARA EXECUTAR A APLICAÇÃO DA IMAGEM
~~~~dockerFILE
USER wallace
~~~~

#### PRIMEIRO PONTO DIRETÓRIO DA APLICAÇÃO / SEGUNDO PONTO DIRETÓRIO DE ORIGEM
~~~~dockerFILE
COPY . .
~~~~

#### INSTALAÇÃO DE DEPÊNCIAS - INSTALANDO PYTHON
~~~~dockerFILE
RUN apk add --no-cache python2 g++ make
~~~~

#### INSTALAÇÃO DAS DEPÊNDENCIAS DO APP
~~~~dockerFILE
RUN npm install --production

COPY . .
~~~~

#### DEFININDO A ROTA DE UMA API
~~~~dockerFILE
ENV API_URL=http://api.products/source/
~~~~

#### EXECUÇÃO VIA TERMINAL
~~~~dockerFILE
CMD ["node", "src/index.js"]
~~~~

#### DEFININDO A PORTA DO CONTAINER
~~~~dockerFILE
EXPOSE 3000
~~~~

# Operando na plataforma Docker

#### CRIANDO BUILD DA IMAGEM
~~~~CMD
docker build -t app .
~~~~

#### INICIANDO UMA IMAGEM
~~~~CMD
docker run app
~~~~

#### RENOMENADO UMA IMAGEM E INSERINDO UMA TAG
~~~~CMD
docker image tag app:latest app:v1.0.1
~~~~

#### Iniciando um container em background a partir de uma imagem e atribuindo um nome para ele
~~~~CMD
docker run -d --name teste app:v1.0
~~~~

#### Exibir containers ativos
~~~~CMD
docker ps
~~~~

#### Exibição de logs
~~~~CMD
docker logs --help

docker logs [parametro] [id container]
~~~~

--docker ports
docker run -d -p 3000:3000 --name teste app:v1.0
~~~~CMD
docker image tag app:latest app:v1.0.1
~~~~

--executando comandos docker
docker exec teste ls
~~~~CMD
docker image tag app:latest app:v1.0.1
~~~~

--iniciando
docker start teste
~~~~CMD
docker image tag app:latest app:v1.0.1
~~~~

--pausando um container 
docker stop teste
~~~~CMD
docker image tag app:latest app:v1.0.1
~~~~

--docker rm -f teste
