# La gestion des utilisateurs {#dynacase-quickstart:7c5b312e-42cf-44e2-b68f-9ddce9b48d71}

Dans Dynacase, la gestion des utilisateurs utilise la notion de _compte_ (_account_ dans la
documentation de référence). Les comptes se répartissent en trois catégories :

-   les _utilisateurs_ : ce type de compte identifie une personne et permet à celle-ci de se connecter sur la plateforme,
-   les _groupes_ : un groupe est un ensemble d'utilisateurs. 
    -   Il peut contenir d'autres groupes
    -   Il peut être contenu dans d'autres groupes, 
    -   La liste des utilisateurs d'un groupe est de deux natures : 
        -   les utilisateurs directement contenu dans le groupe, 
        -   les utilisateurs contenu dans le groupe et les sous groupes du groupe,
-   les _rôles_ : un rôle a pour but de faire le lien entre les utilisateurs, les groupes et les droits :
    -   les droits sont posés sur les rôles
    -   les rôles sont ensuite affectés aux groupes ou aux utilisateurs.

<span class="flag inline nota-bene"></span> Il est à noter que dans le cas de projet intégrés au sein d'un système
d'information, Dynacase peut utiliser un LDAP/AD comme base de référence pour les utilisateurs et un SSO comme système
d'identification des utilisateurs. Ce point n'est pas abordé dans ce tutoriel.

Dans ce chapitre, vous allez apprendre à créer, initialiser et associer les différents comptes utilisateurs.
