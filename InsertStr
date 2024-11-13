#include<stdio.h>
#include<stdlib.h>
#include<string.h>

void troca(char *nome[], int a, int b) {
    char *aux = nome[a];
    nome[a] = nome[b];
    nome[b] = aux;
}

// espaço O(1) tempo O(n^2)
void insertionSort(char *nome[], int n) {
    for (int i = 1; i < n; i++) {
        char *aux = nome[i];
        int j = i - 1;
        while(j >= 0 && strcmp(aux, nome[j]) < 0) {
            nome[j + 1] = nome[j];
            j--;
        }
        nome[j + 1] = aux;
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

    insertionSort(nome,n);

    printf("\nVetor apos a ordenacao:\n\n");
    imprimirVetor(nome, n);

    for(int i = 0; i < n; i++){
        free(nome[i]);
    }

    return 0;
}

