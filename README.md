# 🚆 Verspätungsprognose Deutsche Bahn AG
### Fallstudie – Modul Artificial Intelligence | Hochschule Reutlingen

---

## Projektbeschreibung

Diese Fallstudie untersucht, ob die Ankunftsverspätung eines Zuges der Deutschen Bahn (in Minuten) anhand von Merkmalen wie Zugkategorie, Bahnhof, geografischer Lage, Uhrzeit und Wochentag mittels Machine-Learning-Verfahren vorhergesagt werden kann.

**ML-Typ:** Supervised Learning – Regression  
**Bestes Modell:** Random Forest Regressor (MAE: 1,61 Min | R²: 0,073)  
**Datensatz:** Deutsche Bahn (DB) Delays – Kaggle ([nokkyu/deutsche-bahn-db-delays](https://www.kaggle.com/datasets/nokkyu/deutsche-bahn-db-delays))

---

## Inhalt des Repositories

| Datei | Beschreibung |
|---|---|
| `DB_Verspaetung_Regression.ipynb` | Jupyter Notebook mit vollständigem Code |
| `Hausarbeit_DB_Verspaetungsprognose.docx` | Schriftliche Hausarbeit (alle 9 Pflichtpunkte) |
| `db_delays_sample.zip` | Datensatz (12%-Stichprobe, 247.363 Zeilen) |
| `db_delay_model.pkl` | Gespeichertes Random-Forest-Modell |
| `db_model_features.pkl` | Feature-Namen des Modells |
| `db_station_avg_delay.pkl` | Historische Bahnhofs-Durchschnittswerte |

---

## Methodik

- **Datengrundlage:** 2.061.357 Zugfahrten (Juli 2024), 12%-Stichprobe mit fixiertem Seed
- **Feature Engineering:** Zyklische Zeitkodierung (Sinus/Kosinus), Lag-Feature `station_avg_delay` (Data-Leakage-frei), Rushhour-Indikator
- **Modelle:** Lineare Regression (Baseline), Decision Tree, Random Forest
- **Hyperparameter-Tuning:** GridSearchCV auf 10%-Stichprobe der Trainingsdaten
- **Evaluation:** MAE, RMSE, R² + empirischer Filteransatz-Test

## Ergebnisse

| Modell | MAE (Min.) | RMSE (Min.) | R² |
|---|---|---|---|
| Lineare Regression | 1,63 | 3,55 | 0,060 |
| Decision Tree | 1,62 | 3,56 | 0,053 |
| **Random Forest** | **1,61** | **3,53** | **0,073** |

Das Modell liegt in **80% aller Fälle innerhalb von ±2 Minuten** zur echten Verspätung.

---

## Voraussetzungen

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

Das Notebook läuft lokal in **Jupyter Notebook via Anaconda**.

---

## Ausführung

1. `db_delays_sample.zip` entpacken → `db_delays_sample.csv` im gleichen Ordner ablegen
2. `DB_Verspaetung_Regression.ipynb` in Jupyter öffnen
3. Alle Zellen von oben nach unten ausführen (`Shift + Enter`)

---

## Autor

**Haben Welday** | Matrikelnummer: 820906  
Hochschule Reutlingen | Modul: Artificial Intelligence  
Abgabe: 28.06.2026 | Mündliche Prüfung: 03.07.2026
