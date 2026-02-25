# 🌱 Autonomous AI Crop Guardian (AACG)

## 📌 Description du projet
**Autonomous AI Crop Guardian (AACG)** est un système embarqué intelligent destiné à l’agriculture de précision.  
Il permet de **surveiller l’état de santé des plantes**, **prédire leurs besoins**, **détecter des maladies via l’IA**, et **agir automatiquement** (irrigation, alertes), tout en minimisant la consommation d’eau et de ressources.

Le projet combine **IoT, intelligence artificielle et systèmes embarqués** autour d’un microcontrôleur **ESP32**.

## 🎯 Objectifs principaux
- Surveillance continue de l’environnement des plantes (sol et air)
- Prédiction intelligente des besoins en irrigation
- Détection des maladies végétales par IA
- Automatisation de l’arrosage
- Visualisation simple et claire des données
- Solution autonome, fiable et économe en énergie

## 🧱 Architecture générale
```

Capteurs → ESP32 → Traitement & IA → Actions (pompe, alertes) → Interface utilisateur

```

---

## 🔧 Technologies utilisées

### Matériel
- ESP32
- Capteur d’humidité & température du sol
- Capteur température & humidité (DHT22)
- Capteur de luminosité
- capteur detection maladie (camera )
- Alimentation (batterie ou secteur)


## 🧠 Intelligence Artificielle
- Modèle de prédiction des besoins en eau
- Classification des maladies des plantes
- Apprentissage basé sur des données réelles
- Objectif de précision ≥ **90 %**


 🧠 Principe d’architecture recommandé
```
main (setup / loop)
│
├── Acquisition capteurs
├── Traitement & logique métier
├── IA / décision
├── Actionneurs (pompe)
├── Communication
└── Supervision système
```


📁 Structure complète du projet (recommandée)
```
AACG/
│
├── firmware/
│   ├── src/
│   │   ├── main.cpp       
│   │   │
│   │   ├── sensors/
│   │   │   ├── air_sensor.h
│   │   │   ├── air_sensor.cpp
│   │   │   ├── soil_sensor.h
│   │   │   ├── soil_sensor.cpp
│   │   │   ├── light_sensor.h
│   │   │   ├── camera_sensor.h
│   │   │
│   │   ├── actuators/
│   │   │   ├── pump.h
│   │   │   └── pump.cpp
│   │   │
│   │   ├── ai/
│   │   │   ├── ai_model.h
│   │   │   └── ai_model.cpp
│   │   │
│   │   ├── communication/
│   │   │   ├── wifi_manager.h
│   │   │   ├── mqtt_client.h
│   │   │
│   │   ├── system/
│   │   │   ├── power_manager.h
│   │   │   ├── scheduler.h
│   │   │   └── logger.h
│   │   │
│   │   └── config/
│   │       └── config.h
│   │
│   └── platformio.ini / arduino.json
│
├── ai/
│   ├── training/
│   ├── dataset/
│   └── inference/
│
├── dashboard/
│
├── docs/

```
## 🧩 Rôle de chaque partie

### 🔹 `main.cpp` (ORCHESTRATEUR)

* Initialise le système
* Appelle les fonctions des modules
* Ne contient **aucune logique détaillée**



 Modules capteurs (`sensors/`)

Chaque capteur = **1 module indépendant**

Responsabilités :

* Initialisation
* Lecture brute
* Conversion
* Pré-traitement


🔹 Module IA (`ai/`)

Responsabilités :

* Charger le modèle
* Faire la prédiction
* Retourner un **résultat abstrait**


🔹 Module actionneurs (`actuators/`)

Responsabilités :

* Commander la pompe
* Sécuriser l’activation
* Appliquer les décisions



🔹 Communication (`communication/`)

Responsabilités :

* Wi-Fi
* Envoi données
* Réception commandes distantes

🔹 Supervision système (`system/`)

