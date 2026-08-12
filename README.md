# Interview Room

Treino de entrevistas de emprego em inglês, nível executivo. App estático (um único HTML), pronto para publicar e instalar como aplicativo no iPhone (PWA).

```
index.html            o app completo
manifest.webmanifest  configuração do PWA
sw.js                 service worker (funciona offline após a primeira visita)
robots.txt            bloqueia indexação por buscadores
apple-touch-icon.png  ícone da tela de início do iPhone
icons/                ícones 192 e 512
```

O arquivo já vem com `noindex` e `robots.txt`, então o conteúdo não entra no Google nem no Bing em nenhuma das opções abaixo.

---

## Antes de escolher: o que "privado" significa aqui

O conteúdo pessoal (trajetória, números, respostas) está **dentro do index.html**, que é justamente o arquivo que o navegador precisa baixar. Isso cria uma distinção que decide a escolha da hospedagem:

- **Repositório privado** esconde o código-fonte de quem navega pelo GitHub.
- **Site privado** exige login para abrir a página.

No GitHub Pages, mesmo com repositório privado, **o site publicado continua público** na internet. Quem tiver a URL abre e lê tudo. Ou seja: repositório privado no GitHub protege pouco neste caso específico, porque o que você quer proteger é exatamente o que o site entrega.

| Opção | Repositório | Site | Custo |
|---|---|---|---|
| A. Cloudflare Pages + Access | privado (ou sem repositório) | **exige login por e-mail** | gratuito |
| B. GitHub Pages, repositório público | público | público | gratuito |
| C. GitHub Pages, repositório privado | privado | **público mesmo assim** | GitHub Pro, pago |

Se privacidade é requisito, a opção A é a única que entrega. As instruções das duas primeiras estão abaixo.

---

## Opção A (recomendada): Cloudflare Pages com login por e-mail

Resultado: o app fica em uma URL sua e, ao abrir, pede seu e-mail e um PIN enviado na hora. Só você entra. Gratuito no plano Zero Trust (até 50 usuários).

**1. Publicar o site**

1. Crie conta em `dash.cloudflare.com`.
2. No menu, vá em **Workers & Pages > Create > Pages > Upload assets**.
3. Dê um nome ao projeto (ex.: `interview-room`), arraste **todos os arquivos desta pasta** (mantendo a pasta `icons`) e publique.
4. O site nasce em `https://interview-room.pages.dev`. Nesse momento ele ainda é público, siga para o passo 2.

**2. Trancar com login**

1. No menu lateral, abra **Zero Trust** (na primeira vez ele pede para escolher um plano: selecione o **Free**).
2. Vá em **Access > Applications > Add an application > Self-hosted**.
3. Em domínio, informe o domínio do seu projeto (`interview-room.pages.dev`).
4. Crie uma política: nome "Só eu", ação **Allow**, regra **Emails** com o seu e-mail.
5. Salve. Em provedores de identidade, mantenha **One-time PIN** ativado.

Pronto. Ao abrir a URL, a Cloudflare pede seu e-mail, envia um PIN e libera o acesso. A sessão fica ativa por dias, então na prática você digita o PIN raramente.

**Se preferir versionar no GitHub**: crie o repositório **privado**, suba os arquivos e, no passo 1, escolha **Connect to Git** em vez de Upload assets. O repositório continua privado e o login da Cloudflare protege o site.

---

## Opção B: GitHub Pages (simples, mas o conteúdo fica público)

Só faz sentido se você aceitar que qualquer pessoa com a URL leia suas respostas.

1. Crie um repositório (ex.: `interview-room`) e envie os arquivos na raiz (**Add file > Upload files**).
2. Em **Settings > Pages**, escolha **Deploy from a branch**, branch `main`, pasta `/ (root)`, e salve.
3. Em 1 ou 2 minutos o site estará em `https://SEU-USUARIO.github.io/interview-room/`.

Com repositório privado, o GitHub Pages exige o plano **Pro** (pago) e ainda assim o site publicado continua público. É por isso que essa rota não resolve o requisito de privacidade.

---

## Instalar no iPhone (Safari ou Chrome)

1. Abra a URL do app no Safari ou no Chrome.
2. Toque em **Compartilhar** (quadrado com seta) e em **Adicionar à Tela de Início**.
3. O app abre em tela cheia, com ícone próprio.

Se você usou a opção A, o login da Cloudflare aparece na primeira abertura e depois fica lembrado.

Progresso e chave da API são salvos por navegador: se configurar no Safari e depois usar o Chrome, refaça a configuração da chave.

---

## Ativar a IA (feedback e simulação)

Fora do claude.ai, esses recursos precisam da sua chave da API Anthropic:

1. Crie uma chave em **console.anthropic.com > API Keys**. A conta da API tem cobrança própria; cada feedback ou entrevista simulada custa centavos no modelo Sonnet.
2. No app, toque em **⚙** no topo, cole a chave e salve.

A chave fica gravada **apenas no navegador do seu aparelho** e nunca vai para o repositório. Ainda assim, não divulgue a URL: quem abrir o app não vê sua chave, mas na opção B qualquer pessoa com o endereço lê seu conteúdo.

Sem chave, todo o resto funciona: perguntas, estratégias, respostas modelo, áudio, ditado, cronômetro, kit de improviso e progresso.

---

## Voz no iPhone

- **Ouvir perguntas e modelos (🔊)**: funciona no Safari, no Chrome e no app instalado.
- **Ditado pelo botão 🎙 do app**: funciona **apenas no Safari**. A Apple não libera o reconhecimento de voz da web para outros navegadores no iPhone, então no Chrome o app detecta isso e mostra a alternativa.
- **Ditado no Chrome (ou em qualquer navegador)**: use o **microfone do próprio teclado do iPhone**. O texto entra na caixa de resposta e o cronômetro conta normalmente. Para ditar em inglês, adicione o teclado Inglês (EUA) em Ajustes > Geral > Teclado > Teclados e alterne com a tecla do globo. Requer **Ativar Ditado** nos mesmos ajustes.
- No Safari, o ditado costuma parar sozinho em pausas de fala: é normal, o texto fica preservado, basta tocar no microfone de novo.
- A primeira reprodução de áudio precisa de um toque seu, por regra do iOS.

## Offline

Após a primeira visita, o app abre sem internet (estudo, prática, cronômetro e kit). Feedback e simulação exigem conexão.
