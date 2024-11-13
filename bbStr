#include<stdio.h>
#include<stdlib.h>
#include<string.h>

void troca(char *nome[], int a, int b) {
    char *aux = nome[a];
    nome[a] = nome[b];
    nome[b] = aux;
}

// Complexidade de espaco: O(1)
// Complexidade de tempo: O(n^2)
void bubbleSort(char *nome[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - 1; j++) {
            if (strcmp(nome[j], nome[j + 1]) > 0) {
                troca(nome, j, j + 1);
            }
        }
    }
}

void imprimirVetor(char *nome[], int n) {
    for (int i = 0; i < n; i++) {
        printf("%s", nome[i]);
    }
    printf("\n");
}

int main() {
    FILE *arquivo;
    char *nome[101];
    int n = 0;

    arquivo = fopen("nomes2.txt", "r");

    if(arquivo == NULL){
        printf("Erro ao abrir o arquivo.\n");
        return 1;
    }

    char buffer[20];
    while(fgets(buffer, sizeof(buffer), arquivo)!= NULL && n<101){
        nome[n] = (char *)malloc(strlen(buffer) + 1);
        strcpy(nome[n], buffer);
        n++;
    }
    fclose(arquivo);

    bubbleSort(nome,n);
    imprimirVetor(nome, n);

    for(int i = 0; i < n; i++){
        free(nome[i]);
    }
    return 0;
}
