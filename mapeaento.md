Checklist de mapeamento de uma aplicação Web :

robots.txt </br>
Consulta de Whois </br>
Coleta de subdominios (se aplicavel)</br>
ver codigo fonte</br>
inpecionar posts / gets (como a aplicacao se comporta / encontrar urls)</br>
tentar uma lista de dorks para o site</br>
Dig ou nslookup para verificar endereços de dns</br>
Mapear dns</br>
dns dumpster e securitytrais para mapear subdominios ips e endereços de dns</br>
view dns info, mostra historico de dns</br>
Scan de IPv6 : masscan -p80,443 --rate 10000 ::/0</br>
curl na aplicação , verificar os headers, que podem revelar o backend real</br>
sitemap com burp suite</br>
mapear pontos de vulnerabilidade (apis e diretorios)</br>
nmap e mapeamento de rede</br>

--------------------------------------------

Tentar metodos diferentes em endpoints / mesmo que apresentem 403 para diferentes metodos 
