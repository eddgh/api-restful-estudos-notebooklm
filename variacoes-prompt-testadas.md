[&#9664;](/README.md "Voltar")
## Variações de prompts que testei:

### Respostas obtidas e dificuldades encontradas para extrair a melhor resposta da IA (troubleshooting)

#### Autor:<br>
Uma dificuldade que encontrei foi entender a lógica que a IA do NotebookLM estava utlizando pra montar os Quizzes, flashcards e todo o material do Estudio do Notebook. Acontece que inicialmente o exemplo do restaurante pra explicar de forma quase lúdica o que seria uma API tudo bem, mas depois comecei a notar que todo o restante do material a IA levava pra esse lado de restaurante, cozinha, colheres etc, e isso dificultava bastante o aprendizado porque deixava de ser uma coisa mais tecnica e passava a ser muito mista e confusa, então testei esse novo prompt:

>##### Prompt testado:<br>

"Pra te falar a verdade em alguns quizzes ou flahscards achei as abordagens comparando REST ou RESTful com a cozinha muito massivas e sem liga, porque essa comparação é boa e relevante apenas inicialmente e de maneira quase superficial, explicando todo o contexto da API de forma lúdica e ate serviria pra um mapa mental, mas quando voce desmembra isso em perguntas separadas seja em flascards ou quizzes fica totalmente inadequado. Acho que os quizzes e flashcards precisam abordar os temas e elaborar as perguntas de forma mais técnica."

>Resposta da IA:

Você tem toda a razão! A analogia do garçom e da cozinha cumpre um papel lúdico apenas para a introdução inicial do conceito de API. Quando desmembrada em perguntas de testes e flashcards, essa metáfora esvazia o rigor técnico e não prepara você para problemas reais de arquitetura e desenvolvimento de software.

Para fixar o conhecimento de forma profissional, o que você precisa dominar são os mecanismos reais da Web: semântica de verbos e status codes HTTP, arquitetura stateless, validação de schemas, payloads JSON, middlewares, tratamento de exceções, headers e códigos em Node.js/Express.

A partir de agora, todas as nossas questões, testes e flashcards adotarão uma abordagem 100% técnica e focada em engenharia de software.

Exemplo do Novo Padrão Técnico

Como era (evitar): "O que o garçom faz se o pedido da mesa vier sem o número do prato?"

Como será a partir de agora (Padrão Técnico):

Pergunta: "Em uma rota POST /pedidos, se o cliente enviar um payload JSON sem um campo obrigatório, qual Status Code HTTP deve ser retornado no middleware de validação para indicar erro na entrada de dados?"Resposta: 400 Bad Request, acompanhado de um corpo JSON detalhando os campos ausentes ou inválidos.

[&#x1F51D;](#)