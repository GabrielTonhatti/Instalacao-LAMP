<img src = "https://e-tinet.com/wp-content/uploads/2018/10/mongoDB-banco-de-dados-nosql-1024x512.png" alt="MongoDB">

Instalando mongoDB no Fedora
============================

MongoDB é um suporte de índice totalmente flexível e banco de dados de consultas rico. É classificado como um programa de banco de dados NoSQL, que usa documentos do tipo JSON com esquemas opcionais. Semelhante ao sistema de banco de dados relacional, também oferece suporte a junções em consultas.

O MongoDB lançou uma nova versão estável 4.4 com muitos aprimoramentos importantes. Este tutorial ajudará você a instalar o MongoDB 4.4 em sistemas Fedora Linux.

## Etapa 1 - Configurar Repositório

A equipe oficial do MongoDB fornece um repositório Yum para instalar o MongoDB em um sistema Fedora. Crie um novo arquivo de configuração com o repositório Mongodb yum. Edite um arquivo em um editor:

```
sudo vi /etc/yum.repos.d/mongodb-org-4.4.repo
```

Adicione o conteúdo abaixo

```vim
[Mongodb]
name = MongoDB Repository
baseurl = https: //repo.mongodb.org/yum/redhat/8/mongodb-org/4.4/x86_64/
gpgcheck = 1
habilitado = 1
gpgkey = https: //www.mongodb.org/static/pgp/server-4.4.asc
```

ou caso a primeira forma não de certo, tente essa outra:

```vim
[mongodb-org-4.4]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/8Server/mongodb-org/4.4/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-4.4.asc
```

## Etapa 2 - Instale o MongoDB no Fedora

Vamos usar o gerenciador de pacotes DNF para instalar o servidor MongoDB no sistema Fedora. Isso também instalará todas as dependências necessárias em seu sistema.

Para instalar o MongoDB no Fedora, digite:

```
sudo dnf install mongodb-org mongodb-org-server 
```

<img src = "https://tecadmin.net/wp-content/uploads/2018/07/installing-mongodb-in-fedora.png" alt="MongoDB">

## Etapa 3 - iniciar o serviço MongoDB

O servidor MongoDB foi instalado em seus sistemas Fedora. Vamos habilitar o serviço systemd MongoDB e iniciá-lo.
```
sudo systemctl enable mongod.service 
```
e
```
sudo systemctl start mongod.service 
```
Assim que o serviço for iniciado, verifique o status atual com o seguinte comando.

```
sudo systemctl status mongod.service
```

<img src = "https://tecadmin.net/wp-content/uploads/2018/07/mongodb-service-on-fedora.png" alt="MongoDB">

## Etapa 4 - Conecte-se ao MongoDB Shell

Use o seguinte comando para verificar a versão do MongoDB instalada

```
mongod --version 
```

```
versão db v4.4.4
Informações de compilação: {
    "versão": "4.4.4",
    "gitVersion": "8db30a63db1a9d84bdcad0c83369623f708e0397",
    "openSSLVersion": "OpenSSL 1.1.1k FIPS 25 de março de 2021",
    "módulos": [],
    "alocador": "tcmalloc",
    "meio Ambiente": {
        "distmod": "rhel80",
        "distarch": "x86_64",
        "target_arch": "x86_64"
    }
}
```

Conecte o MongoDB usando a linha de comando e execute alguns comandos de teste para verificar o funcionamento adequado.

```
mongo 

> use mydb;

> db.test.save ({tecadmin: 1001})

> db.test.find ()

{"_id": ObjectId ("60d472f31f5ba51557c8b066"), "tecadmin": 1001}
```

ParabénsVocê instalou com sucesso o servidor mongodb no sistema Fedora. Apenas para a prática, você pode usar o shell do navegador MongoDB .

### <b> Usado apenas para anotação e facilitação na instalação do mongoDB do site: <a href = "https://tecadmin.net/install-mongodb-on-fedora/"> tecadmin.net/install-mongodb-on-fedora/ </a>
