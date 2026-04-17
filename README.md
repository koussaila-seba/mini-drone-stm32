# 🚁 Mini-drone quadricoptère STM32F401

Conception complète d'une carte de vol pour mini-drone quadricoptère avec communication Bluetooth Low Energy et pilotage via application mobile.

> 🎓 **Projet d'équipe (5 personnes)** — Licence 3 EEA, Université Claude Bernard Lyon 1 (2025-2026)

---

## 🎯 Objectif

Concevoir, fabriquer et programmer **from scratch** un mini-drone quadricoptère complet :
- Carte de vol PCB custom (pas de carte ST du commerce)
- Firmware C développé maison
- Communication BLE et pilotage via smartphone
- Châssis 3D imprimé

---

## 🛠️ Architecture technique

### Carte de vol (PCB sous KiCad)
- **Microcontrôleur** : STM32F401 (ARM Cortex-M4) cadencé à 84 MHz
- **Horloge** : quartz externe 16 MHz + PLL
- **Capteur inertiel** : LSM6DSR (accéléromètre + gyroscope 6 axes) sur SPI2
- **Bluetooth** : module BlueNRG-M0A sur SPI1
- **Alimentation** : mesure VBAT via ADC et pont diviseur
- **Moteurs** : 4 moteurs DC coreless commandés en PWM via TIM4 (50 Hz)

### Firmware (STM32CubeIDE, langage C)
- Configuration horloges, drivers SPI/IMU/ADC/PWM
- PID 3 axes (roulis, tangage, lacet)
- Parsing des commandes BLE GATT
- Communication avec l'application mobile **ST BLE Drone**

### Mécanique (CAO 3D + impression 3D)
- Châssis 20×20 cm imprimé en 3D
- Masse totale < 250 g
- Contraintes d'équilibrage et protection des hélices
- Configuration quadricoptère en croix

---

## 📡 Caractéristiques

| Paramètre | Valeur |
|---|---|
| Moteurs | DC coreless 3.7 V, 85×20 mm |
| Hélices | 65 mm (2× CW + 2× CCW) |
| Batterie | LiPo 1S 3.7 V / 600 mAh / 30C |
| Poids total | 200-250 g |
| Autonomie | 8 à 10 minutes |

---

## 📂 Contenu du dépôt

- `/pcb` — schéma et routage KiCad (Gerber)
- `/firmware` — code source C (STM32CubeIDE)
- `/cao` — fichiers 3D du châssis (STL, STEP)
- `/docs` — compte-rendu, roadmap, schémas d'architecture
- `/photos` — photos du drone assemblé et vidéos du vol

---

## 🧰 Technologies utilisées

`STM32F401` `ARM Cortex-M4` `KiCad` `STM32CubeIDE` `C embarqué` `SPI` `PWM` `ADC` `LSM6DSR` `BlueNRG-M0A` `Bluetooth LE` `PID` `CAO 3D` `Impression 3D`

---

## 👥 Équipe et contributions

Répartition des rôles au sein de l'équipe de 5 personnes :
- **Schéma/PCB KiCad** : conception et routage de la carte
- **Firmware STM32** : drivers et intégration périphériques
- **BLE + App mobile** : intégration BlueNRG et communication GATT
- **Stabilisation PID** : réglage des gains sur 3 axes
- **Mécanique 3D** : conception et impression du châssis

**Mes contributions :** participation à la conception schéma/PCB sous KiCad, au firmware C (initialisation horloges, drivers SPI IMU et PWM moteurs), à l'intégration BLE/application mobile, à la mise au point du PID de stabilisation, et à la coordination d'équipe.

---

## 📊 Statut du projet

✅ **Drone fonctionnel — il vole !**

---

## 👤 Auteur

**Koussaila SEBA** — Licence 3 EEA, Université Claude Bernard Lyon 1

- 📧 seba.koussaila.1@gmail.com
- 💼 [LinkedIn](https://linkedin.com/in/koussaila-seba)
- 🐙 [Profil GitHub](https://github.com/koussaila-seba)
