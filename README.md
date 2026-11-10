# Chatbot de suporte para restaurantes · demo do fluxo no n8n

Página interativa que mostra o workflow **"Chatbot CS Restô"** (n8n) funcionando:
a pessoa manda uma dúvida, os nós acendem um por um e o chamado aparece na "planilha".

## O que tem em cada arquivo

| Arquivo | Para que serve | Pode mexer? |
|---|---|---|
| `css/tema.css` | Fontes, cores, cantos, espaços. **O visual inteiro sai daqui.** | Sim, à vontade |
| `css/estilo.css` | Organização da página (colunas, cartões, balões) | Sim |
| `index.html` | Textos da página (título, descrição, rodapé) e link das fontes | Sim, nos textos |
| `js/base-de-conhecimento.js` | As perguntas e respostas do bot (a aba FAQ) | Sim, para incluir perguntas |
| `js/fluxo.js` | O funcionamento do fluxo, igual ao n8n | **Não precisa** |

Trocou a fonte? Troque em `css/tema.css` **e** no link do Google Fonts dentro do `index.html`.

## Como o bot se comporta

- **Pergunta que está na base** → responde, categoriza e registra como *Resolvido*.
- **Pergunta fora da base** → "Não encontrei essa informação na base de conhecimento. Vou encaminhar para o suporte." e registra como *Encaminhado*, categoria *Suporte*.
- **3 ou mais chamados na mesma categoria** → a resposta ganha a "💡 Dica do time de CS".
- **Saudação ou conversa solta** ("oi", "bom dia, tudo bem?", "quero falar com alguém") → resposta pronta pedindo a dúvida, **sem abrir chamado**. Se a pessoa continuar só conversando: "Preciso saber sua dúvida, por favor. Escolha uma das opções ou digite abaixo."

As respostas desta demo são **simuladas**: a página procura a pergunta mais parecida na base,
sem chamar a IA. Assim é grátis, não precisa de chave e nunca sai do ar.

## Testar no computador

Abra o `index.html` no navegador (dois cliques). Não precisa instalar nada.

## Publicar na Vercel

1. Crie um repositório no GitHub e suba esta pasta inteira.
2. Em vercel.com, clique em **Add New → Project** e escolha o repositório.
3. Em *Framework Preset*, deixe **Other**. Não precisa de comando de build.
4. Clique em **Deploy**. O link público sai no final.

Toda vez que você mandar uma mudança pro GitHub, a Vercel atualiza o site sozinha.

## Se for refazer no n8n de verdade

O nó **"Filtra Saudação"** é novo e não existe no fluxo original. No n8n, ele seria um nó *Code*
ou *IF* logo depois do "When chat message received": se a mensagem for só cumprimento,
devolve a resposta pronta e encerra, sem passar pela planilha nem pela IA.
