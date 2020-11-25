Sumário
[Backup Mongo](#mongo)
[Backend Convida](#convida)

<a name="mongo"/>

## BACKUP DO MONGO - UFPR CONVIDA - ESSE MÉTODO SÓ FUNCIONA PARA VERSÕES ABAIXO DO MONGODB 4.4  
</hr>

<code>$sudo docker ps</code> para ver as informações dos containers e pegar o CONTAINER_ID  
<code>$sudo docker exec -it CONTAINER_ID bash</code> - ABRE UM TERMINAL DENTRO DO CONTAINER  
<code>$cd bin</code>  
<code>$mongodump</code>  
<code>$cd dump</code>  
<ul><li>Checar se criou os arquivos dentro da pasta dump/convida:</li></ul>  
<code>$exit</code> para sair do terminal do container</br>
<code>$sudo docker cp IDDOCONTAINER:/bin/dump/convida</code> (caminho do diretório dump)</br>
<code>/home/convida/backup/pasta-com-o-dia-do-backup</code> (caminho de destino)</br>
<code>$git add pasta-do-backup</code></br>
<code>$git commit -m “dia do backup”</code></br>
<code>$git push</code>


<a name="convida"/>

## Tutorial rodar o backend convida localmente

Pré-requisitos:  
Ter o docker instalado na sua máquina (https://docs.docker.com/engine/install/)
Ter o docker-compose instalado na sua máquina (https://docs.docker.com/compose/install/)
Ter o Git instalado na sua máquina (https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
Tutorial
Passo 1: Clonar o projeto do backend
Passo 2: Fazer o download do repositório de backups como um .zip (https://github.com/ufpr-convida/backup)
Passo 3: Na pasta raiz do projeto clonado abrir um terminal e rodar o comando:
$ sudo docker compose-build
Se tudo ocorrer corretamente, você deverá ver  algo parecido com a seguinte mensagem:

NOTA: Esse comando pode demorar um pouco para ser concluído, principalmente da primeira vez que for rodado.
Em seguida rodar:
$ sudo docker compose-up
Caso o comando seja bem sucedido,você verá algo como essa imagem:


Passo 4: Com os containers rodando, em um novo terminal, digite o seguinte comando:
$ sudo docker ps
Você deverá obter uma saída como essa:

Copie o CONTAINER ID do container mongo.
Passo 5: Descompactar em uma pasta de sua preferência o conteúdo do .zip do repositório de backup.
Passo 6: Copiar a pasta convida do repositório do backup com a data mais recente para dentro do container do mongo através do seguinte comando(você pode obter o caminho digitando pwd no terminal aberto naquela pasta):
$ sudo docker cp caminhodapastaconvida iddocontainermongo:bin/dump 
Exemplo: sudo docker cp /home/alethor/Downloads/backup-main/backup-9-10-2020 6b5e7708d23d:/bin/dump
Passo 7: Abrir um terminal dentro do container do banco de dados mongo através do seguinte comando:
$ sudo docker exec -it iddocontainermongo bash
	Seu terminal ficará dessa forma:


Passo 8: Dentro do terminal do container rodar o seguinte comando:
# cd /bin
Em seguida rodar:
# mongorestore
Caso o comando seja bem sucedido você verá algo como essa saída:


Dessa forma você terá uma cópia do banco de dados da produção rodando localmente na sua máquina.
Caso você precise iniciar novamente os container, repita o Passo 3.


