[&#9664;](/README.md "Voltar")
# Entrega Final - Estudo Guiado


### O seu Guia de Estudos passo a passo
<br>

Aqui está o seu Miniguia de Estudos (com Foco na AÇÃO) para todos os 11 Módulos. Ele foi estruturado como um roteiro prático do que estudar, o que praticar e como validar o seu aprendizado em cada etapa:<br><br>

>📌 Módulo 01: A Base Conceitual e a Teoria do Garçom (REST / RESTful)

Passo 1: Entenda a analogia (Teoria): Estude a função da API como o "garçom" intermediário entre o cliente (mesa) e o banco de dados (cozinha).

Passo 2: Domine os princípios (REST): Leia sobre os conceitos de desacoplamento cliente-servidor e comunicação stateless.

Passo 3: Prática (Mão na massa): Monte um servidor Express básico em Node.js com rotas simuladas em memória.

Passo 4: Valide o entendimento: Faça requisições com cURL ou Postman e diferencie na prática o conceito de REST (regras) de RESTful (a API que aplica as regras).<br><br>

>📌 Módulo 02: O Protocolo HTTP, Verbos e Operações CRUD

Passo 1: Entenda a base (HTTP): Estude a estrutura das mensagens HTTP (Request, Response, Headers e Body).

Passo 2: Mapeie o CRUD aos verbos: Associe GET a Read, POST a Create, PUT a Update total, PATCH a Update parcial e DELETE a Delete.

Passo 3: Prática (Mão na massa): Crie rotas completas de CRUD para gerenciar um recurso estático (ex.: produtos) em um array.

Passo 4: Valide os Status Codes: Certifique-se de que cada verbo retorne seu status semântico ideal (200 OK, 201 Created e 204 No Content).<br><br>

>📌 Módulo 03: Construindo Sua Primeira API com Express (Node.js)

Passo 1: Configure o ambiente: Crie o arquivo package.json, ative o suporte a ES Modules e instale o framework Express.

Passo 2: Configure os middlewares base: Injeta app.use(express.json()) para permitir a leitura de objetos JSON no corpo da requisição.

Passo 3: Prática (Mão na massa): Crie um endpoint de checagem de saúde (GET /) e rotas para cadastro e consulta de registros.

Passo 4: Valide a execução: Execute o servidor com node --watch server.js e valide se a API processa e responde payloads em JSON corretamente.<br><br>

>📌 Módulo 04: Gerenciamento, Variáveis de Ambiente, Params e URLs

Passo 1: Anatomia da URL: Diferencie na prática Path Params (req.params), Query Params (req.query) e Headers (req.headers).

Passo 2: Configure variáveis de ambiente: Use process.env para extrair dados sensíveis (portas, chaves de API e ambiente).

Passo 3: Prática (Mão na massa): Crie uma rota de busca e filtragem dinâmica combinando Path e Query Params (ex.: categoria, busca, ordem e paginação).

Passo 4: Valide com cabeçalhos: Crie um middleware de validação do cabeçalho x-api-key para bloquear acessos sem chave válida.<br><br>

>📌 Módulo 05: Conexão a Banco de Dados no Padrão MVC (MongoDB/Mongoose)

Passo 1: Estruture a arquitetura: Organize seu projeto separando responsabilidades nas pastas config, models, controllers e routes.

Passo 2: Defina Schemas NoSQL: Crie um modelo Mongoose definindo campos obrigatórios, tipos de dados e timestamps.

Passo 3: Prática (Mão na massa): Substitua dados em memória por chamadas assíncronas do Mongoose (find, create, findByIdAndUpdate, findByIdAndDelete).

Passo 4: Valide a persistência: Insira e consulte registros confirmando que os dados estão sendo gravados no MongoDB.<br><br>

>📌 Módulo 06: Guia de Autenticação JWT (Rotas Públicas e Privadas)

Passo 1: Entenda o fluxo Stateless: Compreenda como o servidor valida a identidade do cliente por meio de tokens assinados sem guardar sessões.

Passo 2: Criptografe senhas: Na rota de cadastro, encripte a senha do usuário com a biblioteca bcryptjs antes de salvar.

Passo 3: Prática (Mão na massa): Na rota de login, compare as senhas e gere um token assinado usando jsonwebtoken e uma chave secreta.

Passo 4: Valide a proteção: Crie o middleware autenticarToken para extrair o cabeçalho Authorization: Bearer <token> e liberar o acesso apenas a rotas privadas.<br><br>

>📌 Módulo 07: Tratamento Global de Erros, Status Codes e Resiliência

Passo 1: Mapeie os erros: Estude a aplicação correta dos códigos HTTP 400, 401, 404, 500 e 503.

Passo 2: Crie exceções customizadas: Implemente a classe AppError para separar falhas de regra de negócio conhecidas de erros críticos de servidor.

Passo 3: Prática (Mão na massa): Estruture um Middleware Global de Erros com 4 parâmetros (err, req, res, next) no final da cadeia de rotas.

Passo 4: Valide com resiliência: Aplique o padrão Circuit Breaker para proteger a API contra lentidão ou indisponibilidade em integrações externas.<br><br>

>📌 Módulo 08: Inversão de Fluxo — Webhooks e Integrações

Passo 1: Inversão de papel: Entenda por que o modelo assíncrono de notificações ativas (Webhooks) supera a consulta contínua (Polling).

Passo 2: Prática (Mão na massa): Crie uma rota POST /webhooks/pagamentos para escutar disparos de eventos de gateways de pagamento.

Passo 3: Garanta a segurança: Valide a chave secreta enviada no cabeçalho personalizado (x-webhook-secret) para rejeitar requisições falsas.

Passo 4: Valide a resposta: Aplique a regra de ouro respondendo imediatamente com status HTTP 200 para evitar que o gateway reenvie requisições.<br><br>

>📌 Módulo 09: Conexão com Frontend e Segurança com CORS

Passo 1: Entenda o SOP: Compreenda a Política de Mesma Origem (Same-Origin Policy) e por que os navegadores bloqueiam requisições de origens diferentes por padrão.

Passo 2: Prática (Mão na massa): Instale e configure o middleware cors definindo uma lista branca (whitelist) de origens, métodos e cabeçalhos permitidos.

Passo 3: Desvende o Preflight: Analise como o navegador envia requisições do tipo OPTIONS antes de disparar operações de modificação de dados.

Passo 4: Valide o bloqueio: Faça chamadas simulando origens não autorizadas no cabeçalho Origin e confirme a resposta 403 Forbidden.<br><br>

>📌 Módulo 10: Validação Elegante de Schemas e Payloads com Zod

Passo 1: Abandone validações manuais: Substitua checagens repetitivas do tipo if (!campo) por contratos formais de entrada.

Passo 2: Defina Schemas com Zod: Crie schemas declarativos encadeando regras de obrigatoriedade, tipos, tamanhos mínimos e conversões.

Passo 3: Prática (Mão na massa): Construa um middleware genérico de validação que executa schema.safeParse(req.body) e higieniza os dados.

Passo 4: Valide os erros: Envie requisições com dados incorretos e confirme o retorno formatado em 400 Bad Request indicando os campos inválidos.<br><br>

>📌 Módulo 11: Documentação Viva de API com Swagger / OpenAPI

Passo 1: Entenda a especificação: Estude como a OpenAPI Specification (OAS) resolve o problema de documentações desatualizadas em arquivos estáticos.

Passo 2: Configure as ferramentas: Instale swagger-ui-express e swagger-jsdoc no projeto Express.

Passo 3: Prática (Mão na massa): Escreva anotações @swagger em formato JSDoc sobre suas rotas descrevendo parâmetros, schemas e respostas.

Passo 4: Valide de forma interativa: Acesse a rota /api-docs no navegador e use a função "Try it out" para testar requisições em tempo real sem precisar do Postman.
<br><br>[&#x1F51D;](#entrega-final---estudo-guiado)



