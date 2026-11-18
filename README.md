# Drogaria Java 💊

Projeto web em Java para estudo de cadastro e persistência de dados de uma drogaria. A aplicação utiliza JSF e PrimeFaces na interface, Hibernate no acesso ao banco e MySQL para armazenamento.

## Tecnologias

- Java 8 e Maven
- JSF 2.2, PrimeFaces 5.2 e OmniFaces 1.11
- Hibernate 4.3 e MySQL
- JUnit 4

## Como executar

### Pré-requisitos

- JDK 8 e Maven.
- MySQL instalado e em execução, com uma versão compatível com o driver MySQL Connector/J 5.1 usado pelo projeto.
- Um servidor compatível com Java Servlet 3.1 e `javax.*`, como Tomcat 8.5 ou 9.

### Configuração

1. Clone o repositório:

   ```bash
   git clone https://github.com/Pio69/drogaria-java.git
   cd drogaria-java
   ```

2. Crie um banco de dados MySQL chamado `drogaria` e ajuste a URL, o usuário e a senha no arquivo `src/main/resources/hibernate.cfg.xml` para o seu ambiente. Evite publicar credenciais reais no repositório.
3. Gere o arquivo WAR:

   ```bash
   mvn clean package -DskipTests
   ```

4. Implante `target/Drogaria.war` no servidor e inicie-o. Com o Tomcat na porta padrão e o contexto `Drogaria`, uma das páginas pode ser acessada em `http://localhost:8080/Drogaria/pages/estados.xhtml`.

O Hibernate está configurado com `hbm2ddl.auto=update`, que pode alterar o esquema do banco. Use um banco de desenvolvimento separado. As dependências do projeto são antigas e podem exigir ajustes para funcionar em ambientes atuais.

## Estrutura

```text
src/main/java/br/com/leonardo/drogaria/
├── bean/    # controle de interface JSF
├── dao/     # operações de persistência
├── domain/  # entidades do domínio
└── util/    # configuração do Hibernate
src/main/resources/          # configuração do banco
src/main/webapp/pages/       # páginas JSF
src/test/                    # testes das classes de acesso a dados
```

Os testes de persistência usam o banco configurado no Hibernate e podem alterar seus dados. Revise-os e configure um banco de testes isolado antes de executar `mvn test`.
