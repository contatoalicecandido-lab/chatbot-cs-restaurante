# atendimento. · chatbot de suporte com IA (fluxo no n8n)

Demo interativa de um chatbot de suporte feito no n8n. A pessoa escreve uma dúvida no chat e a mensagem corre pelo fluxo, nó por nó:

1. **Chat** recebe a pergunta.
2. **Google Sheets** lê a base de perguntas e respostas (aba FAQ).
3. **Code** monta o prompt.
4. **HTTP Request · Groq (LLaMA)** responde usando só o que está na base.
5. **Code** lê a resposta e a categoria.
6. **Google Sheets** registra o chamado (aba Chamados).
7. **Google Sheets** busca o histórico da categoria.
8. **Code** conta as repetições.
9. **IF** confere se passou do limite definido pela equipe.
10. **Gmail** avisa a equipe para criar um material de apoio sobre o assunto.

Cumprimentos e conversa solta ("bom dia", "obrigada") recebem resposta pronta e não viram chamado.

Na página dá para clicar em cada nó e ver o que entrou e o que saiu, arrastar os nós, mudar o limite do alerta e simular movimento no painel.

Nesta demonstração a busca na base roda no navegador; no fluxo real quem responde é a IA.

**Feito por Alice Cândido** · Customer Success e automação · n8n · Google Sheets · Groq · Gmail
