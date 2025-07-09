# 🌐 Web Application Mapping Checklist

Um guia prático para mapeamento técnico de uma aplicação web durante análises de segurança ou reconhecimento passivo/ativo.

---

## 📑 Sumário

- [1. Informações Iniciais](#-1-informações-iniciais)
- [2. Análise de Tráfego e Interações](#-2-análise-de-tráfego-e-interações)
- [3. Pesquisas Avançadas (Google Dorks)](#-3-pesquisas-avançadas-google-dorks)
- [4. DNS Intelligence](#-4-dns-intelligence)
- [5. Revisão de Headers e Infraestrutura](#-5-revisão-de-headers-e-infraestrutura)
- [6. Histórico e Sitemap](#-6-histórico-e-sitemap)
- [7. Mapeamento de Rede e Vulnerabilidades](#-7-mapeamento-de-rede-e-vulnerabilidades)
- [Recomendações Adicionais](#-recomendações-adicionais)

---

## 🔍 1. Informações Iniciais

- Verificar o arquivo `robots.txt`  
  Exemplo: `https://dominio.com/robots.txt`

- Realizar consulta WHOIS  
  Ferramentas:
  - [whois.domaintools.com](https://whois.domaintools.com)
  - [whois.icann.org](https://whois.icann.org)

- Coletar subdomínios (se aplicável)  
  Ferramentas recomendadas:
  - Sublist3r
  - assetfinder
  - findomain

- Revisar código-fonte da página inicial e páginas importantes  
  Procurar por:
  - Comentários
  - URLs ocultas
  - Chaves expostas
  - Endpoints sensíveis

---

## 📡 2. Análise de Tráfego e Interações

- Inspecionar requisições GET/POST no DevTools (aba **Network**)  
- Entender os fluxos da aplicação  
- Identificar endpoints relevantes  

### Burp Suite:
- Ativar o proxy e navegar pela aplicação  
- Registrar endpoints automaticamente

### Testar métodos HTTP (mesmo com resposta 403):

```bash
curl -X OPTIONS http://target.com/endpoint
curl -X PUT http://target.com/endpoint
```

---

## 🔎 3. Pesquisas Avançadas (Google Dorks)

Criar lista personalizada de dorks para o domínio-alvo:

```text
site:dominio.com inurl:admin
site:dominio.com filetype:log
site:dominio.com intitle:"index of"
```

---

## 🧠 4. DNS Intelligence

- Fazer `dig` e `nslookup` para obter informações de DNS:

```bash
dig dominio.com
nslookup dominio.com
```

- Mapear registros DNS:
  - A, AAAA, MX, TXT, CNAME, NS

### Ferramentas online:
- [DNS Dumpster](https://dnsdumpster.com)
- [SecurityTrails](https://securitytrails.com/dns-trails)

### Histórico de DNS:
- [ViewDNS.info](https://viewdns.info/)

### Scan IPv6 (opcional):

```bash
masscan -p80,443 --rate 10000 ::/0
```

---

## 🕵️‍♂️ 5. Revisão de Headers e Infraestrutura

Verificar headers da aplicação com `curl`:

```bash
curl -I https://dominio.com
```

Buscar por informações como:
- `Server`
- `X-Powered-By`
- `Set-Cookie`
- Possível uso de proxies ou WAFs

---

## 🗺️ 6. Histórico e Sitemap

- Verificar arquivos arquivados na **Wayback Machine**:

```text
https://web.archive.org/cdx/search/cdx?url=*.dominio.com/*&output=text&fl=original&collapse=urlkey
```

> Substituir `dominio.com` pelo alvo real.

- Gerar sitemap via **Burp Suite** (navegando com o proxy ativo)

---

## 🔥 7. Mapeamento de Rede e Vulnerabilidades

### Escaneamento com Nmap:

```bash
nmap -sV -sC -p- dominio.com
```

### Identificar pontos sensíveis:
- APIs públicas (`/api/v1/`)
- Pastas de upload (`/uploads/`)
- Painéis administrativos (`/admin`, `/dashboard`)
- Arquivos sensíveis:
  - `/config.php`
  - `.env`
  - `.git/config`

---

## 🛠️ Recomendações Adicionais

- Use proxies e **user-agents** variados para evitar bloqueios  
- Sempre respeite a política de segurança do alvo (`robots.txt`, `security.txt`)  
- Mantenha **logs detalhados** das etapas realizadas para documentação

---

> 🔐 **Disclaimer:** Este checklist é para fins educacionais. Realize atividades de análise apenas com autorização explícita do proprietário do sistema.
