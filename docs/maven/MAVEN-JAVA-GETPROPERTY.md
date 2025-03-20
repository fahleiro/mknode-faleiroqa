
# Como Usar o `getProperty` em Java com Maven CLI

## Introdução

No Maven, você pode passar propriedades personalizadas para o seu projeto durante a execução de testes via linha de comando. Essas propriedades podem ser acessadas dentro do código Java usando o método `System.getProperty()`. Isso permite que você defina valores diretamente pela linha de comando sem precisar modificar o código fonte ou os arquivos de configuração.

Neste guia, vamos mostrar como passar valores usando o comando `mvn test -Dproperty=propertyX` e como recuperar esses valores durante a execução de testes em Java.

## Passos para Configurar e Usar Propriedades via CLI do Maven

### 1. Definindo a Propriedade no Maven

Primeiro, você precisa passar a propriedade via linha de comando ao executar o Maven. O comando básico para passar uma propriedade é:

```bash
mvn test -Dproperty=propertyX
```

No comando acima, `-Dproperty=propertyX` define uma propriedade chamada `property` com o valor `propertyX`. Essa propriedade ficará disponível durante a execução dos testes.

### 2. Acessando a Propriedade no Código Java

Dentro do seu código Java, você pode acessar o valor dessa propriedade usando o método `System.getProperty()`. Aqui está um exemplo simples de como usar isso dentro de um teste:

#### Exemplo de código Java:

```java
import org.junit.Test;

import static org.junit.Assert.assertEquals;

public class PropertyTest {

    @Test
    public void testGetProperty() {
        // Recuperando o valor da propriedade 'property'
        String propertyValue = System.getProperty("property");

        // Exibindo o valor da propriedade (opcional)
        System.out.println("Valor da propriedade: " + propertyValue);

        // Validando que o valor da propriedade é igual a 'propertyX'
        assertEquals("propertyX", propertyValue);
    }
}
```

### 3. Executando o Teste

Com o código acima, ao executar os testes com o Maven e passando a propriedade pela linha de comando, o valor da propriedade será acessado dentro do teste.

Para rodar os testes, você pode usar o seguinte comando no terminal:

```bash
mvn test -Dproperty=propertyX
```

### 4. Resultado Esperado

Durante a execução do teste, o Maven irá passar o valor de `propertyX` para o código Java, e o método `System.getProperty("property")` retornará esse valor. O teste irá então validar se o valor recuperado é igual a `propertyX`.

**Saída esperada no console:**

```bash
Valor da propriedade: propertyX
```

E o teste será bem-sucedido se o valor da propriedade for igual a `propertyX`.

## Conclusão

Usar `System.getProperty()` em conjunto com o comando `mvn test -Dproperty=propertyX` é uma maneira eficiente de passar e recuperar propriedades durante a execução dos testes no Maven. Isso pode ser útil para configurar parâmetros dinâmicos, como URLs de ambientes, tokens de autenticação e outros valores que precisam ser ajustados sem alterar o código diretamente.

Essa abordagem é especialmente útil em integração contínua (CI), onde valores podem ser passados dinamicamente durante o processo de build e testes.