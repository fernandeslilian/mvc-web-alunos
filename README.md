# Projeto MVC Web - Cadastro de Alunos

Este projeto é uma aplicação web simples desenvolvida para demonstrar na prática o funcionamento da arquitetura **MVC (Model-View-Controller)**. A aplicação permite o cadastro e a listagem de alunos.

## Tecnologias Utilizadas
* **Java**
* **Spring Boot** (Spring Web)
* **Thymeleaf** (Motor de templates para a View)
* **Maven** (Gerenciador de dependências)

## Arquitetura MVC na Prática

Este projeto foi construído com uma separação física de diretórios que reflete diretamente a separação arquitetural. Cada camada tem uma responsabilidade única e bem definida:

### 1. Model (`com.exemplo.mvc.model.Aluno`)
A camada Model representa os dados e as regras de negócio da aplicação.
* **Responsabilidade:** No nosso projeto, a classe `Aluno` garante que um aluno não pode ser instanciado sem um nome (validação da regra de negócio).
* **Isolamento:** Esta camada é totalmente independente de requisições HTTP e de HTML. Ela não sabe que a web existe.

### 2. Controller (`com.exemplo.mvc.controller.AlunoController`)
 Controller atua como o maestro ou coordenador da aplicação.
* **Responsabilidade:** Ele recebe as requisições do usuário (como os verbos `@GetMapping` e `@PostMapping`), processa a intenção (cadastrar um aluno), e decide qual tela mostrar em seguida.
* **Limitações arquiteturais:** O Controller **não** valida regras de negócio (isso é papel do Model)e **não** renderiza o HTML diretamente. Ele apenas repassa os dados do Model para a View.

### 3. View (`src/main/resources/templates/`)
A camada View é responsável puramente pela interface com o usuário e apresentação visual.
* **Arquivos:** `alunos-form.html` (para entrada de dados) e `alunos-lista.html` (para exibição).
* **Responsabilidade:** Ela usa o Thymeleaf para capturar os dados que foram enviados pelo Controller (a lista de alunos) e exibi-los na tela. A View não toma decisões lógicas nem acessa o banco de dados.

## Como Executar o Projeto

1. Certifique-se de ter o Java instalado em sua máquina.
2. Abra a pasta raiz do projeto no **Visual Studio Code**.
3. Aguarde o VS Code importar as dependências do Maven.
4. Para rodar a aplicação, você pode:
   * Abrir o arquivo `MvcApplication.java` e clicar em **Run**.
   * Ou abrir o terminal e digitar: `mvn spring-boot:run.
5. Abra o navegador e acesse: `http://localhost:8080/alunos`
