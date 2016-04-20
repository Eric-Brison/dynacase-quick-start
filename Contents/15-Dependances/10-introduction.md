# Gestion des dépendances {#dynacase-qs:10724c51-b509-4e1b-8fd4-c066e7be55db}

Dans les chapitres suivants, vous allez utiliser des fonctionnalités fournies par d'autres modules.

Afin de s'assurer que ces fonctionnalités sont disponibles, on va exprimer des dépendances entre les modules.

Lors de l'installation ou de la mise à jour d'un module, ses dépendances sont également installées.

<span class="flag inline nota-bene"></span> Si au moins l'une des dépendances ne peut pas être satisfaite,
alors l'installation ou la mise à jour ne peuvent être effectuées.

## Ajout d'une dépendance {#dynacase-qs:55127850-67e1-4c12-9c5e-9fbd719c2b30}

Les dépendances s'expriment dans le fichier `info.xml` au moyen de la section `requires`.
Chaque dépendance est exprimée sous la forme d'une balise `module`.

Dans les chapitres suivants, plusieurs fonctionnalités seront utilisées.
Afin que les modules correspondants soient installés, dans le fichier `info.xml`, remplacer la section `requires` par :

    [xml]
    <requires>
        <module comp="ge" name="dynacase-core" version="3.2"/>
        <module name="dynacase-onefam" comp="ge" version="3.2"/>
        <module name="dynacase-admin-uis" comp="ge" version="1.0"/>
        <module name="dynacase-app-switcher" comp="ge" version="1.0"/>
    </requires>

Le fichier xml complété peut-être consulté [ici][source_info.xml].

Cela exprime les dépendances suivantes :

-   module __dynacase-onefam__ (`name="dynacase-onefam"`)
    en version __supérieure ou égale__ (`comp="ge"`) à __3.2__ (`version="3.2"`)
-   module __dynacase-admin-uis__ (`name="dynacase-admin-uis"`)
    en version __supérieure ou égale__ (`comp="ge"`) à __1.0__ (`version="1.0"`)
-   module __dynacase-onefam__ (`name="dynacase-app-switcher"`)
    en version __supérieure ou égale__ (`comp="ge"`) à __1.0__ (`version="1.0"`)

## Mise en place des modifications {#dynacase-qs:f7a021d5-01e2-4147-a19b-3c4beecadd36}

Vous allez maintenant déployer vos modifications :

    <devtool> deploy -s . --url http://admin:anakeen@<nomDeDomaine>/dynacase-control/ --port <port> --context dynacase

En vous rendant sur dynacase-control (`http://<nomDeDomaine>/dynacase-control/`), vous pouvez constater que les modules
exprimés en dépendance ont été installés.

<!-- links -->
[source_info.xml]: https://github.com/Anakeen/dynacase-quick-start-code/blob/3.2-after-15-10/info.xml