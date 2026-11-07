# In arrivo

*Où en sont mes colis ?*

Une petite appli web (PWA) pour suivre ses commandes en ligne quand elles se multiplient : boutiques différentes, transporteurs différents, dates qui glissent.

## Ce qu'elle fait

- **Un écran qui trie tout seul** : *En retard*, *Aujourd'hui*, *À retirer*, *À venir*. Les colis reçus sont rangés en bas.
- **Saisie par collage** : on colle un mail, un message WhatsApp ou une notification (Cartes, appli d'une boutique…). L'appli y cherche la boutique, le transporteur, le numéro de suivi, le lien de suivi, le n° de commande, l'étape et la date annoncée, puis propose une fiche à vérifier.
- **Mise à jour d'une commande existante** : un nouveau message (« livraison reportée », « colis livré »…) est rattaché à la bonne commande grâce au numéro de suivi ou de commande.
- **Historique des dates promises** : « Annoncée : 5 nov. → 8 nov. → 11 nov. (repoussée 2 fois) ». Une commande dont la date est dépassée passe en *En retard*.
- **Retrait en magasin** (Fnac, point relais) : lieu de retrait et date limite, avec une alerte quand elle approche.
- **Bouton « Suivre »** : ouvre la page de suivi du transporteur (bpost, PostNL, DPD, DHL, UPS, GLS, Colissimo, Mondial Relay, Chronopost, FedEx, Amazon), ou 17track quand le transporteur n'est pas reconnu.
- **Sauvegarder / Restaurer** : export et import des commandes dans un fichier JSON.

## Principes

- **Sans serveur, sans compte** : tout reste dans le navigateur (`localStorage`, clé `inarrivo_commandes`).
- **Pas de suivi automatique** : chaque transporteur a ses procédures, l'appli ne les interroge pas. Elle reconnaît le transporteur et ouvre sa page, on met l'étape à jour d'un geste.
- **Reconnaissance sans IA** : de simples motifs (numéros de suivi, dates en français, mots-clés), exécutés localement. Rien n'est envoyé nulle part.

## Fichiers

| Fichier | Rôle |
|---|---|
| `index.html` | L'appli (HTML, CSS et JavaScript en un seul fichier) |
| `manifest.json` | Installation sur l'écran d'accueil |
| `sw.js` | Fonctionnement hors ligne |
| `icon.png`, `icon-192.png`, `icon-512.png` | Icônes |

## Mise à jour

À chaque déploiement, incrémenter `CACHE_NAME` dans `sw.js` (`inarrivo-v1` → `inarrivo-v2`…) pour que les téléphones récupèrent la nouvelle version.

## Installation sur iPhone

Ouvrir l'adresse dans Safari → bouton Partager → **Sur l'écran d'accueil**.

> Les données de l'appli installée et celles de l'onglet Safari sont séparées : utiliser toujours la même (de préférence l'appli installée).
