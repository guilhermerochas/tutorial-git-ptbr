# Tutorial da ferramenta de Versionamento Git

O git se tornou uma ferramenta essencial na vida de grande parte de desenvolvedores que trabalham em projetos em equipe atualmente, se tornando a mais popular no quesito e sendo usado pelas maiores empresas no mercado hoje em dia, por sua modernidade, facilidade e código aberto.
Criado por Linus Torvaldos (Conhecido pelo desenvolvimento do Kernel do GNU/Linux), o Git é um Sistema de Controle de Versão que ajuda no controle de fluxo de projetos, gerando para ele historicos de alterações, tratamento de conflito na alteração de um mesmo arquivo, ramificações (branchs) que ajudam no controle de testes e features isolando de algo que já esteja funcionando e a possibilidade de manter o código guardado em repositórios como GitHub, GitLab ou Azure Devops, sem a necessidade de trocar os comandos para utilizar.

## O Tutorial

Nesse tutorial quero te mostrar a usar principalmente a linha de comando, mesmo que editores de código como Visual Studio Code possuam ferramentas e extensões para utilizar de uma maneira mais visual, o terminal ainda tem grandes vantagens e ainda lhe dará a maior parte das opções possiveis.

Para isso é preciso instalar o git, no caso do GNU/Linux ele pode ser instalado pelos gerenciadores de pacote como `yum` para sistemas baseados em Red Hat ou `apt` para baseados em Debian com o seguinte comando 

```bash
sudo apt install git-all #ou
sudo yum install git-all
```

No caso do MacOSX, se você tiver o `brew` você pode instalar facilmente com

```bash
brew install git
```

Para Windows é necessario baixar o [Git Bash](https://git-scm.com/download/win) para melhor usabilidade

Para mais informações acesse o seguinte website: [Instalando o Git](https://git-scm.com/book/pt-br/v2/Come%C3%A7ando-Instalando-o-Git)

### Inicializando um projeto com o git

Para inicializar um projeto localmente com o git é possivel com o seguinte comando dentro do diretório do projeto:

```bash
git init
```

A partir disso qualquer alteração dentro do projeto poderá ser registrada e controlada.

### Como alterações funcionam

Quando você inicializa o git em um projeto com `git init` a ferramenta cria para você uma branch (geramente chamada master) e um arquivo chamado .git que apenas é visivel caso digite `ls -a` em algum terminal bash (ou para windows o git bash), não remova a pasta .git pois ela guarda o registro de alterações.

O git trabalha com um sistema chamado commit. Um commit é o ato de tornar permanente uma ou um conjunto de alterações feitas podendo ser até mesmo etiquetadas por mensagens como "adiçaõ do arquivo arquivo.txt", ou seja, caso você adicione um arquivo naquele diretorio o git inicialmente não irá reconhecer e nem gravar o historico de alterações.

![inicialização e adição de arquivo](https://github.com/guilhermerochas/tutorial-git-ptbr/blob/main/imgs/exemplo_init.png)

No exemplo acima fazemos os seguintes passos: criamos um diretório, inicializamos o git dentro dele, criamos um arquivo simples e, com o comando `git status`, checamos o historico de alterações. É mostrado que o arquivo que adicionamos não é possivel de ser registrada pelo historico e para isso precisamos adiciona-la.

Vamos usar o seguinte comando:

```bash
git add <arquivo> #caso queira adicionar um conjunto de arquivos, vá a raiz do projeto e digite: git add .
git commit #caso queira adicionar um comentario da alteração pode com: git commit -m "<comentario>"
```

![primeiro commit](https://github.com/guilhermerochas/tutorial-git-ptbr/blob/main/imgs/primeiro_commit.png)

Vemos que agora o git não reclama mais do arquivo e podemos seguir em frente. Vamos supor que aquele arquivo é um arquivo que nós nao queremos que o git tenha mais conhecimento dele para remover depois, para fazer isso use:

```bash
git rm --cached <arquivo>
```

### Mostrando o Histórico 

Você no momento fez vários commits e adições no seu projeto e agora você quer ver o historico dessas alterações:

```bash
git log
```

Ele irá te mostrar todas as alterações já feitas naquele projeto junto com um id para cada commit. Caso você queira apenas ver as ultimas 10 alterações do projeto pode usar:

```bash
git log -n 10
```

Mas como saber o que aquele commit especifico fez no meu projeto? use o `git show`:
```bash
git show <parte_do_id>
```

### Ramificações (ou branchs)

O git possui um sistema muito bom chamado branches, que no caso são ramificações que podem isolar o desenvolvimento do projeto, sendo possivel criar varias ramificações para por exemplo produção, desenvolvimento, uma nova feature. 
Como foi mostrado usando o Git Bash para windows, a branch que estamos utilizando aparece logo acima entre parênteses, mas em alguns shells mais antigos como `sh` ou `bash` não possuem essa opção, para verificar a branch atual use:

```bash
git branch
```

que ele irá mostrar com um `*` a branch atual sendo utilizada. Para criar uma nova branch use:

```bash
git checkout -b <nome_branch>
```

Ele irá criar e automaticamente mudar para a nova ramificação. se quiser voltar apenas use `git checkout <nome_branch>` para voltar para a existente.

### Repositórios

Até agora o que eu mostrei foram apenas modificações locais mas geralmente git é necessário quando temos uma equipe trabalhando e fazendo commits para um local que podemos facilmente acessar e fazer nossos commits tambem. para isso temos o repositório de código, como o proprio GitHub por exemplo, onde podemos mandar nossas alterações e obter a ultima versão do historico de alterações.

Vamos primeiro criar um novo repositório, que pode ser feito com a ajuda desse [Tutorial](https://docs.github.com/pt/free-pro-team@latest/github/getting-started-with-github/create-a-repo).

Agora existe algumas maneiras de como podemos adicionar de como podemos linkar nosso repositorio com nosso projeto atual, nesse tutorial irei mostrar duas das maneiras que vi que são mais utilizadas.

- Clonar o projeto, mover os arquivos nos quais estava trabalhando para o clone, adicionar eles ao repositório e mandar as alterações para o repositório

```bash
git clone <url_do_repositório> #se quiser adicionar um nome diferente á pasta criada use: git clone <url_do_repositório> <nome_pasta>
cd <nome_repositório>
mv ../caminho/do/projeto/* .
git add .
git commit -m "<comentario>"
git push origin <branch_remota>
```

Vimos comandos novos até o momento, vamos explicar cada um: </br>
`git clone <url_do_repositório>`: ele faz um clone de tudo o que está no repositório remoto para dentro de uma pasta do seu computador. </br>
`git push origin <branch>`: esse comando manda todos os commits que não estão no repositório para ele, agora sendo visivel por todo o time. `origin` nesse caso é o nome que o repositório dá para o clone do projeto para ter uma maneira de identificar para onde que os commits devem ir. </br>


- Dentro do projeto adicionar um link remoto, pegar todas as alterações do repositório remoto, e mandar as alterações. dentro do projeto git digite:

```bash
git remote add <nome_remoto> <url_do_repositório>
git pull <nome_remoto> <branch_remota>
git push <nome_remoto> <branch_remota>
```

é possivel que de um erro com a mensagem dizendo que o git se recusa a fazer o merge de históricos não relacionados, o que é possivel de se resolver com o comando:
```bash
git pull <nome_remoto> <branch_remota> --allow-unrelated-histories
```

