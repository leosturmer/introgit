# Introdução ao GIT

## Inicializar um repositório

Para inicializar um novo repositório do Git:

```bash
mkdir nome_projeto
cd nome_projeto
git init
```

Configurar dados do usuário do repositório:

```bash
git config --local user.name [nome do usuário]
git config --local user.email [e-mail do usuário]

Exemplo: 

git config --local user.name leosturmer
git config --local user.email leosturmer@email.com

```

> **Obs. 1.** Não utilize seu e-mail verdadeiro, pois ele será inveiado junto com seus commits para o repositório remoto e ficará visível a spammers e outros tipos de abusos.
>
> **Obs. 2.** `[]` significa que o parâmetro é opcional, enquanto `<>` indica que é obrigatório

Após estes comandos, você terá um repositório vazio e um diretório de trabalho contendo apenas o diretório `.git`. ele não é visível, a não ser com o comando:

```bash
no Linux e MacOS
ls -la

no Windows
dir /a

Pasta de C:\pasta

08/07/2025  09:44    <DIR>          .
08/07/2025  09:44    <DIR>          ..
08/07/2025  09:43    <DIR>          .git
08/07/2025  10:02               469 README.md
               1 arquivo(s)            469 bytes
               3 pasta(s)   41.997.410.304 bytes disponíveis
```

## Fazer um commit

Para fazer um commit, precisamos ter alguma modificação feita no diretório do projeto.

> Commits registram no repositório as modificações feitas nos arquivos do projeto.

Vamos acrescentar um arquivo novo. Essa será nossa modificação.

No Linux:
```bash
$ echo "# Novo projeto" > README.md 
```

No Windows:
```cmd
> echo "# Novo projeto" > README.md
```

### Verificar modificações

Verificamos as modificações feitas no repositório usando `git status`. 

```bash
$ git status
```

O resultado será algo como:

```bash
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)
```

### Adicionar arquivo ao `STAGE`

`Stage` é uma área virtual onde ficam "empilhados" os arquivos e modificações que entrarão *no próximo commit*. Uma espécie de "fila de espera" ou "preparação para o commit".

Para adicioanr uma arquivo aos que entrarão no próximo commit:

```bash
$ git add <arquivo>

Exemplo:

$ git add README.md
```

Se conferirmos status do repositório agora, veremos que o arquivo `README.md` tem *status* de **NEW**.

```bash
$ git status

On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md
```

### Commit

O commit exige uma lingha de documentação para ser adicionada ao registro feito no repositório. Por isso, o commit é feito em duas partes:

Primeiro damos o comando:
```bash
$ git commit 
```

Depois, é aberto um editor de texto onde devemos escrever a documentação. ela deve dizer **o que foi feito nesta alteração**. 

> Por padrão, o Git usa o editor `Vim`. 
>
> Para digitar, é necessário clicar na tecla `<i>`. Ao finalizar, apertar a tecla `<ESC>` e digitar o comando `<:wq>` (*write* e *quit*). Após dar enter o Vim será fechado e voltará para a tela do Bash.

## Lendo o log do repositório

Para ver a lista dos commits feitos no repositório:

```bash
$ git log
```

Exemplo de saída:

```bash
commit 4f28138d437c340cd9117d7d5d564dc574fe07ba (HEAD -> main)
Author: leosturmer <leosturmer@email>
Date:   Tue Jul 8 11:29:48 2025 -0300

    Primeiro commit
```

