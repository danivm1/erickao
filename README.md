## BACKUP DO MONGO - UFPR CONVIDA - ESSE MÉTODO SÓ FUNCIONA PARA VERSÕES ABAIXO DO MONGODB 4.4
<code>$sudo docker container ls para ver as informações dos containers e pegar o CONTAINER_ID</code>
<code>$sudo docker exec -it CONTAINER_ID bash - ABRE UM TERMINAL DENTRO DO CONTAINER</code>
<code>$cd bin</code>
<code>$mongodump</code>
<code>$cd dump</code>
<code>checar se criou os arquivos dentro da pasta dump/convida</code>
<code>$exit para sair do terminal do container</code>
<code>$sudo docker cp IDDOCONTAINER:/bin/dump/convida (caminho do diretório dump)</code>
<code>/home/convida/backup/pasta-com-o-dia-do-backup (caminho de destino)</code>
<code>$git add <pasta-do-backup></code>
<code>$git commit -m “dia do backup”</code>
<code>$git push</code>