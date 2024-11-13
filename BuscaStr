#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

// Função para comparar os primeiros caracteres de duas strings, ignorando maiúsculas e minúsculas
int comparaPrefixoIgnoreCase(const char *str, const char *prefixo) {
    while (*prefixo) {
        if (tolower((unsigned char)*str) != tolower((unsigned char)*prefixo)) {
            return 0;  // Prefixo não corresponde
        }
        str++;
        prefixo++;
    }
    return 1;  // Prefixo corresponde
}

// Função de busca binária para encontrar o índice da primeira ocorrência do prefixo
int buscaBinariaPrefixo(char *v[], int n, const char *prefixo) {
    int s = 0, e = n - 1;
    int lenPrefixo = strlen(prefixo);
    int resultado = -1;

    while (s <= e) {
        int m = (s + e) / 2;

        // Usando comparaPrefixoIgnoreCase para a busca binária
        if (comparaPrefixoIgnoreCase(v[m], prefixo)) {
            // Se o prefixo é encontrado, guarda o índice e continua à esquerda para encontrar a primeira ocorrência
            resultado = m;
            e = m - 1;
        } else if (strncasecmp(v[m], prefixo, lenPrefixo) < 0) {
            s = m + 1;  // Prefixo está à direita
        } else {
            e = m - 1;  // Prefixo está à esquerda
        }
    }
    return resultado;  // Retorna o índice ou -1 se não encontrado
}

// Função para imprimir todos os resultados que começam com o prefixo
void imprimirResultados(char *v[], int n, const char *prefixo) {
    int index = buscaBinariaPrefixo(v, n, prefixo);

    if (index == -1) {
        printf("Nenhum nome encontrado com o prefixo: %s\n", prefixo);
        return;
    }

    printf("Palavras que começam com '%s':\n", prefixo);

    // Imprime os nomes que começam com o prefixo, partindo do índice encontrado
    int i = index;
    while (i < n && comparaPrefixoIgnoreCase(v[i], prefixo)) {
        printf("%s\n", v[i]);
        i++;
    }
}

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

int main() {
    FILE *arquivo;
    char *nome[101];
    int n = 0;
    char tecas[21];

    // Abrindo o arquivo para leitura
    arquivo = fopen("nomes.txt", "r");

    if (arquivo == NULL) {
        printf("Erro ao abrir o arquivo.\n");
        return 1;
    }

    char buffer[100];
    while (fgets(buffer, sizeof(buffer), arquivo) != NULL && n < 101) {
        buffer[strcspn(buffer, "\n")] = 0;  // Remove o '\n' do final da linha
        nome[n] = (char *)malloc(strlen(buffer) + 1);
        strcpy(nome[n], buffer);
        n++;
    }
    fclose(arquivo);

    // Ordena os nomes ignorando maiúsculas e minúsculas
    //qsort(nome, n, sizeof(char *), (int (*)(const void *, const void *))strcasecmp);

    // Solicitando o prefixo para busca
    printf("Digite o prefixo que deseja buscar: \n");
    fgets(tecas, sizeof(tecas), stdin);
    tecas[strcspn(tecas, "\n")] = '\0';

    // Imprime os resultados da busca
    quickSort(nome, 0, n-1);
    imprimirResultados(nome, n, tecas);

    // Liberando a memória alocada
    for (int i = 0; i < n; i++) {
        free(nome[i]);
    }

    return 0;
}
