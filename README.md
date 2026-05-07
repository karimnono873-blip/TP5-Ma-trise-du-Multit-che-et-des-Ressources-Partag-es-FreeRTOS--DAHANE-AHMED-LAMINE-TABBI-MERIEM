# 🌌 TP 5 : Multitâche & Ressources Partagées (FreeRTOS) - Systèmes Embarqués

Bienvenue dans le dépôt du **Travail Pratique N°5**. Ce projet constitue une évolution majeure dans la conception de systèmes embarqués, passant d'une architecture séquentielle (Bare Metal) à l'intégration d'un **Système d'Exploitation Temps Réel (RTOS)** : FreeRTOS.

L'objectif est d'apprendre à gérer des tâches concurrentes, l'ordonnancement basé sur les priorités, et la protection des ressources critiques du microcontrôleur **STM32 Nucleo-C031C6**.

## 🚀 Fonctionnalités du Jumeau Numérique (Web)

Afin d'illustrer visuellement les concepts abstraits du multitâche, le fichier `compte_rendu_tp5.html` intègre un simulateur dynamique (HTML/JS) comprenant :
* **Comparateur Séquentiel / Concurrent :** Visualisation en temps réel de l'impact des délais bloquants (`HAL_Delay`) par rapport aux délais gérés par l'OS (`vTaskDelay`).
* **Simulateur de Race Condition :** Démonstration visuelle du "scrambling" de données sur un bus I2C (Écran LCD) lorsque deux tâches tentent d'y accéder sans protection.
* **Simulateur de Mutex :** Résolution du conflit via verrouillage par Mutex, garantissant un affichage propre.
* **Ingénierie RTOS (Post-Lab) :** Réponses d'ingénierie détaillées concernant les états de tâches (Blocked state), l'impact de la modification des priorités (Préemption), l'utilisation avancée des Queues vs Mutex, et la gestion des Sémaphores binaires.

## 📋 Manipulations Réalisées (Code C via FreeRTOS)

1. **Création de Tâches (`xTaskCreate`) :**
   * Implémentation de 3 tâches indépendantes gérant le clignotement de LEDs sur `PA5`, `PA6` et `PA7` à des fréquences distinctes, éliminant l'effet de goulot d'étranglement de la boucle `while(1)`.
2. **Protection Mutex (`xSemaphoreCreateMutex`) :**
   * Encapsulation des requêtes d'écriture de l'écran LCD avec `xSemaphoreTake()` et `xSemaphoreGive()` pour éviter l'entrelacement des données I2C.
3. **Synchronisation Asynchrone :**
   * Utilisation d'un sémaphore binaire pour réveiller instantanément une tâche en état de veille (0% CPU) suite à un événement matériel (appui sur un bouton).

## 🛠️ Matériel & Outils Requis

* **Carte :** STM32 Nucleo-C031C6.
* **Périphériques :** LEDs externes, Bouton poussoir, Écran LCD I2C 16x2.
* **Logiciel :** STM32CubeIDE (avec Middleware FreeRTOS activé via le gestionnaire de packages) ou Wokwi.
* **Environnement Web :** Navigateur web moderne pour lancer le rapport interactif.

## 👥 Équipe du Projet

**Année Universitaire :** 2025/2026
* **Binôme :** Dahane Ahmed Lamine & Tabbi Meriem
* **Enseignante Responsable :** Mme. Afaf Saoud
* **Département :** Électronique
