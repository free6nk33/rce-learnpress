Ce script Bash exploite une vulnérabilité possible dans le plugin LearnPress sur WordPress, en particulier pour les thèmes qui utilisent Kingster, afin de tenter de récupérer des clés AWS (AKIA keys) à partir des fichiers de configuration d'un serveur compromis.
Fonctionnalités :

Exploit sur des domaines multiples : Le script lit un fichier de domaines et teste chacun d'eux pour la vulnérabilité de LearnPress en exécutant plusieurs charges utiles (payloads).
Requête d'exploitation : En utilisant des requêtes spécifiques à l'API LearnPress (/wp-json/lp/v1/load_content_via_ajax/), le script injecte des charges utiles qui tentent d'exécuter des commandes sur le serveur via la méthode LP_Helper::maybe_unserialize.
Construction dynamique de l'URL : Le script construit une URL en ajoutant une chaîne de caractères aléatoire au service Interactsh pour vérifier les interactions potentielles avec le serveur cible.
Extraction de clés AWS (AKIA) : Il cherche des clés AWS dans les réponses et enregistre les résultats dans un fichier de sortie.
Gestion d'en-têtes personnalisés : Le script génère des en-têtes pour les requêtes HTTP en fonction des domaines testés.

Utilisation :

    ./script.sh <fichier_de_domaines> <interactsh_url> <fichier_de_sortie>

<fichier_de_domaines> : Fichier contenant une liste de domaines à tester.
<interactsh_url> : URL du service Interactsh pour vérifier les interactions d'exploitation.
<fichier_de_sortie> : Fichier où seront stockées les clés AWS trouvées.
