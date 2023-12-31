# project-se-tp

On veut effectuer en parallèle(En utilisant le modèle producteurs/consommateur) le produit de deux matrices: 
B (n1* m1)  et C (n2 * m2) ⇒ la matrice résultante A=B*C ;
Q1: Quelles sont les structures de données à utiliser ?

Les matrices sont remplis par des valeurs aléatoires
       Matrices (B, C, A) : Utilisées pour stocker les données des matrices B, C et la matrice résultante A.

Les résultats intermédiaires seront placés dans un tampon de taille “T[N]”.
       Tampon (T) : tampon partagé entre les threads producteurs et consommateurs pour stocker les résultats intermédiaires.
Q2: Comment allez-vous protéger l'accès à ces données?

Chaque threads producteurs calcule une ligne de la matrice résultante A et range les résultat dans le tampon T
    on utulise des sémaphores pour synchroniser l'accès aux données partagées entre les threads ( empty , full ,mutex)
    empty :  Gère la quantité d'espace vide dans le tampon qui stocke les résultats intermédiaires
    full :  Gère la quantité d'espace occupé dans le tampon
    mutex : Assure un accès exclusif au tampon partagé entre les threads
Q3: Quels sont les risques?

Les threads consommateurs consomment l'élément T[y]  le place dans la matrice résultante A  au bon emplacement!
   Concurrence : Risque d'accès simultané aux données partagées par plusieurs threads    
   interblocage : Risque qu'un ensemble de threads se bloque mutuellement
