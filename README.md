# Criando repositórios
Todo controle de versão ocorre em repositórios de código. Para criá-los, utilizamos o comando **git init**. Entretanto, esse comando raramente será usado por você, pois ele criará um repositório somente na máquina local.

A forma mais tradicional de trabalhar é com um repositório remoto, digamos, criado no GitHub. Nesse caso, ao invés de criar um repositório do zero, você gerar um **clone** e sincronizá-lo de tempos em tempos.

Para fazer isso, usamos o comando **git clone**, seguido do nome do repositório. Isso criará na sua máquina local uma pasta, com a cópia do repositório remoto. Por exemplo, para clonar o repositório do código da JVM do OpenJDK, você poderia usar o comando: `git clone https://github.com/openjdk/jdk.git openjdk`

Isso criaria em sua máquina uma pasta chamada openjdk, com todo o código do repositório remoto dentro. A pasta criada em sua máquina será o repositório local. O repositório do Git de onde você clonou é o repositório remoto. O nome do repositório (dado no último parâmetro) é opcional e, se omitido, criará a pasta com o mesmo nome do repositório remoto (jdk, neste caso).

Todo código modificado, salvo no disco, compõe ainda um terceiro conceito, chamado cópia de trabalho. Isso porque você poderá restaurar um arquivo modificado na sua cópia de trabalho para a versão que está em seu repositório local a qualquer momento.

# Modificando arquivos no repositório
Todos os arquivos em um repositório podem ser controlados ou não controlados. Os arquivos controlados são aqueles que o Git está monitorando e saberá se foram ou não modificados, ou estão prestes a serem adicionados ao repositório (staged). 

Obviamente, você fez o clone de um repositório, todos os arquivos clonados em seu interior serão controlados e não modificados. Quando você modifica um arquivo, ele passará para o estado de arquivo modificado. E, quando você criar um arquivo novo, ele não será controlado. Sua IDE mostrará esses status de maneira visual.

Para que um **arquivo seja controlado**, é necessário utilizar o comando **git add**. Isso trocará a arquivo criado para um estado chamado de **staged**. Isto é, ele será adicionado ao repositório local assim que as modificações forem confirmadas. Você pode utilizar o comando de duas formas:

* git add : para adicionar um único arquivo.
* git add .: para adicionar todos os arquivos não controlados.
* 
Para excluir um arquivo, é possível utilizar o comando **git rm**. Ele excluirá o arquivo do disco, mas essa exclusão também será considerada staged. Isto é, ela também precisará ser confirmada. 

E como confirmamos essas modificações? Por meio do comando **git commit**. Ele não só enviará as informações ao repositório local, como também permitirá que você associe a elas uma mensagem de commit. Trata-se de um texto, no qual você descreve de maneira sucinta as modificações que fez. É esse texto que será exibido caso você queira ver o histórico das suas modificações.

# Mantendo arquivos não controlados
Algumas vezes, você poderá ter arquivos não controlados que deseja manter apenas em seu disco local, mas não os enviar para o repositório. Alguns exemplos de arquivos desse tipo seriam:

* Um arquivo desse tipo poderia ser o xml, em que estão as configurações do banco de dados que a aplicação usará, e que será diferente para cada desenvolvedor da equipe.
* Outra possibilidade seriam os arquivos específicos da sua IDE favorita, que não se referem ao código da aplicação em si.
* Os arquivos binários gerados pela JVM (.class, .java) e que podem ser recompilados por qualquer desenvolvedor.

Para evitar que um arquivo seja controlado, criamos um arquivo chamado *.gitignore* e colocamos lá dentro o nome do arquivo ou pastas que queremos ignorar. Isso evitará que ele seja adicionado caso o git add . seja utilizado.

Há, inclusive, uma variação do comando git rm, útil para quando queremos remover um arquivo do repositório, mas não do disco – por exemplo, um arquivo que você havia esquecido de adicionar ao .gitignore. É por meio da opção **--cached**, por exemplo: `git rm --cached README`.

# Revertendo alterações
Às vezes, você começou a editar um arquivo e se arrependeu, e gostaria de retorná-lo a versão que está atualmente em seu repositório. Para isso, deve utilizar o comando de **revert**. Ele exigirá o código do último commit, o que pode ser trabalhoso. Felizmente, sua IDE conseguirá obter essa informação automaticamente.

# Enviando arquivos ao repositório remoto
Por fim, você pode usar os comandos **git push** e **git pull** para enviar ou receber arquivos do repositório remoto.

Note que você pode trabalhar no repositório local por bastante tempo, antes de dar um push. Isso fará com que o Git agrupe todas as modificações necessárias e as envie de maneira muitíssimo eficiente. Na verdade, sua eficiência foi um dos atributos que o tornou tão popular.

 
