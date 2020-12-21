# Tutorial da ferramenta de Versionamento Git

O git se tornou uma ferramenta essencial na vida de grande parte de desenvolvedores que trabalham em projetos em equipe atualmente, se tornando a mais popular no quesito e sendo usado pelas maiores empresas no mercado hoje em dia, por sua modernidade, facilidade e código aberto.
Criado por Linus Torvaldos (Conhecido pelo desenvolvimento do Kernel do GNU/Linux), o Git é um Sistema de Controle de Versão que ajuda no controle de fluxo de projetos, gerando para ele historicos de alterações, tratamento de conflito na alteração de um mesmo arquivo, ramificações (branchs) que ajudam no controle de testes e features isolando de algo que já esteja funcionando e a possibilidade de manter o código guardado em repositórios como GitHub, GitLab ou Azure Devops, sem a necessidade de trocar os comandos para utilizar.

## O Tutorial

Nesse tutorial quero te mostrar a usar principalmente a linha de comando, mesmo que editores de código como Visual Studio Code possuam ferramentas e extensões para utilizar de uma maneira mais visual, o terminal ainda tem grandes vantagens e ainda lhe dará a maior parte das opções possiveis.

Para isso é preciso instalar o git, no caso do GNU/Linux ele pode ser instalado pelos gerenciadores de pacote como `yum` para sistemas baseados em Red Hat ou `apt` para baseados em debian com o seguinte comando 

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

