[&#9664;](/README.md "Voltar")
# Entrega Final - Resumos Estruturados
<br>

>Módulo 01: A Base Conceitual e a Teoria do Garçom

Definição de API: <br>- Atua como intermediária de comunicação entre cliente e servidor (analogia do garçom no restaurante), processando requisições sem expor as regras internas da aplicação.

Acesso ao Banco: <br>- A aplicação cliente não deve acessar o banco de dados diretamente para preservar a segurança da infraestrutura, evitar problemas de desempenho e isolar as regras de negócio.

REST vs. RESTful: <br>- REST é o modelo de arquitetura baseado no protocolo HTTP. RESTful é o sistema ou API que implementa e cumpre rigorosamente as regras do modelo REST na prática.

Regra de Ouro (Interface Uniforme): <br>- A API abstrai a infraestrutura interna do servidor e expõe uma interface segura e padronizada para a troca de dados.
<br><br>

>Módulo 02: O Protocolo HTTP e os Verbos (CRUD na Prática)

Estrutura das Mensagens HTTP:<br>- Composta por requisição (Request) e resposta (Response), contendo métodos, URIs, cabeçalhos (headers) e corpo (body).

Métodos HTTP & CRUD:
<br>- GET: Lê/Busca dados (Read).
<br>- POST: Cria um novo registro no servidor (Create).
<br>- PUT: Substitui um registro por completo (Update Total).
<br>- PATCH: Modifica apenas campos específicos (Update Parcial).
<br>- DELETE: Remove permanentemente um registro (Delete).

Status Codes Frequentes:
<br>- 200 OK: Sucesso na requisição com retorno de dados.
<br>- 201 Created: Registro criado com sucesso via POST.
<br>- 204 No Content: Sucesso na operação sem corpo de retorno (ex: DELETE).
<br>- 400 Bad Request: Requisição malformada ou dados de entrada inválidos.
<br>- 404 Not Found: Recurso não localizado no servidor.
<br>- 500 Internal Server Error: Erro não previsto no código do servidor.

Regra de Ouro (Idempotência e Semântica): <br>- Chamadas com o método GET apenas consultam dados sem modificar o estado do servidor. Utilize PUT para substituição total e PATCH para alterações parciais.<br><br>

>Módulo 03: Construindo Sua Primeira API com Express

Definição & Setup:

Express: <br>- Framework web minimalista para Node.js focado no gerenciamento de rotas e middlewares.

Inicialização: <br>- Instanciação da aplicação com express(), escuta em porta com app.listen() e mapeamento de rotas com app.get() e app.post().

Parsing de JSON: <br>- Habilitação do middleware app.use(express.json()) no arquivo principal.

Regra de Ouro (Body Parsing): <br>- Sem o middleware express.json(), o Express não consegue interpretar payloads em formato JSON enviados no corpo da requisição (req.body).<br><br>

>Módulo 04: Gerenciamento, Variáveis de Ambiente, Query Params e URLs

Anatomia de URLs e Acesso no Express:

Path Params (req.params): <br>- Parâmetros obrigatórios definidos no caminho da rota (ex: /produtos/:id) para identificar recursos específicos.

Query Params (req.query): <br>- Parâmetros opcionais enviados após a ? (ex: ?busca=teclado&limite=10) para ordenação, busca, filtragem e paginação.

Headers (req.headers): <br>- Metadados da requisição, como tokens de autorização e chaves de API (x-api-key).

Configuração Segura: <br>- Uso de variáveis de ambiente (process.env) para isolar credenciais e configurações sensíveis do código-fonte.

Regra de Ouro: <br>- Use Path Params para dados identificadores obrigatórios do recurso e Query Params para opções flexíveis de visualização e filtro.<br><br>

>Módulo 05: Conexão a Banco NoSQL com MongoDB, Mongoose e MVC

Persistência NoSQL:

MongoDB & Mongoose: <br>- Banco NoSQL schema-less baseado em documentos JSON/BSON e biblioteca ODM para modelagem de schemas fortemente tipados.

Camadas da Arquitetura MVC para APIs:<br>- 
Model: Define o Schema da coleção e realiza as operações com o banco de dados.

Controller: <br>- Processa as regras de negócio, recebe os dados da requisição HTTP e retorna o JSON adequado.

Routes: <br>- Mapeia os métodos HTTP e URIs direcionando as requisições aos métodos dos Controllers.

View: Na API REST, a View corresponde ao próprio payload JSON retornado ao cliente.

Regra de Ouro: <br>- O Controller não deve acessar o banco diretamente ou conter schemas; a manipulação de dados pertence exclusivamente aos Models.<br><br>

>Módulo 06: Guia de Autenticação JWT (Rotas Públicas e Privadas)

Arquitetura Stateless:

JSON Web Token (JWT): <br>- Token criptografado trafegado entre cliente e servidor, dispensando o armazenamento de sessões no servidor.

Componentes de Segurança:

Encriptação de Senha: <br>- Hashing de senhas com a biblioteca bcrypt antes de salvar no banco.

Assinatura e Validação: <br>- Emissão de tokens com jwt.sign() e interceptação de rotas privadas por middleware que valida o cabeçalho Authorization: Bearer <token>.

Regra de Ouro: <br>- A chave secreta de assinatura (JWT_SECRET) deve ficar estritamente oculta no ambiente e o payload do token nunca deve conter senhas ou dados sensíveis.<br><br>

>Módulo 07: Tratamento Global de Erros, Status Codes e Resiliência

Arquitetura Centralizada:

Middleware Global de Erros: <br>- Middleware com 4 parâmetros (err, req, res, next) registrado ao final de todas as rotas do Express para capturar exceções da aplicação.

Classes Customizadas (AppError): <br>- Diferenciam erros operacionais previstos na regra de negócio (status 400, 401, 404) de falhas não tratadas no código.

Resiliência (Circuit Breaker): <br>- Padrão com três estados (CLOSED, OPEN, HALF-OPEN) para interromper chamadas a serviços externos instáveis e evitar falhas em cascata no sistema, retornando erro 503 Service Unavailable.

Regra de Ouro: <br>- Passe todas as exceções capturadas nos fluxos assíncronos para a função next(error), garantindo que o tratamento permaneça centralizado.<br><br>

>Módulo 08: Inversão de Fluxo — Webhooks e Integrações

Conceito (Event-Driven vs. Polling):

Webhooks: <br>- Em vez de a aplicação realizar consultas repetitivas ao servidor (Polling), o serviço externo dispara uma requisição HTTP POST imediata para um endpoint da API quando um evento acontece.

Mecanismos de Proteção:

Validação de Origem: <br>- Verificação de cabeçalhos secretos (Secret Headers como x-webhook-secret) para autenticar o emissor da mensagem.

Regra de Ouro (Aviso de Recebimento / ACK):<br>-  O ouvinte do Webhook deve validar o segredo e responder imediatamente com status 200 OK, delegando processamentos demorados para segundo plano para evitar reenvios duplicados.<br><br>

>Módulo 09: Conexão com Frontend e Segurança com CORS

Mecanismo de Segurança do Navegador:

SOP (Same-Origin Policy): <br>- Política do navegador que impede por padrão que um script acesse dados de uma origem (domínio/porta) diferente.

CORS (Cross-Origin Resource Sharing): <br>- Cabeçalhos HTTP adicionados pelo servidor para autorizar origens e métodos específicos no navegador.

Requisição Preflight: <br>- Chamada prévia automática do tipo HTTP OPTIONS realizada pelo navegador antes de enviar requisições com métodos que alteram dados ou possuem cabeçalhos personalizados.

Regra de Ouro: <br>- Configure o middleware CORS no Express especificando uma lista explícita de domínios confiáveis em vez de liberar com asterisco (*) em ambiente de produção.<br><br>

>Módulo 10: Validação Elegante de Schemas e Payloads com Zod

Schemas Declarativos:

Zod: <br>- Biblioteca para definição de contratos de dados fortemente tipados, eliminando verificações manuais repetitivas com if.

Recursos Principais:

Parse Seguro (schema.safeParse): <br>- Executa a validação do corpo da requisição (req.body) sem lançar exceções não tratadas.

Coerção de Tipos (z.coerce): <br>- Converte tipos automaticamente (ex: converte string "25" para o número 25).

Regra de Ouro:<br>-  O middleware de validação do Zod deve interromper requisições inválidas com erro 400 Bad Request e sobrescrever o req.body com os dados sanitizados antes que cheguem ao Controller.<br><br>

>Módulo 11: Documentação Viva de API com Swagger / OpenAPI

Especificação & Interface:

OpenAPI Specification (OAS): <br>- Padrão universal (JSON/YAML) para descrever a estrutura e os contratos de APIs REST.

Swagger UI & swagger-jsdoc: <br>- O swagger-jsdoc gera a especificação OpenAPI lendo anotações JSDoc (@swagger) no código-fonte, enquanto o swagger-ui-express disponibiliza o painel visual interativo no caminho /api-docs.

Testes em Tempo Real: <br>- O recurso "Try it out" permite executar requisições HTTP e visualizar os retornos JSON diretamente pelo navegador.

Regra de Ouro: <br>- Gerar a documentação a partir do código garante que a especificação evolua junto com as rotas, evitando documentações manuais estáticas desatualizadas.
<br><br>[&#x1F51D;](#)
