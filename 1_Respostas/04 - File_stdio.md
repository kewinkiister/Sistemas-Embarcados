

Para todas as questões, utilize as funções da biblioteca stdio.h de leitura e de escrita em arquivo (fopen(), fclose(), fwrite(), fread(), dentre outras). Compile os códigos com o gcc e execute-os via terminal.

1 -    Crie um código em C para escrever "Ola mundo!" em um arquivo chamado 'ola_mundo.txt'.

```
      #include<stdio.h>
      #include<stdlib.h>
      #include<string.h>

      int main(){
      FILE *fp;
      char string[100];
      fp = fopen("ola_mundo.txt","w");

            if(!fp){
                printf("Erro na abertura do arquivo");
            exit(0);}

      fprintf (fp, "Ola mundo!\n");
      fclose(fp);
      return 0;
      }
```

2 -  Crie um código em C que pergunta ao usuário seu nome e sua idade, e escreve este conteúdo em um arquivo com o seu nome e extensão '.txt'. Por exemplo, considerando que o código criado recebeu o nome de 'ola_usuario_1':

```
      #include<stdio.h>
      #include<stdlib.h>
      #include<string.h>

      int main(){
      FILE *fp;
      char string1[100];
      int i, idade;
      fp = fopen("rodrigo.txt","w");

            if(!fp){
                printf("Erro na abertura do arquivo");
            exit(0);}

      printf("Nome: ");
      scanf("%[^\n]", string1);

      printf("Idade: ");
      scanf(" %d", &idade);
      
      fprintf(fp,"Nome: %s", string1);
      fprintf(fp,"\nIdade: %d anos\n", idade);
      fclose(fp);
      return 0;
      }

      $ ./questao4_2
      $ Digite o seu nome: Rodrigo
      $ Digite a sua idade: 23
      $ cat rodrigo.txt
      $ Nome: Rodrigo
      $ Idade: 23 anos
```

3 -    Crie um código em C que recebe o nome do usuário e e sua idade como argumentos de entrada (usando as variáveis argc e *argv[]), e escreve este conteúdo em um arquivo com o seu nome e extensão '.txt'. Por exemplo, considerando que o código criado recebeu o nome de 'ola_usuario_2':
   
```
      #include<stdio.h>
      #include<stdlib.h>
      #include<string.h>

      int main(int argc, const char * argv[]){
      FILE *fp;
      int i;
      fp = fopen("rodrigo4_2.txt","w");

            if(!fp){
                printf("Erro na abertura do arquivo");
            exit(0);}

      for(i=1; i < argc; i++){
            if(i=1){
                  fprintf(fp, "Nome: %s\n", argv[i]);
                  }
            if(i=2){
                  fprintf(fp, "Idade: %s anos\n", argv[i]);
                  }

            }
      fclose(fp);
      return 0;
      }
     
      $ ./ola_usuario_2 Rodrigo 23
      $ cat rodrigo4_2.txt
      $ Nome: Rodrigo
      $ Idade: 23 anos
```

4 -    Crie uma função que retorna o tamanho de um arquivo, usando o seguinte protótipo: int tam_arq_texto(char *nome_arquivo); Salve esta função em um arquivo separado chamado 'bib_arqs.c'. Salve o protótipo em um arquivo chamado 'bib_arqs.h'. Compile 'bib_arqs.c' para gerar o objeto 'bib_arqs.o'.
      


   5 - Crie uma função que lê o conteúdo de um arquivo-texto e o guarda em uma string, usando o seguinte protótipo: char* le_arq_texto(char *nome_arquivo); Repare que o conteúdo do arquivo é armazenado em um vetor interno à função, e o endereço do vetor é retornado ao final. (Se você alocar este vetor dinamicamente, lembre-se de liberar a memória dele quando acabar o seu uso.) Salve esta função no mesmo arquivo da questão 4, chamado 'bib_arqs.c'. Salve o protótipo no arquivo 'bib_arqs.h'. Compile 'bib_arqs.c' novamente para gerar o objeto 'bib_arqs.o'.

  6 -  Crie um código em C que copia a funcionalidade básica do comando cat: escrever o conteúdo de um arquivo-texto no terminal. Reaproveite as funções já criadas nas questões anteriores. Por exemplo, considerando que o código criado recebeu o nome de 'cat_falsificado':
     
```
      #include<stdio.h>
      #include<stdlib.h>
      #include<string.h>

      int main(int argc, char*argv[]){
      FILE *fp;
      int i;
      char c;
      char arquivo[100];

      for(i=1; i < argc; i++){
            fp = fopen(argv[i],"r");
      }
            if(!fp){
                printf("Erro na abertura do arquivo");
            exit(-1);}

      while((c = getc(fp)) != EOF){
            printf("%c", c);
      }
      fclose(fp);

      return 0;
      }
      
$ echo Ola mundo cruel! Ola universo ingrato! > ola.txt
$ ./cat_falsificado ola.txt
$ Ola mundo cruel! Ola universo ingrato!
```

  7 -  Crie um código em C que conta a ocorrência de uma palavra-chave em um arquivo-texto, e escreve o resultado no terminal. Reaproveite as funções já criadas nas questões anteriores. Por exemplo, considerando que o código criado recebeu o nome de 'busca_e_conta':
  
 ```
$ echo Ola mundo cruel! Ola universo ingrato! > ola.txt
$ ./busca_e_conta Ola ola.txt
$ 'Ola' ocorre 2 vezes no arquivo 'ola.txt'.
```

