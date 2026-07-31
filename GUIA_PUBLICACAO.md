# Guia de Publicação — Site JM Engenharia (custo zero)

Da etapa 1 até o site no ar em **https://jm-engenharia.com**, usando GitHub + Vercel (planos gratuitos) e VS Code.

---

## Etapa 1 — Preparar o projeto no seu computador

1. Copie a pasta `jm-engenharia-site` para um local definitivo (ex.: `Documentos\Projetos\jm-engenharia-site`).
2. Abra a pasta no **VS Code** (Arquivo → Abrir Pasta).
3. Para visualizar localmente: clique com o botão direito em `index.html` → "Open with Live Server" (instale a extensão **Live Server** se não tiver) ou simplesmente abra o `index.html` no navegador.

Estrutura do projeto:

```
jm-engenharia-site/
├── index.html        ← site completo (one-page)
├── obrigado.html     ← página de confirmação do formulário
├── GUIA_PUBLICACAO.md
├── README.md
└── assets/
    ├── logo-jm.png
    ├── logo-jm-branco.png
    ├── logo-engrenagem.png
    └── favicon.png
```

---

## Etapa 2 — Criar o repositório no GitHub

1. Acesse https://github.com e faça login (ou crie a conta gratuita).
2. Clique em **New repository**.
3. Nome: `jm-engenharia-site` · Visibilidade: **Private** (recomendado) · Não marque "Add README".
4. Clique em **Create repository**.

### Enviar os arquivos

**Opção A — Sem instalar nada (mais fácil):**
na página do repositório recém-criado, clique em "uploading an existing file", arraste TODOS os arquivos e a pasta `assets`, e clique em **Commit changes**.

**Opção B — Pelo terminal do VS Code (requer Git instalado — https://git-scm.com):**

```bash
cd caminho/para/jm-engenharia-site
git init
git add .
git commit -m "Site JM Engenharia - versão inicial"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/jm-engenharia-site.git
git push -u origin main
```

---

## Etapa 3 — Publicar na Vercel (grátis)

1. Acesse https://vercel.com e clique em **Sign Up → Continue with GitHub** (isso já conecta as duas contas).
2. No painel, clique em **Add New… → Project**.
3. Localize `jm-engenharia-site` na lista e clique em **Import**.
4. Não altere nada (Framework Preset: **Other**; sem build command — é um site estático).
5. Clique em **Deploy**. Em menos de 1 minuto o site estará no ar em um endereço tipo `jm-engenharia-site.vercel.app`.

> A partir de agora, **todo commit no GitHub publica automaticamente** uma nova versão do site.

---

## Etapa 4 — Conectar o domínio jm-engenharia.com

1. Na Vercel, abra o projeto → aba **Settings → Domains**.
2. Digite `jm-engenharia.com` e clique em **Add** (adicione também `www.jm-engenharia.com`; a Vercel redireciona um para o outro).
3. A Vercel mostrará os registros DNS necessários. No painel do provedor onde você registrou o domínio, crie:

| Tipo  | Nome | Valor                  |
|-------|------|------------------------|
| A     | @    | `76.76.21.21`          |
| CNAME | www  | `cname.vercel-dns.com` |

> Use exatamente os valores que a tela da Vercel exibir (podem variar). A propagação leva de minutos até ~24 h. O certificado **HTTPS é gerado automaticamente** pela Vercel, sem custo.

4. Quando o status dos domínios ficar "Valid Configuration", o site estará em https://jm-engenharia.com com cadeado de segurança.

---

## Etapa 5 — Ativar o formulário de contato (FormSubmit, grátis)

O formulário envia as mensagens para **contato@jm-engenharia.com** sem precisar de servidor.

1. Com o site já no ar, abra-o e envie **uma mensagem de teste** pelo formulário.
2. O FormSubmit enviará um e-mail de confirmação para contato@jm-engenharia.com — clique em **Activate Form** (uma única vez).
3. Pronto: todas as próximas mensagens chegarão direto na caixa de entrada, formatadas em tabela.

---

## Etapa 6 — Adicionar o vídeo institucional (YouTube)

1. Suba o arquivo `VÍDEO_DETALHADO_JM_ENG_CONSULT_AMBIENTAL.mp4` no YouTube (canal da JM; pode marcar como "Não listado" se preferir que só apareça no site).
2. Copie o ID do vídeo — é o trecho após `watch?v=` na URL (ex.: em `youtube.com/watch?v=ABC123xyz`, o ID é `ABC123xyz`).
3. No `index.html`, localize a linha (quase no fim do arquivo):

```js
const YOUTUBE_ID = "";
```

4. Cole o ID entre as aspas: `const YOUTUBE_ID = "ABC123xyz";`
5. Salve, faça commit e push (ou re-upload no GitHub). A seção de vídeo aparecerá automaticamente no site.

---

## Etapa 7 — Manutenção e atualizações

- **Editar textos/serviços:** altere o `index.html` no VS Code, salve e envie ao GitHub (commit + push ou upload). A Vercel republica sozinha.
- **Métricas de visitantes:** na Vercel, aba **Analytics** do projeto (plano gratuito já inclui o essencial).
- **E-mail profissional:** como você já tem o domínio, pode ativar caixa de e-mail no seu provedor/registrador para usar contato@jm-engenharia.com como remetente real.

### Evoluções futuras (opcionais, quando fizer sentido)

- **Supabase (grátis):** guardar leads do formulário em banco PostgreSQL com painel de consulta.
- **Blog/portfólio de obras:** transformar em projeto Next.js mantendo o mesmo visual — a Vercel continua hospedando de graça.

---

## Resumo de custos

| Item                     | Custo |
|--------------------------|-------|
| Hospedagem (Vercel)      | R$ 0  |
| Código no GitHub         | R$ 0  |
| Certificado HTTPS        | R$ 0  |
| Formulário (FormSubmit)  | R$ 0  |
| Vídeo (YouTube)          | R$ 0  |
| Domínio jm-engenharia.com| já adquirido |
