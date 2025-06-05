Checklist de mapeamento de uma aplicação Web :

robots.txt
Consulta de Whois
Coleta de subdominios (se aplicavel)
ver codigo fonte
inpecionar posts / gets (como a aplicacao se comporta / encontrar urls)
tentar uma lista de dorks para o site
Dig ou nslookup para verificar endereços de dns
Mapear dns
dns dumpster e securitytrais para mapear subdominios ips e endereços de dns
view dns info, mostra historico de dns
Scan de IPv6 : masscan -p80,443 --rate 10000 ::/0
curl na aplicação , verificar os headers, que podem revelar o backend real
sitemap com burp suite
mapear pontos de vulnerabilidade (apis e diretorios)
nmap e mapeamento de rede
