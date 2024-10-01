
# Gerenciamento de Pessoas - API

Este projeto consiste em uma API para gerenciar pessoas. A API foi desenvolvida utilizando **Spring Boot** com **Spring Web**, **JPA**, **MySQL** e **Lombok**. 

A entidade principal da aplicação é **Person**, que possui os seguintes atributos:

- **nome** (String)
- **cpf** (String)
- **idade** (Integer)

## Funcionalidades

- **POST /persons**: Cria uma nova Person no banco de dados.
- **GET /persons/{id}**: Retorna uma Person pelo seu ID.
- **DELETE /persons/{id}**: Deleta uma Person pelo seu ID.

---

## Índice

- [Pré-requisitos](#pré-requisitos)
- [Instalação](#instalação)
- [Configuração do Banco de Dados](#configuração-do-banco-de-dados)
- [Desenvolvimento](#desenvolvimento)
  - [1. Criação da Entity](#1-criação-da-entity)
  - [2. Criação do Repository](#2-criação-do-repository)
  - [3. Criação do DTO](#3-criação-do-dto)
  - [4. Criação do Controller](#4-criação-do-controller)
- [Testes](#testes)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)

---

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte instalado em seu ambiente:

- [JDK 17+](https://www.oracle.com/java/technologies/javase-jdk17-downloads.html)
- [Maven 3.8+](https://maven.apache.org/install.html)
- [MySQL 8+](https://dev.mysql.com/downloads/)
- [IntelliJ IDEA ou outra IDE de sua escolha](https://www.jetbrains.com/idea/download/)

---

## Instalação

1. Clone o repositório para sua máquina local:

   ```bash
   git clone https://github.com/THAISHRM/gerenciamento_backend.git
   ```

2. Navegue até o diretório do projeto:

   ```bash
   cd gerenciamento-de-pessoas
   ```

3. Instale as dependências:

   ```bash
   mvn clean install
   ```

4. Certifique-se de que seu banco de dados MySQL esteja rodando. 

---

## Configuração do Banco de Dados

Configure as variáveis de conexão com o banco de dados no arquivo `application.properties`, localizado em `src/main/resources`:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/personDb
spring.datasource.username=root
spring.datasource.password=senha
spring.jpa.hibernate.ddl-auto=update
```

---

## Desenvolvimento

### 1. Criação da Entity

A classe **Person** será mapeada como uma tabela no banco de dados. Utilize a anotação `@Entity` para definir essa classe. Ela também conterá os atributos **id**, **nome**, **cpf** e **idade**.

Exemplo:

```java
@Entity
public class Person {
    
    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private UUID id;
    private String nome;
    private String cpf;
    private Integer idade;

    // Getters e Setters
}
```

### 2. Criação do Repository

Crie a interface **PersonRepository**, que estende `JpaRepository`. Essa interface permite a comunicação com o banco de dados.

```java
public interface PersonRepository extends JpaRepository<Person, UUID> {
}
```

### 3. Criação do DTO

Crie a classe **PersonDTO** para transferir os dados da entidade **Person**.

```java
public class PersonDTO {
    
    private String nome;
    private String cpf;
    private Integer idade;

    // Getters e Setters
}
```

### 4. Criação do Controller

Crie o controlador **PersonController** que terá os endpoints para criar e buscar uma Person por ID. Utilize o `@RestController` e defina os métodos POST, GET e DELETE.

---

## Testes

Você pode utilizar o **Postman** ou outra ferramenta de sua preferência para testar os endpoints da API.

1. **POST /persons**: Enviar um JSON no corpo da requisição para criar uma nova Person:
   
   ```json
   {
     "nome": "João Silva",
     "cpf": "123.456.789-00",
     "idade": 30
   }
   ```

2. **GET /persons/{id}**: Retornar uma Person existente pelo ID.

---

## Tecnologias Utilizadas

- **Spring Boot**: Framework para construção da API.
- **Spring Data JPA**: Para persistência e comunicação com o banco de dados.
- **MySQL**: Base de dados.
- **Lombok**: Simplificação do código Java com anotações.
- **Maven**: Gerenciamento de dependências.

—

## Equipe

<table>
  <tr>
   <td align="center">
      <a href="https://github.com/AngeloRafaelbr">
        <img src="https://avatars.githubusercontent.com/u/147670666?v=4" width="100px;" alt="Foto do Ângelo"/><br>
        <sub>
          <b>Ângelo Santos - 01589358</b>
        </sub>
      </a>
    </td>
   
   <td align="center">
      <a href="https://github.com/livyagdc">
        <img src="https://avatars.githubusercontent.com/u/144238732?v=4" width="100px;" alt="Foto da Livya"/><br>
        <sub>
          <b>Livya Carvalho - 01645272</b>
        </sub>
      </a>
    </td>
   
   <td align="center">
      <a href="https://github.com/THAISHRM">
        <img src="https://avatars.githubusercontent.com/u/144055463?v=4" width="100px;" alt="Foto da Thais"/><br>
        <sub>
          <b>Thais Melo - 01068175</b>
        </sub>
      </a>
   </td>
    
  </tr>
</table>
