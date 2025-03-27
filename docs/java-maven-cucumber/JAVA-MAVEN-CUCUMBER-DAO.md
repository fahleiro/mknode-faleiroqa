
# Integração com DAO no Projeto de Automação

## Introdução
O pacote `dao` é responsável por lidar com a interação com o banco de dados no projeto de automação de testes. Ele permite que dados sejam consultados, armazenados e manipulados diretamente, facilitando a validação e a verificação de informações.

## Estrutura Atualizada do Projeto
A estrutura do projeto é expandida para incluir o pacote `dao` na mesma hierarquia de `interactions`:

```
/projeto
├── src
│   ├── main
│   │   └── java
│   │       └── br/com/projeto/packages
│   ├── test
│       ├── java
│       │   └── br/com/projeto
│       │       ├── dao
│       │       │   ├── Connections.java
│       │       │   ├── ProdutoDAO.java
│       │       │   └── Produto.java
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

## Classes no Pacote `dao`

### 1. Classe `Connections`
Gerencia a conexão com o banco de dados MySQL.

```java
package br.com.projeto.dao;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class Connections {
    private static final String URL = "jdbc:mysql://localhost:3306/seubanco";
    private static final String USER = "seuusuario";
    private static final String PASSWORD = "suasenha";

    public static Connection openConnection() throws SQLException {
        System.out.println("Abrindo conexão com o banco de dados...");
        return DriverManager.getConnection(URL, USER, PASSWORD);
    }

    public static void closeConnection(Connection connection) {
        if (connection != null) {
            try {
                connection.close();
                System.out.println("Conexão com o banco de dados encerrada.");
            } catch (SQLException e) {
                System.err.println("Erro ao fechar a conexão: " + e.getMessage());
            }
        }
    }
}
```

### 2. Classe `Produto`
Representa um objeto que será manipulado pelo DAO.

```java
package br.com.projeto.dao;

public class Produto {
    private int id;
    private String nome;
    private double preco;

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getNome() {
        return nome;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public double getPreco() {
        return preco;
    }

    public void setPreco(double preco) {
        this.preco = preco;
    }
}
```

### 3. Classe `ProdutoDAO`
Gerencia as operações de banco de dados para a classe `Produto`.

```java
package br.com.projeto.dao;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class ProdutoDAO {

    public Produto buscarProdutoPorId(int id) {
        String query = "SELECT * FROM produtos WHERE id = ?";
        try (Connection connection = Connections.openConnection();
             PreparedStatement statement = connection.prepareStatement(query)) {

            statement.setInt(1, id);
            ResultSet resultSet = statement.executeQuery();

            if (resultSet.next()) {
                Produto produto = new Produto();
                produto.setId(resultSet.getInt("id"));
                produto.setNome(resultSet.getString("nome"));
                produto.setPreco(resultSet.getDouble("preco"));
                return produto;
            }
        } catch (SQLException e) {
            System.err.println("Erro ao buscar produto: " + e.getMessage());
        }
        return null;
    }
}
```

## Exemplo de Uso no Teste
Abaixo está um exemplo de interação com o DAO em um teste utilizando getters e setters.

```java
import br.com.projeto.dao.Produto;
import br.com.projeto.dao.ProdutoDAO;

public class TesteProdutoDAO {

    public static void main(String[] args) {
        ProdutoDAO produtoDAO = new ProdutoDAO();
        Produto produto = produtoDAO.buscarProdutoPorId(1);

        if (produto != null) {
            System.out.println("Produto encontrado:");
            System.out.println("ID: " + produto.getId());
            System.out.println("Nome: " + produto.getNome());
            System.out.println("Preço: " + produto.getPreco());
        } else {
            System.out.println("Produto não encontrado.");
        }
    }
}
```

---

Com essa estrutura e exemplos, o pacote `dao` estará integrado ao projeto de automação, possibilitando consultas eficientes e centralizadas ao banco de dados.
