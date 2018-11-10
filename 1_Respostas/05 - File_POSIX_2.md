

Para todas as questões, utilize as funções da norma POSIX (open(), close(), write(), read() e lseek()). Compile os códigos com o gcc e execute-os via terminal.

1 -    Crie um código em C para escrever "Ola mundo!" em um arquivo chamado 'ola_mundo.txt'.

    #include <stdio.h>
    #include <stdlib.h>
    #include <unistd.h>
    #include <fcntl.h>
    #include <termios.h>
    #include <string.h>

    int main(){
    char buf[30];
    int fp;

    fp = open("olamundo.txt", O_WRONLY | O_CREAT, S_IRWXU);	

     sprintf(buf,"Olá Mundo");
     write(fp,buf,strlen(buf));
     close(fp);

      return 0;
    }
  
2 -    Crie um código em C que pergunta ao usuário seu nome e sua idade, e escreve este conteúdo em um arquivo com o seu nome e extensão '.txt'. Por exemplo, considerando que o código criado recebeu o nome de 'ola_usuario_1':

  #include <stdio.h>
  #include <stdlib.h>
  #include <unistd.h>
  #include <fcntl.h>
  #include <termios.h>
  #include <string.h>

  int main(){

  char nome[30];
  char buf[30];
  int fp,idade, i=0;

  printf("Digite seu nome: ");
  scanf("%s", nome);
  printf("Digite sua idade: ");
  scanf("%d", &idade);

    fp = open("questao2.txt", O_WRONLY | O_CREAT, S_IRWXU);	

    sprintf(buf,"Nome: %s\nIdade: %d\n", nome, idade);
    write(fp,buf,strlen(buf));
    close(fp);

    return 0;
  }

$ ./ola_usuario_1
$ Digite o seu nome: Rodrigo
$ Digite a sua idade: 30
$ cat questao2.txt
$ Nome: Rodrigo
$ Idade: 30 anos

3 -     Crie um código em C que recebe o nome do usuário e e sua idade como argumentos de entrada (usando as variáveis argc e 
*argv[]), e escreve este conteúdo em um arquivo com o seu nome e extensão '.txt'. Por exemplo, considerando que o código criado 
recebeu o nome de 'ola_usuario_2':

  #include <stdio.h>
  #include <stdlib.h>
  #include <unistd.h>
  #include <fcntl.h>
  #include <termios.h>
  #include <string.h>

  int main(int argc, char*argv[]){

  char nome[30];
  char buf[60];
  int fp,idade, i=0;



    fp = open("questao2.txt", O_WRONLY | O_CREAT, S_IRWXU);	

    sprintf(buf,"Nome: %s\nIdade: %s\n", argv[1], argv[2]);
    write(fp,buf,strlen(buf));
    close(fp);

    return 0;
  }


$ ./ola_usuario_2 Eu 30
$ cat Eu.txt
$ Nome: Eu
$ Idade: 30 anos

4 -     Crie uma função que retorna o tamanho de um arquivo, usando o seguinte protótipo: int tam_arq_texto(char *nome_arquivo); 
Salve esta função em um arquivo separado chamado 'bib_arqs.c'. Salve o protótipo em um arquivo chamado 'bib_arqs.h'. 
Compile 'bib_arqs.c' para gerar o objeto 'bib_arqs.o'.

5 -    Crie uma função que lê o conteúdo de um arquivo-texto e o guarda em uma string, usando o seguinte protótipo: 
char* le_arq_texto(char *nome_arquivo); Repare que o conteúdo do arquivo é armazenado em um vetor interno à função, 
e o endereço do vetor é retornado ao final. (Se você alocar este vetor dinamicamente, lembre-se de liberar a memória 
dele quando acabar o seu uso.) Salve esta função no mesmo arquivo da questão 4, chamado 'bib_arqs.c'.
Salve o protótipo no arquivo 'bib_arqs.h'. Compile 'bib_arqs.c' novamente para gerar o objeto 'bib_arqs.o'.

6 -    Crie um código em C que copia a funcionalidade básica do comando cat: escrever o conteúdo de um arquivo-texto no terminal. 
Reaproveite as funções já criadas nas questões anteriores. Por exemplo, considerando que o código criado recebeu o nome de
'cat_falsificado':

$ echo Ola mundo cruel! Ola universo ingrato! > ola.txt
$ ./cat_falsificado ola.txt
$ Ola mundo cruel! Ola universo ingrato!

7 -     Crie um código em C que conta a ocorrência de uma palavra-chave em um arquivo-texto, e escreve o resultado no terminal. R
eaproveite as funções já criadas nas questões anteriores. Por exemplo, considerando que o código criado recebeu o nome de 
'busca_e_conta':

$ echo Ola mundo cruel! Ola universo ingrato! > ola.txt
$ ./busca_e_conta Ola ola.txt
$ 'Ola' ocorre 2 vezes no arquivo 'ola.txt'.


