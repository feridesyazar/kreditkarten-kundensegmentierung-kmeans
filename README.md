# 💳 Kreditkarten-Kundensegmentierung mit K-Means

## Projektüberblick

Wie lassen sich Kreditkartenkunden anhand ihrer Nutzung und ihres Zahlungsverhaltens in sinnvolle Gruppen einteilen?

In diesem Data-Science-Projekt werden **8.950 Kreditkartenkunden** mithilfe von **K-Means-Clustering** segmentiert. Ziel ist es, Gemeinsamkeiten und Unterschiede beim Einkaufen, bei Bargeldvorschüssen und bei Zahlungen sichtbar zu machen.

- **Lernverfahren:** Unsupervised Learning (Clustering)
- **Datensatz:** `CC GENERAL.csv` mit 8.950 Zeilen und 18 Spalten
- **Modell:** K-Means mit sieben ausgewählten Merkmalen
- **Programmiersprache:** Python (Jupyter Notebook)

## Daten und Merkmale

Für das Clustering nutzen wir sieben Merkmale:

| Merkmal | Bedeutung |
|---|---|
| `BALANCE` | Kreditkartensaldo |
| `PURCHASES` | Gesamtsumme der Einkäufe |
| `CASH_ADVANCE` | Gesamtsumme der Bargeldvorschüsse |
| `CREDIT_LIMIT` | Kreditlimit |
| `PAYMENTS` | Gesamtsumme der Zahlungen |
| `PURCHASES_FREQUENCY` | Einkaufshäufigkeit |
| `PRC_FULL_PAYMENT` | Anteil vollständiger Zahlungen |

Eine Beschreibung aller 18 Spalten befindet sich im **Data Dictionary** des Notebooks.

## Vorgehensweise

1. **Daten einlesen und untersuchen (EDA):** Datentypen, fehlende Werte, Duplikate und Verteilungen prüfen
2. **Daten vorbereiten:** Ausgewählte Merkmale verwenden und fehlende Werte darin durch den jeweiligen Median ersetzen
3. **Daten transformieren:** Geldbeträge mit `log1p` transformieren und die Merkmale mit `StandardScaler` skalieren
4. **Clusterzahl bewerten:** Für K = 2 bis 7 die Elbow-Methode und den Silhouette Score vergleichen
5. **Modell trainieren:** K-Means auf die vorbereiteten Daten anwenden
6. **Kundengruppen analysieren:** Medianwerte, Gruppengrößen, Heatmap und Streudiagramm auswerten; zusätzlich PCA zur Visualisierung
7. **Ergebnisse exportieren:** Kundenkennung und Clusterzuordnung in `credit_card_segments.csv` speichern

## Ergebnisse

Im dokumentierten Notebook-Durchlauf wurden **fünf Cluster** gebildet. Der **Silhouette Score beträgt ca. 0,292**, berechnet auf einer festen Stichprobe von 1.200 Kunden. Die Gruppen verteilen sich wie folgt:

| Cluster | Kunden | Anteil | Beschreibung |
|---|---:|---:|---|
| 0 | 1.732 | 19,4 % | Hohe Kartensalden und Bargeldvorschüsse, mittlere Einkaufsbeträge |
| 1 | 1.330 | 14,9 % | Niedrige Kartensalden und geringe Einkaufsaktivität |
| 2 | 1.297 | 14,5 % | Häufige Einkäufe und oft vollständige Zahlungen |
| 3 | 2.394 | 26,7 % | Regelmäßige Einkäufe, mittlere Kartensalden und wenig Bargeldvorschüsse |
| 4 | 2.197 | 24,5 % | Hohe Bargeldvorschüsse und sehr geringe Einkaufsaktivität |

**Einordnung:** Die Cluster sind interpretierbar, aber nicht besonders deutlich voneinander getrennt. Da K = 4 nahezu denselben Silhouette Score erreicht, ist K = 5 keine eindeutig optimale Lösung. Die Clusternummern stellen keine Rangfolge dar.


## Grenzen des Projekts

Dieses Projekt zeigt eine explorative Kundensegmentierung anhand eines Beispieldatensatzes und ausgewählter Merkmale. Der Silhouette Score beschreibt die Trennung der Cluster, **nicht** die Vorhersagegenauigkeit. Die Segmente sollten vor einer geschäftlichen Anwendung fachlich und mit weiteren Daten validiert werden. Aus ihnen lässt sich **keine zuverlässige individuelle Kreditwürdigkeit** ableiten.

## Quellen

- [Credit Card Dataset for Clustering – Kaggle](https://www.kaggle.com/datasets/arjunbhasin2013/ccdata)
- [scikit-learn: KMeans](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html)
- [scikit-learn: Silhouette Score](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.silhouette_score.html)

