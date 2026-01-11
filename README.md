# Calculatrice-Graphique
# Expressions Manager v2.0

![Java](https://img.shields.io/badge/Java-17%2B-orange)
![JavaFX](https://img.shields.io/badge/JavaFX-20-blue)
![License](https://img.shields.io/badge/License-MIT-green)

**Expressions Manager** est une application JavaFX conçue pour parser, visualiser et évaluer des expressions mathématiques. Basée sur une architecture stricte Modèle-Vue-Contrôleur (MVC), elle permet de manipuler des arbres arithmétiques, de gérer des variables partagées et de filtrer dynamiquement les données.


## ✨ Fonctionnalités Clés

* **Parsing Avancé :** Analyse de chaînes arithmétiques (ex: `a + b * 3`) pour construire des arbres d'expressions orientés objet.
* **Gestion des Variables :** Support des variables partagées. Une variable définie dans une expression (ex: `a=2`) est accessible et partagée par toutes les autres expressions du modèle.
* **Structure Visuelle :** Visualisation hiérarchique des opérations via un `TreeView` dynamique.
* **Évaluation Temps Réel :**
    * Support des types numériques : `Integer`, `Float` et `Double`.
    * Réévaluation automatique des calculs lorsque la valeur d'une variable est modifiée.
* **Filtrage et Recherche :** Possibilité de filtrer les expressions par texte, par type d'opérateur (ex: additions, affectations) ou par type d'opérande.
* **Persistance :** Sauvegarde et chargement des expressions depuis des fichiers texte.
* **Interface Personnalisable :** Configuration de l'affichage (boutons texte/icône) et du niveau de logs via les préférences.

## 🏗 Architecture

Ce projet respecte le patron de conception **MVC (Modèle-Vue-Contrôleur)** :

### 1. Le Modèle (Package `expressions`)
Le cœur logique repose sur une hiérarchie générique d'expressions (`Expression<E>`) :
* **Expressions Terminales :** Constantes et Variables.
* **Expressions Binaires :** Addition, Soustraction, Multiplication, Division, Puissance et Affectation.
* **Parser :** Un analyseur syntaxique (recursive descent parser) qui convertit le texte en objets.
* **Observables :** Utilisation intensive des `ObservableList` et `ObjectProperty` de JavaFX pour la réactivité de l'interface.

### 2. La Vue (Package `application`)
* **FXML :** L'interface utilisateur est définie dans le fichier `ExpressionsFrame.fxml`.
* **Composants :** Utilisation de `TreeView` pour la structure et `TableView` pour l'affichage tabulaire des données.

### 3. Le Contrôleur
* Fait le lien entre la vue et le modèle.
* Gère les événements utilisateur (boutons, menus) et la logique de mise à jour de l'interface (bindings).

## 🚀 Installation et Démarrage

### Prérequis
* **Java JDK 17** ou supérieur.
* **JavaFX SDK** (Version 20 ou compatible avec votre JDK).

### Installation

1.  **Cloner le dépôt :**
    ```bash
    git clone [https://github.com/votre-username/expressions-manager-javafx.git](https://github.com/votre-username/expressions-manager-javafx.git)
    cd expressions-manager-javafx
    ```

2.  **Configurer JavaFX :**
    Téléchargez le SDK JavaFX depuis [GluonHQ](https://gluonhq.com/products/javafx/). Décompressez l'archive sur votre machine.

### Lancer l'application

JavaFX ne faisant plus partie du JDK standard, il est nécessaire de spécifier le chemin des modules au lancement.

**En ligne de commande :**
```bash
java --module-path /chemin/vers/javafx-sdk/lib --add-modules javafx.controls,javafx.fxml -jar ExpressionsManager.jar
