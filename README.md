# magicien
magicien
#include <stdio.h>

// Algorithme d’Euclide étendu
int euclide_etendu(int a, int b, int *x, int *y) {
    if (b == 0) {
        *x = 1;
        *y = 0;
        return a;
    }

    int x1, y1;
    int d = euclide_etendu(b, a % b, &x1, &y1);

    *x = y1;
    *y = x1 - (a / b) * y1;

    return d;
}

int main() {
    printf("=== Programme pour resoudre a*x + b*y = c ===\n\n");
    int a, b, c;
    printf("Entrer a : ");
    scanf("%d", &a);
    printf("Entrer b : ");
    scanf("%d", &b);
    printf("Entrer c : ");
    scanf("%d", &c);
    int x0, y0;
    int d = euclide_etendu(a, b, &x0, &y0);
    printf("\nLe PGCD de (%d, %d) est : %d\n", a, b, d);
    if (c % d != 0) {
        printf("Pas de solution entiere car %d ne divise pas %d.\n", d, c);
    } else {
        int k = c / d;
        int xp = x0 * k;
        int yp = y0 * k;
        int alpha = b / d;
        int beta = -a / d;
        printf("\nSolution particuliere : (x, y) = (%d, %d)\n", xp, yp);
        printf("Forme generale : x = %d + %d*k, y = %d + %d*k, k appartient Z\n", xp, alpha, yp, beta);
    }
    // === Partie Magie ===
    printf("\n=== Magicien des mathematiques ===\n");
    int jour, mois;
    printf("Entrez votre jour de naissance (1-31) : ");
    scanf("%d", &jour);
    printf("Entrez votre mois de naissance (1-12) : ");
    scanf("%d", &mois);
    // Calcul magique
    int total = jour * 31 + mois * 12;
    printf("Vous avez calcule : %d\n", total);
    // Deviner le jour et le mois
    int devine_jour = total % 31;
    if (devine_jour == 0) devine_jour = 31; // correction si modulo = 0
    int devine_mois = (total - devine_jour * 31) / 12;
    printf("Le magicien devine : Vous etes ne(e) le %d/%d !\n", devine_jour, devine_mois);

    return 0;
}
