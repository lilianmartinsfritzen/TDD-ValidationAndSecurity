<p align="center">
  <a href="#sobre">V&V</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#desafio">Desafio</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#resolucao">Resolução</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#tecnologias">Tecnologias</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#execucao">Execução</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#licenca">Licença</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#desenvolvedora">🙋🏻‍♀️</a>
</p>

<p align="center">
  <img src="https://img.shields.io/static/v1?label=PRs&message=welcome&color=49AA26&labelColor=000000" alt="PRs welcome!" />
<a href="https://github.com/lilianmartinsfritzen/TDD-challenge/blob/main/LICENSE">
  <img alt="License" src="https://img.shields.io/static/v1?label=license&message=MIT&color=49AA26&labelColor=000000" />
</a>
</p>

<h1> Verification and Validation (V&V) - TDD </h1>

<h2 id="sobre">Sobre V&V - Verificação e validação de software</h2> 
<div align="justify">

  É o processo no qual aferimos se as especificações e requisitos do sistema estão sendo atendidas pelo software em desenvolvimento, ou seja, a aplicação deve cumprir a finalidade pretendida. Verificação e Validação (V&V), que fazem parte da engenharia de software e também são reconhecidas como controle de qualidade, costumam fazer parte das atribuições dos testadores, como parte do ciclo de vida de desenvolvimento do projeto. De forma mais resumida podemos dizer que a Verificação busca identificar se o software atinge os objetivos propostos sem erros e/ou ausências, já a Validação verifica se o software é de fato o que deveria ter sido desenvolvido, se atende aos requisitos de alto nível. 

  Fonte: [Wikipedia-V&V](https://en.wikipedia.org/wiki/Software_verification_and_validation "Wikipedia Software verification and validation")
    
  <h4>⚗️ TDD - Test-driven development:</h4>
  Consiste em um desenvolvimento guiado por testes, esse método de desenvolver software se apoia em um ciclo curto de repetições e associa-se ao conceito de verificação e validação. O código é escrito a fim de validar as necessidades descritas no teste automatizado juntamente com as do software.
  <br>
  <br>

  Fonte: [Wikipedia-TDD](https://pt.wikipedia.org/wiki/Test-driven_development "Wikipedia Test-driven development")
  <br>

  <h4>✅ Autenticação e Autorização:</h4>
  A autenticação no contexto do HTTP é fornecida uma estrutura geral para controle de acesso, comumente é utilizado o esquema "Basic", sendo usada para que um cliente forneça informações de autenticação e também por um servidor onde define uma solicitação do cliente. A autenticação ocorre quando o cliente inclui um campo de cabeçalho de solicitação com as credenciais, como usuário e senha. 
  <br>
  <br>
  A autorização, por sua vez, verifica nas regras de negócios se o usuário autenticado está autorizado a executar/acessar a funcionalidade/rota requisitada.
  <br>
  <br>
  
  Fonte: [MDN Autenticação HTTP](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Authentication "MDN Autenticação HTTP")

</div>

<h2 id="desafio">🏆 Desafio</h2> 
<div align="justify">
  Para a conclusão do capítulo 3 - Validação e Segurança do Bootcamp Spring e React - o professor Nelio Alves da <a href="https://devsuperior.com.br">Escola DevSuperior</a> propos como desafio a tarefa abaixo.<br><br>
  <strong> 📝 TAREFA:</strong> Validação e Segurança
 
  Implemente as funcionalidades necessárias para que os testes do projeto bds04 sejam executados sem falhas:
  https://github.com/devsuperior/bds04
  <br>

  Neste sistema, somente as rotas de leitura de eventos e cidades são públicas. Usuários CLIENT podem também inserir novos eventos. Os demais acessos são permitidos apenas a usuários ADMIN.

  <strong>Validações de City:</strong>
  - Nome não pode ser vazio
  <br>

  <strong>Validações de Event:</strong>
  - Nome não pode ser vazio
  - Data não pode ser passada
  - Cidade não pode ser nula

  <img src="https://user-images.githubusercontent.com/83084256/136260380-771db60c-f48f-44b7-9e38-b9789d7c8e3f.png" width="450"/>
</div>

<h2 id="resolucao">Resolução</h2> 
<div align="justify">
  Na aplicação continha apenas as entidades e o DTO de City e Events implementados, juntamente com os testes.
  Após analisar o conteúdo da aplicação e os testes resolvi seguir a seguinte ordem de implementação dos códigos:
<br>
<br>

<div align="left">

  - Modelo de dados User-Roles;
  - Adicionar pacotes Repository, Services, Controllers e pacotes de exceção para Services e Controllers;
  - Infraestrutura de validação;
  - Infraestrutura de segurança;
  - Releitura dos testes, implementar funcionalidades e executar testes.
</div>

  <h3>🚧 Modelo de dados User-Roles</h3>
  Modelo de dados User-Roles incluídos e verificados no banco de dados H2. Neste primeiro passo decidi utilizar um código provisório para liberação dos endpoints, conforme explicado pelo professor Nélio, desta forma consegui verificar se as tabelas foram inseridas corretamente no H2. Se não inserisse essas informações todos os caminhos estariam bloqueados, pois o pom.xml já está com todas as bibliotecas de segurança, spring-boot-starter-validation, spring-boot-starter-validation e spring-security-oauth2-autoconfigure.

  <br>
  <br>
 
  <h3>🚧 Adicionar pacotes Repository, Services, Controllers e pacotes de exceção para Services e Controllers</h3>
  Na aplicação continha apenas os pacotes entities e o dto, sendo necessário adicionar todos os demais pacotes como, Repository, Services, Controllers, bem como as exceções do Controllers e Services. Após a implementação dos pacotes todos os endpoints foram verificados no Postman.
  <br>
  <br>

  <h3>🚧 Infraestrutura de validação</h3>
    Infraestrutura de validação incluída ao projeto, composta pelos arquivos FieldMessage, ValidationError e o método MethodArgumentNotValidException no ControllerExceptionHandler, este último, inclusive, é de extrema importância para as validações.
    
  <br>
  <br>

</div>

 <h3>🚧 Infraestrutura de segurança</h3>
  Infraestrutura de segurança adicionada ao projeto, incluindo variáveis de ambiente no application.properties, retirada do arquivo provisório SecurityConfig que liberava os endpoints. <br><br>

  Criada a classe UserService que implementa as interfaces do Spring Security, UserDetails e  UserDetailsService, juntamente com a WebSecurityConfigurerAdapter, classe para configuração de segurança web onde é necessário implementar o AuthenticationManager. <br><br>

  Já no AppConfig conterá algumas configurações do aplicativo como os Beans BCrypt, JwtAccessTokenConverter e JwtTokenStore. E concluindo a infraestrutura foi incluído AuthorizationServerConfigurerAdapter que é a classe de configuração para Authorization Server e ResourceServerConfigurerAdapter que é a classe de configuração para Resource Server. 🤯
  <br>
  <br>

 <h3>🚧 Releitura dos testes, implementar funcionalidades e executar testes</h3>

   <strong>Teste de Integração CityController:</strong> <br>

    Deve retornar 401 (Unauthorized) quando um usuário não logado tentar inserir uma cidade.
    Deve retornar 403 (Forbidden) quando um Client logado tentar inserir uma cidade.
    Deve retornar 201 (Created), inserir a cidade, quando o Admin estiver logado e os dados estiverem corretos.
    Deve retornar 422 (Unprocessable Entity) quando Admin estiver logado, mas tentar inserir a cidade com o nome em branco.
    Deve retornar uma lista com todas as cidades ordenadas por nome.

  <strong>Teste de Integração EventController:</strong>	<br>

    Deve retornar 401 (Unauthorized) quando o usuário não logado tentar inserir um evento.
    Deve retornar 201 (Created), inserir o evento, quando o Client estiver logado e os dados estiverem corretos.
    Deve retornar 201 (Created), inserir o evento, quando o Admin estiver logado e os dados estiverem corretos.
    Deve retornar 422 (Unprocessable Entity) quando Admin estiver logado, mas tentar inserir o nome do evento em branco.
    Deve retornar 422 (Unprocessable Entity) quando Admin estiver logado, mas tentar inserir o evento com data passada.
    Deve retornar 422 (Unprocessable Entity) quando Admin estiver logado, mas tentar inserir o evento sem informar a cidade.
    Deve retornar os eventos de forma paginada.
  
  Fonte: [Códigos de status de respostas HTTP](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status "Códigos de status de respostas HTTP")

<h2 id="tecnologias">🚀 Tecnologias</h2> 

- Java 11
- Spring boot
- JPA
- Maven
- OAuth 2.0
- JWT


<h2 id="execucao">🕹 Execução</h2> 

Pré-requisitos: **Java 11 e Postman (ou a API Client que preferir)**

```bash
# Clonar repositório
git clone https://github.com/lilianmartinsfritzen/TDD-ValidationAndSecurity
# Entrar na pasta abaixo
cd bds04
# Executar o projeto
./mvnw spring-boot:run

# Caminhos utilizados no Postman
GET - All Cities: http://localhost:8080/cities
GET - Events Paged: http://localhost:8080/events

# Dados para Login
POST - LOGIN: http://localhost:8080
ENDPOINT: /oauth/token (Utilizado o padrão OAuth)

AUTHORIZATION: 
Type: Basic Auth
```
|USERNAME|PASSWORD|
|--|:--:|
|myclientid|myclientsecret||

```bash
Body: x-www-form-urlencoded
Ana - CLIENT
```
|KEY|VALUE|DESCRIPTION|
|--|:--:|--|
|username|ana@gmail.com||
|password|123456||
|grand_type|password||
```bash
Body: x-www-form-urlencoded
Bob - ADMIN
```
|KEY|VALUE|DESCRIPTION|
|--|:--:|--|
|username|bob@gmail.com||
|password|123456||
|grand_type|password||

```bash
# Caminhos utilizados com Body
POST - New City: http://localhost:8080/cities

{
  "name": "New city"
}


POST - New Event: http://localhost:8080/events

{
  "name": "Novo evento",
  "url": "https://novoevento.com.br",
  "date": "2023-07-15",
  "cityId": 1
}
```
<h2 id="licenca">📃 Licença</h2> 

Esse projeto está sob a licença MIT. Veja o arquivo [LICENSE](https://github.com/lilianmartinsfritzen/TDD-ValidationAndSecurity/blob/main/LICENSE) para mais detalhes.

<h2 id="desenvolvedora">Desenvolvedora</h2> 
  <img src="https://user-images.githubusercontent.com/83084256/134750093-acf555ae-b1b0-4a4e-a22c-421bf98f15a0.png" width="100" height="100" /> <br>
<a href="https://www.linkedin.com/in/lilian-martins-fritzen/" target="_blank">
  <img src="https://img.shields.io/static/v1?label=Linkedin&message=lilianmartinsfritzen&color=0A66C2&style=for-the-badge&logo=linkedin" />
</a>
