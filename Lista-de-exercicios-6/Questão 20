#include<stdio.h>
#include<stdlib.h>

#define MAX 4

int main () {

     FILE *pa;
     char nome[40];
     char linha[80];

     struct pessoa {
            char nome[40];
            int ano;
     } turma [MAX], back[MAX];

     int i;

     for (i=0; i<MAX; i++) {
         puts("Nome ? ");
         fgets(turma[i].nome, 40, stdin);
         puts("Ano  ? "); fgets(linha, 80, stdin);
         sscanf(linha, "%d", &turma[i].ano);
     }

     puts ("\nImprimindo\n");
     for (i=0; i<MAX; i++) {
         printf("Nome = %s\n", turma[i].nome);
         printf("Ano  = %d\n\n", turma[i].ano);
     }

     puts("\nGravando\n");
     puts("Qual o nome do arquivo?"); fgets(nome, 40, stdin);

     if (( pa = fopen(nome, "w+b")) == NULL ) {
        puts("Arquivo nao pode ser aberto");
        exit(1);
     }

     for (i=0; i<MAX; i++) {
         if (fwrite( &turma[i], sizeof (struct pessoa), 1, pa) != 1)
            puts("Erro na escrita.");
     }

     rewind(pa);

     for (i=0; i<MAX; i++) {
         if (fread( &back[i], sizeof (struct pessoa), 1, pa) != 1) {
            puts("Erro na escrita.");
            if (feof(pa)) break;
            puts("Erro na leitura.");
         }
     }

     puts("Imprimindo o vetor lido.");

     for (i=0; i<MAX; i++) {
         printf("Nome = %s\n", back[i].nome);
         printf("Ano  = %d\n\n", back[i].ano);
     }
     exit(0);
}
