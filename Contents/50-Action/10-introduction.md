# Action {#dynacase-qs:3e7da180-3454-4344-a8a1-73f958365aa5}

Une [action][DocIntroAction] permet d'étendre les fonctionnalités de Dynacase. Vous pouvez :

-   manipuler des documents,
-   exporter dans un format spécifique (XML, JSON, XLS, PDF, etc.),
-   implémenter le protocole SOAP,
-   implémenter un point d'accès REST,
-   mettre en place une IHM spécifique,
-   etc.

Le système d'action est composé de trois éléments :

-   une fonction PHP qui est exécutée lors de l'appel de l'action,
-   un layout (optionnel) qui permet de faciliter le rendu du retour de l'action,
-   un système d'ACL (optionnel) qui permet de sécuriser l'action.

Les actions peuvent être appelée :

-   en web avec une URL formatée de la manière suivante `<url_du_contexte>?app=<APPLICATION>&action=<ACTION>&param1=<param1>&param2=...`
-   en [CLI à l'aide du WIFF][DocCLIAction].

<!-- links -->

[DocIntroAction]: #core-ref:5f3cfda3-6293-4b3b-8b9f-616e9f9b029f "Documentation : introduction action"
[DocCLIAction]: #core-ref:63832d9f-61a8-4846-a9d5-c34ee58de4a6 "Documentation : action appel CLI"