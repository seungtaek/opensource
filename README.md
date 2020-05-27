# Script de configuration post-installation pour les serveurs CentOS 7 

(c) Niki Kovacs, 2020

Ce référentiel fournit un script "automagique" de configuration post-installation pour
des serveurs fonctionnant sous CentOS 7 ainsi qu'une collection de scripts d'aide et
des modèles de fichiers de configuration pour les services communs.

## En bref

Effectuez les étapes suivantes.

 1. Installer un système CentOS 7 minimal.

 2. Créer un utilisateur non "root" avec des privilèges d'administrateur.

 3. Installer Git : `sudo yum install git`

 4. Saisissez le scénario : `git clone https://gitlab.com/kikinovak/centos-7.git`

 5. Changement dans le nouveau répertoire : "cd centos-7".

 6. Exécutez le script : sudo ./centos-setup.sh --setup

 7. Prenez une tasse de café pendant que le scénario fait tout le travail.

 8. Redémarrage.


## Personnalisation d'un serveur CentOS

Transformer une installation CentOS minimale en un serveur fonctionnel bout toujours
jusqu'à une série d'opérations plus ou moins longues. Votre kilométrage peut
varient bien sûr, mais voici ce que je fais habituellement sur une nouvelle installation CentOS :

 * Personnaliser le shell Bash : prompt, alias, etc.

 * Personnalisez l'éditeur Vim.

 * Mise en place de dépôts officiels et de dépôts de tiers.

 * Installer un ensemble complet d'outils en ligne de commande.

 * Enlever une poignée de paquets inutiles.

 * Permettre à l'utilisateur admin d'accéder aux journaux du système.

 * Désactivez IPv6 et reconfigurez certains services en conséquence.
 
 * Configurer un mot de passe persistant pour `sudo`.

 * Etc.

Le script `centos-setup.sh` effectue toutes ces opérations.

Configurez Bash et Vim et définissez une résolution de console par défaut plus lisible :

```
# ./centos-setup.sh --shell
```

Mettre en place des dépôts officiels et des dépôts de tiers :

```
# ./centos-setup.sh --repos
```

Installez les groupes de paquets `Core` et `Base` avec quelques outils supplémentaires :

```
# ./centos-setup.sh --extra
```

Retirez une poignée de paquets inutiles :

```
# ./centos-setup.sh --prune
```

Permettre à l'utilisateur administrateur d'accéder aux journaux du système :

```
# ./centos-setup.sh --logs
```

Désactivez l'IPv6 et reconfigurez les services de base en conséquence :

```
# ./centos-setup.sh --ipv4
```

Configurez la persistance du mot de passe pour sudo :

```
# ./centos-setup.sh --sudo
```

Réalisez tout cela en une seule fois :

```
# ./centos-setup.sh --setup
```

Déshabillez les paquets et revenez à un système de base amélioré :

```
# ./centos-setup.sh --strip
```

Afficher le message d'aide :

```
# ./centos-setup.sh --help
```

Si vous voulez savoir ce qui se passe exactement sous le capot, ouvrez un deuxième terminal
et de consulter les journaux :

```
$ tail -f /tmp/centos-setup.log
```
