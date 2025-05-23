# Aplicação de Gestão de Pacientes e Médicos Odontologico

## Integrantes:
- Thiago Carrillo
- Igor Oviedo
- Cauã Ferrigolli 

## Tecnologias Utilizadas
- **Linguagem**: C#
- **Framework**: .NET
- **Banco de Dados**: Oracle
- **Swagger/OpenAPI**: Documentação da API
- **Padrão de Criação**: Logger Manager (para gerenciamento de logs)
- **Arquitetura**: MVC (Model-View-Controller)

---

## Artefatos do Projeto

  ## Práticas de Clean Code Aplicadas

1. **Segregação de Responsabilidades**: cada classe tem responsabilidade única (Controllers, Services, Models).  
2. **Naming Conventions**: usamos PascalCase para classes e métodos, camelCase para variáveis locais.  
3. **Async/Await**: controllers assíncronos (`Task<IActionResult>`) para operações de I/O.  
4. **Injeção de Dependências**: serviços registrados via DI e configurados como singleton para o modelo ML.  
5. **Documentação**: comentários XML em métodos públicos e uso de `README.md` detalhado.

---

## Arquitetura Monolítica

A arquitetura monolítica mantém todos os módulos (UI, lógica de negócio, acesso a dados e ML) em um único deploy, facilitando a manutenção inicial.

---

## Testes Implementados

- **Testes Unitários**: criados com xUnit para as classes de modelo `Paciente` e `Medico`, validando regras de negócio e mapeamento de dados.  
- **Testes de Integração**: testes de integração com o banco de dados Oracle usando xUnit.

---

## Funcionalidades de IA Generativa

Além da predição binária com FastTree, este projeto inclui um módulo de IA generativa para geração de relatórios clínicos: a partir de dados de entrada do paciente, a aplicação sugere um texto de resumo médico inicial, usando um modelo de linguagem integrado (via Azure OpenAI ou GPT local).

---

## Integração com RabbitMQ

Para notificação de médicos, o sistema utiliza RabbitMQ para enfileirar e enviar e-mails automatizados sempre que uma nova predição é gerada, garantindo comunicação assíncrona e escalável.

---

### Implementação da API (Monolítica com MVC)
A escolha do padrão MVC em uma arquitetura monolítica se deve a:
- **Simplicidade**: A implementação centralizada em um único projeto facilita a gestão e o desenvolvimento inicial, sem a complexidade de uma estrutura distribuída.
- **Facilidade de Testes**: A separação das camadas facilita a realização de testes unitários e a identificação de problemas na aplicação.
- **Escalabilidade**: Apesar de ser monolítica, a aplicação pode ser escalada horizontalmente utilizando técnicas como contêineres e balanceamento de carga.

### Padrão de Criação na API (Logger Manager)
Foi utilizado o padrão Logger Manager para gerenciar os logs da aplicação. Este padrão centraliza a criação de logs, permitindo monitorar e depurar a aplicação de forma eficiente. O Logger Manager garante que os logs sejam registrados de forma consistente e com alta performance, além de possibilitar configurações para diferentes níveis de log (informação, erro, etc.).


