# Agrégateur Météo — Mini-Projet Fullstack

Application web Django qui permet de consulter la météo d'une ville en temps réel via l'API OpenWeatherMap.

## Fonctionnalités

- Recherche météo par nom de ville
- Affichage de la température, de l'humidité et de la description météo
- Message d'erreur si la ville est introuvable
- Historique des recherches en base de données (SQLite)
- Cache : si la même ville a été recherchée il y a moins de 15 minutes, les données sont récupérées depuis la base sans rappeler l'API

## Installation

### 1. Cloner le projet

```bash
git clone <url-du-repo>
cd meteo_app
```

### 2. Créer un environnement virtuel et installer les dépendances

```bash
python -m venv venv
source venv/bin/activate        # Linux/Mac
venv\Scripts\activate           # Windows

pip install -r requirements.txt
```

### 3. Configurer la clé API



Ouvrir `.env` et mettre  votre clé obtenue sur [openweathermap.org](https://openweathermap.org/api).

```
OPENWEATHER_API_KEY=votre_cle_ici
```

> ⚠️ Ne jamais committer le fichier `.env`. Il est déjà dans `.gitignore`.

### 4. Initialiser la base de données

```bash
python manage.py migrate
```

### 5. Lancer le serveur

```bash
python manage.py runserver
```

Ouvrir [http://127.0.0.1:8000](http://127.0.0.1:8000) dans le navigateur.

## Structure du projet

```
meteo_app/
├── weather_project/        # Configuration Django
│   ├── settings.py
│   └── urls.py
├── weather/                # Application principale
│   ├── models.py           # Modèle WeatherSearch (historique)
│   ├── views.py            # Vue principale + appel API + cache
│   ├── urls.py
│   └── templates/
│       └── weather/
│           └── index.html  # Interface utilisateur
├── .env.example
├── .gitignore
├── manage.py
└── requirements.txt
```
