#include<stdio.h>
#include<stdlib.h>
#include<string.h>

// Complexidade de tempo e espaço = O(n)
void merge(char *nome[], int s, int m, int e) {
    char *tmp[(e - s) + 1];
    int i = s, j = m + 1, k = 0;
    while (i <= m && j <= e) {
        tmp[k++] = (strcmp(nome[i], nome[j]) < 0) ? nome[i++] : nome[j++];
    }
    while (i <= m) {
        tmp[k++] = nome[i++];
    }
    while (j <= e) {
        tmp[k++] = nome[j++];
    }
    for (i = s, k = 0; i <= e; i++, k++) {
        nome[i] = tmp[k];
    }
}

// Complexidade de tempo O(n log n) e espaço O(n)
void mergeSort(char *nome[], int s, int e) {
    if (s < e) {
        int m = (s + e) / 2;
        //printf("%d %d %d\n", s, m, e);
        mergeSort(nome, s, m);
        mergeSort(nome, m + 1, e);
        merge(nome, s, m, e);
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

    mergeSort(nome, 0, n-1);

    printf("\nVetor apos a ordenacao:\n\n");
    imprimirVetor(nome, n);

    for(int i = 0; i < n; i++){
        free(nome[i]);
    }

    return 0;
}
