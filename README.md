# Installation-DNS

## 1. Ajout d'un nouveau DNS dans Windows Server
Ouvrir le Gestionnaire de serveur

Cliquer sur Ajouter des rôles et fonctionnalités

Sélectionner Installation basée sur un rôle ou une fonctionnalité

Choisir le serveur cible et cliquer sur Suivant

Cocher Serveur DNS, puis cliquer sur Suivant jusqu'à l'installation

Une fois l'installation terminée, cliquer sur Fermer


## 2. Configuration de la zone DNS

Ouvrir la Console de gestion DNS (dnsmgmt.msc).

Dans l'arborescence, cliquer droit sur Zones de recherche directe et sélectionner Nouvelle zone....

Sélectionner Zone principale, cliquer sur Suivant.

Nommer la zone : wilders.lan, puis cliquer sur Suivant.

Accepter l'option de fichier de zone par défaut et cliquer sur Suivant.

Choisir N'autoriser que les mises à jour sécurisées.

Cliquer sur Terminer.

## 3. Ajout des enregistrements A

Dans la console Gestion DNS, développer la zone wilders.lan.

Cliquer droit et sélectionner Nouvel hôte (A ou AAAA).

Ajouter l'entrée :

Nom : ns

Adresse IP : 192.168.1.1

Ajouter une autre entrée :

Nom : client

Adresse IP : 192.168.1.2

Cliquer sur OK et fermer la boîte de dialogue.

## 4. Ajout d'un alias CNAME

Dans la console Gestion DNS, cliquer droit sur la zone wilders.lan et sélectionner Nouvelle entrée d'alias (CNAME).

Ajouter l'entrée :

Nom d'alias : dns

Nom de l'hôte cible : ns.wilders.lan

Cliquer sur OK.

## 5. Configuration du client

Sur une machine cliente Windows, configurer le serveur DNS :

Ouvrir Paramètres réseau et Internet.

Sélectionner Ethernet > Modifier les options de l’adaptateur.

Faire un clic droit sur l’interface réseau et choisir Propriétés.

Sélectionner Protocole Internet version 4 (TCP/IPv4) et cliquer sur Propriétés.

Choisir Utiliser l’adresse de serveur DNS suivante et entrer 192.168.1.1.

Cliquer sur OK et fermer les fenêtres.

# Commandes Windows Server et Windows 10

nslookup ns.wilders.lan
nslookup client.wilders.lan
nslookup dns.wilders.lan
