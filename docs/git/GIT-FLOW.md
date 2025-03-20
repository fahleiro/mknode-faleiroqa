
# GIT FLOW

### O que é?
**Git Flow** é uma estratégia de branching que organiza o desenvolvimento em diferentes tipos de branches, facilitando a colaboração e o controle de versões.

### Principais Branches
- **`main`**: contém o código em produção.
- **`develop`**: contém o código em desenvolvimento.

### Branches Auxiliares
- **`feature`**: para desenvolver novas funcionalidades.
- **`release`**: para preparar uma nova versão.
- **`hotfix`**: para corrigir problemas críticos em produção.

### Como Usar?
1. **Iniciar o Git Flow**:
   ```bash
   git flow init
   ```
2. **Criar uma feature**:
   ```bash
   git flow feature start nome-da-feature
   ```
3. **Finalizar uma feature**:
   ```bash
   git flow feature finish nome-da-feature
   ```
4. **Criar uma release**:
   ```bash
   git flow release start nome-da-release
   ```
5. **Finalizar uma release**:
   ```bash
   git flow release finish nome-da-release
   ```
6. **Criar um hotfix**:
   ```bash
   git flow hotfix start nome-do-hotfix
   ```
7. **Finalizar um hotfix**:
   ```bash
   git flow hotfix finish nome-do-hotfix
   ```

### Vantagens
- Organização clara do fluxo de trabalho.
- Separação entre desenvolvimento e produção.
- Suporte para várias releases simultâneas.

### Desvantagens
- Pode ser complexo para times pequenos ou projetos simples.

