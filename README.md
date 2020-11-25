## BACKUP DO MONGO - UFPR CONVIDA - ESSE MÉTODO SÓ FUNCIONA PARA VERSÕES ABAIXO DO MONGODB 4.4
<code>$sudo docker ps</code> para ver as informações dos containers e pegar o CONTAINER_ID  
<code>$sudo docker exec -it CONTAINER_ID bash</code> - ABRE UM TERMINAL DENTRO DO CONTAINER  
<code>$cd bin</code>  
<code>$mongodump</code>  
<code>$cd dump</code>  
<ul><li>checar se criou os arquivos dentro da pasta dump/convida</li></ul>  
<code>$exit</code> para sair do terminal do container</br>
<code>$sudo docker cp IDDOCONTAINER:/bin/dump/convida</code> (caminho do diretório dump)  
<code>/home/convida/backup/pasta-com-o-dia-do-backup</code> (caminho de destino)  
<code>$git add pasta-do-backup</code>  
<code>$git commit -m “dia do backup”</code>  
<code>$git push</code>  