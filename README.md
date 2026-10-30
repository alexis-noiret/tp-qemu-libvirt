# 🖥️ TP QEMU, KVM & libvirt — Mini-lab offensif isolé

> Mise en place d'une pile de virtualisation (QEMU/KVM/libvirt) puis construction d'un mini-lab offensif isolé (VM attaquante Kali / VM victime Metasploitable2) : scan, exploitation, remédiation.

## 📋 Contexte

Projet réalisé dans le cadre du **Bachelor IT Cybersécurité** à **La Plateforme**, en bare metal sur un laptop personnel (EndeavourOS), dans un **laboratoire isolé et sécurisé** (réseau virtuel sans aucune route vers l'extérieur, machines volontairement vulnérables dédiées uniquement à cet usage).

📄 **Le compte rendu complet, détaillé étape par étape avec toutes les commandes et captures d'écran, est dans [`compte-rendu-tp-qemu-libvirt.pdf`](./compte-rendu-tp-qemu-libvirt.pdf).**

## 🎯 Compétences démontrées

- **BC01·C4** : Administrer et sécuriser une infrastructure virtualisée (QEMU / KVM / libvirt)
- **BC01·C1 / C2** : Bonnes pratiques d'administration, conception de réseaux virtuels isolés
- **BC02·C5 / C6** : Automatisation (virt-install, cloud-init)
- **BC03·C8** : Mesure du niveau de sécurité d'une infrastructure (scan, identification de vulnérabilités)
- **BC03·C10** : Détection et traitement d'un incident de sécurité (snapshot, exploitation, restauration)

## 🏗️ Résumé de l'architecture

- Réseau `default` (NAT) : VM `debian13` de validation de la pile
- Réseau `isolated-lab` (isolé, sans route externe) : `kali-attacker` (attaquant) et `metasploitable2-victim` (victime)

Vulnérabilité exploitée : backdoor **UnrealIRCd 3.2.8.1** sur Metasploitable2 → accès root sans authentification, puis restauration via snapshot libvirt (`snapshot-sain`).

## 📁 Structure du dépôt

```
tp-qemu-libvirt/
├── README.md
├── compte-rendu-tp-qemu-libvirt.pdf    ← document complet (étapes, commandes, captures)
└── xml/
    ├── debian13.xml
    ├── kali-attacker.xml
    ├── metasploitable2-victim.xml
    ├── network-default.xml
    └── network-isolated-lab.xml
```

## ⚠️ Cadre légal et éthique

Toutes les techniques présentées (scan, exploitation) ont été appliquées exclusivement sur des machines virtuelles personnelles, dédiées et volontairement vulnérables, dans un réseau sans accès extérieur. Vocation strictement pédagogique.

---

**Auteur** : Alexis Noiret — [@alexis-noiret](https://github.com/alexis-noiret)
Bachelor IT Cybersécurité — La Plateforme
