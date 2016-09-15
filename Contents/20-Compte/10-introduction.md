# La gestion des utilisateurs {#dynacase-qs:7c5b312e-42cf-44e2-b68f-9ddce9b48d71}

Dans Dynacase, la gestion des utilisateurs utilise la notion de _compte_ ([_account_][core-ref:accounts] dans la
documentation de référence). Les comptes se répartissent en trois catégories :

Les _utilisateurs_
:   ce type de compte identifie une personne et permet à celle-ci de se connecter sur la plateforme.

Les _groupes_
:   un groupe est un ensemble d'utilisateurs.
    
    -   Il peut contenir d'autres groupes
    -   Il peut être contenu dans d'autres groupes, 
    -   La liste des utilisateurs d'un groupe est de deux natures :
        -   les utilisateurs directement contenus dans le groupe, 
        -   les utilisateurs contenus dans le groupe et ses sous groupes.

les _rôles_
:   un rôle a pour but de faire le lien entre les utilisateurs et les droits :
    
    -   les droits sont posés sur les rôles
    -   les rôles sont ensuite affectés directement aux utilisateurs, ou par l'intermédiaire des groupes.

<span class="flag inline nota-bene"></span> Il est à noter que dans le cas de projets intégrés au sein d'un système
d'information, Dynacase peut utiliser un LDAP/AD comme base de référence pour les utilisateurs et un SSO comme système
d'authentification des utilisateurs. Ce point n'est pas abordé dans ce tutoriel.

Dans ce chapitre, vous allez apprendre à créer, initialiser et associer les différents comptes utilisateurs.

<!-- links -->
[core-ref:accounts]: #core-ref:2bd98eec-5b03-4af0-b9d6-1bbf78fe9733
