<h1>
    <a href="https://www.dio.me/">
     <img align="center" width="40px" src="https://hermes.digitalinnovation.one/assets/diome/logo-minimized.png"></a>
    <span> Santander-Bootcamp-2024 -JAVA</span> 
    <a href="https://glysns.gitbook.io/java-basico">
</h1>
DESAFIO BOOTCAMP - DIO @Santader - Publicando Sua API REST na Nuvem Usando Spring Boot 3, Java 17 e Railway.

# java_web_spring_Livro

## Descrição

Este projeto é uma API REST para gerenciar livros. Utiliza Java 17 e Spring Boot 3 para criar a aplicação e Railway para fazer o deploy na nuvem. A API permite realizar operações CRUD (Criar, Ler, Atualizar, Excluir) em um banco de dados de livros.

## Tecnologias Utilizadas

- Java 17
- Spring Boot 3
- Spring Data JPA
- H2 Database (para desenvolvimento)
- Railway (para deploy)
- OpenAPI (Swagger)

## Configuração do Projeto

### Dependências

As principais dependências usadas neste projeto estão listadas abaixo e são gerenciadas pelo Maven:

```xml
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <dependency>
        <groupId>com.h2database</groupId>
        <artifactId>h2</artifactId>
        <scope>runtime</scope>
    </dependency>
    <dependency>
        <groupId>org.springdoc</groupId>
        <artifactId>springdoc-openapi-ui</artifactId>
        <version>1.5.10</version>
    </dependency>
</dependencies>

##Estrutura do Projeto

src/main/java/com/livro/
|-- controller/
|   `-- LivroController.java
|-- model/
|   `-- Livro.java
|-- repository/
|   `-- LivroRepository.java
|-- service/
|   `-- LivroService.java
|-- LivroApplication.java


Exemplos de Código
Entity
java
Copiar código
@Entity
public class Livro {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String titulo;
    private String autor;

    // Getters and Setters
}
Repository
java
Copiar código
@Repository
public interface LivroRepository extends JpaRepository<Livro, Long> {
}
Service
java
Copiar código
@Service
public class LivroService {
    @Autowired
    private LivroRepository repository;

    public List<Livro> findAll() {
        return repository.findAll();
    }

    public Livro save(Livro livro) {
        return repository.save(livro);
    }
}
Controller
java
Copiar código
@RestController
@RequestMapping("/api/livros")
public class LivroController {
    @Autowired
    private LivroService service;

    @GetMapping
    public List<Livro> getAll() {
        return service.findAll();
    }

    @PostMapping
    public Livro create(@RequestBody Livro livro) {
        return service.save(livro);
    }
}
Documentação da API
A documentação da API pode ser acessada através do Swagger em http://localhost:8080/swagger-ui.html.

Deploy na Railway
Passos para o Deploy
Crie uma conta na Railway.

Crie um novo projeto e conecte seu repositório GitHub onde está o código da sua aplicação.

Adicione um arquivo Procfile na raiz do projeto com o seguinte conteúdo:

bash
Copiar código
web: java -jar target/java_web_spring_Livro-0.0.1-SNAPSHOT.jar
Adicione um banco de dados no Railway e configure as credenciais no application.properties:

properties
Copiar código
spring.datasource.url=jdbc:postgresql://{HOST}:{PORT}/{DATABASE}
spring.datasource.username={USERNAME}
spring.datasource.password={PASSWORD}
spring.jpa.hibernate.ddl-auto=update
Faça commit e push das alterações para o GitHub.

No Railway, acione o deploy automático pelo GitHub e acompanhe o deploy.

## Testes
Após o deploy, a API estará disponível na URL fornecida pelo Railway. Acesse essa URL e verifique se a API está funcionando corretamente.

## Contribuição
Contribuições são bem-vindas! Sinta-se à vontade para abrir issues e pull requests para melhorar este projeto.

## Licença
Este projeto está licenciado sob a Licença MIT. Consulte o arquivo LICENSE para obter mais informações.



## Este README fornece uma visão geral completa do projeto, desde a configuração inicial até o deploy na Railway.




Feito com 💜 por Leyane Leite
