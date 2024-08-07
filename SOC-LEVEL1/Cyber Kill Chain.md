# Repositório da sala [Cyber Kill Chain](https://tryhackme.com/r/room/cyberkillchainzmt)

## INTRODUÇÃO

Entender a importância do termo "Cyber Kill Chain" e como podemos usá-lo para nos defendermos de ataques de ransomware, violações desegurança e ATP

### 1-RECONNAISSANCE:
Reconhecimento é a discoberta e coleta de informação de sistema e da vítima. A ferramenta OSINT ( Intelligence Open Source ) é a primeira passodo atacante para realizar as fases seguintes do ataque. O invasor precisa estudar a vítima coletando todas as informações disponíveis sobre a empresa e seus funcionários. 
**theHarvester** – além de coletar e-mails, esta ferramenta também é capaz de coletar nomes, subdomínios, IPs e URLs usando múltiplas fontes de dados públicas 
**Hunter.io** - esta é uma ferramenta de busca de e-mail que permitirá obter informações de contato associadas ao domínio
**OSINT Framework** - OSINT Framework fornece a coleção de ferramentas OSINT baseadas em várias categorias

### 2-WEAPONIZATION:
Depois que um invasor reunir informações suficientes sobre seu alvo, ele escolherá um ou vários vetores de ataque para iniciar a intrusão em seu espaço. Um vetor de ataque é um meio para um hacker obter acesso não autorizado aos seus sistemas e informações.

### 3-DELIVERY:
Agora que um hacker obteve acesso aos seus sistemas, ele terá a liberdade necessária para entregar a carga útil de tudo o quetem reservado para você (malware, ransomware, spyware, etc.). Eles criarão programas para todos os tipos de ataques, sejam eles imediatos, retardados ou desencadeados por uma determinada ação (ataque de bomba lógica).

### 4-EXPLOIT:
Depois que a carga pretendida do invasor é entregue, a exploração de um sistema começa, dependendo do tipo de ataque.

### 5-INSTALLATION
Se um hacker vir a oportunidade para ataques futuros, seu próximo passo será instalar um backdoor para acesso consistente aos sistemas do alvo. Dessa forma, eles podem entrar e sair da rede do alvo sem correr o risco de serem detectados ao entrar novamente por meio de outros vetores de ataque.

### 6-COMMAND & CONTROL
Agora que os programas e backdoors estão instalados, um invasor assumirá o controle dos sistemas e executará qualquer ataque que  tenha reservado para você. Quaisquer ações tomadas aqui têm apenas o propósito de manter o controle de sua situação com o alvo, que pode assumir todos os tipos de formas, como plantio de ransomware, spyware ou outros meios de exfiltração de dados no futuro.

### 7-ACTIONS ON OBJECTIVES
Tudo levou a isso. Este é o estágio de execução contínua em que um invasor age contra seu alvo e pode criptografar seus dados para resgate, exfiltrar seus dados para ganho monetário, derrubar sua rede por meio de negação de serviço ou monitorar o comportamento do seu sistema em busca de quaisquer outras aberturas por meio de spyware. para citar apenas alguns resultados potenciais.

### CONCLUSÃO:
O tradicional Cyber Kill Chain foi projetado para proteger o perímetro da rede e proteger contra ameaças de malware. Mas as ameaças à segurança cibernética desenvolveram-se drasticamente hoje em dia e os adversários estão a combinar múltiplos TTP (táticas, técnicas e procedimentos) para atingir o seu objetivo. Os adversários são capazes de derrotar a inteligência de ameaças modificando os hashes dos arquivos e os endereços IP. As empresas de soluções de segurança estão desenvolvendo tecnologias como IA (Inteligência Artificial) e diferentes algoritmos para detectar até mesmo alterações leves e suspeitas.

### REFERÊNCIAS:
1- https://www.varonis.com/blog/what-is-osint </p>
2- https://www.csoonline.com/article/569163/cybercriminal-group-mails-malicious-usb-dongles-to-targeted-companies.html</p>
3- https://www.trustedsec.com/blog/intro-to-macros-and-vba-for-script-kiddies</p>
4- https://www.trellix.com/security-awareness/cybersecurity/what-is-a-zero-day-exploit/

<details>

  <summary>Respostas Desafio</summary>
  
1.  **flags{OSINT framework}**
2.  **flag{email harvesting}**
3.  **flag{Macro}**
4.  **flag{Watering hole attack}**
5.  **flag{Zero Day}**
6.  **flag{Timestomping}**
7.  **flag{Web shell}**
8.  **flag{DNS Tunneling}**
9.  **flag{Shadow Copy}**
10.  **flag{THM{7HR347_1N73L_12_4w35om3}}**</details>

