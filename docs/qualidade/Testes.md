# Testes

## Estrutura Básica

1. **Cenario**
   - Identificar se o teste é negativo ou não - utilizar o termo `NEG` para NEGATIVOS
   - O que será testado
      - Padrão: _`Processo X` de `massa de dados YZ`_
      - Exemplo teste Normal: _Validar `login` `de usuario cadastrado`_
      - Exemplo teste Negativo: _`[NEG]` Validar `login` `de usuario não cadastrado`_

1. **Primeira Step**
   - Captura e validação de dados necessários
      - Padrão: _Dado que possuo `algo`_
      - Exemplo: _Dado que possuo `um usuário`_

2. **Segunda Step**
   - Execução da ação
   - Padrão: _Quando realizo `algo`_
   - Exemplo: _Quando realizo `login`_

3. **Terceira Step**
   - Validação dos resultados da ação
      - Padrão: _Entao valido `algo`_
      - Exemplo: _Entao valido `o elemento`_

   
## Ordem de Execução
   - Captura de dados
   - Validação dos dados
   - Execução das ações
   - Validação dos resultados da ação

## Exemplo de .feature

```gherkin
Feature: Login do Sistema

  @test1
  Scenario: Validar login de usuario cadastrado
    Dado que possuo um usuário
    Quando realizo login
    Entao valido o acesso ao sistema

  @test2
  Scenario: [NEG] Validar login de usuario não cadastrado
    Dado que possuo um usuário não cadastrado
    Quando realizo login com credenciais inválidas
    Entao valido a mensagem de erro

  @test3
  Scenario: Validar fluxo completo de cadastro e login
    Dado que possuo um novo usuário
    Quando realizo o cadastro do usuário
    E realizo login com as credenciais cadastradas
    Entao valido o acesso ao sistema
```
