# VIZU — Localizador de Clientes

App PWA para busca de clientes e traçado de rotas via Google Maps.  
Desenvolvido para uso em campo por equipes de vendas e logística.

---

## Funcionalidades

- Busca de clientes por nome, cidade ou endereco
- Abre rota direta no Google Maps com um clique
- Base de clientes integrada ao Google Sheets (privada)
- Instalável como app no Android (PWA)
- Funciona offline após o primeiro acesso com internet

---

## 🗂️ Estrutura do projeto

```
vizu/
├── index.html        # App principal
├── manifest.json     # Configuracao do PWA
├── sw.js             # Service Worker (cache offline)
├── _headers          # Headers do servidor (Netlify/GitHub Pages)
└── icons/
    ├── icon-192x192.png
    └── icon-512x512.png
```

> **Nota:** O arquivo `clientes.csv` foi removido do repositório e colocados em uma planilha priavada do google sheets.


## Integração com Google Sheets

Os clientes são carregados via **Google Apps Script**, que funciona como uma API privada protegida por chave de acesso.

### Como funciona

1. A lista de clientes fica em uma planilha Google privada
2. Um Apps Script expõe os dados apenas para requisições com a chave correta
3. O app busca os dados na inicialização e salva em cache local para uso offline

### Atualizar a base de clientes

Basta editar a planilha Google diretamente — sem necessidade de atualizar nenhum arquivo do repositório.

### Estrutura esperada na planilha

| nome, endereco, cidade, telefone, lat, lng.


##  Deploy

O app está publicado via GitHub Pages:

🔗 [https://tiozapa.github.io/vizu/](https://tiozapa.github.io/vizu/)

### Como atualizar o app

1. Edite o arquivo desejado localmente
2. Faça upload no GitHub substituindo o arquivo antigo
3. Aguarde 1-2 minutos para o GitHub Pages atualizar

> Quem usa o app instalado **não precisa reinstalar** — as atualizações chegam automaticamente na próxima abertura com internet ou ao atualizar a pagina.

---

## Instalar como app no Android

1. Acesse o link no **Chrome para Android**
2. Toque no menu (⋮) → **"Adicionar à tela inicial"**
3. O app aparece na tela inicial como um app nativo


## Privacidade

- O repositório GitHub é **público**, mas não contém dados de clientes
- Os dados ficam em uma planilha Google **privada**
- A API só responde com os dados mediante **chave de acesso** configurada no código
- O cache offline fica armazenado **localmente no dispositivo** do usuário, sendo possivel pesquisar clientes offline mas sem direcionar para google maps pois o maps  precisa de internet


## Tecnologias utilizadas

- HTML5 + CSS3 + JavaScript (Vanilla)
- [Google Apps Script](https://script.google.com) — API dos clientes
- [Google Sheets](https://sheets.google.com) — Banco de dados
- [Google Maps](https://maps.google.com) — Navegação e rotas
- [GitHub Pages](https://pages.github.com) — Hospedagem
- PWA (Progressive Web App) — Instalação e cache offline
- [CLAUDE IA](https://claude.ai/) - geração de logos icones e o manifest para o PWA
