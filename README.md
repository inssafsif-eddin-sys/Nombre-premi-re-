#include <stdio.h>
#include <stdbool.h>
#include <math.h>

int main() {
    int n;

    printf("Entrez un nombre maximum : ");
    scanf("%d", &n);

    // Tableau pour marquer les nombres premiers
    bool estPremier[n + 1];

    // Initialisation : on considère tous les nombres premiers
    for (int i = 0; i <= n; i++) {
        estPremier[i] = true;
    }

    // 0 et 1 ne sont pas premiers
    estPremier[0] = false;
    estPremier[1] = false;

    // Crible d'Eratosthène
    for (int i = 2; i <= sqrt(n); i++) {
        if (estPremier[i]) {
            for (int j = i * i; j <= n; j += i) {
                estPremier[j] = false;
            }
        }
    }

    // Affichage des nombres premiers
    printf("Les nombres premiers jusqu'a %d sont :\n", n);
    for (int i = 2; i <= n; i++) {
        if (estPremier[i]) {
            printf("%d ", i);
        }
    }

    printf("\n");
    return 0;
}
