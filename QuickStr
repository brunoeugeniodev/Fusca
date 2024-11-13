#include<stdio.h>
#include<stdlib.h>
#include<string.h>

void swap(char *nome[], int a, int b) {
    if (a == b) return;
    char *tmp = nome[a];
    nome[a] = nome[b];
    nome[b] = tmp;
}

int partition(char *nome[], int s, int e) { // O(n)
    char *pivot = nome[e];
    int i = s - 1;
    for (int j = s; j < e; j++) {
        if (strcmp(nome[j], pivot) < 0){
            swap(nome, ++i, j);
        }
    }
    swap(nome, i + 1, e);
    return i + 1;
}

// O(n log n) caso médio, O(n^2) pior caso
// complexidade de espaço O(1)
void quickSort(char *nome[], int s, int e) {
    if (s < e) {
        int p = partition(nome, s, e);
        //imprimir(v, 8);
        //printf("%d %d %d\n", s, p, e);
        quickSort(nome, s, p - 1);
        quickSort(nome, p + 1, e);
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

    quickSort(nome,0 ,n-1);

    printf("\nVetor apos a ordenacao:\n\n");
    imprimirVetor(nome, n);

    for(int i = 0; i < n; i++){
        free(nome[i]);
    }

    return 0;
}
