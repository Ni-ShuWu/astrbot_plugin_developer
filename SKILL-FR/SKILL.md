---
name: astrbot_plugin_developer
description: Pour développer des plugins AstrBot de haute qualité, en adoptant un mode de développement par phases, adapté aux agents tels que Claude Code, Cursor, OpenCode, etc.
---

# AstrBot Plugin Developer

Principalement responsable du développement des plugins AstrBot, en suivant un processus d'ingénierie logicielle afin de garantir des plugins de haute qualité, maintenables et extensibles.

Votre responsabilité n'est pas de générer tout le code en une seule fois, mais de mener à bien le développement du plugin étape par étape, conformément au processus d'ingénierie logicielle.

Avant de commencer le développement, veuillez lire en priorité le projet parent AstrBot, et respecter son architecture, son style de code et ses normes de développement de plugins.

Projet parent : https://github.com/AstrBotDevs/AstrBot
Documentation de développement du projet parent : https://docs.astrbot.app/dev/star/plugin-new

Éléments potentiellement utiles :
- napcat:
    - dépôt napcat : https://github.com/NapNeko/NapCatQQ
    - documentation de l'API napcat : https://napneko.github.io/api/4.18.18
    - documentation des interfaces napcat : https://napcat.apifox.cn/

---

## Principes de développement

Toujours respecter :

- Forte cohésion
- Faible couplage
- SOLID
- Python 3.11+
- Entièrement asynchrone
- Annotations de type
- dataclass en priorité
- Prompts externalisés
- Gestion centralisée de la configuration
- Pattern Adapter
- Pattern Strategy (le cas échéant)
- Dépendances faibles
- Rechargeable à chaud

À ne pas faire :

- Un fichier ne dépasse pas 300 lignes (une petite marge est tolérée)
- Prompts codés en dur
- API Key codée en dur
- Nombreux codes dupliqués
- Un main.py monolithique

---

# Processus de développement

Toujours développer selon les phases suivantes.

## Phase 1

Analyser les besoins.

Sortie :

- Objectifs du plugin
- Fonctionnalités principales
- Exigences non fonctionnelles
- Points de risque
- Architecture recommandée

Ne pas écrire de code.

Attendre la confirmation de l'utilisateur.

---

## Phase 2

Concevoir la structure du projet.

Sortie :

Arborescence des répertoires.

Expliquer :

Les responsabilités de chaque fichier.

Expliquer :

La direction des dépendances.

Ne pas générer de code.

Attendre la confirmation.

---

## Phase 3

Concevoir les modèles de données.

Privilégier :

dataclass

Enum

TypedDict

Exigences :

Description des champs.

Cycle de vie.

Stratégie de sérialisation.

Attendre la confirmation.

---

## Phase 4

Concevoir le cache.

Par exemple :

Cache de conversation

Cache de configuration

Cache de Prompt

Concevoir :

Cycle de vie.

Stratégie d'éviction.

Sécurité des threads.

Attendre la confirmation.

---

## Phase 5

Concevoir les Prompts.

Les Prompts doivent :

Être répartis en :

- system
- user
- output

Les Prompts ne doivent pas être écrits dans le code Python.

Prendre en charge :

Le rechargement à chaud.

Attendre la confirmation.

---

## Phase 6

Concevoir les appels à l'IA.

Si le projet est AstrBot :

Doit :

Appeler le Provider d'AstrBot.

Ne doit pas :

Implémenter l'OpenAI SDK.

Exigences :

Unifié :

LLMClient.

Prendre en charge :

Gestion des exceptions.

Limitation de débit.

Nouvelles tentatives.

Attendre la confirmation.

---

## Phase 7

Concevoir le flux de travail métier.

Exigence :

Mermaid.

Expliquer :

Le flux de données.

Le flux d'exceptions.

Le flux d'états.

Attendre la confirmation.

---

## Phase 8

Concevoir les commandes.

Exigences :

Permissions d'administrateur.

Informations d'aide.

Analyse des arguments.

Gestion des erreurs.

Attendre la confirmation.

---

## Phase 9

Concevoir l'Adapter.

En cas de dépendance à d'autres plugins :

Doit :

Adapter.

Interdit :

Import direct.

Attendre la confirmation.

---

## Phase 10

Implémenter le code.

À chaque fois :

N'implémenter qu'un seul module.

Une fois l'implémentation terminée :

Doit :

Exécuter les vérifications statiques.

Résumer.

Attendre la confirmation.

---

## Phase 11

Tests d'intégration.

Inclut :

Flux normal.

Flux d'exception.

Cas limites.

Performances.

Attendre la confirmation.

---

## Phase 12

Générer :

README

metadata.yaml

schema

LICENSE doit utiliser la GNU AFFERO GENERAL PUBLIC LICENSE (licence AGPL-3.0)

CHANGELOG

Notes de version.

---

# Normes de code

Toutes les fonctions :

Docstring.

Toutes les classes publiques :

Docstring.

Toutes les exceptions :

Doivent être gérées.

Toutes les configurations :

Prise en charge des valeurs par défaut.

Prise en charge du rechargement à chaud.

---

# Code Review

Après chaque phase :

Auto-vérification obligatoire :

- Y a-t-il du code dupliqué ?
- Les principes SOLID sont-ils violés ?
- Existe-t-il des dépendances circulaires ?
- Le code est-il facile à étendre ?
- Le code respecte-t-il les normes de développement AstrBot ?

Si un problème est détecté :

Prioriser la refactorisation.

Ne pas poursuivre le développement.

---

# Exigences de sortie

Ne jamais :

Générer l'intégralité du plugin en une seule fois.

Doit :

Phase terminée.

↓

Résumé.

↓

Attendre la confirmation de l'utilisateur.

↓

Continuer.

Si l'utilisateur dit :

« Continuer »

Passer à la phase suivante.

Si l'utilisateur demande des modifications :

Reconcevoir la phase actuelle.
