# Controle de Gastos v2.1

Bem-vindo ao projeto **Controle de Gastos**, uma aplicação web moderna para gerenciamento de finanças pessoais. Desenvolvido com Spring Boot no backend e uma interface reativa com htmx, este projeto foi projetado para ser robusto, eficiente e fácil de manter.

O objetivo principal é demonstrar uma arquitetura de software limpa (MVC), o poder do htmx para criar UIs dinâmicas sem JavaScript complexo e um fluxo de deploy profissional para a nuvem usando Docker e Render.

[![Java](https://img.shields.io/badge/Java-21-blue.svg)](https://www.oracle.com/java/technologies/downloads/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.3.5-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Htmx](https://img.shields.io/badge/htmx-1.9.12-blueviolet)](https://htmx.org/)
[![Docker](https://img.shields.io/badge/Docker-Ready-blue)](https://www.docker.com/)

## ✨ Funcionalidades Principais

* **CRUD Completo de Lançamentos**: Adicione, visualize, altere e exclua receitas e despesas.
* **Interface Dinâmica**: A interface é atualizada em tempo real sem recarregar a página, graças ao htmx.
* **Design Responsivo**: Layout limpo e funcional que se adapta a diferentes tamanhos de tela.
* **Tema Light/Dark**: Alterne entre os modos de visualização claro e escuro para maior conforto visual.
* **Pronto para Deploy**: Containerizado com Docker e configurado para deploy fácil em plataformas como o Render.

## 🛠️ Tecnologias Utilizadas

| Categoria      | Tecnologia                                       |
| -------------- | ------------------------------------------------ |
| **Backend** | Java 21, Spring Boot, Spring Data JPA            |
| **Frontend** | Thymeleaf, htmx, CSS                             |
| **Banco de Dados** | H2 (Desenvolvimento), PostgreSQL (Produção)      |
| **Deploy** | Docker, Render                                   |
| **Build** | Maven                                            |

## 🚀 Como Executar o Projeto

Siga os passos abaixo para configurar e executar a aplicação em seu ambiente local.

### Pré-requisitos

Antes de começar, certifique-se de que você tem as seguintes ferramentas instaladas:

* [Java Development Kit (JDK) 21](https://www.oracle.com/java/technologies/downloads/#java21)
* [Apache Maven](https://maven.apache.org/download.cgi)
* [Git](https://git-scm.com/downloads)
* [Docker](https://www.docker.com/products/docker-desktop/) (Opcional, para execução via container)

### 1. Clone o Repositório

```bash
git clone [https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git](https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git)
cd SEU-REPOSITORIO
```

### 2. Execute a Aplicação (Desenvolvimento)

Para um ambiente de desenvolvimento, a aplicação utiliza um banco de dados em memória H2, que não requer nenhuma configuração externa.

**Usando o Maven Wrapper:**

No terminal, a partir da raiz do projeto, execute o comando:

```bash
# Para Linux/macOS
./mvnw spring-boot:run

# Para Windows
./mvnw.cmd spring-boot:run
```

A aplicação estará disponível em `http://localhost:8080`.

**Usando sua IDE:**

Importe o projeto como um projeto Maven em sua IDE preferida (IntelliJ, Eclipse, VS Code) e execute a classe principal `ControleDeGastosApplication.java`.

## 🚢 Deploy (Produção com Docker e Render)

Este projeto está pronto para ser implantado na nuvem. O `Dockerfile` na raiz do projeto cria uma imagem otimizada para produção.

### 1. Configuração do Banco de Dados

* Crie um banco de dados PostgreSQL em um serviço como o [Neon](https://neon.tech/) ou qualquer outro provedor.
* Guarde as credenciais de conexão (URL, Usuário e Senha).

### 2. Deploy no Render

* Faça o push do seu código para um repositório no GitHub.
* No painel do [Render](https://render.com/), crie um **"New Web Service"** e conecte seu repositório.
* Configure o serviço da seguinte forma:
    * **Runtime**: `Docker`
    * **Build Command**: (deixe em branco)
    * **Start Command**: (deixe em branco)
* Adicione as seguintes **Environment Variables**:
    * `SPRING_PROFILES_ACTIVE`: `prod`
    * `DB_URL`: A URL de conexão JDBC do seu banco de dados Neon (ex: `jdbc:postgresql://host:port/dbname`).
    * `DB_USERNAME`: O nome de usuário do seu banco de dados.
    * `DB_PASSWORD`: A senha do seu banco de dados.
* Clique em **"Create Web Service"** para iniciar o deploy.

## 📁 Estrutura do Projeto

```
controle-de-gastos/
├── .mvn/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── br/com/controledegastos/
│   │   │       ├── ControleDeGastosApplication.java
│   │   │       ├── controller/
│   │   │       ├── model/
│   │   │       └── repository/
│   │   └── resources/
│   │       ├── templates/
│   │       │   └── index.html
│   │       ├── application.properties
│   │       └── application-prod.properties
│   └── test/
├── .gitignore
├── Dockerfile
├── mvnw
├── mvnw.cmd
└── pom.xml
```
