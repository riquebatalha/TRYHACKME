                                                                                  
# Relatório da sala [Pyramid of Pain](https://tryhackme.com/r/room/pyramidofpainax):
A Pyramid of Pain é uma lista de indicadores de ataque que podem ser usados para detectar as ações dos agressores e, quando negadas, para avaliar a quantidade de "dor" que um agressor causaria.

### 1-HASHES VALUES:
Utilizando o VirusTotal, podemos analisar arquivos suspeitos, domínios, URLS e IPS para detectar malware ou outras violações
Na pergunta em específico, foi nos fornecido um hash de algum aplicativo, e ao analisá-lo, descobrimos que é um Sales_Receipt 5606.xls.

### 2-IP'S ADDRESS:
Conhecer o IP do adversário é de extrema importância. Uma defesa comum é bloquear, dropar, ou dar um deny inbound para o IP no paramêtro ou Firewall externo

### 3-DOMAIN NAME:
Nomes de Domínio podem ser um pouco mais difíceis para o invasor alterar, pois eles provavelmente precisariam comprar o domínio, registrá-lo e modificar os registros DNS. Infelizmente partêm padrões frouxos e fornecem APIs para tornar ainda mais fácil para o invasor alterar o domínio.

### 4-HOSTS ARTIFACTS(Annoying)
Hosts Artifacts são os rastros que os invasores deixam no sistema, como valores de registro, execução de processos suspeitos, padrões de ataque ou IOCs (Indicadores de Comprometimento), arquivos descartados por aplicativos maliciosos ou qualquer coisa exclusiva da ameaça atual.

### 5-NETWORK ARTIFACTS(Annoying)
Network Artifacts são vestígios residuais deixados pelas ações de invasores ou agentes maliciosos em um sistema de computador ou rede.

### 6-TOOLS(CHALLENGING)
Normalmente, são softwares que o adversário traz consigo para executar uma variedade de atividades, como criar backdoors para um canal C2, farejadores de rede e crackers de senhas.

### 7-TTP(TOUGH)
Táticas, Técnicas e Procedimentos – TTPs (TOUGH): A tática fornece a descrição do comportamento, a técnica fornece mais detalhes do comportamento da perspectiva da tática, e o procedimento forneceria detalhes profundos sobre a técnica em si. Exemplo: A Tática é “Descoberta” e a técnica sendo usada é “Varredura de Serviço de Rede”.
  
### <summary>REFERÊNCIAS</summary>

1 - https://gblogs.cisco.com/ca/2020/08/26/the-canadian-bacon-cisco-security-and-the-pyramid-of-pain/ </p>
2 - https://www.sentinelone.com/blog/revisiting-the-pyramid-of-pain-leveraging-edr-data-to-improve-cyber-threat-intelligence/ </p>
3 - https://socradar.io/re-examining-the-pyramid-of-pain-to-use-cyber-threat-intelligence-more-effectively/


<details>
  
<summary>Repostas do Desafio</summary>

1.  **flag{Sales_Receipt 5606.xls}**
2.  **flag{50.87.136.52}**
3.  **flag{craftingalegacy.com}**
4.  **flag{craftingalegacy.comum}**
5.  **flag{Domain name}**
6.  **flag{Punycode attack}**
7.  **flag{https://tryhackme.com/}**
8.  **flag{96.126.101.6}**
9.  **flag{G_jugk.exe}**
</details>

