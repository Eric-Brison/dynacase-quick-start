# Sécurité {#dynacase-qs:3e38794d-93eb-464e-9a69-1828ece189ac}

Ce chapitre va vous permettre de mettre en place les notions de sécurité sur vos familles.

## Objectifs {#dynacase-qs:13665808-ee26-47c9-b1b9-02e0e65c19eb}

-   Mettre en place les droits basiques sur les documents, droits sur le [CRUD][wikiCRUD],
-   Mettre en place les droits basiques sur la définition des familles,
-   Mettre en place les contrôles de vue permettant de restreindre la vue d'un document suivant le type d'utilisateur.

## Cadre {#dynacase-qs:ef53c139-18b2-4d79-a83c-c51c0424c646}

Lors de la phase de spécification, les droits suivants ont été identifiés. L'application nécessite :

-   Pour les _référentiels_ et _chapitres_ :
    -   _Création_ : Uniquement par les utilisateurs ayant le rôle : _Auditeur_,
    -   _Vue_ : Tous les utilisateurs,
    -   _Modification_ : Uniquement par les utilisateurs ayant le rôle : _Auditeur_,
    -   _Suppression_ : Uniquement par les utilisateurs ayant le rôle : _Auditeur_.
-   Audit :
    -   _Création_ : Uniquement par les utilisateurs ayant le rôle : _Responsable des audits_,
    -   Les droits de _vue_, _modification_ et _suppression_ seront abordés lors de la réalisation du cycle de vie,
-   Fiche de non-conformité :
    -   _Création_ : Uniquement par les utilisateurs ayant le rôle : _Responsable des audits_.
    -   Les droits de _vue_, _modification_ et _suppression_ seront abordés lors de la réalisation du cycle de vie,

La définition des familles doit pouvoir être mise à jour par les administrateurs fonctionnels.

En outre, il y a une demande particulière, les auditeurs veulent que dans les fiches de non conformité
la partie **Écart** puisse être vue par _tous les utilisateurs pouvant voir le document_,
mais être modifiée uniquement par les _auditeurs_.

## Théorie {#dynacase-qs:98e77eba-96ad-49cb-9eae-19ef01141fc2}

La sécurité applicative des documents dans Dynacase repose sur la notion de [profil][DocProfil].

Un profil est une matrice de droits.
Il permet d'indiquer quel _utilisateur_/_groupe_/_rôle_ peut effectuer quelle action.
Il existe deux types d'affectations :

-   _statique_ : l'affectation ne varie pas suivant le contenu du document,
-   _dynamique_ : l'affectation varie suivant le contenu du document.

On peut compléter la notion de sécurité avec deux autres éléments :

-   le [masque][DocMasque] : c'est un document permettant de re-définir les visibilités pour une famille,
    le masque est associé à un document via un cycle de vie ou un contrôle de vue
    et permet de rendre des attributs invisibles, non-modifiables, etc.
-   le [contrôle de vue][DocCVDOC] : ce type de document permet d'indiquer des règles de composition
    de la vue d'un document en fonction des droits de l'utilisateur.
    Il permet notamment d'utiliser un masque pour changer les visibilités suivant le profil d'un utilisateur.

## Profil de famille {#dynacase-qs:1aecb6e4-0046-4ecc-b9d0-8af9e13faf9b}

Vous allez commencer par définir les profils de famille.

Le profil de famille permet de définir :

-   qui peut _voir_, _modifier_ __la configuration__ de la famille,
-   qui peut _créer_ __des documents__ de cette famille 

### Création {#dynacase-qs:651a15e9-ebbf-4e85-8f0f-652d64fcf5cd}

Connectez vous à l'interface d'administration : `http://<nomDeDomaine>/dynacase/admin.php`.

Sélectionnez l'application <kbd class="menu"><kbd><samp>Gestion des documents</samp></kbd>&gt;<kbd><samp>Explorateur de documents</samp></kbd></kbd>.

![ Explorateur de document ](30-50-docadmin.png "Explorateur de document")

Cette application permet de créer tous les types de documents de votre contexte.

Cliquez ensuite sur `Création > Profil` dans l'onglet de droite s'ouvre l'interface suivante :

![ Création document profil ](30-50-docadmin-creation-systeme.png "Création document profil")

Déroulez la liste et choisissez le type de document `Profil de famille`. L'interface suivante est présentée :

![ Création document profil famille ](30-50-docadmin-creation-pfam.png "Création document profil famille")

Complétez le titre avec `Profil de référentiel` et cliquez sur `Créer`. Vous obtenez l'interface suivante :

![ Profil famille désactivé ](30-50-docadmin-pfam-consult.png "Profil famille désactivé")

### Paramétrage {#dynacase-qs:1cd2c714-d287-4ca6-8282-c5a20393c0ea}

Le profil de famille est créé __désactivé__.
C'est à dire que toutes les familles associées à ce profil sont libres d'accès,
donc tous les utilisateurs peuvent effectuer toutes les actions.

Cliquez sur `Activer` en bas à droite. L'interface se recharge.

![ Profil famille activé ](30-50-docadmin-pfam-active.png "Profil famille activé")

Le profil de famille est maintenant activé.
C'est à dire que toutes les familles associées à ce profil sont restreintes
donc aucun utilisateur (sauf l'administrateur) ne peut effectuer une action.

Cliquez sur `Accessibilités`. Une nouvelle fenêtre s'ouvre et présente la matrice de droits.

![ Profil famille matrice de droits ](30-50-docadmin-pfam-rights.png "Profil famille matrice de droits")

Cette matrice présente par défaut uniquement les rôles du contexte.
La bonne pratique veut que les droits soient associés via les rôles et non pas directement via les groupes.

Vous allez créer le profil pour les familles _Chapitres_ et _Référentiels_. 

Cliquez sur le bouton `∴` devant `Auditeur`. L'interface devient semblable à :

![ Profil famille matrice de droits : modification ](30-50-docadmin-pfam-edit-rights.png "Profil famille matrice de droits : modification")

Cochez ensuite les cases `Create` et `Créer manuellement`.

<span class="flag inline nota-bene"></span> Il existe deux possibilités de création :

-   le droit `create` donne aux utilisateurs la possibilité de faire créer des documents en son nom par le code,
-   le droit `Créer manuellement` donne aux utilisateur la possibilité de créer des documents via les interfaces Dynacase.

Cliquez sur le `∴` devant Administrateur fonctionnel et cochez les cases
`Voir`, `Modifier`, `Voir les droits` et `Modifier les droits`.
Ces droits donnent la possibilité aux administrateurs fonctionnels d'agir sur la définition de la famille.

![ Profil famille matrice de droits : modification ](30-50-docadmin-pfam-rights-checked.png "Profil famille matrice de droits : modification")

Cliquez sur `Modifier les privilèges`, l'interface se présente ensuite de cette manière :

![ Profil famille matrice de droits : consultation ](30-50-docadmin-pfam-rights-validated.png "Profil famille matrice de droits : consultation")

### Export {#dynacase-qs:c6ed1357-b76f-4a83-9204-c8de33fff66f}

Vous allez ensuite exporter les documents de profil.

Commencez par associer un nom logique au profil, dans l'interface du document profil <kbd class="menu"><kbd><samp>Autres</samp></kbd>&gt;<kbd><samp>Propriétés</samp></kbd></kbd>.
Cliquez sur `affecter un nom logique` et donnez au document le nom logique `PFAM_REFERENTIEL`.

Ensuite, sélectionnez le document pour pouvoir l'exporter, dans l'interface du document `Autres > Ajouter au porte-documents`.  
Une fois le porte-documents ouvert, pensez à supprimer les documents qui ne vous intéressent pas
et cliquez sur `Outils > Exportation du dossier`.

<span class="flag inline nota-bene"/>
Vous pouvez remarquer que le nom logique du document est préfixé
de manière à rapidement identifier son type : `PFAM` pour _Profil de famille_.

L'interface suivante est présentée :

![ Profil famille : export ](30-50-docadmin-pfam-export.png "Profil famille : export")

Étant donné que vous exportez un profil, vous devez dans l'entrée `profil` choisir `avec les profils`.

![ Profil famille : export ](30-50-docadmin-pfam-export-with-profil.png "Profil famille : export")

Cliquez sur `Exporter`.

Un fichier CSV vous est envoyé. Ouvrez le fichier :

![ Profil famille : CSV ](30-50-docadmin-pfam-export-csv.png "Profil famille : CSV")

Les spécificités du format sont décrites dans la [documentation][DocProfilExport]. 

### Ajout des profils de famille dans les fichiers d'import {#dynacase-qs:84222982-26c8-4a1c-9c93-01e82b913b44}

Vous pouvez remarquer les points suivants :

-   les profils sont composés de deux éléments :
    -   `DOC` : un document profil : ce document porte la référence du profil,
    -   `PROFIL` : cette ligne contient l'ensemble des règles de profilage (la définition de la matrice).
-   la ligne `PROFIL` : elle contient :
    +    la référence au nom logique du profil (`PFAM_REFERENTIEL`)
    +   un mot-clé indiquant que les droits sont exprimés par rapport à des profils (`:useAccount`)
    +   un ensemble de droits sous la forme `clé=valeur` pour lesquels :
        *   la clé est un droit (`view`, `edit`, etc.),
        *   la valeur est une référence vers un _compte_ (_groupe_, _rôle_, _utilisateur_).

#### Profil de famille de référentiel {#dynacase-qs:5aacd15f-7202-4a62-b565-ddba8518b304}

Vous allez maintenant intégrer le profil dans les fichiers de paramétrage de la famille.
Ouvrez le fichier `/COGIP_AUDIT/COGIP_AUDIT_REFERENTIEL__PARAM.csv` :

-   copiez les 4 lignes du fichiers d'import en début du fichier de paramétrage,
    
    cela permet que le profil soit créé et initialisé lors de l'import de ce fichier
    
-   ajoutez juste avant l'instruction `END`, une ligne contenant :
    -   dans la première case `PROFID`,
    -   dans la deuxième case, le nom logique du profil soit : `PFAM_REFERENTIEL`.
    
    Cela permet d'associer le profil à la famille.

<span class="flag inline nota-bene"/>
Bien que le profil soit _conçu_ pour une famille donnée (vous avez en effet spécifié avec quelle famille il peut être
utilisé lors de sa création), il faut explicitement déclarer ce profil sur la famille.
En effet, la famille spécifiée lors de la création du profil indique que _ce profil peut être utilisé avec cette famille,
ainsi que ses sous-familles_, mais n'indique aucunement que ce sera le profil utilisé par ces familles (il peut notamment
exister plusieurs profils compatibles, et le profil à appliqué est changé par du code).

Ce qui donne dans votre cas :

![ Import référentiel ](30-50-import-pfam-ref.png "Import référentiel")

Vous pouvez retrouver le fichier complété dans [les sources][tuto_param_ref].

#### Profil de famille de chapitre {#dynacase-qs:71093ab5-b57d-4b3b-b58c-bb6067ce4afd}

Vous allez maintenant valuer le profil de famille _Chapitres_.
Votre spécification indique que celui-ci est similaire à celui du référentiel.

Vous avez deux choix :

-   vous pouvez noter uniquement la référence dans le fichier `__PARAM` du chapitre
    et dans ce cas les deux familles seront liées par le même profil,
-   soit dupliquer une nouvelle fois les quatre lignes de définition de profil
    et changer le nom logique pour obtenir un nouveau profil similaire.

Les deux solutions ont toutes les deux des avantages et des défauts.
Toutefois il est considéré comme une bonne pratique de dupliquer les profils de deux familles
pour pouvoir les faire évoluer de manière distincte.

Ouvrez le fichier `/COGIP_AUDIT/COGIP_AUDIT_CHAPITRE__PARAM.csv`:

-   copiez les quatre lignes de profil comme précédemment,
-   modifiez les deux références au nom logique pour le passer de `PFAM_REFERENTIEL` à `PFAM_CHAPITRE`,
-   renommer le titre du profil en "Profil de chapitre'
-   ajoutez juste à la ligne du dessus de l'instruction `END`, une ligne contenant :
    -   dans la première case `PROFID`,
    -   dans la deuxième case, le nom logique du profil soit : `PFAM_CHAPITRE`.

Ce qui donne dans votre cas :

![ Import chapitre ](30-50-import-pfam-chapitre.png "Import chapitre")

Vous pouvez retrouver le fichier complété dans [les sources][tuto_param_chapitre].

#### Profil de famille d'audit {#dynacase-qs:5bcdd917-3580-4cf4-8ece-6696e88c2da5}

Vous allez maintenant valuer le profil de famille _Audits_.
Votre spécification indique que celui-ci est similaire à celui du référentiel avec juste une différence :
le compte ayant le droit de _création_ est le rôle _Responsable des audits_.

Ouvrez le fichier `/COGIP_AUDIT/COGIP_AUDIT_AUDIT__PARAM.csv`:

-   copiez les quatre lignes de profil comme précédemment,
-   modifiez les deux références au nom logique pour le passer de `PFAM_REFERENTIEL` à `PFAM_AUDIT`,
-   renommer le titre du profil en "Profil d'audit'
-   modifiez les tuples :
    -   `create=role_auditeur` en `create=role_responsable_audit`,
    -   `icreate=role_auditeur` en `icreate=role_responsable_audit`,
-   ajoutez juste avant l'instruction `END`, une ligne contenant :
    -   dans la première case `PROFID`,
    -   dans la deuxième case, le nom logique du profil soit : `PFAM_AUDIT`.

Ce qui donne dans votre cas :

![ Import audit ](30-50-import-pfam-audit.png "Import audit")

Vous pouvez retrouver le fichier complété dans [les sources][tuto_param_audit].

#### Profil de famille de Fiche de non-conformité {#dynacase-qs:70215d94-966b-42a9-a453-c5651bc045b7}

Vous allez maintenant valuer le profil de famille _Fiche de non-conformité_.
Votre spécification indique que celui-ci est similaire à celui du référentiel avec juste une différence :
le compte ayant le droit de _création_ est le rôle _Responsable des audits_.

Ouvrez le fichier `/COGIP_AUDIT/COGIP_AUDIT_FNC__PARAM.csv`:

-   copiez les quatre lignes de profil comme précédemment,
-   modifiez les deux références au nom logique pour le passer de `PFAM_REFERENTIEL` à `PFAM_FNC`,
-   renommer le titre du profil en "Profil de FNC"
-   modifiez les tuples :
    -   `create=role_auditeur` en `create=role_responsable_audit`,
    -   `icreate=role_auditeur` en `icreate=role_responsable_audit`,
-   ajoutez juste avant l'instruction `END`, une ligne contenant :
    -   dans la première case `PROFID`,
    -   dans la deuxième case, le nom logique du profil soit : `PFAM_FNC`.

Ce qui donne dans votre cas :

![ Import fiche de non-conformité ](30-50-import-pfam-fnc.png "Import fiche de non-conformité")

Vous pouvez retrouver le fichier complété dans [les sources][tuto_param_fnc].

## Profil de document {#dynacase-qs:62aad07c-8c51-423d-907a-ed7a0d8b5f5d}

Vous allez maintenant créer les [profils de documents][DocProfilDocument].
Un profil de document permet de définir qui peut :

-   voir,
-   modifier,
-   supprimer,
-   etc.

un document.

### Création {#dynacase-qs:54194696-d4ab-43de-b4ac-50a93bcfc878}

Connectez vous à l'interface d'administration : `http://<nomDeDomaine>/dynacase/admin.php`.

Sélectionnez l'application <kbd class="menu"><kbd><samp>Gestion des documents</samp></kbd>&gt;<kbd><samp>Explorateur de documents</samp></kbd></kbd>.

Cliquez ensuite sur `Création > Profil` dans l'onglet de gauche s'ouvre l'interface de création,
sélectionnez dans cette interface `Profil de document`.

Rentrez dans le formulaire le titre `Profil des documents référentiels` et sélectionnez la famille `Référentiel qualité`,
cliquez ensuite sur `Créer`.

### Paramétrage {#dynacase-qs:db2662db-966e-4b53-b778-454f7d69f286}

L'interface affiche ensuite le document de profil en consultation.
Cliquez sur `activer` et une fois l'interface rechargée cliquez sur `Accessibilités`, la matrice des droits s'ouvre.

Donnez les droits suivants :

-   rôle _Utilisateur COGIP_ :
    +   voir,
    +   envoyer,
-   rôle _Auditeur_ :
    +   voir,
    +   modifier,
    +   supprimer.

<span class="flag inline nota-bene"></span> Techniquement, il n'est pas nécessaire de donner le droit _voir_
au rôle _Auditeur_, puisque les gens ayant ce rôle sont également censés avoir le rôle _Utilisateur COGIP_.
Cependant, ce paramétrage pourra être amené à évoluer.
Afin d'éviter les mauvaises surprises lors de la mise à jour des profils,
il est conseillé de donner _explicitement_ le droit _voir_ aux comptes auxquels on donne le droit _modifier_.

Vous obtenez la matrice suivante :

![ Import Profil de document ](30-50-create-pdoc-view.png "Import Profil de document")

### Export {#dynacase-qs:9d267ad0-d8de-4ebc-a1bb-dee3fb3f97b4}

Ajoutez le nom logique `PDOC_REFERENTIEL` au document au moyen du menu
<kbd class="menu"><kbd><samp>Autres</samp></kbd>&gt;<kbd><samp>Propriétés</samp></kbd></kbd>.
Ajoutez le au porte-documents au moyen du menu
<kbd class="menu"><kbd><samp>Autres</samp></kbd>&gt;<kbd><samp>Ajouter au porte-documents</samp></kbd></kbd>
(pensez à supprimer les éventuels autres documents) et cliquez ensuite sur
<kbd class="menu"><kbd><samp>Outils</samp></kbd>&gt;<kbd><samp>exportation du dossier</samp></kbd></kbd>.
Vous devez indiquer dans la partie `Profil` `Avec les profils` et ensuite cliquer sur `Exporter`.

Le fichier CSV suivant vous est envoyé :

![ CSV Profil de document ](30-50-export-pdoc.png "CSV Profil de document")

Le fichier se présente exactement de la même manière que celui de [profil de famille][dynacase-qs:pfam-description]
et contient le même type d'informations.

<span class="flag inline nota-bene"/>
Vous pouvez remarquer que le nom logique du document est préfixé de manière à rapidement identifier son type :
`PDOC` pour _Profil de document_.

### Ajout des profils de document dans les fichiers d'import {#dynacase-qs:4e232fc8-f150-44c5-8384-04226190a5e7}

#### Profil de document de référentiel {#dynacase-qs:57d9f0b4-3799-4d33-8521-8bf79714d1ff}

Ouvrez le fichier `./COGIP_AUDIT/COGIP_AUDIT_REFERENTIEL__PARAM.csv`.

Ajoutez :

-   les 4 lignes du fichier d'export,
-   ajoutez juste avant l'instruction `END`, une ligne contenant :
    -   dans la première case `CPROFID`,
    -   dans la deuxième case, le nom logique du profil soit : `PDOC_REFERENTIEL`.

![ Profil de document : import référentiel ](30-50-import-pdoc-referentiel.png "Profil de document : import référentiel")

Vous pouvez retrouver le fichier complété dans [les sources][tuto_param_ref].

#### Profil de document de chapitre {#dynacase-qs:5e2a95fe-474c-498d-b902-f625a234b575}

Vous allez maintenant valuer le profil de famille Chapitres.
Votre spécification indique que celui-ci est similaire à celui du référentiel.

Ouvrez le fichier `/COGIP_AUDIT/COGIP_AUDIT_CHAPITRE__PARAM.csv`:

-   copiez les quatre lignes de profil comme précédemment,
-   modifiez les deux références au nom logique pour le passer de `PDOC_REFERENTIEL` à `PDOC_CHAPITRE`,
-   modifiez le titre en 'Profil des documents chapitre"
-   modifiez le nom logique (colonne `dpdoc_famid`) et le titre (colonne `dpdocfam`) de la famille associée en
    `COGIP_AUDIT_CHAPITRE` | `Chapitre`
-   ajoutez juste avant l'instruction `END`, une ligne contenant :
    -   dans la première case `CPROFID`,
    -   dans la deuxième case, le nom logique du profil soit : `PDOC_CHAPITRE`.
    
![ Profil de document : import chapitre ](30-50-import-pdoc-chapter.png "Profil de document : import chapitre")

Vous pouvez retrouver le fichier complété dans [les sources][tuto_param_chapitre].

#### Profil de document d'audit et de fiche de non-conformité {#dynacase-qs:0dfd0cb1-c566-4149-9ef8-8c568427d574}

L'audit et les fiches de non conformité ne vont pas avoir pour l'instant de profil de document,
car ils ont un cycle de vie et leur profil de document est fixé par leur cycle de vie.

## Contrôle de vue {#dynacase-qs:80954137-faa1-4860-ac5b-902929614282}

Vous allez maintenant configurer le contrôle de vue.

Le [contrôle de vue][DocCVDOC] va vous permettre de définir des [masques][DocMasque] variant suivant l'utilisateur connecté.

### Masque {#dynacase-qs:0d5ee6ee-aafb-4a1f-b3fc-b0a0ef9d3fd9}

Vous allez commencer par créer le [masque][DocMasque].

#### Création {#dynacase-qs:fa8b629c-79a7-42d0-a0f2-d6efc0dfa01d}

Connectez vous à l'interface d'administration : `http://<nomDeDomaine>/dynacase/admin.php`, sélectionnez l'application
<kbd class="menu"><kbd><samp>Gestion des documents</samp></kbd>&gt;<kbd><samp>Explorateur de documents</samp></kbd></kbd>,
cliquez sur
<kbd class="menu"><kbd><samp>Création</samp></kbd>&gt;<kbd><samp>Documents système</samp></kbd></kbd>
et sélectionnez dans la liste déroulante en haut à droite `Masque de saisie`.

Vous obtenez l'interface ci-dessous :

![ Masque : Création ](30-50-create-mask.png "Masque : Création")

Veuillez compléter les éléments suivants :

-   Titre du masque : `Édition standard`,
-   Choisissez la famille : `Fiche de non-conformité`

![ Masque : Création ](30-50-create-mask2.png "Masque : Création")

Mettez l'attribut tab `Écarts` à la visibilité `Statique` et l'attribut array `Écarts` à `Tableau statique`.

![ Masque : Création ](30-50-create-mask3.png "Masque : Création")

Et cliquez sur `Sauver`.

![ Masque : Création ](30-50-create-mask4.png "Masque : Création")

Vous pouvez remarquer qu'en ayant fixé l'attribut encadrant en lecture seule,
tous les attributs qu'il contient sont passés en lecture seule.

#### Export {#dynacase-qs:d60a13f2-82cd-4bb5-9807-c57af6be2ded}

Ajoutez un nom logique au document en cliquant sur
<kbd class="menu"><kbd><samp>Autres</samp></kbd>&gt;<kbd><samp>Propriétés</samp></kbd></kbd>
et fixez le nom logique à `MASK_FNC_DEFAULT`.

Ajoutez le masque au porte-documents, en cliquant sur
<kbd class="menu"><kbd><samp>Autres</samp></kbd>&gt;<kbd><samp>Ajoutez au porte-documents</samp></kbd></kbd>.

<span class="flag inline nota-bene"></span>
Pensez à supprimer les éventuels autres documents du porte-documents.

Le contenu du porte-documents sera exporté avec le contrôle de vue.

<span class="flag inline nota-bene"/>
Vous pouvez remarquer que le nom logique du document est préfixé de manière à rapidement identifier son type :
`MASK` pour _Masque_.

### Contrôle de vue {#dynacase-qs:7d459926-2a4e-4c6f-9b3c-bdc400a29020}

#### Création {#dynacase-qs:9643ca08-b086-4e99-b821-f8dd60b73733}

Connectez vous à l'interface d'administration : `http://<nomDeDomaine>/dynacase/admin.php`,
sélectionnez l'application
<kbd class="menu"><kbd><samp>Gestion des documents</samp></kbd>&gt;<kbd><samp>Explorateur de documents</samp></kbd></kbd>,
cliquez sur <kbd class="menu"><kbd><samp>Création</samp></kbd>&gt;<kbd><samp>Documents système</samp></kbd></kbd>
et sélectionnez dans la liste déroulante en haut à droite
<kbd class="menu"><kbd><samp>Contrôle de vue</samp></kbd></kbd>.

Vous obtenez l'interface ci-dessous :

![ Contrôle de vue : Création ](30-50-cvdoc-creation.png "Contrôle de vue : Création")

L'interface vous permet de :

-   configurer quel utilisateur aura accès à quelle vue,
-   configurer la vue de création.

Vous allez compléter :

-   le titre : `Fiche de non conformité`,
-   Famille (les deux attributs) : `Fiche de non-conformité`.

Vous devez obtenir un formulaire similaire à :

![ Contrôle de vue : Création ](30-50-cvdoc-creation2.png "Contrôle de vue : Création")

Ajoutez une vue en cliquant sur le `+` du tableau vue.

Chaque ligne vous propose les options suivantes :

`Id vue`
:   identifiant logique de la vue,

`Label`
:   un label pour la vue (utilisé pour les menu et les interfaces d'admin),

`Type`
:   le type de vue soit une vue d'édition (modification), soit de consultation,

`Zone`
:   indique la [zone][DocZone] utilisée pour représenter le document.
    
    Une zone permet de re-définir complètement la représentation d'un document,

`Masque`
:   indique le [masque][DocMasque] associé à cette vue.
    
    le masque permet de définir les visibilités applicable lors de la représentation du document,

`Affichable`
:   indique si la vue est accessible via un menu sur le document,

`Ordre`
:   parmi toutes les vues utilisables par un utilisateur,
    c'est la vue ayant l'ordre le plus faible qui est sélectionnée.

Vous allez ajouter deux vues :

-   `modif_default` :
    cette vue sera la celle par défaut, utilisée pour afficher le document pour tous les utilisateurs.
    Elle restreint les visibilités pour la partie _écart_ en appliquant le masque que vous avez défini.
-   `modif_auditeur` :
    cette vue ne sera proposée qu'aux utilisateurs ayant le rôle `Auditeur` et n'utilisera pas de masque.

Complétez le tableau des vues comme présenté ci-dessous :

![ Contrôle de vue : Création ](30-50-cvdoc-creation3.png "Contrôle de vue : Création")

Cliquez sur Créer.

#### Paramétrage {#dynacase-qs:2e34eab3-a689-493a-b313-b6e3267c5d3b}

Vous allez maintenant paramétrer les droits associés au contrôle de vue.
Ceci permet d'exprimer quelles vues sont proposées à l'utilisateur en fonction de ses rôles et groupes d'appartenance.

Cliquez sur <kbd class="menu"><kbd><samp>Autres</samp></kbd>&gt;<kbd><samp>Sécurité</samp></kbd>&gt;<kbd><samp>Profil dédié</samp></kbd></kbd>.
La page se recharge, cliquez maintenant sur
<kbd class="menu"><kbd><samp>Autres</samp></kbd>&gt;<kbd><samp>Sécurité</samp></kbd>&gt;<kbd><samp>Accessibilités...</samp></kbd></kbd>.

L'interface suivante vous est présentée :

![ Contrôle de vue : Paramétrage ](30-50-cvdoc-param.png "Contrôle de vue : Paramétrage")

Veuillez compléter la matrice avec le paramétrage suivant :

![ Contrôle de vue : Paramétrage ](30-50-cvdoc-param1.png "Contrôle de vue : Paramétrage")

Les droits que vous avez attribués correspondent à :

-   les droits de modifications et de paramétrage du contrôle de vue pour les administrateurs de la plateforme,
-   le droit de modification par défaut pour tous les utilisateurs,
-   le droit de modification auditeur pour les auditeurs.

<span class="flag inline nota-bene"></span>
Les utilisateurs ayant le rôle `auditeurs` ont donc accès aux deux vues de modification.
Mais la vue dédiée aux auditeurs à un ordre plus faible, elle est donc utilisée prioritairement.

#### Export {#dynacase-qs:533f114b-d23a-4962-aa2e-f1fec59b7d32}

Vous allez maintenant exporter le contrôle de vue et son masque.

Ajoutez un nom logique `CVDOC_FNC` au contrôle de vue au moyen du menu
<kbd class="menu"><kbd><samp>Autres</samp></kbd>&gt;<kbd><samp>Propriétés</samp></kbd></kbd>.
Ajoutez le contrôle de vue au porte-documents, en cliquant sur
<kbd class="menu"><kbd><samp>Autres</samp></kbd>&gt;<kbd><samp>Ajoutez au porte-documents</samp></kbd></kbd>.

<span class="flag inline nota-bene"/>
Vous pouvez remarquer que le nom logique du document est préfixé de manière à rapidement identifier son type :
`CVDOC` pour _Contrôle de vue_.

Le porte-documents doit présenter le masque et le contrôle de vue.

![Porte-documents : contrôle de vue et masque](30-50-export-cvdoc.png "Porte-documents : contrôle de vue et masque")

Cliquez ensuite sur
<kbd class="menu"><kbd><samp>Outils</samp></kbd>&gt;<kbd><samp>Exportation du dossier</samp></kbd></kbd>,
la fenêtre d'export s'ouvre.

Vous devez indiquer dans la partie `Profil` `Avec les profils` et ensuite cliquer sur `Exporter`.

Vous obtenez le fichier suivant :

![Porte-documents : contrôle de vue et masque](30-50-import-cvdoc.png "Porte-documents : contrôle de vue et masque")

Ce fichier contient :

-   la configuration du masque (lignes 1 à 3),
-   le profil par défaut des documents systèmes `PRF_ADMIN_EDIT`,
    et son affectation au masque nouvellement créé (lignes 4 à 8).
    
    ce profil est fourni par Dynacase et est appliqué aux documents systèmes
    pour restreindre leur droit de modification,
-   la définition du contrôle de vue (lignes 9 à 11)
-   la définition du profil du contrôle de vue (ligne 12).

### Ajout du contrôle de vue dans les fichiers d'import {#dynacase-qs:ebdec2ce-5ea4-4ab9-8299-42bde28ffb4f}

Vous allez ajouter le contenu de ce fichier dans le fichier de paramétrage de la famille associée.
Ouvrez `./COGIP_AUDIT/COGIP_AUDIT_FNC__PARAM.csv` :

-   copiez les lignes 1 à 3 et 9 à 12 du fichiers d'export au début du fichier param,
-   ajoutez juste avant le `END` :
    -   dans la première case `CVID`,
    -   dans la seconde case `CVDOC_FNC`

Vous obtenez le fichier suivant :

![Famille paramétrage : Fiche de non-conformité](30-50-import-cvdoc-ref.png "Famille paramétrage : Fiche de non-conformité")

Vous pouvez retrouver le fichier complété dans [les sources][tuto_param_fnc].

## Mise en place des modifications {#dynacase-qs:d26ea9af-dc4c-4c90-9a53-0963a06fdfe5}

Vous allez maintenant déployer vos modifications :

    <devtool> deploy  -s . --url http://admin:anakeen@<nomDeDomaine>/dynacase-control/ --port <port> --context dynacase

**Attention** : Les profils ne s'appliquent que sur les nouveaux documents, les documents déjà existant n'étant pas
profilés ceux-ci sont accessibles par tous les utilisateurs. En production, il vous faudrait faire [un script de migration][doc_migration]
pour profiler les documents pré-existants.

Vous devez donc créer de nouveaux documents pour tester.

Vous pouvez maintenant vous connecter à l'application et consulter une fiche de non-conformité
avec un utilisateur ayant le profil `Auditeur` (marthe.karine/p@ssw0rd).

![FNC profil auditeur](30-50-fnc-auditeur.png "FNC profil auditeur")

![FNC profil DSI](30-50-fnc-dsi.png "FNC profil DSI")

Vous pouvez remarquer que l'utilisateur ayant le profil **auditeur** peut ajouter des lignes d'écart
alors que celui qui n'a pas ce profil. Le DSI dans l'exemple ci-dessus (arnic.marina/p@ssw0rd), ne le peut pas.

## Voir aussi {#dynacase-qs:a8ae1a02-f60f-4b81-a207-ad5ff44a8d10}

-   [Les sources après ce chapitre][tuto_zip],
-   [Profil][DocProfilExport],
-   [Contrôle de vue][DocCVDOC],
-   [Zone][DocZone].

<!-- links -->

[wikiCRUD]: https://fr.wikipedia.org/wiki/CRUD "Wikipedia : CRUD"
[DocProfil]: #core-ref:bdc11019-9650-4910-8182-2c9fcdee5fda "Documentation : Profil"
[DocCVDOC]: https://docs.anakeen.com/dynacase/3.2/dynacase-doc-core-reference/website/book/core-ref:017f061a-7c12-42f8-aa9b-276cf706e7e0.html "Documentation : Contrôle de vue"
[DocProfilExport]: #core-ref:602c6331-7cdb-4b24-8a56-ffd11e00502f "Documentation : Profil"
[DocProfilDocument]: #core-ref:f1575705-10e8-4bf2-83b3-4c0b5bfb77cf "Documentation : Profil Document"
[DocMasque]: https://docs.anakeen.com/dynacase/3.2/dynacase-doc-core-reference/website/book/core-ref:327ad491-06df-4e5b-b49a-695c75439fe1.html "Documentation : masque"
[DocZone]: #core-ref:49b96dc9-64e9-4f5a-a167-396282625c1e "Documentation : Zone"
[tuto_zip]: https://github.com/Anakeen/dynacase-quick-start-code/archive/3.2-after-30-50.zip
[tuto_param_audit]: https://github.com/Anakeen/dynacase-quick-start-code/blob/3.2-after-30-50/COGIP_AUDIT/COGIP_AUDIT_AUDIT__PARAM.csv
[tuto_param_chapitre]: https://github.com/Anakeen/dynacase-quick-start-code/blob/3.2-after-30-50/COGIP_AUDIT/COGIP_AUDIT_CHAPITRE__PARAM.csv
[tuto_param_fnc]: https://github.com/Anakeen/dynacase-quick-start-code/blob/3.2-after-30-50/COGIP_AUDIT/COGIP_AUDIT_FNC__PARAM.csv
[tuto_param_ref]: https://github.com/Anakeen/dynacase-quick-start-code/blob/3.2-after-30-50/COGIP_AUDIT/COGIP_AUDIT_REFERENTIEL__PARAM.csv
[deploy_instruct]: #dynacase-qs:e53aa0c3-6fa8-4083-8bb8-b64bd750ab9e
[doc_migration]: http://docs.anakeen.com/dynacase/3.2/dynacase-doc-core-reference/website/book//core-ref:d2bd57f9-7b5a-46b0-8570-6b5b0710d7c3.html
[dynacase-qs:pfam-description]: #dynacase-qs:84222982-26c8-4a1c-9c93-01e82b913b44
