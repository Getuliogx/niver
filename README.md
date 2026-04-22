# Birthday Live Alert

Projeto pronto para cadastrar aniversários via comando no chat e mostrar alerta na live.

## O que está incluído

- `backend/` → API Node.js + SQLite + overlay + painel admin
- `streamelements-widget/` → arquivos para colar no Custom Widget do StreamElements

## Comando do chat na Twitch (StreamElements)

Crie um comando custom chamado `!niver` com esta resposta:

```text
$(customapi https://SEU-BACKEND.com/api/register?user=$(user)&date=$(1)&time=$(2))
```

Exemplo no chat:

```text
!niver 12/08 09:30
```

Resposta esperada:

```text
@getulio aniversário salvo para 12/08 às 09:30.
```

## Como rodar localmente

1. Entre em `backend/`
2. Copie `.env.example` para `.env`
3. Troque `ADMIN_KEY`
4. Rode:

```bash
npm install
npm start
```

## URLs

- Overlay simples: `http://localhost:3000/overlay`
- Painel admin: `http://localhost:3000/admin?key=SUA_CHAVE`
- Health: `http://localhost:3000/health`

## StreamElements Custom Widget

Cole o conteúdo de:

- `streamelements-widget/widget.html` no HTML
- `streamelements-widget/widget.css` no CSS
- `streamelements-widget/widget.js` no JS
- `streamelements-widget/widget.json` em Fields

Depois ajuste `API Base URL` para a URL do seu backend.

## Onde o GitHub entra

Use o GitHub para:

- guardar o código
- versionar tudo
- conectar deploy no Render/Railway/Fly.io

GitHub Pages sozinho não roda a API Node, então ele não substitui o backend.

## Como funciona

- viewer manda `!niver DD/MM HH:MM`
- StreamElements chama `/api/register`
- a API salva no SQLite
- o overlay consulta `/api/overlay/alerts`
- quando a hora chega, o aviso aparece uma vez naquele ano

## Kick

A parte visual funciona igual no Kick usando browser source/URL do overlay.

Para ler comando do chat na Kick, o ideal é usar um bot próprio ou integração separada.
