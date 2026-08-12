# Interview Room

Treino de entrevistas de emprego em inglês, nível executivo. App estático (HTML único), pronto para GitHub Pages e para instalação como aplicativo no iPhone (PWA).

## Arquivos

```
index.html            o app completo
manifest.webmanifest  configuração do PWA
sw.js                 service worker (funciona offline após a primeira visita)
apple-touch-icon.png  ícone da tela de início do iPhone
icons/                ícones 192 e 512
```

## Publicar no GitHub Pages

1. Crie um repositório no GitHub (ex.: `interview-room`). Pode ser público: nenhuma chave ou dado pessoal fica no código.
2. Envie todos os arquivos desta pasta para a raiz do repositório (Add file > Upload files).
3. Em **Settings > Pages**, escolha **Deploy from a branch**, branch `main`, pasta `/ (root)` e salve.
4. Em 1 a 2 minutos o app estará em `https://SEU-USUARIO.github.io/interview-room/`.

## Instalar no iPhone

1. Abra a URL acima no **Safari** (precisa ser o Safari).
2. Toque em **Compartilhar** (quadrado com seta) e depois em **Adicionar à Tela de Início**.
3. O app abre em tela cheia, com ícone próprio, como um aplicativo.

## Ativar a IA (feedback e simulação)

Fora do claude.ai, os recursos de IA precisam da sua própria chave da API Anthropic:

1. Crie uma chave em **console.anthropic.com > API Keys** (a conta da API tem cobrança própria; cada feedback ou entrevista simulada custa centavos usando o modelo Sonnet).
2. No app, toque em **⚙** no topo, cole a chave e salve.

A chave fica gravada **apenas no navegador do seu aparelho** (localStorage). Ela nunca vai para o repositório nem para o GitHub. Por isso mesmo, trate este app como pessoal: não divulgue a URL como serviço para terceiros usarem com a sua chave, e nunca cole a chave em nenhum arquivo do repositório.

Sem chave, tudo o mais funciona normalmente: perguntas, estratégias, respostas modelo, áudio das perguntas e modelos, ditado, cronômetro, kit de improviso e progresso.

## Notas sobre voz no iPhone

- **Ouvir perguntas e modelos (🔊)**: funciona no Safari e no app instalado.
- **Ditado (🎙)**: usa o reconhecimento de voz do iOS. Requer Ajustes > Geral > Teclado > **Ativar Ditado**. No iOS o ditado costuma parar sozinho em pausas de fala: é normal, o texto fica preservado, basta tocar no microfone de novo para continuar. Se o microfone não for liberado no app instalado, use pelo Safari, onde a permissão é pedida normalmente.
- A primeira reprodução de áudio precisa de um toque seu (regra do iOS), por isso nada toca sozinho ao abrir.

## Offline

Depois da primeira visita, o app abre sem internet (estudo, prática, cronômetro e kit). Feedback e simulação exigem internet, pois falam com a API.
