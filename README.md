# 👤 Cadastro de Usuário

API REST para **cadastro de usuários** (CRUD completo), desenvolvida em **Java** com **Spring Boot**. O projeto usa banco de dados em memória (H2), o que permite executá-lo localmente sem nenhuma configuração adicional.

![Java](https://img.shields.io/badge/Java-17%2B-orange?logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?logo=springboot&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-C71A36?logo=apachemaven&logoColor=white)
![H2](https://img.shields.io/badge/H2%20Database-0000bb)
![Status](https://img.shields.io/badge/status-em%20desenvolvimento-yellow)

## 📑 Sumário

- [Sobre o projeto](#-sobre-o-projeto)
- [Funcionalidades](#-funcionalidades)
- [Tecnologias](#-tecnologias)
- [Pré-requisitos](#-pré-requisitos)
- [Como executar](#-como-executar)
- [Endpoints da API](#-endpoints-da-api)
- [Banco de dados (H2)](#-banco-de-dados-h2)
- [Estrutura do projeto](#-estrutura-do-projeto)
- [Próximos passos](#-próximos-passos)
- [Autor](#-autor)

## 📖 Sobre o projeto

Este projeto implementa as quatro operações básicas de persistência — **C**reate, **R**ead, **U**pdate e **D**elete — para a entidade *usuário*. Ele foi construído para praticar e demonstrar boas práticas do ecossistema Spring: organização em camadas, injeção de dependência, persistência com JPA e redução de código repetitivo com Lombok.

## ✨ Funcionalidades

- ✅ Cadastrar um novo usuário
- ✅ Listar todos os usuários
- ✅ Buscar usuário por ID
- ✅ Atualizar dados de um usuário
- ✅ Remover um usuário

## 🛠 Tecnologias

| Tecnologia | Uso |
| --- | --- |
| [Java](https://www.oracle.com/java/) | Linguagem principal |
| [Spring Boot](https://spring.io/projects/spring-boot) | Framework para construção da API |
| [H2 Database](https://www.h2database.com/) | Banco de dados em memória |
| [Lombok](https://projectlombok.org/) | Redução de código boilerplate (getters, setters, construtores) |
| [Maven](https://maven.apache.org/) | Gerenciamento de dependências e build |

## 📋 Pré-requisitos

- **JDK 17** ou superior (ajuste conforme a versão definida no `pom.xml`)
- **Git**
- Maven é opcional: o projeto inclui o **Maven Wrapper** (`mvnw`)

Verifique sua instalação:

```bash
java -version
```

## 🚀 Como executar

**1. Clone o repositório**

```bash
git clone https://github.com/Gabriel1Dev/cadastro-usuario.git
cd cadastro-usuario
```

**2. Execute a aplicação**

Linux / macOS:

```bash
./mvnw spring-boot:run
```

Windows:

```bash
mvnw.cmd spring-boot:run
```

**3. Acesse**

A API ficará disponível em `http://localhost:8080` (porta padrão do Spring Boot).

### Gerar o `.jar`

```bash
./mvnw clean package
java -jar target/*.jar
```

### Executar os testes

```bash
./mvnw test
```

## 🔌 Endpoints da API

| Método | Rota | Descrição |
| --- | --- | --- |
| `POST` | `/usuarios` | Cadastra um novo usuário |
| `GET` | `/usuarios` | Lista todos os usuários |
| `GET` | `/usuarios/{id}` | Busca um usuário pelo ID |
| `PUT` | `/usuarios/{id}` | Atualiza um usuário |
| `DELETE` | `/usuarios/{id}` | Remove um usuário |

### Exemplo de requisição

**POST** `/usuarios`

```json
{
  "nome": "Maria Silva",
  "email": "maria.silva@email.com"
}
```

**Resposta** `201 Created`

```json
{
  "id": 1,
  "nome": "Maria Silva",
  "email": "maria.silva@email.com"
}
```

Você pode testar os endpoints com [Postman](https://www.postman.com/), [Insomnia](https://insomnia.rest/) ou `curl`:

```bash
curl -X GET http://localhost:8080/usuarios
```

## 🗄 Banco de dados (H2)

O H2 roda **em memória**: os dados são recriados a cada inicialização da aplicação. Se o console estiver habilitado em `application.properties`, você pode acessá-lo em:

```
http://localhost:8080/h2-console
```

Configuração de exemplo:

```properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=
spring.h2.console.enabled=true
```

## 📂 Estrutura do projeto

```
cadastro-usuario/
├── .mvn/wrapper/        # Maven Wrapper
├── src/
│   ├── main/
│   │   ├── java/        # Código-fonte (controller, service, repository, model)
│   │   └── resources/   # application.properties
│   └── test/            # Testes
├── mvnw / mvnw.cmd      # Scripts do Maven Wrapper
└── pom.xml              # Dependências e configuração do build
```

## 🔭 Próximos passos

- [ ] Validação de dados com Bean Validation
- [ ] Tratamento global de exceções
- [ ] Documentação da API com Swagger / OpenAPI
- [ ] Testes unitários e de integração
- [ ] Persistência em banco relacional (PostgreSQL ou MySQL)
- [ ] Containerização com Docker
