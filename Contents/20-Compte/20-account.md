# Initialisation des comptes {#dynacase-qs:b4800208-9c02-45bc-badc-9948c2277eae}

## Objectifs {#dynacase-qs:d3ca62ec-47fb-42a9-8402-3c580a6382f7}

-   Utiliser l'interface d'administration pour initialiser des comptes,
-   Exporter les comptes,
-   Initialiser des comptes à l'aide des formats d'import,
-   Produire le paquet `webinst` en important les comptes.

## Cadre {#dynacase-qs:fdbc640b-3030-45f5-ad2f-486d3eead6c3}

Lors de la phase de spécification, les éléments suivants ont été identifiés. L'application nécessite :

-   les _rôles_ :
    -   Utilisateur COGIP
    -   Responsable des audits,
    -   Auditeur,
    -   Administrateur fonctionnel.
-   les _groupes_ :
    -   Utilisateurs COGIP,
    -   DSI,
    -   Section Risque Opérationnel et Qualité.

De plus, une bonne pratique est de faire le lien entre les _utilisateurs_ et les _rôles_ au travers des _groupes_.
Nous allons donc également créer les groupes suivants :

-   Responsable des audits,
-   Auditeurs,
-   Administrateur fonctionnel.

Enfin, l'application doit être initialisée avec les utilisateurs suivants :

-   Jean Martin :
    -   section Risque Opérationnel et Qualité,
    -   auditeur,
-   Priscilla Arthaud :
    -   section Risque Opérationnel et Qualité,
    -   auditeur,
-   Arnaud Luc :
    -   section Risque Opérationnel et Qualité,
    -   auditeur,
-   Karine Marthe :
    -   section Risque Opérationnel et Qualité,
    -   auditeur,
    -   responsable des audit,
    -   administrateur fonctionnel,
-   Marina Arnic :
    -   responsable de la DSI,
    -   administrateur fonctionnel.

Les arborescences de rôles, groupes et utilisateurs définis sont les suivants :

-   __Utilisateurs COGIP__
    +   Rôles :
        *   _Utilisateur COGIP_
    +   Membres directs
    +   Sous-groupes :
        *   __DSI__
            -   Rôles
            -   Membres directs
                +   _Marina Arnic_
            -   Sous-groupes
        *   __Auditeurs__
            -   Rôles
                +   _Auditeur_
            -   Membres directs
            -   Sous-groupes
                +   __Responsables des audits__
                    *   Rôles
                        -   _Responsable des audits_
                    *   Membres directs
                        -   _Karine Marthe_
                    *   Sous-groupes
                +   __Section Risque Opérationnel et Qualité__
                    *   Rôles
                    *   Membres directs
                        -   _Jean Martin_
                        -   _Priscilla Arthaud_
                        -   _Arnaud Luc_
                        -   _Karine Marthe_
                    *   Sous-groupes
        *   __Administrateurs fonctionnels__
            -   Rôles
                +   _Administrateur fonctionnel_
            -   Membres directs
                +   _Karine Marthe_
                +   _Marina Arnic_
            -   Sous-groupes

<span class="flag inline nota-bene"></span> Nous avons choisi de respecter les bonnes pratiques
et de ne donner aucun rôle directement à un utilisateur.
Ainsi, les rôles des utilisateurs sont obtenus par leurs groupes d'appartenance (directs et indirects).
L'administrateur n'a donc pas à se demander de quels droits dispose un nouvel utilisateur,
il suffit de mettre l'utilisateur dans le(s) groupe(s) métier qui lui correspondent.

## Interface de gestion des utilisateurs {#dynacase-qs:08baa9d0-d741-4509-b5c5-7b72e74399c3}

Pour initialiser les différents types de comptes, vous pouvez utiliser l'interface web.
Veuillez vous rendre sur l'interface d'administration : `http://<nomDeDomaine>/dynacase/admin.php`,
puis cliquer sur `Gestion des utilisateurs`.

![ Création d'utilisateur ](20-10-users.png "Création d'utilisateurs")

Cette interface permet de créer des utilisateurs, des groupes et des rôles.

<span class="flag inline nota-bene"></span> Vous pouvez replier la partie gauche de l'interface en cliquant sur le
bouton tout en haut à gauche.

## Initialisation des comptes {#dynacase-qs:a8db534a-251b-41a6-927e-0e4dc259b776}

Vous allez dans un premier temps créer un rôle, un groupe, puis un utilisateur depuis l'interface.
la création se fera dans cet ordre car :

-   le groupe référence le rôle
-   l'utilisateur référence le groupe

Dans un second temps, les documents ainsi créés seront exportés.

Enfin, vous utiliserez les formats d'import et d'export pour créer les autres rôles, groupes et utilisateurs.

<span class="flag inline nota-bene"></span> Tous les éléments nécessaires au paramétrage de l'application
doivent être importés pour permettre les installations et mises à jour de l'application
dans divers environnements (développement, pré-production, production).

### Initialisation du premier rôle {#dynacase-qs:1a5c2498-c522-491b-a7a3-f73d03b13116}

Pour créer un rôle, veuillez vous rendre dans
[l'interface de gestion des utilisateurs][dynacase-qs:users],
puis cliquer sur `tous les rôles`.

![ Rôle : liste des rôles ](20-10-role-creation.png "Rôle : liste des rôles")

Appuyez ensuite sur `Créer un rôle`, un formulaire est affiché.
Vous devez compléter le champ obligatoire :

-   _Libellé_ : `Utilisateurs COGIP`.

Appuyez ensuite sur le bouton `Créer`.

Le rôle nouvellement créé s'affiche :

![ Rôle : Création ](20-10-role-creation2.png "Rôle : Création")

### Initialisation du premier groupe {#dynacase-qs:78e478c8-e1bf-4766-9ae1-de45e13e3068}

Pour créer un groupe, veuillez vous rendre dans
[l'interface de gestion des utilisateurs][dynacase-qs:users],
puis cliquer sur `tous les groupes`.

![ Groupe : liste des groupes ](20-10-group-creation.png "Groupe : liste des groupes")

Appuyez ensuite sur `Créer un groupe d'utilisateur`, un formulaire est affiché.
Vous devez compléter les deux champs obligatoires :

-   _Nom_ : `Utilisateurs COGIP`,
-   _Identifiant_ : `GRP_USER_COGIP`.
-   _Rôles associés_ : `Utilisateur COGIP`

Appuyez ensuite sur le bouton `Créer`.

Le groupe nouvellement créé s'affiche :

![ Groupe : Création ](20-10-group-creation2.png "Groupe : Création")

Vous allez maintenant indiquer que ce groupe est un sous-groupe du groupe `Utilisateurs`.
Pour cela, utilisez le menu `Modifier la hiérarchie` et cliquez sur `Utilisateurs` dans la nouvelle fenêtre :

![ Groupe : Modification de la hiérarchie ](20-10-group-creation3.png "Groupe : Modification de la hiérarchie")

Puis cliquez sur le menu `sauver`.

### Initialisation du premier utilisateur {#dynacase-qs:653a946b-9655-4728-9c65-50c90bb771df}

Pour créer un utilisateur, veuillez cliquer sur le bouton `Créer un utilisateur`, l'interface de création apparaît :

![ Utilisateur : création ](20-10-user-creation1.png "Utilisateur : création")

Veuillez compléter le formulaire en fournissant les nom, prénom, login, mail et mot de passe de l'utilisateur :

-   _nom_ : `Martin`,
-   _prénom_ : `Jean`,
-   _mail_ : `martin.jean@quickstartcogip.com`,
-   _login_ : `martin.jean`,
-   _mot de passe_ : `p@ssw0rd`.

Ensuite cliquez sur le bouton `Créer`.

Votre utilisateur est ajouté et est affiché.

![ Utilisateur : création ](20-10-user-creation2.png "Utilisateur : création")

Les utilisateurs ont quelques spécificités, vous pouvez :

-   modifier les groupes dans lequel l'utilisateur est présent (via le menu `Gestion du compte`),
-   ajouter un suppléant à l'utilisateur en cours, le suppléant possède tous les droits de l'utilisateur,
-   indiquer une date d'expiration du compte, passé cette date le compte est désactivé et l'utilisateur
    ne peut plus se connecter à plateforme,
-   désactiver le compte à l'aide du menu `Compte`.

Vous allez maintenant indiquer que l'utilisateur est membre du groupe `Utilisateurs COGIP`.
Pour cela, utilisez le menu <kbd class="menu"><kbd><samp>Gestion du compte</samp></kbd>&gt;
<kbd><samp>Changer de groupes</samp></kbd></kbd>
et cliquez sur `Utilisateurs` dans la nouvelle fenêtre pour le désélectionner, puis cliquez sur `Utilisateurs COGIP`
pour le sélectionner :

![ Utilisateur : Modification de la hiérarchie ](20-10-user-creation3.png "Utilisateur : Modification de la hiérarchie")

<span class="flag inline nota-bene"></span> `Utilisateurs` est en bleu, alors que `Utilisateurs COGIP` est en vert.
Cela signifie que l'utilisateur est __membre direct__ du groupe `Utilisateurs COGIP`,
alors qu'il est __membre indirect__ du groupe `Utilisateurs` (en effet, il est membre d'un de ses sous-groupes).

Puis cliquez sur le menu `sauver`.

### Export des comptes {#dynacase-qs:137414aa-e378-4ece-b343-6e0ddc4d27c0}

Vous allez maintenant exporter les comptes créés. Veuillez fermer la fiche utilisateur,
et utiliser les filtres dans la grille pour ne voir que cet utilisateur dans la liste.

![ Utilisateur : export ](20-10-user-export1.png "Utilisateur : export")

Cliquez ensuite sur le bouton Exporter les utilisateurs. La fenêtre suivante s'ouvre :

![ Utilisateur : export ](20-10-user-export2.png "Utilisateur : export")

Cette fenêtre affiche les options d'export, ainsi que la liste des groupes qui seront exportés
(dans notre cas, il est indiqué `Sélection : Tous les groupes, Identifiant : cogip`,
ce qui correspond à notre filtrage).

Choisissez les options suivantes :

-   Exporter avec les schémas XML : Oui
    
    Les xsd ont déjà été exportées avec les comptes, il n'est pas nécessaire de les télécharger plusieurs fois.
    Toutefois, activer cette option inclut dans le xml la référence à la xsd,
    ce qui sera utile lors de la mise à jour du fichier _à la main_
    
-   Exporter les mots de passe cryptés : Oui
    
    Indique que les mots de passe doivent être exportés.
    Comme dynacase ne stocke pas les mots de passe en clair, seul le hash correspondant peut être exporté.
    Sans cette option, le mot de passe est vide (et les utilisateurs importés ne peuvent donc pas se connecter).
    
-   Exporter les rôles associés : Oui
    
    Indique que les rôles référencés par cet utilisateur seront également exportés.
    
-   Exporter les groupes des utilisateurs : Oui
    
    Indique que les groupes référencés par cet utilisateur seront également exportés.
    
-   Exporter les données documentaires spécifiques : Oui
    
    Indique que les informations du document (comme le libellé) seront également exportées.
    Sans cette option, seules les données systèmes du rôle sont exportées.

Puis cliquez sur exporter les comptes.

Vous obtenez un fichier zip contenant :

-   un répertoire `XSD`
    
    Déposez ce répertoire à la racine du module.
    <span class="flag inline nota-bene"></span> puisque ce répertoire n'est pas référencé dans le fichier
    [`build.json`][dynacase-qs:build.json], il ne sera pas déployé. ce répertoire ne sert qu'au développement.
    
-   un fichier xml
    
    Déposez ce fichier dans le répertoire `COGIP_AUDIT` sous le nom `accounts.xml`.
    
    Puisque les options __Exporter les rôles associés__ et __Exporter les groupes des utilisateurs__
    ont été sélectionnées, le xml généré contient les données du rôle, du groupe et de l'utilisateur
    nouvellement créés.
    
    Le fichier xml correspondant peut être téléchargé [ici][github:accounts.xml]

## Ajout des nouveaux comptes dans le fichier d'import {#dynacase-qs:1d608a55-3178-48ed-9ed3-216b3920d07e}

### Format d'import / export {#dynacase-qs:9f1e3e32-bb48-4e6b-807a-37ff31c0f705}

Le format du xml est défini dans [le manuel de référence][core-ref:xml_accounts].

### Ajout des instructions d'import {#dynacase-qs:bef50695-1c40-485b-97a2-928c2c8a591c}

Il vous reste à ajouter l'instruction d'import du fichier dans le fichier `info.xml`.

Ce fichier déclare les actions réalisées lors de l'installation ou la mise à jour du paquet.
Vous allez donc ajouter la ligne suivante pour demander l'import des utilisateurs :

    [xml]
    <process command='./wsh.php --api=importAccounts --file=COGIP_AUDIT/accounts.xml'/>

-   dans le bloc `<post-install></post-install>` (actions à réaliser après le déploiement des fichiers lors d'une installation)
    entre les lignes
    
        [xml]
        <process command="programs/record_application COGIP_AUDIT" />
    et
        [xml]
        <process command="programs/update_catalog" />
-   dans le bloc `<post-upgrade></post-upgrade>` (actions à réaliser après le déploiement des fichiers lors d'une mise à jour)
    entre les lignes
    
        [xml]
        <process command="programs/record_application COGIP_AUDIT"/>
    et
        [xml]
        <process command="programs/post_migration COGIP_AUDIT"/>

Le fichier xml complété peut-être consulté [ici][github:info.xml].

### Ajout des autres comptes {#dynacase-qs:28c4dbb7-97ea-4902-94ca-7e04db2d6d43}

#### Paramétrage de la xsd {#dynacase-qs:33074523-ab44-49f3-8a89-cf5f24a60486}

En ouvrant le fichier `COGIP_AUDIT/accounts.xml`, vous pouvez constater qu'il référence le schéma `accounts.xsd`
(`xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="XSD/accounts.xsd"`).
Toutefois, puisque nous avons déposé le répertoire XSD à la racine du contexte,
nous pouvons redéfinir son emplacement en remplaçant la ligne précédente par

    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="../XSD/accounts.xsd"

<span class="flag inline nota-bene"></span> cette étape n'est pas obligatoire.
Toutefois, si votre IDE supporte les xsd, le xml sera validé au fur et à mesure de sa complétion,
et l'IDE pourra même vous proposer de l'auto-completion.

#### renommage du rôle {#dynacase-qs:e08713c5-3885-4a5d-9e77-6de66be1b6a4}

Vous remarquez que le rôle qui a été créé via l'interface contient une référence aléatoire.
Étant donné que la référence sera utilisée dans le profilage, vous allez remplacer cette référence.
Toutefois, la référence servant de clé d'identification du rôle,
l'import d'un rôle avec le même libellé (`displayName`), mais une `référence` différente ne fera pas une mise à jour,
mais va créer un nouveau rôle. il faut donc :

-   remplacer toutes les occurrences de cette référence aléatoire par une référence compréhensible
    (`role_utilisateurs_cogip`)
-   supprimer le rôle `Utilisateurs COGIP` avec la référence aléatoire depuis l'interface Dynacase.

#### Ajout des rôles {#dynacase-qs:b7d88777-6d2b-43a1-baf5-e1c4927dd3fe}

Dans la section `<roles/>`, nous allons ajouter les 2 rôles manquants :

-   _Auditeur_
-   _Administrateur fonctionnel_

Le bloc `<roles></roles>` a donc le contenu suivant :

    [xml]
    <roles>
      <role id="13">
        <reference>role_utilisateurs_cogip</reference>
        <displayName>Utilisateur COGIP</displayName>
        <document family="ROLE">
          <role title="Utilisateur COGIP" revision="0" modification-date="2016-04-20T13:42:00" version="" state=""/>
        </document>
      </role>
      <role>
        <reference>role_responsable_audit</reference>
        <displayName>Responsable des audits</displayName>
        <document family="ROLE">
          <role title="Responsable des audits"/>
        </document>
      </role>
      <role>
        <reference>role_auditeur</reference>
        <displayName>Auditeur</displayName>
        <document family="ROLE">
          <role title="Auditeur"/>
        </document>
      </role>
      <role>
        <reference>role_admin_fonc</reference>
        <displayName>Administrateur fonctionnel</displayName>
        <document family="ROLE">
          <role title="Administrateur fonctionnel"/>
        </document>
      </role>
    </roles>

#### Ajout des groupes {#dynacase-qs:5269e199-4dfa-4d9c-936b-b7d568cd1a4d}

Dans la section `<groups/>`, nous allons ajouter les 3 groupes manquants :

-   _DSI COGIP_
    +   membre du groupe _Utilisateurs COGIP_
-   _Auditeurs_
    +   membre du groupe _Utilisateurs COGIP_
    +   rôle _Auditeur_
-   _Administrateurs fonctionnels_
    +   membre du groupe _Utilisateurs COGIP_
    +   rôle _Administrateur fonctionnel_
-   _Responsables des audits_
    +   membre du groupe _Auditeurs_
    +   rôle _Responsable des audits_
-   _Section Risque Opérationnel et Qualité_
    +   membre du groupe _Auditeurs_

Le bloc `<groups></groups>` a donc le contenu suivant :

    [xml]
    <groups>
      <group id="2">
        <reference>all</reference>
        <displayName>Utilisateurs</displayName>
        <document family="IGROUP">
          <igroup name="GDEFAULT" title="Utilisateurs" revision="0" modification-date="2016-04-20T14:09:04" version="" state=""/>
        </document>
      </group>
      <group id="12">
        <reference>grp_user_cogip</reference>
        <displayName>Utilisateurs COGIP</displayName>
        <associatedRoles reset="false">
          <associatedRole reference="role_utilisateurs_cogip"/>
        </associatedRoles>
        <parentGroups reset="false">
          <parentGroup reference="all"/>
        </parentGroups>
        <document family="IGROUP">
          <igroup title="Utilisateurs COGIP" revision="0" modification-date="2016-04-20T14:40:10" version="" state=""/>
        </document>
      </group>
      <group>
        <reference>grp_dsi</reference>
        <displayName>DSI</displayName>
        <associatedRoles reset="false">
        </associatedRoles>
        <parentGroups reset="false">
          <parentGroup reference="grp_user_cogip"/>
        </parentGroups>
        <document family="IGROUP">
          <igroup title="DSI"/>
        </document>
      </group>
      <group>
        <reference>grp_auditeurs</reference>
        <displayName>Auditeurs</displayName>
        <associatedRoles reset="false">
          <associatedRole reference="role_auditeur"/>
        </associatedRoles>
        <parentGroups reset="false">
          <parentGroup reference="grp_user_cogip"/>
        </parentGroups>
        <document family="IGROUP">
          <igroup title="Auditeurs"/>
        </document>
      </group>
      <group>
        <reference>grp_admin_fonc</reference>
        <displayName>Administrateurs fonctionnels</displayName>
        <associatedRoles reset="false">
          <associatedRole reference="role_admin_fonc"/>
        </associatedRoles>
        <parentGroups reset="false">
          <parentGroup reference="grp_user_cogip"/>
        </parentGroups>
        <document family="IGROUP">
          <igroup title="Administrateurs Fonctionnels"/>
        </document>
      </group>
      <group>
        <reference>grp_responsable_audit</reference>
        <displayName>Responsables des audits</displayName>
        <associatedRoles reset="false">
          <associatedRole reference="role_responsable_audit"/>
        </associatedRoles>
        <parentGroups reset="false">
          <parentGroup reference="grp_auditeurs"/>
        </parentGroups>
        <document family="IGROUP">
          <igroup title="Responsables des audits"/>
        </document>
      </group>
      <group>
        <reference>grp_section_risque_operationnel_qualite</reference>
        <displayName>Section Risque Opérationnel et Qualité</displayName>
        <associatedRoles reset="false">
        </associatedRoles>
        <parentGroups reset="false">
          <parentGroup reference="grp_auditeurs"/>
        </parentGroups>
        <document family="IGROUP">
          <igroup title="Section Risque Opérationnel et Qualité"/>
        </document>
      </group>
    </groups>

#### Ajout des utilisateurs {#dynacase-qs:4ecc84f3-1fce-4edf-be30-c66c0b4fa54f}

Dans la section `<users/>`, nous allons ajouter les utilisateurs manquants :

-   Priscilla Arthaud :
    -   Membre du groupe section Risque Opérationnel et Qualité,
    -   Membre indirect du groupe auditeur,
-   Arnaud Luc :
    -   Membre du groupe section Risque Opérationnel et Qualité,
    -   Membre indirect du groupe auditeur,
-   Karine Marthe :
    -   Membre du groupe section Risque Opérationnel et Qualité,
    -   Membre du groupe responsable des audit,
    -   Membre du groupe administrateur fonctionnel,
    -   Membre indirect du groupe auditeur,
-   Marina Arnic :
    -   Membre du groupe responsable de la DSI,
    -   Membre du groupe administrateur fonctionnel.

Le bloc `<users></users>` a donc le contenu suivant :

    [xml]
    <users>
      <user id="11">
        <login>martin.jean</login>
        <firstname>Jean</firstname>
        <lastname>Martin</lastname>
        <mail>martin.jean@quickstartcogip.com</mail>
        <status activated="true"/>
        <password crypted="true">$5$W5l3wgIyC3wKO6ML$Vl875jOLPfxZO8iM/Pvfc/NvV2CjoqGSfOPNUXBUM6B</password>
        <parentGroups reset="false">
          <parentGroup reference="grp_section_risque_operationnel_qualite"/>
        </parentGroups>
        <document family="IUSER">
          <iuser title="Martin Jean" revision="0" modification-date="2016-04-20T14:40:10" version="" state=""/>
        </document>
      </user>
      <user>
        <login>arthaud.priscilla</login>
        <firstname>Priscilla</firstname>
        <lastname>Arthaud</lastname>
        <mail>arthaud.priscilla@quickstartcogip.com</mail>
        <status activated="true"/>
        <password crypted="true">$5$W5l3wgIyC3wKO6ML$Vl875jOLPfxZO8iM/Pvfc/NvV2CjoqGSfOPNUXBUM6B</password>
        <parentGroups reset="false">
          <parentGroup reference="grp_section_risque_operationnel_qualite"/>
        </parentGroups>
        <document family="IUSER">
          <iuser title="Arthaud Priscilla"/>
        </document>
      </user>
      <user>
        <login>luc.arnaud</login>
        <firstname>Arnaud</firstname>
        <lastname>Luc</lastname>
        <mail>luc.arnaud@quickstartcogip.com</mail>
        <status activated="true"/>
        <password crypted="true">$5$W5l3wgIyC3wKO6ML$Vl875jOLPfxZO8iM/Pvfc/NvV2CjoqGSfOPNUXBUM6B</password>
        <parentGroups reset="false">
          <parentGroup reference="grp_section_risque_operationnel_qualite"/>
        </parentGroups>
        <document family="IUSER">
          <iuser title="Luc Arnaud"/>
        </document>
      </user>
      <user>
        <login>marthe.karine</login>
        <firstname>Karine</firstname>
        <lastname>Marthe</lastname>
        <mail>marthe.karine@quickstartcogip.com</mail>
        <status activated="true"/>
        <password crypted="true">$5$W5l3wgIyC3wKO6ML$Vl875jOLPfxZO8iM/Pvfc/NvV2CjoqGSfOPNUXBUM6B</password>
        <parentGroups reset="false">
          <parentGroup reference="grp_section_risque_operationnel_qualite"/>
          <parentGroup reference="grp_responsable_audit"/>
          <parentGroup reference="grp_admin_fonc"/>
        </parentGroups>
        <document family="IUSER">
          <iuser title="Marthe Karine"/>
        </document>
      </user>
      <user>
        <login>arnic.marina</login>
        <firstname>Marina</firstname>
        <lastname>Arnic</lastname>
        <mail>arnic.marina@quickstartcogip.com</mail>
        <status activated="true"/>
        <password crypted="true">$5$W5l3wgIyC3wKO6ML$Vl875jOLPfxZO8iM/Pvfc/NvV2CjoqGSfOPNUXBUM6B</password>
        <parentGroups reset="false">
          <parentGroup reference="grp_dsi"/>
          <parentGroup reference="grp_admin_fonc"/>
        </parentGroups>
        <document family="IUSER">
          <iuser title="Arnic Marina"/>
        </document>
      </user>
    </users>

et de changer le groupe parent de Jean Martin par `grp_section_risque_operationnel_qualite`

## Mise en place des modifications {#dynacase-qs:c7522c13-68ab-47c7-b592-6c672b963820}

Vous allez maintenant déployer vos modifications :

    <devtool> deploy -s . --url http://admin:anakeen@<nomDeDomaine>/dynacase-control/ --port <port> --context dynacase

Vous pouvez maintenant vous rendre dans la gestion des utilisateurs :

![ Importation : résultat ](20-20-final.png "Importation : résultat")

Vous pouvez voir que les groupes ont été ajoutés, l'arborescence respectée et les différents rôles associés.

<span class="flag inline nota-bene"></span>  Le recalcul de l'arborescence des groupes et des droits est asynchrone,
il peut y avoir un décalage de quelques minutes entre l'installation du paquet et la visualisation des données sur le contexte.

## Conclusion {#dynacase-qs:ebfe623e-99c3-4b85-92a5-a790685b3e7e}

Dans ce chapitre, vous avez parcouru l'ensemble des techniques pour créer, associer et importer les différents éléments
nécessaires à la gestion des comptes Dynacase.

Ces éléments vous serviront dans toutes les autres phases de vos projets pour fixer les droits, définir des vues particulières, etc.

## Pour aller plus loin {#dynacase-qs:ff368e8d-9630-408d-9644-5383753f2ac0}

Vous pouvez consulter les chapitres suivants de la documentation :

-   [les comptes][core-ref:account],
-   [le format d'import CSV][formatCSV],
-   [les sources après le tutoriel][github:sources_final].

<!-- links -->
[core-ref:account]:         #core-ref:2bd98eec-5b03-4af0-b9d6-1bbf78fe9733 "Doc Dynacase : Comptes"
[core-ref:xml_accounts]:    #core-ref:d9e6f16a-6627-4f12-9d5f-a136b21e7cc3
[devtools:build.json]:      #devtools:f0fb9907-44e1-4956-aea1-14beb5cc077c
[dynacase-qs:users]:        #dynacase-qs:08baa9d0-d741-4509-b5c5-7b72e74399c3
[github:accounts.xml]:      https://github.com/Anakeen/dynacase-quick-start-code/blob/3.2-init-accounts/COGIP_AUDIT/accounts.xml
[github:info.xml]:          https://github.com/Anakeen/dynacase-quick-start-code/blob/3.2-init-accounts/info.xml
[github:sources_final]:     https://github.com/Anakeen/dynacase-quick-start-code/archive/3.2-after-20-20.zip "Github : source après le tutoriel"