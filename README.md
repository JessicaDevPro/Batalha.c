# Batalha.c
#include <stdio.h>
#include <stdlib.h>

// Nível Novato - Funções básicas
void nivel_novato() {
    printf("=== NÍVEL NOVATO ===\n");
    printf("Tabuleiro 5x5 - 2 Navios (Vertical e Horizontal)\n\n");
    
    // Tabuleiro 5x5
    int tabuleiro[5][5] = {0};
    
    // Navio vertical (3 posições)
    int navio_vertical[3][2] = {
        {1, 1},  // linha 1, coluna 1
        {2, 1},  // linha 2, coluna 1  
        {3, 1}   // linha 3, coluna 1
    };
    
    // Navio horizontal (3 posições)
    int navio_horizontal[3][2] = {
        {2, 2},  // linha 2, coluna 2
        {2, 3},  // linha 2, coluna 3
        {2, 4}   // linha 2, coluna 4
    };
    
    // Posicionar navios no tabuleiro
    for(int i = 0; i < 3; i++) {
        tabuleiro[navio_vertical[i][0]][navio_vertical[i][1]] = 1;
        tabuleiro[navio_horizontal[i][0]][navio_horizontal[i][1]] = 1;
    }
    
    // Exibir coordenadas dos navios
    printf("Coordenadas do Navio Vertical:\n");
    for(int i = 0; i < 3; i++) {
        printf("(%d, %d) ", navio_vertical[i][0], navio_vertical[i][1]);
    }
    printf("\n");
    
    printf("Coordenadas do Navio Horizontal:\n");
    for(int i = 0; i < 3; i++) {
        printf("(%d, %d) ", navio_horizontal[i][0], navio_horizontal[i][1]);
    }
    printf("\n\n");
    
    // Exibir tabuleiro
    printf("Tabuleiro (0=vazio, 1=navio):\n");
    for(int i = 0; i < 5; i++) {
        for(int j = 0; j < 5; j++) {
            printf("%d ", tabuleiro[i][j]);
        }
        printf("\n");
    }
    printf("\n");
}

// Nível Aventureiro - Tabuleiro expandido com diagonais
void nivel_aventureiro() {
    printf("=== NÍVEL AVENTUREIRO ===\n");
    printf("Tabuleiro 10x10 - 4 Navios (Vertical, Horizontal, 2 Diagonais)\n\n");
    
    // Tabuleiro 10x10
    int tabuleiro[10][10] = {0};
    
    // Navio vertical (4 posições)
    for(int i = 2; i < 6; i++) {
        tabuleiro[i][2] = 1;
    }
    
    // Navio horizontal (4 posições)
    for(int j = 5; j < 9; j++) {
        tabuleiro[3][j] = 1;
    }
    
    // Navio diagonal direita (3 posições)
    for(int k = 0; k < 3; k++) {
        tabuleiro[1 + k][6 + k] = 1;
    }
    
    // Navio diagonal esquerda (3 posições)
    for(int k = 0; k < 3; k++) {
        tabuleiro[7 + k][3 - k] = 1;
    }
    
    // Exibir tabuleiro completo
    printf("Tabuleiro 10x10 (0=vazio, 1=navio):\n");
    printf("   ");
    for(int j = 0; j < 10; j++) {
        printf("%d ", j);
    }
    printf("\n");
    
    for(int i = 0; i < 10; i++) {
        printf("%d: ", i);
        for(int j = 0; j < 10; j++) {
            printf("%d ", tabuleiro[i][j]);
        }
        printf("\n");
    }
    printf("\n");
}

// Nível Mestre - Habilidades especiais
void nivel_mestre() {
    printf("=== NÍVEL MESTRE ===\n");
    printf("Habilidades Especiais: Cone, Cruz e Octaedro\n\n");
    
    // Matriz para habilidades (5x5 cada)
    int cone[5][5] = {0};
    int cruz[5][5] = {0};
    int octaedro[5][5] = {0};
    
    // Habilidade Cone
    printf("Habilidade CONE:\n");
    for(int i = 0; i < 5; i++) {
        int largura;
        if(i == 0) largura = 1;
        else if(i == 1) largura = 3;
        else largura = 5;
        
        int inicio = (5 - largura) / 2;
        for(int j = inicio; j < inicio + largura; j++) {
            cone[i][j] = 1;
        }
    }
    
    // Exibir cone
    for(int i = 0; i < 5; i++) {
        for(int j = 0; j < 5; j++) {
            printf("%d ", cone[i][j]);
        }
        printf("\n");
    }
    printf("\n");
    
    // Habilidade Cruz
    printf("Habilidade CRUZ:\n");
    for(int i = 0; i < 5; i++) {
        for(int j = 0; j < 5; j++) {
            // Linha do meio ou coluna do meio
            if(i == 2 || j == 2) {
                cruz[i][j] = 1;
            }
        }
    }
    
    // Exibir cruz
    for(int i = 0; i < 5; i++) {
        for(int j = 0; j < 5; j++) {
            printf("%d ", cruz[i][j]);
        }
        printf("\n");
    }
    printf("\n");
    
    // Habilidade Octaedro
    printf("Habilidade OCTAEDRO:\n");
    for(int i = 0; i < 5; i++) {
        for(int j = 0; j < 5; j++) {
            // Pontas superior, inferior e meio
            if((i == 0 && j == 2) ||  // Topo
               (i == 1 && j >= 1 && j <= 3) ||  // Meio superior
               (i == 2 && j >= 0 && j <= 4) ||  // Centro
               (i == 3 && j >= 1 && j <= 3) ||  // Meio inferior
               (i == 4 && j == 2)) {   // Base
                octaedro[i][j] = 1;
            }
        }
    }
    
    // Exibir octaedro
    for(int i = 0; i < 5; i++) {
        for(int j = 0; j < 5; j++) {
            printf("%d ", octaedro[i][j]);
        }
        printf("\n");
    }
    printf("\n");
    
    // Demonstração das habilidades em um tabuleiro maior
    printf("=== APLICAÇÃO DAS HABILIDADES NO TABULEIRO 10x10 ===\n");
    
    int tabuleiro_habilidades[10][10] = {0};
    
    // Aplicar cone na posição (1,1)
    for(int i = 0; i < 5; i++) {
        for(int j = 0; j < 5; j++) {
            if(cone[i][j] == 1) {
                tabuleiro_habilidades[1 + i][1 + j] = 1;
            }
        }
    }
    
    // Aplicar cruz na posição (1,6)
    for(int i = 0; i < 5; i++) {
        for(int j = 0; j < 5; j++) {
            if(cruz[i][j] == 1) {
                tabuleiro_habilidades[1 + i][6 + j] = 1;
            }
        }
    }
    
    printf("Tabuleiro com Habilidades (0=não afetado, 1=área de habilidade):\n");
    printf("   ");
    for(int j = 0; j < 10; j++) {
        printf("%d ", j);
    }
    printf("\n");
    
    for(int i = 0; i < 10; i++) {
        printf("%d: ", i);
        for(int j = 0; j < 10; j++) {
            printf("%d ", tabuleiro_habilidades[i][j]);
        }
        printf("\n");
    }
}

// Função principal
int main() {
    printf("DESAFIO BATALHA NAVAL - TRÊS NÍVEIS DE COMPLEXIDADE\n");
    printf("===================================================\n\n");
    
    // Executar todos os níveis
    nivel_novato();
    nivel_aventureiro(); 
    nivel_mestre();
    
    printf("===================================================\n");
    printf("Desafio concluído com sucesso!\n");
    
    return 0;
}
s