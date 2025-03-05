# NanoProcessor-MIPS4 - Processeur MIPS 4 bits - Implémentation sous Logisim  

## Table des Matières  

1. [Présentation du projet](#présentation-du-projet)  
2. [Caractéristiques techniques](#caractéristiques-techniques)  
3. [Installation et Utilisation](#installation-et-utilisation)  
   - [Prérequis](#prérequis)  
   - [Ouverture du projet](#ouverture-du-projet)  
   - [Simulation](#simulation)  
4. [Architecture du Processeur](#architecture-du-processeur)  
5. [Jeu d'instructions](#jeu-dinstructions)  
6. [Références](#références)  

---

## Présentation du projet  

Ce projet consiste en la conception et l’implémentation d’un **processeur MIPS 4 bits** en utilisant **Logisim**.  
L'objectif principal est de simuler l'exécution d'instructions de base, en respectant l’architecture MIPS simplifiée.  

Ce processeur est capable d’exécuter des opérations arithmétiques et logiques, de gérer la mémoire et d'effectuer des branchements conditionnels.  

![nano-mips](https://github.com/user-attachments/assets/fff03f9f-3c7c-465c-af09-26b9f55f9edc)

---

## Caractéristiques techniques  

- **Architecture** : Processeur **MIPS 4 bits**  
- **Logiciel utilisé** : [Logisim](https://sourceforge.net/projects/circuit/)  
- **Composants principaux** :
  - **UCC (Unité de Contrôle et de Commande)** : Génère les signaux de contrôle pour les différentes unités.  
  - **PC (Program Counter)** : Registre contenant l'adresse de l'instruction en cours.  
  - **PGM ROM (Mémoire Programme)** : Stocke le programme sous forme de code machine.  
  - **IR (Instruction Register)** : Contient l’instruction en cours d’exécution.  
  - **RF (Registre de Fichiers)** : Stocke les registres généraux du processeur.  
  - **ALU (Unité Arithmétique et Logique)** : Exécute les opérations arithmétiques et logiques.  
  - **SR (Status Register)** : Stocke les indicateurs de statut (zéro, négatif, etc.).  
  - **AR (Address Register)** : Utilisé pour l'accès à la mémoire.  
  - **DR (Data Register)** : Contient les données lues ou écrites en mémoire.  
  - **DATA RAM** : Mémoire RAM de **16B**, utilisée pour stocker les données temporaires.  

---

## Installation et Utilisation  

### Prérequis  
Avant d’exécuter la simulation, assurez-vous d’avoir :  
- **Logisim** installé ([Téléchargement ici](https://sourceforge.net/projects/circuit/))  
- **Le fichier du projet Logisim** (`nano-mips.circ`)  

### Ouverture du projet  
1. Lancez **Logisim**.  
2. Cliquez sur **File > Open** et sélectionnez `nano-mips.circ`.  

### Simulation  
1. Activez le **signal d'horloge** (`clk`) pour exécuter les instructions.  
2. Observez l’évolution des registres et des mémoires après chaque cycle d'horloge.  
3. Modifiez le contenu de la mémoire programme (`PGM ROM`) pour tester différentes instructions.  

---

## Architecture du Processeur  

Le processeur suit une **architecture classique en cinq étapes** :  
1. **Fetch** : Récupération de l'instruction depuis la mémoire programme (`PGM ROM`).  
2. **Decode** : Décodage de l'instruction dans le registre d’instruction (`IR`).  
3. **Execute** : Exécution de l'instruction via l'**ALU** ou une autre unité.  
4. **Memory** : Accès à la mémoire RAM (`DATA RAM`) si nécessaire.  
5. **Write Back** : Écriture du résultat dans un registre (`RF`).  

L'**UCC (Unité de Contrôle et de Commande)** génère les signaux de contrôle pour coordonner ces étapes.  

---

## Jeu d'instructions  

Le processeur exécute un ensemble d’instructions simplifié basé sur **MIPS**.  

| Opcode | Instruction | Description |
|--------|------------|-------------|
| 0000   | `ADD` Rd, Rs, Rt | Addition entre deux registres |
| 0001   | `SUB` Rd, Rs, Rt | Soustraction entre deux registres |
| 0010   | `AND` Rd, Rs, Rt | Opération logique AND |
| 0011   | `OR` Rd, Rs, Rt | Opération logique OR |
| 0100   | `XOR` Rd, Rs, Rt | Opération logique XOR |
| 0101   | `LD` Rd, [Addr] | Chargement depuis la mémoire |
| 0110   | `ST` Rs, [Addr] | Stockage en mémoire |
| 0111   | `BEQ` Rs, Rt, Offset | Branchement si égalité |
| 1000   | `JMP` Addr | Saut inconditionnel |

---

## Fichiers de Test et Signaux de Contrôle  

Le projet comprend les fichiers suivants :

- **test.rom** : Fichier binaire contenant les instructions à charger dans la mémoire.
- **test.txt** : Fichier texte décrivant les instructions à tester.
- **control-signals.rom** : Fichier binaire contenant les signaux de contrôle associés aux instructions.
- **control-signals.txt** : Fichier texte définissant les signaux de contrôle nécessaires à l'exécution des instructions.

Ces fichiers sont utilisés pour charger les instructions et configurer les signaux de contrôle, nécessaires au bon fonctionnement de la simulation.

---

## Références  

- **Documentation Logisim** : [https://www.cburch.com/logisim/](https://www.cburch.com/logisim/)  
- **My professor MIPS Walkthrough - 1** : [https://www.el-kalam.com/tutoriels/tutoriel-de-construction-dun-processeur/)
- **My professor MIPS Walkthrough - 2** : [https://www.el-kalam.com/cours/conception-hardware/architecture-mips/)  
