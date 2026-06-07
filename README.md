# 🚁 Mini-drone quadricoptère STM32F401 — Architecture Plastronique 3D

Conception complète d'une carte de vol (FCU) pour mini-drone quadricoptère, avec
électronique intégrée au châssis par technologie plastronique 3D (IME), communication
Bluetooth Low Energy et pilotage via application mobile.

> 🎓 **Projet d'équipe (5 personnes)** — Licence 3 EEA
> Université Claude Bernard Lyon 1 / INSA Lyon — Laboratoire Ampère (2025–2026)

---

## 🎯 Objectif

Concevoir et fabriquer une carte de vol de mini-drone en appliquant la **plastronique 3D** :
les pistes conductrices sont intégrées directement dans la structure du châssis par la
technologie **IME (In-Mold Electronics)**, au lieu d'un PCB séparé relié par câblage.

- Carte de vol custom sous KiCad — schéma 7 blocs validé (0 erreur ERC)
- Firmware C embarqué basé sur le code open source ST, adapté à notre architecture
- Communication BLE et pilotage via smartphone
- Châssis 3D modélisé et imprimé, intégrant les contraintes plastroniques

---

## 🛠️ Architecture technique

### Carte de vol (KiCad 9.0.1)
- **Microcontrôleur** : STM32F401CCU6 (ARM Cortex-M4) à 84 MHz
- **Horloge** : quartz externe 16 MHz + PLL
- **Capteur inertiel** : LSM6DSR (accéléromètre + gyroscope) sur SPI2
- **Bluetooth** : module BlueNRG-M0A (BLE 4.2) sur SPI1
- **Alimentation** : LDO 3.3 V + mesure VBAT via ADC et pont diviseur
- **Moteurs** : 4 sorties PWM via TIM4 (50 Hz) vers ESC externes

### Firmware (STM32CubeIDE, langage C)
- Configuration horloges, drivers SPI / IMU / ADC / PWM
- Correcteur PID double boucle 3 axes (roulis, tangage, lacet)
- Parsing des commandes BLE GATT
- Compatible avec l'application mobile **ST BLE Drone**

### Mécanique (CAO 3D + impression 3D)
- Châssis croix 16×16 cm modélisé sous Autodesk Fusion 360
- Moule plastronique en 2 itérations (profil trapézoïdal, nervures de renfort)
- Impression PLA sur PRUSA MK4 (FabLab)
- Masse cible < 250 g — configuration quadricoptère en croix

---

## 📡 Caractéristiques

| Paramètre | Valeur |
|---|---|
| Microcontrôleur | STM32F401CCU6 — 84 MHz Cortex-M4 |
| Moteurs | DC coreless 3.7 V, 85×20 mm |
| Hélices | 65 mm (2× CW + 2× CCW) |
| Batterie | LiPo 1S 3.7 V / 600 mAh / 30C |
| Poids cible | < 250 g |
| Autonomie théorique | 13.8 min (8–10 min estimés en vol réel) |

---

## ⚙️ Contraintes techniques relevées

- **Routage monocouche** imposé par la plastronique IME (pas de plan de masse)
- Correction de **5 court-circuits GND/+3V3** non détectés par l'ERC standard
- Intégration de composants absents de KiCad (BlueNRG-M0A, LSM6DSR via SnapMagic)
- Conception du moule en 2 itérations pour résoudre les problèmes de démoulage
- Dimensionnement chiffré : pont diviseur VBAT, PWM 50 Hz, fréquence SPI

---

## 📂 Contenu du dépôt

- `/pcb` — schéma et routage KiCad (Gerber)
- `/firmware` — code source C (STM32CubeIDE)
- `/cao` — fichiers 3D du châssis et du moule (STL, STEP)
- `/docs` — rapport final, cahier des charges, présentation
- `/photos` — captures du schéma, du châssis 3D et du circuit de test

---

## 📄 Documentation

- 📘 [Rapport final du projet](docs/Rapport_Drone_FCU_Plastronique.pdf)
- 📋 [Cahier des charges](docs/Cahier_des_charges.pdf)
- 🎤 [Présentation de soutenance](docs/Presentation_soutenance.pdf)

---

## 🧰 Technologies utilisées

`STM32F401` `ARM Cortex-M4` `KiCad` `STM32CubeIDE` `C embarqué` `SPI` `PWM` `ADC`
`LSM6DSR` `BlueNRG-M0A` `Bluetooth LE` `PID` `Plastronique 3D` `IME` `Autodesk Fusion 360` `Impression 3D`

---

## 👥 Équipe et contributions

Projet réalisé en équipe de 5 personnes, avec répartition des rôles :

- **Schéma / PCB KiCad** — conception et routage de la carte de vol
- **Firmware STM32** — drivers et intégration des périphériques
- **BLE + App mobile** — intégration BlueNRG et communication GATT
- **Stabilisation PID** — réglage des gains sur 3 axes
- **Mécanique 3D** — conception du moule et du châssis

**Mes contributions (Koussaila SEBA) :** conception et routage du schéma KiCad
(responsable principal), participation au firmware C (init horloges, drivers SPI IMU
et PWM moteurs), contribution à l'intégration BLE, et coordination de l'équipe.

---

## 📊 Statut du projet

✅ **Conception électronique complète et validée** (schéma KiCad — 0 erreur ERC)
✅ **Châssis 3D modélisé et imprimé**
✅ **Firmware adapté et documenté**
🔄 **Tests de vol et réglage PID — prévus en phase suivante (V2)**

---

## 👤 Auteur

**Koussaila SEBA** — Licence 3 EEA, Université Claude Bernard Lyon 1

- 📧 seba.koussaila.1@gmail.com
- 💼 [LinkedIn](https://linkedin.com/in/koussaila-seba)
- 🐙 [Profil GitHub](https://github.com/koussaila-seba)
