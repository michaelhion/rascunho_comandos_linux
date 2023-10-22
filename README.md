pwd --retorna o path de onde vc esta, serve pra te ajudar se localizar no sistema
ls -- lista o conteudo do diretório
ls -a --lista o conteudo do diretório e os arquivos ocultos
ls -l --lista com detalhes pode ser combinado com ls-a ficando ls -al
ll -- é um atalho para o comando ls -al
qualquer comando --help -- serve para dar detalhes sobre o comando e os parametros que ele aceita, mostra a documentação do comando
man comando -- mostra o manual do comando, para fechar é só digitar "q" que significa "quit"
cd -- muda diretorio "change dir"

OBS.: a hierarquia do sistema começa no "/", sendo todos os diretorios do sistema começam no barra, por exemplo o /etc,/var, 

"cd -"  --esse comando serve para voltar no diretorio anterior que vc estava, por exemplo se vc estiver no /var e antes estava no /opt vc pode usar esse comando para voltar para o /opt

OBS.: Quando usamos o comando ls -la tem uma coluna na lista que é somente "." ou "..", um ponto (".") significa o diretorio pai, dois pontos ("..") significa o diretorio parente, ou seja o diretorio que tiver dois pontos vai estar dentro do diretorio pai.

cd ~ -vai retornar para o /home

mkdir -- cria diretorio
"mkdir -p dir1/dir2/dir3" -- o "-p" indica que o dir2 sera parente do dir1 e o dir3 sera parente do dir2, isso facilita caso seja necessário criar um diretorio dentro do outro

cd~/labs --esse comando vai para a pasta labs que esta no home (supondo que exista essa pasta, mas pode ser qualquer pasta dentro do home)

touch -- cria arquivo

rmdir - apaga diretorios
rm - apaga arquivos

OBS.: rm também pode ser utilizado para apagar diretórios, sendo mais prático que o rmdir, para apagar diretorio usamos "-r" de recursividade. Essa recursividade significa que do ponto que estamos pra frente tudo sera apagado(Ex.: estou no dir1 e quero apagar tudo que estiver, no caso tenho isso dir2/dir3, sendo assim uso o rm -r para remover todos os outros diretorios e o que estiver nele de arquivo).

OBS.: o rm também pode ser usado com o "-f", esse -f força os arquivos serem removidos, sem o prompt perguntar nada, trecho da documentação é bem claro com isso "-f, --force           ignore nonexistent files and arguments, never prompt". O problema desse comando é que o que for apado não pode ser recuperado, pra isso é necessário voltar algum backup do sistema

OBS.: é possivel criar diretórios com letras letras maiusculas como por exemplo "Dir1", também é possivel criar diretorio que tenha espaço no nome, para fazer isso é necessário usar uma barra "\" assim para fazer o escape do espaço. Exemplo Diretorio\ 1

cp -copia arquivos de um diretorio para outro

OBS.: cp vai precisar do -r, só que com isso ele copia o diretorio e não o conteudo, para copiar corretamente podemos fazer de duas formas:
	1- entrar no diretorio que vai ser copiado e fazer cp -r * ../destino (isso se estiver no mesmo path, senão precisa ser o path completo)
	2- no diretorio raiz onde estão os dois diretorios fazer um "cp -r origem/* destino"
	3- se o diretorio de destino não existir posso fazer cp -rm origem destino

ls + path do diretorio - lista o conteudo do diretorio especifico de qualquer lugar
mv - move arquivos entre diretorios
OBS.: 1- se o diretorio não existir esse comando renomeia o diretorio
	  2- preciso criar o diretorio de destino para então mover os arquivos usando mv origem/* destino (estou pegando todo conteudo do oriem e enviado pro destino)
	  
	  
history -lista todos comandos utilizados no terminal

OBS.: "globbing" termo técnico para usar caracteres "coringas" (caracteres que representam qualquer coisa, por exemplo o * que significa tudo ou nada incluso,e o interrogação) exemplo.: tenho os arquivos arq  arq1  arq10  arq100  arq2  arq3  tmp1  tmp2, quero todos os arqs entre 10 e 19, então devo utilizar o seguinte comando ls arq1?. Digamos que quero qualquer arquivo que tenho "1" no nome então utilizo o "*1*" que significa qualquer coisa antes do "1" e depois do "1".Também é possivel especificar range de numeros e letras. Exemplo arq[1-5] (arq que tenha de 1 a 5),arq[1,3] (arq que tenha 1 ou 3), [A,a]rq[1-5] (especifica o "a" maiusculo ou minusculo)

cat -mostra conteudo do arquivo
grep -filtra uma palavra em um arquivo especifico. Exemplo grep http services, o parametro -i serve para ignorar maiusculas e minusculas, -l lista o nome do arquivo que tem o termo procurado, -L lista os arquivos que não tem o termo procurado
OBS.: Para diretorios dentro do diretorio raiz é necessário usar a recursividade -r, assim ele vai buscar em todas pastas a partir do ponto que estiver

more + nomeArquivo -mostra o conteudo do arquivo de forma paginada, sendo que a tecla de espaço serve para ir pra próxima pagina e a tecla "b" serve para voltar uma pagina (b de back), a tecla enter server para avançar uma linha

less + nomeArquivo - faz quase a mesma coisa que o more, só que a seta para cima e a seta para baixo serve para navegar entre as linha do arquivo, o espaço também serve para avançar uma pagina e o b para voltar essa pagina

tail - mostra as ultimas linhas do arquivo

head - mostra as primeras linhas do arquivo

tail -n numeroDeLinhas - é possivel especificar o numero de linha que o tail vai exibir por exemplo  tail -n 3 services (vai listar as ultimas 3 linhas do arquivo services)

head -n numeroDeLinhas - é possivel especificar o numero de linha que o tail vai exibir por exemplo  tail -n 3 services (vai listar as primeiras 3 linhas do arquivo services)

find nomeDiretorio -name nomeDoArquivo- procura arquivo em um diretorio, ele tem recursividade nele, também é possivel dizer que tipo de arquivo vc quer pesquisr por exemplo find / -name *.conf (ira buscar qualquer arquivo que contenha o final .conf a partir do diretorio "/")

find + nomeDiretorio -maxdepth 2 -ele só vai entrar dois niveis de subdiretórios, exemplo diretorio arq/sub1/sub2/sub3 nesse exemplo ele irá procurar ate o sub2
OBS.: doc do comando " -maxdepth levels
              Descend at most levels (a non-negative  integer)  levels  of  directories  below  the  starting-points.
              -maxdepth 0 means only apply the tests and actions to the starting-points themselves."
			  
find + nomeDiretorio -amin -5 - vai procurar arquivos modificados em um espaço de tempo em minutos, no caso em 5 minutos
find + nomeDiretorio -atime -2- vai procurar arquivos modificados em um espaço de tempo em dias, no caso em 2 dias
sudo find / -size +100M - com permissão de root vou pesquisar arquivos no diretorio / que contenham mais de 100 megas
find nomeDiretorio -iname - o iname faz ele ignorar o letras maiusculas e minusculas
  
 
