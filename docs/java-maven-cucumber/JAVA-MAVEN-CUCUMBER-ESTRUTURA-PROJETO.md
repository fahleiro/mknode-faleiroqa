
# Estrutura de Projeto para Automação de Testes

A organização dos diretórios e arquivos do projeto é fundamental para garantir um fluxo claro, eficiente e colaborativo. É importante lembrar que o QA raramente trabalha de forma isolada, e, em casos de transição de equipe ou saída de um membro, um repositório bem estruturado e documentado se torna essencial para facilitar o entendimento e a continuidade por parte de outros profissionais.

---

## Estrutura do Projeto

```
/projeto
├── src
│   ├── main
│   │   └── java
│   │       └── br/com/projeto/packages
│   ├── test
│       ├── java
│       │   └── br/com/projeto
│       │       ├── interactions
│       │       ├── pages
│       │       ├── runner
│       │       ├── steps
│       │       ├── utils
│       └── resources
│           └── features
├── pom.xml
└── README.md
```

---

## Descrição dos Diretórios e Arquivos

### Diretórios Principais

- **`src/main/java`**  
  Contém o código de produção, incluindo módulos e lógica de negócio essenciais para o sistema.

  _ps: no dia-a-dia de empresas pode ser comum não haver códigos aqui, passando a utilizar somente a pasta 'test'_

- **`src/test/java`**  
  Local dos testes automatizados. Subdividido em:
  - **`interactions`**: Implementação de ações e interações reutilizáveis no sistema.
  - **`pages`**: Páginas mapeadas no padrão Page Object Model.
  - **`runner`**: Configuração e execução de cenários de testes.
  - **`steps`**: Passos definidos no formato de BDD (ex.: Gherkin para Cucumber).
  - **`utils`**: Classes utilitárias para funções comuns, como manipulação de dados e logs.

- **`src/test/resources`**  
  Contém:
  - **`features`**: Arquivos `.feature` do Cucumber, onde os cenários de teste são definidos.

---

### Arquivos Essenciais

- **`pom.xml`**  
  Arquivo de configuração do Maven. Define dependências, plugins e configurações de build do projeto.

- **`README.md`**  
  Documentação do projeto, contendo informações sobre a configuração, execução e manutenção.

---

Essa estrutura organiza o código de maneira que facilite a colaboração em equipe e escalabilidade do projeto. Adicione comentários e documentações claras para que novos membros possam se integrar facilmente.
