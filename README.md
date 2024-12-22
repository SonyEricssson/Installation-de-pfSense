# Installation de pfSense

<img src="https://github.com/user-attachments/assets/3831c95d-d9e3-48dd-9bfd-60e2a3f3f0bc" alt="SSH" width="100">

## Introduction

Ce guide explique comment installer pfSense, une solution open-source de pare-feu et de routeur basée sur FreeBSD.

---

## Prérequis

- ISO de pfSense téléchargé depuis le [site officiel de pfSense](https://www.pfsense.org/).

- Une machine physique ou virtuelle prête pour l'installation.

---

## Étapes d'Installation

Démarrez la machine avec l'ISO pfSense monté.

Lorsque l'écran d'accueil apparaît, appuyez sur Enter pour commencer l'installation.

Acceptez les conditions d'utilisation en appuyant sur **Accept**.

## Partitionnement Automatique

- <span style="color:lightblue"> **Sélectionnez Auto (UFS)**</span> à l'écran de partitionnement.

- **Pourquoi UFS** ?UFS (Unix File System) est le système de fichiers natif de FreeBSD, sur lequel pfSense est basé. Il est stable, fiable et adapté aux environnements réseau. Il offre une bonne performance pour les opérations de pare-feu et de routage.

- Appuyez sur **Enter** pour valider.

- <span style="color:lightblue"> **Choisissez MBR**</span> (DOS Partitions) comme schéma de partition si ce n'est pas déjà sélectionné.

- Pourquoi MBR ?MBR (Master Boot Record) est recommandé pour maximiser la compatibilité avec une large gamme de matériels, en particulier les systèmes plus anciens ou non-EFI. C'est une option simple et largement supportée.

- Appuyez sur **OK** pour confirmer.

## Finaliser l'Installation

- Une fois l'installation terminée, pfSense redémarre automatiquement.
- Pendant le redémarrage, retirez l'ISO pour éviter de relancer l'installation.
- Sur une machine virtuelle : clic droit sur la <span style="color:lightblue">**VM > Settings > Retirer l'ISO.**</span>

## Configuration d'un Second Commutateur Virtuel

**Votre machine pfSense aura besoin de deux cartes réseaux :**

- La première, connectée sur votre réseau local pour communiquer avec internet.

- La seconde, connectée sur un réseau privé (sur lequel vous pourrez connecter d'autres VM plus tard).

## Édition des Commutateurs

Pour éditer les commutateurs :

```bash
VMware Menu : Edit > Virtual Network Editor
```
⚠️ **Attention ! La VM doit être éteinte.**

## Ajouter un Nouveau Commutateur

- Nom : "pfsense_lan"

- Type : Host-only (réseau privé)

- Réseau : 10.10.10.0/24

- Désactiver DHCP
