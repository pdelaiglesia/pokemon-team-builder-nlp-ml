# Pokemon Team Builder using NLP and Machine Learning

Este proyecto construye equipos de Pokémon optimizados para un tipo específico utilizando datos de Wikidex, PokeAPI, procesamiento de texto con spaCy y clasificación mediante KNN. El sistema analiza estadísticas base, movimientos, sinergias de tipos y descripciones textuales para seleccionar Pokémon adecuados tanto ofensiva como defensivamente.

## Objetivo del proyecto

Desarrollar un generador automático de equipos Pokémon que:
- Reúna Pokémon de un tipo específico desde Wikidex.
- Extraiga estadísticas y movimientos desde PokeAPI.
- Clasifique movimientos como ofensivos o defensivos usando técnicas de NLP.
- Construya equipos defensivos y ofensivos.
- Combine ambos equipos maximizando sinergias de tipo.

## Componentes principales

### 1. Obtención de Pokémon por tipo y generación
Se utiliza web scraping con `BeautifulSoup` para extraer Pokémon desde Wikidex por generación y tipo.

### 2. Extracción de estadísticas desde PokeAPI
Funciones que consultan:
- Defensa
- HP
- Ataque
- Ataque especial

### 3. Construcción de equipos
Se generan dos equipos:
- Equipo defensivo basado en defensa, hp y ataque.
- Equipo ofensivo basado en ataque especial y potencia de movimientos.

### 4. Procesamiento de lenguaje natural
Se usa spaCy para:
- Tokenizar descripciones de movimientos.
- Obtener lemas.
- Construir vocabulario.
- Vectorizar textos.

### 5. Clasificador KNN
A partir de movimientos vectorizados:
- Se entrena un modelo KNN para categorizar movimientos como ofensivos o defensivos.
- Se clasifica cada movimiento del equipo final.

### 6. Cálculo de sinergias
Los equipos ofensivo y defensivo se combinan:
- Se buscan Pokémon con el mayor número de tipos.
- Se genera un equipo final con sinergia óptima.

## Archivos externos utilizados

power_moves_bug.csv
pokemon_moves.csv
defense_team_bug.csv
offensive_team_bug.csv
Final_team_BUG.csv

Se emplean como respaldo cuando la API sufre sobrecarga.

## Requisitos

Instalar dependencias:


pip install requests pandas bs4 spacy scikit-learn
python -m spacy download en_core_web_sm

## Ejecución

El archivo principal ejecuta:


main(searched_type, power_type, url_moves, url_power, nlp)


Parámetros:
- `searched_type`: tipo en español (para Wikidex)
- `power_type`: tipo en inglés (para PokeAPI)
- `url_moves`: CSV con movimientos preprocesados
- `url_power`: CSV con movimientos del tipo base
- `nlp`: modelo spaCy cargado

Ejemplo:

team = main("Tipo Bicho", "bug", url_moves, url_power, nlp_en)
team

## Resultados

El programa devuelve:
- Equipo defensivo con estadísticas
- Equipo ofensivo con estadísticas
- Equipo final con:
  - Nombre del Pokémon
  - Tipos
  - Cuatro mejores movimientos
  - Clase original del movimiento
  - Clase predicha por el modelo KNN

## Estructura del proyecto

- `main.py` — código principal
- `pokemon_moves.csv` — movimientos y descripciones
- `power_moves_bug.csv` — movimientos del tipo especificado
- CSV opcionales para manejo de errores
- `README.md` — documentación del proyecto

## Autoría

- Pablo de la Iglesia Otero

