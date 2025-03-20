
# COMANDOS GIT

### Clonar um repositório
```bash
git clone <url-do-repositorio>
```
- Clona um repositório remoto para o diretório local.

### Adicionar arquivos para o controle de versão
```bash
git add src/.../arquivo.final
```
- Adiciona arquivos específicos para o stage (área de preparação).  
- Pode ser usado como:
```bash
git add .
```
- Adiciona **todos os arquivos** do diretório atual (inclusive subdiretórios) para o stage.

### Criar um commit
```bash
git commit -m "comentario"
```
- Salva as mudanças no repositório local com uma mensagem descritiva.  
- Use mensagens claras, como:
```bash
git commit -m "Corrige erro na validação de formulários"
```

### Armazenar mudanças temporariamente
```bash
git stash
```
- Salva temporariamente as mudanças do seu diretório de trabalho e retorna ao último estado do repositório.  
- Útil quando você precisa mudar de branch rapidamente sem perder alterações não commitadas.  
- Para recuperar as mudanças:
```bash
git stash apply
```

### Exibir o status do repositório
```bash
git status
```
- Mostra os arquivos modificados, adicionados, ou não rastreados no repositório.

### Exibir histórico de commits
```bash
git log
```
- Mostra o histórico de commits.  
- Para um log mais compacto:
```bash
git log --oneline
```

### Sincronizar alterações com o repositório remoto
```bash
git pull
```
- Baixa e mescla as mudanças do repositório remoto na branch atual.

```bash
git push
```
- Envia os commits locais para o repositório remoto.

### Criar e alternar entre branches
```bash
git branch nome-da-branch
```
- Cria uma nova branch.

```bash
git checkout nome-da-branch
```
- Altera para a branch especificada.

```bash
git checkout -b nome-da-branch
```
- Cria e já alterna para a nova branch.

### Mesclar branches
```bash
git merge nome-da-branch
```
- Mescla as mudanças de outra branch para a branch atual.

### Apagar branches
```bash
git branch -d nome-da-branch
```
- Apaga uma branch já mesclada.  
- Para forçar a exclusão (mesmo sem mesclar):
```bash
git branch -D nome-da-branch
```

### Configurar usuário globalmente
```bash
git config --global user.name "Seu Nome"
git config --global user.email "seuemail@example.com"
```

---

### Dicas
- Antes de um `push`, sempre sincronize com o repositório remoto usando `git pull`.
- Use `git log --graph --oneline` para visualizar o histórico com um gráfico das branches.
- Sempre crie commits atômicos (pequenas mudanças relacionadas a um único objetivo).

<script type="text/javascript">
	atOptions = {
		'key' : '71a1dd532287ae867038be06f4a24109',
		'format' : 'iframe',
		'height' : 60,
		'width' : 468,
		'params' : {}
	};
</script>
<script type="text/javascript" src="//www.highperformanceformat.com/71a1dd532287ae867038be06f4a24109/invoke.js"></script>