# Sécurité des cycles de vie {#dynacase-qs:440ada84-6adb-4acc-94be-5d9f42a71ec3}

## Objectifs {#dynacase-qs:8b745aaa-bfd5-4f2d-885c-f6aa27d82a7b}

-   Mettre en place les autorisations de transition,
-   Mettre en place les profils par étape.

## Cadre {#dynacase-qs:1b96d939-42fb-434a-9379-08d8c7e365a6}

Lors de la phase d'analyse, les points suivants ont été relevés :

-   Cycle de vie des audits : Seul les utilisateurs suivant peuvent effectuer les transitions :
    -   _Démarrer_ : Responsable de l'audit et auditeurs,
    -   _Renvoyer en planification_ : Responsable de l'audit,
    -   _Annuler l'audit_ : Responsable de l'audit,
    -   _Accorder la certification_ :  Responsable de l'audit et auditeurs,
    -   _Refuser la certification_ : Responsable de l'audit.

-   Fiche d'audit :
    - Brouillon :
        -   _Voir_ : Tous les utilisateurs,
        -   _Modifier_ : Rôle auditeur,
        -   _Supprimer_ : Personne,
    -   Annulé :
        -   _Voir_ : Tous les utilisateurs,
        -   _Modifier_ : Personne,
        -   _Supprimer_ : Personne,
    -   Planifié :
        -   _Voir_ : Tous les utilisateurs,
        -   _Modifier_ : Rôle auditeur,
        -   _Supprimer_ : Personne,
    -   Certifié :
        -   _Voir_ : Tous les utilisateurs,
        -   _Modifier_ : Personne,
        -   _Supprimer_ : Personne,
    -   Refusé :
        -   _Voir_ : Tous les utilisateurs,
        -   _Modifier_ : Personne,
        -   _Supprimer_ : Personne,

## Théorie {#dynacase-qs:8a31ac4f-7f7c-4d51-bc95-261272893958}

Le paramétrage des droits associés à un cycle de vie sont de deux natures.

-   Les droits associés aux transitions.
    Ces droits permettent de définir quels utilisateurs peuvent franchir quelle transition,
-   Des profil associés au document lors des changement d'étape.
    Ces profils permettent de définir qui peut voir, modifier, supprimer le document.

## Profilage du cycle {#dynacase-qs:bba49d4c-8ea4-4cd3-a064-f8c006c9ef1c}

Vous allez commencer par profiler le document cycle de vie,
ce qui va vous permettre de définir quel type d'utilisateur peut effectuer quelle transition.

Connectez vous à l'interface d'administration : `http://<nomDeDomaine>/dynacase/admin.php`.

Allez dans l'application <kbd class="menu"><kbd><samp>Gestion des documents</samp></kbd>&gt;<kbd><samp>Explorateur de documents</samp></kbd></kbd>,
cliquez ensuite sur `les cycles` et sélectionnez le cycle `Audit Audit`.

Cliquez sur <kbd class="menu"><kbd><samp>Autres</samp></kbd>&gt;<kbd><samp>Sécurité</samp></kbd>&gt;<kbd><samp>Profil dédié</samp></kbd></kbd>.
La page se recharge, cliquez maintenant sur
<kbd class="menu"><kbd><samp>Autres</samp></kbd>&gt;<kbd><samp>Sécurité</samp></kbd>&gt;<kbd><samp>Accessibilités...</samp></kbd></kbd>.

L'interface suivante vous est présentée :

![ Cycle de vie : Audit : Profil ](40-40-wdoc-profil-empty.png "Cycle de vie : Audit : Profil")

<span class="flag inline nota-bene"></span>
Les deux premières et la dernière colonnes sont dédiées aux droits associés au document cycle
(qui peut _voir_, _modifier_ et _voir les droits du document cycle_).

<span class="flag inline nota-bene"></span>
Le code couleur des types de droits peut être consulté en cliquant sur le bouton `Légende`.

<span class="flag inline nota-bene"></span>
Les entrées en jaune et en orange sont des champs provenant du document associé au cycle de vie.

<span class="flag inline nota-bene"></span>
L'affectation de droit est décrite dans [le chapitre sécurité des documents][ParamDroit].

Modifiez la matrice comme ci-dessous :

![ Cycle de vie : Audit : Profil ](40-40-wdoc-profil-checked.png "Cycle de vie : Audit : Profil")

Et cliquez sur `Modifier les privilèges`.

Votre cycle est maintenant profilé.
La liste des transitions présentée sur le document tient compte du profil de la personne connectée.

## Profil des étapes {#dynacase-qs:99be7d83-d8c0-407f-894a-b44e1df6bfa4}

Vous allez maintenant ajouter des profils de document au différentes étapes.

### Création des profils {#dynacase-qs:88533bb0-692a-4d4e-a61d-d5fbc29a4e78}

Vous allez commencer par créer les profils. 

#### Profil : Brouillon {#dynacase-qs:30ab6e0d-632d-4011-a546-dbac1c9b76fe}

Cliquez sur `Création > Profil`. Remplissez les valeurs suivantes :

-   __Titre__ : `Audit WFL : Brouillon`,
-   __Famille__ : `Audit`.

Cliquez sur `Créer`.

Cliquez sur `Activer`. La page se recharge. Cliquez sur `Accessibilités`

Remplissez la matrice comme ci-dessous :

![ Profil Audit : Brouillon ](40-40-pdoc-brouillon.png "Profil Audit : Brouillon")

Cliquez sur `Modifier les privilèges`.

Ajoutez le nom logique `Autres > Propriétés` : `PDOC_AUDIT_BROUILLON`.

#### Profil : Planifié {#dynacase-qs:7589a8f6-4975-431a-94b9-cf0d879bc127}

Cliquez sur `Création > Profil`. Remplissez les valeurs suivantes :

-   __Titre__ : `Audit WFL : Planifié`,
-   __Famille__ : `Audit`.

Cliquez sur `Créer`.

Cliquez sur `Activer`. La page se recharge. Cliquez sur `Accessibilités`.

Remplissez la matrice comme ci-dessous :

![ Profil Audit : Planifié ](40-40-pdoc-planif.png "Profil Audit : Planifié")

Cliquez sur `Modifier les privilèges`.

Ajoutez le nom logique `Autres > Propriétés` : `PDOC_AUDIT_PLANIFIE`.

#### Profil : Désactivé {#dynacase-qs:24afdcf5-a615-4ede-a14f-437847d12fe6}

Cliquez sur `Création > Profil`. Remplissez les valeurs suivantes :

-   __Titre__ : `Audit WFL : Désactivé`,
-   __Famille__ : `Audit`.

Cliquez sur `Créer`.

Cliquez sur `Activer`. La page se recharge. Cliquez sur `Accessibilités`.

Remplissez la matrice comme ci-dessous :

![ Profil Audit : Désactivé ](40-40-pdoc-disabled.png "Profil Audit : Désactivé")

Cliquez sur `Modifier les privilèges`.

Ajoutez le nom logique `Autres > Propriétés` : `PDOC_AUDIT_DISABLED`.

<span class="flag inline nota-bene"></span>
Un seul profil est créé et utilisé pour tous les états où le document est désactivé (_Annulé_, _Certifié_, _Refusé_).

### Affectation des profils {#dynacase-qs:24184161-6f14-4cde-bfaf-9868a84657fe}

Allez dans l'application <kbd class="menu"><kbd><samp>Gestion des documents</samp></kbd>&gt;<kbd><samp>Explorateur de documents</samp></kbd></kbd> cliquez ensuite sur `les cycles`
et sélectionnez le cycle `Audit Audit`.

Cliquez sur `Modifier`, sélectionnez l'onglet `Étapes` pour chaque onglet d'étape associé le profil :

-   Profil Brouillon : Audit WFL Brouillon,
-   Profil Planifié : Audit WFL Planifié,
-   Profil Annulé : Audit WFL Désactivé,
-   Profil Certifié : Audit WFL Désactivé,
-   Profil Refusé : Audit WFL Désactivé,

Vous obtenez le document suivant :

![ Cycle de vie ](40-40-pdoc-wdoc-associated.png "Cycle de vie")

<span class="flag inline nota-bene"></span>
__Attention__ les profils ne sont affectés au document qu'à l'arrivée dans l'étape.
Si des documents sont déjà dans cette étape alors le profil n'est pas affecté.

## Exportation {#dynacase-qs:5d73ab75-ffa4-4509-8efc-32b3073bcfea}

Utilisez la procédure décrite dans le [chapitre précédent][ExportCycle].

Vous devez obtenir un fichier `./COGIP_AUDIT/COGIP_AUDIT_AUDIT__PARAM.csv` semblable à :

![ Export cycle de vie avec sécurité ](40-40-security-param.png "Export cycle de vie avec sécurité")

Vous pouvez trouver le fichier complété dans [les sources][tuto_audit_param].

## Mise en place des modifications {#dynacase-qs:211833c4-a5e7-4685-a14e-8b52f634417c}

Vous allez maintenant déployer vos modifications :

    <devtool> deploy -s . --url http://admin:anakeen@<nomDeDomaine>/dynacase-control/ --port <port> --context dynacase

Vous pouvez ensuite consulter les modifications apportées via l'application `http://<nomDeDomaine>/dynacase/`.

## Conclusion {#dynacase-qs:c4e5ebfa-74b7-4565-819d-34537af6317e}

Vous savez maintenant paramétrer les éléments de sécurité associés au cycle de vie.
Vous pouvez définir qui peut effectuer quelle transition et qui peut _voir_/_modifier_/_supprimer_ les documents suivant l'étape.

## Voir aussi {#dynacase-qs:44b393d1-c6ad-448b-997d-e9cc1d47fd89}

-   [Les sources après ce chapitre][tuto_zip],
-   [Import profil cycle de vie][DocCSVWFL],
-   [Profil de document][DocProfilDocument].

<!-- links -->

[DocProfilDocument]: #core-ref:f1575705-10e8-4bf2-83b3-4c0b5bfb77cf "Documentation : profil de document"
[DocCSVWFL]: #core-ref:e0d99925-df0d-4d51-8ebc-d44c4dd03873 "Documentation : Import cycle de vie"
[ParamDroit]: #dynacase-qs:1cd2c714-d287-4ca6-8282-c5a20393c0ea
[ExportCycle]: #dynacase-qs:6633ab3c-ab35-48ad-93a9-71898bfad9f3
[tuto_zip]: https://github.com/Anakeen/dynacase-quick-start-code/archive/3.2-after-40-40.zip
[tuto_audit_param]: https://github.com/Anakeen/dynacase-quick-start-code/blob/3.2-after-40-40/COGIP_AUDIT/COGIP_AUDIT_AUDIT__PARAM.csv#L4-L13
[deploy_instruct]: #dynacase-qs:e53aa0c3-6fa8-4083-8bb8-b64bd750ab9e