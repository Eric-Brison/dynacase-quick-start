# Utilisation de Dynacase Document UIs {#dynacase-qs:fc3b273d-5107-48cc-bbc0-08d0a514d4ee}

Dynacase Document UIs est un module Dynacase permettant de générer une représensation des documents au moyen des technologies HTML5.

Le rendu des documents sans ce module est fait par le serveur, sous la forme d'une page HTML4 monolythique. Dynacase Document UIs permet à la génération de se faire côté client au moyen de Javascript, HTML5 et CSS.

Cela apporte les avantages suivants :

-   Répartition de la charge entre les clients
-   Puisque le serveur n'envoie plus que les données, et ne construit plus la page, cela allège la charge du serveur.
-   Souplesse
-   Puisque le rendu est fait en javascript au dernier moment, il est facile de prendre en compte des éléments de
    contexte, et de faire un rendu extrêmement personnalisé
-   Comportement surchargeable
-   De par cette souplesse, il devient très facile de surcharger le comportement du document
    pour implémenter des fonctionnalités avancées.

Pour une présentation plus détaillée de Dynacase Document UIs, se reporter au [manuel de référence][ddui-ref:index].

## Cadre {#dynacase-qs:20fdb9b8-8986-4f9a-bbf9-f78523a443b7}

Au vu de cette présentation, on vous a demandé d'utiliser Dynacase Document UIs pour rendre le document plus attrayant.

## Ajout de la dépendance à Dynacase-Document-uis {#dynacase-qs:bc05ca09-d000-41dc-ac23-92f25979c520}

comme pour les [dépendances précédentes][dynacase-qs:dependances],
il suffit d'ajouter une ligne au fichier `info.xml`.

VOus allez ajouter la ligne suivante dans la balise `<requires/>` :

    [xml]
    <module name="dynacase-document-uis" comp="ge" version="1.0"/>

puis déployer à nouveau le module :

    <devtool> deploy -s . --url http://admin:anakeen@<nomDeDomaine>/dynacase-control/ --port <port> --context dynacase

Vous pouvez ensuite importer les documents d'exemples du fichier [`COGIP_AUDIT/COGIP_AUDIT_DDUI.csv`][gh:COGIP_AUDIT/COGIP_AUDIT_DDUI.csv], puis vous rendre sur la page `http://<nomDeDomaine>/dynacase/api/v1/documents/DDUI_AUDIT.html`
pour consulter le document tel que rendu par _Dynacase Document UIs_.

pour plus de détails sur les fonctionnalités de Dynacase Document UIS,
se reporter au [quick start correspondant][ddui-qs:]

<!-- links -->
[ddui-ref:index] #ddui-ref:
[dynacase-qs:dependances] #dynacase-qs:10724c51-b509-4e1b-8fd4-c066e7be55db
[gh:COGIP_AUDIT/COGIP_AUDIT_DDUI.csv]: https://github.com/Anakeen/dynacase-quick-start-code/blob/3.2-after-30-70/COGIP_AUDIT/COGIP_AUDIT_DDUI.csv
[ddui-qs:]: #ddui-qs: