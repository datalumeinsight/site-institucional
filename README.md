# Site institucional: Datalume Insight

Site de **https://datalumeinsight.com.br**, da DATALUME INSIGHT LTDA (CNPJ 60.778.624/0001-66).
É um site estático em HTML/CSS, sem build. O deploy acontece no Netlify a cada push na branch `main`.

```
public/
├── index.html          → Home: Sobre, Serviços, Como trabalhamos, Dados da empresa, Contato
├── privacidade.html    → Política de Privacidade (LGPD)
├── termos.html         → Termos de Uso
├── robots.txt / sitemap.xml
└── assets/ (styles.css, logo.svg)
netlify.toml            → configuração do Netlify (pasta publicada, redirect www, headers)
```

## Editar e publicar

1. Edite os arquivos em `public/`.
2. Para visualizar localmente, rode `python -m http.server 8000 --directory public` e abra http://localhost:8000.
3. Faça commit e push na `main`. O Netlify publica sozinho em cerca de 1 minuto.

> Dados da empresa (e-mail, telefone, endereço) aparecem nos 3 HTML e no JSON-LD do `index.html`.
> Quando algum mudar, use buscar e substituir em `public/`.

---

## Configuração inicial (uma vez)

### 1. Domínio no registro.br
Registre **datalumeinsight.com.br** com titular **CNPJ 60.778.624/0001-66**, não CPF.

### 2. Conectar o Netlify ao GitHub
1. Entre em https://app.netlify.com usando **"Sign up with GitHub"** com a conta `datalumeinsightltda-cmd`.
2. Clique em **Add new site → Import an existing project → GitHub**.
3. Autorize o Netlify e selecione o repositório **site-institucional**.
4. Deixe tudo como está. O `netlify.toml` já define a pasta `public`. Clique em **Deploy**.

### 3. Domínio próprio no Netlify
1. Vá em **Domain management → Add a domain** e digite `datalumeinsight.com.br` (adicione também o `www`).
2. No registro.br, abra o domínio, vá em **DNS → Editar zona** e crie os registros que o Netlify indicar:
   - `A` para `datalumeinsight.com.br` apontando para o IP do Netlify (hoje `75.2.60.5`)
   - `CNAME` para `www` apontando para `<seu-site>.netlify.app`
3. Espere a propagação. O HTTPS (Let's Encrypt) é ativado sozinho.

### 4. E-mail no domínio (recomendado)
Hoje o site usa `contato@datalumeapp.com`, que é de outro domínio. Para o D-U-N-S e para a Apple, prefira
`contato@datalumeinsight.com.br` (Zoho Mail, Google Workspace ou Microsoft 365) e atualize os HTML.

---

## Pedido do D-U-N-S

- **Apple Developer:** https://developer.apple.com/enroll/duns-lookup/
- **Google Play ou outros:** https://www.dnb.com/duns/get-a-duns.html

| Campo        | Valor                          |
|--------------|--------------------------------|
| Legal name   | DATALUME INSIGHT LTDA          |
| Address      | Rua Pais Leme, 215, Conj. 1713 |
| District     | Pinheiros                      |
| City / State | São Paulo / SP                 |
| ZIP          | 05424-150                      |
| Country      | Brazil                         |
| Phone        | +55 61 98666-5795              |
| Website      | https://datalumeinsight.com.br |
| CNPJ         | 60.778.624/0001-66             |

### Checklist
- [ ] Site abrindo em https://datalumeinsight.com.br (HTTPS)
- [ ] Domínio registrado no CNPJ
- [ ] Razão social e endereço idênticos ao Cartão CNPJ (**Rua Pais Leme**)
- [ ] Telefone atendendo, porque a D&B pode ligar para verificar
- [ ] E-mail funcionando, de preferência @datalumeinsight.com.br
