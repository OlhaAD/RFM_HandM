# RFM-Analyse der Kundenbasis von H&M

## Einführung
In der modernen, kundenorientierten Marktumgebung wird die Analyse des Kundenverhaltens für den Erfolg von Einzelhandelsunternehmen immer entscheidender. Dies gilt insbesondere für große Einzelhändler wie H&M, bei denen die Kundenbindung und -loyalität direkt die wirtschaftlichen Kennzahlen des Unternehmens beeinflussen. Dieses Projekt widmet sich der Analyse von RFM (Recency, Frequency, Monetary), die es ermöglicht, die aktuelle Marktposition des Unternehmens zu bewerten und die wertvollsten Kunden für das Geschäft zu identifizieren.
## Wie man das Projekt startet
- Klone das Repository auf deinen lokalen Computer:
```sh
git clone https://github.com/your-username/your-repository.git
```
- Daten für die Analyse:
Die Daten sind zu groß, um sie auf GitHub zu speichern. Im Projekt werden direkte Links zu 3 Dateien auf meinem Google Drive verwendet: articles, customers und transactions.

- Öffne die Notebooks:
Öffne die Notebooks im Ordner /notebooks über Google Colab oder Jupyter Notebook, um den Code anzusehen und auszuführen.

- Installiere die erforderlichen Abhängigkeiten:
Installiere die erforderlichen Abhängigkeiten mit dem folgenden Befehl:
```sh
pip install -r requirements.txt
```
(Es wird angenommen, dass du eine Datei requirements.txt erstellt hast, die alle notwendigen Bibliotheken auflistet).

**Beispielcode für den Zugriff auf Daten auf Google Drive in Google Colab**
```python
from pydrive.auth import GoogleAuth
from pydrive.drive import GoogleDrive
from google.colab import auth
from oauth2client.client import GoogleCredentials
import pandas as pd

# Authentifizierung und Autorisierung
auth.authenticate_user()
gauth = GoogleAuth()
gauth.credentials = GoogleCredentials.get_application_default()
drive = GoogleDrive(gauth)

# Herunterladen von Dateien von Google Drive
file_ids = {
    'articles': '1H-g4oAbw1ZjYDOncx3xU3oro3tH3UIg6',
    'customers': '1KLM7Vum2O35MR17ULRLneM0uGVX61-VR',
    'transactions': '18ESMoz4VDe_ZCZzRPKKZS-UargXvrRdi'
}

for name, file_id in file_ids.items():
    downloaded = drive.CreateFile({'id': file_id})
    downloaded.GetContentFile(f'{name}.csv')
    print(f'{name}.csv downloaded')

# Lesen der Daten in DataFrames
df_articles = pd.read_csv('articles.csv')
df_customers = pd.read_csv('customers.csv')
df_transactions = pd.read_csv('transactions.csv')

# Anzeige der ersten Zeilen jedes DataFrames
print(df_articles.head())
print(df_customers.head())
print(df_transactions.head())
```
## Ziele und Aufgaben
### Ziele
Das Hauptziel dieses Projekts ist die Entwicklung einer Kundensegmentierungsmethode basierend auf der RFM-Analyse, um die Marketingstrategien von H&M zu optimieren. Dies umfasst:
- Identifikation und Analyse verschiedener Kunden-Segmente.
- Bewertung der Effektivität der aktuellen Marketing- und Vertriebsstrategien.
- Erhöhung des Engagements und der Kundenbindung.
### Aufgaben
Im Rahmen dieses Projekts konzentrieren wir uns auf folgende Schlüsselaufgaben:

- **Implementierung der RFM-Analyse:** Entwicklung und Einführung eines Algorithmus zur Berechnung der Recency, Frequency und Monetary-Werte für jeden Kunden. Dieser Algorithmus wird helfen, die wertvollsten Kunden zu identifizieren und die Dynamik ihrer Käufe zu verstehen.

- **Kundensegmentierung:** Basierend auf den RFM-Werten werden die Kunden in verschiedene Gruppen klassifiziert. Dies ermöglicht die Entwicklung zielgerichteter Marketingstrategien, die auf die Bedürfnisse und das Verhalten jeder Gruppe abgestimmt sind.

- **Analyse der Ergebnisse und Formulierung von Empfehlungen:** Bewertung der Wirksamkeit der Segmentierung und Analyse des Verhaltens verschiedener Kundengruppen. Auf Basis dieser Daten werden Vorschläge zur Verbesserung der Marketing- und Kommunikationsstrategien formuliert, um das Engagement und die Loyalität der Kunden zu erhöhen.

## Detaillierte Methodik
### Werkzeuge und Bibliotheken
In diesem Projekt wurden die folgenden Werkzeuge und Bibliotheken verwendet:

- **Python:** Die Hauptprogrammiersprache für Datenanalyse und Modellierung.

- **Pandas:** Bibliothek zur Datenverarbeitung und -analyse. Verwendet für die Arbeit mit DataFrames.

- **NumPy:** Bibliothek zur Arbeit mit Arrays und zur Durchführung numerischer Berechnungen.

- **Seaborn:** Auf matplotlib basierende Bibliothek zur Datenvisualisierung. Verwendet zur Erstellung statistischer Diagramme.

- **Matplotlib:** Die Hauptbibliothek zur Erstellung von Diagrammen und zur Datenvisualisierung.

- **Squarify:** Eine Bibliothek zur Erstellung von Treemap-Diagrammen.

- **textwrap:** Eine Bibliothek zum Umbruch von Textzeilen, damit der Text in die angegebenen Grenzen passt.

- **Plotly:** Eine Bibliothek für interaktive Datenvisualisierung.

### Datensammlung und Vorverarbeitung
**Datenquelle:**
Die Daten für dieses Projekt stammen von https://www.kaggle.com/competitions/h-and-m-personalized-fashion-recommendations/data

**Datenbankstruktur:**
Die Datenbank ist in drei Dateien unterteilt: ArticlesHM, CustomersHM und TransactionsHM.

**ArticlesHM** ist eine Tabelle, die alle Artikel von H&M enthält, mit insgesamt **105 542 Zeilen** und den folgenden Spalten:
- **article_id:** Artikel-ID, Datentyp - int64
- **prod_name:** Artikelname, Datentyp - object
- **product_type_name:** Produkttypname, Datentyp - object
- **product_group_name:** Produktgruppenname, Datentyp - object
- **graphical_appearance_name:** Name des grafischen Erscheinungsbildes, Datentyp - object
- **colour_group_name:** Farbgruppenname, Datentyp - object
- **index_name:** Name des Unterabschnitts, Datentyp - object
- **index_group_name:** Name des Abschnitts, Datentyp - object
- **section_name:** Sektionsname, Datentyp - object
- **garment_group_name:** Kategorie, Datentyp - object
- **detail_desc:** Details, Datentyp - object

**CustomersHM** ist eine Tabelle, die Informationen über H&M-Kunden enthält, mit insgesamt **1 371 979 Zeilen** und den folgenden Spalten:
- **customer_id:** Kunden-ID, Datentyp - object
- **Active:** Aktivitätsstatus, Datentyp - float64
- **club_member_status:** Clubmitgliedsstatus, Datentyp - object
- **fashion_news_frequency:** Häufigkeit der Modenachrichten, Datentyp - object
- **age:** Alter des Kunden, Datentyp - float64
- **postal_code:** Postleitzahl, Datentyp - object

**TransactionsHM** ist eine Tabelle, die Informationen über H&M-Verkäufe enthält, mit insgesamt **31 788 323 Zeilen** und den folgenden Spalten:
- **t_dat:** Verkaufsdatum, Datentyp - object
- **customer_id:** Kunden-ID, Datentyp - object
- **article_id:** Artikel-ID, Datentyp - int64
- **price:** Preis, Datentyp - float64
- **sales_channel_id:** Vertriebskanal, Datentyp - int64
Diese Dateien wurden zuvor von Fehlern und Auslassungen bereinigt und außerdem für die Analyse im vorherigen Projekt aggregiert. In diesem Projekt liegt der Schwerpunkt auf der Entwicklung und Implementierung der RFM-Analyse.
### Implementierung der RFM-Analyse
Die RFM-Analyse ist ein Marketinginstrument, das zur Segmentierung von Kunden und zur Bestimmung von Kundengruppen basierend auf ihrer bisherigen Kaufaktivität verwendet wird. Diese Analysemethode basiert auf drei Hauptparametern, die den Namen RFM geben:
- **Recency (Aktualität)** – wie kürzlich ein Kunde den letzten Kauf getätigt hat. Kunden, die kürzlich gekauft haben, sind wahrscheinlicher auf neue Angebote ansprechbar. Es ist wichtig zu verstehen, wie lange Kunden aktiv bleiben.
- **Frequency (Häufigkeit)** – wie oft ein Kunde innerhalb eines bestimmten Zeitraums kauft. Kunden, die häufiger einkaufen, sind wahrscheinlich loyaler und wertvoller für das Unternehmen.
- **Monetary (Monetärer Wert)** – die Gesamtsumme des Geldes, die ein Kunde ausgegeben hat. Dieser Parameter hilft zu bestimmen, welche Kunden den größten Umsatz generieren.

Der Einsatz der RFM-Analyse ermöglicht Unternehmen:
- Die Wahrscheinlichkeit von Antworten auf Marketingaktionen zu erhöhen, indem Angebote an die aussichtsreichsten Kunden gerichtet werden.
- Die Personalisierung von Angeboten zu verbessern, indem Angebote erstellt werden, die den spezifischen Bedürfnissen verschiedener Segmente entsprechen.
- Die allgemeine Effektivität von Marketinganstrengungen zu steigern, indem Ressourcen optimiert und auf die profitabelsten Kunden konzentriert werden.

#### Kundensegmentierung nach dem Zeitpunkt des letzten Kaufs
Im Rahmen der RFM-Analyse ist die Bewertung der Rezente des letzten Kaufs eines Kunden (Recency) einer der Schlüsselindikatoren. Hierfür wurden Daten zu Käufen vom 20. September 2018 bis zum 22. September 2020 verwendet. Für jeden Kunden wurde die Anzahl der Tage seit seinem letzten Kauf bis zum letzten Datum in den Daten (22.09.2020) berechnet.

```python
Frühestes Datum: 2018-09-20 00:00:00
Letztes Date: 2020-09-22 00:00:00
```

Die Daten wurden mittels eines Histogramms und eines Boxplots visualisiert, die die Verteilung der Tage seit dem letzten Kauf unter allen Kunden zeigen. Das Histogramm verdeutlicht, wie häufig Kunden für wiederholte Käufe zurückkehren, während der Boxplot Informationen über die Medianwerte und die Verteilung der Tage zwischen den Käufen bietet.

Das Histogramm zeigt, dass die meisten Käufe innerhalb der ersten 100 Tage nach dem vorherigen Kauf getätigt werden, danach nimmt die Anzahl der Käufe mit der Zeit ab. Der Boxplot zeigt, dass der Medianwert bei 151 Tagen liegt, was darauf hinweist, dass die Hälfte aller Kunden innerhalb von etwa fünf Monaten nach dem letzten Kauf wiederholt kauft.

![TageSeitLetztenKaufHistAndBoxPlot](https://github.com/OlhaAD/RFM_HandM/blob/main/visualisations/TageSeitLetztenKaufHistAndBoxPlot.png)

Basierend auf dem Histogramm der Verteilung der Tage seit dem letzten Kauf können die folgenden Gruppen für die Kundensegmentierung definiert werden:
- **Sehr aktive Kunden:** Kunden, die innerhalb der letzten 30 Tage oder weniger einen Kauf getätigt haben.
- **Aktive Kunden:** Kunden, die einen Kauf zwischen 31 und 100 Tagen getätigt haben.
- **Mäßig aktive Kunden:** Kunden, die einen Kauf zwischen 101 und 365 Tagen getätigt haben.
- **Langfristig inaktive Kunden:** Kunden, deren letzter Kauf mehr als ein Jahr zurückliegt.

```python
def recency_score(rec):
  if rec > 365:
    return 4
  elif (rec > 100) and (rec <= 365):
    return 3
  elif (rec > 30) and (rec <= 100):
    return 2
  else:
    return 1
df_rfm['recency']= df_rfm['days_since_last_purchase'].apply(recency_score)
```

**Visualisierung der Verteilung der Kunden nach Recency-Gruppen**

Der Graph zeigt, dass die meisten Kunden zur Gruppe 3 gehören, was darauf hinweist, dass ein erheblicher Teil der Kundenbasis im letzten Jahr Einkäufe getätigt hat. Es ist auch wichtig zu beachten, dass selbst in Gruppe 4, wo Kunden als langfristig inaktiv gelten, immer noch eine signifikante Anzahl von Kunden vorhanden ist, was auf das Potenzial hinweist, diese Kunden durch gezielte Marketingkampagnen wieder zu gewinnen.

![RecencyVerteilung](https://github.com/OlhaAD/RFM_HandM/blob/main/visualisations/RecencyGruppeHist.png)

#### Segmentierung der Kunden nach Kaufhäufigkeit
Die Analyse basiert auf Transaktionsdaten der letzten zwei Jahre. Das Histogramm und das Boxplot zeigen die Verteilung der Anzahl der Käufe pro Kunde.

![AnzahlVerkaufeProKundeHistAndBoxPlot](https://github.com/OlhaAD/RFM_HandM/blob/main/visualisations/AnzahlVerk%C3%A4ufeProKundeHistAndBoxPlot.png)

Basierend auf diesen Daten wurden die Kunden in vier Gruppen eingeteilt:
- **Sehr aktive Kunden:** Haben mehr als 27 Käufe im gesamten Zeitraum getätigt. Diese Gruppe nähert sich dem oberen Quantil und zeigt eine hohe Kaufhäufigkeit.
- **Aktive Kunden:** Haben zwischen 10 und 26 Käufen in zwei Jahren getätigt. Diese Gruppe liegt zwischen dem Median und dem oberen Quantil und zeigt eine mäßig hohe Aktivität.
- **Mäßig aktive Kunden:** Haben zwischen 4 und 9 Käufen getätigt. Der Bereich dieser Kunden liegt zwischen dem ersten Quantil und dem Median und spiegelt eine moderate Kauftätigkeit wider.
- **Weniger aktive Kunden:** Haben weniger als 3 Käufe getätigt. Diese Kunden liegen unter dem ersten Quantil und zeigen eine geringe Kaufhäufigkeit.

**Visualisierung der Kundenverteilung nach Kaufhäufigkeitsgruppen**
Dieses Diagramm zeigt die Verteilung der H&M-Kunden nach vier Gruppen der Kaufhäufigkeit im Rahmen der RFM-Analyse. Die Gruppen sind basierend auf der Anzahl der Käufe definiert, die die Kunden im analysierten Zeitraum getätigt haben:
- **Gruppe 1:** Kunden mit sehr hoher Kaufhäufigkeit.
- **Gruppe 2:** Kunden mit hoher Kaufhäufigkeit.
- **Gruppe 3:** Kunden mit mittlerer Kaufhäufigkeit.
- **Gruppe 4:** Kunden mit niedriger Kaufhäufigkeit.

Das Diagramm zeigt eine gleichmäßige Verteilung der Kunden über diese vier Gruppen, was die Vielfalt der Einkaufsaktivitäten in der Kundenbasis von H&M hervorhebt.

![FrequencyGruppeVerteilung](https://github.com/OlhaAD/RFM_HandM/blob/main/visualisations/FrequencyGruppeHist.png)

#### Segmentierung der Kunden nach Ausgabesumme
Die verwendeten Histogramme und Boxplots illustrieren die Verteilung der Gesamtausgaben der Kunden. Diese Visualisierungen ermöglichen es, deutlich zu sehen, wie die Ausgaben unter den verschiedenen Kundengruppen verteilt sind, und Haupttrends sowie Anomalien im Verbraucherverhalten zu identifizieren.

![AusgabesummePerKundeHistBoxPlot](https://github.com/OlhaAD/RFM_HandM/blob/main/visualisations/EinkaufssummeProKundeHistAndBoxPlot.png)

Auf Basis dieser Daten wurden die Kunden in die folgenden vier Gruppen eingeteilt:
- **Niedrige Ausgabensumme:** Kunden, deren Ausgaben unter dem ersten Quartil (Q1, weniger als 0.09) liegen. Diese Kunden geben deutlich weniger aus im Vergleich zu den anderen.
- **Mittlere Ausgabensumme:** Die Hauptgruppe der Kunden, deren Ausgaben zwischen dem ersten und dritten Quartil (Q1 und Q3) liegen, was einem Betrag von 0.1 bis 0.7 entspricht. Diese Kunden repräsentieren das standardmäßige Verbraucherverhalten.
- **Hohe Ausgabensumme:** Kunden, deren Ausgaben das dritte Quartil (Q3, 0.7) überschreiten, aber nicht den Bereich der Ausreißer erreichen, mit Ausgaben bis zu 1.5. Diese Kunden geben mehr als der Durchschnitt aus, und ihre Einkaufsaktivität könnte auf eine höhere Loyalität oder ein höheres Einkommen hinweisen.
- **Sehr hohe Ausgabensumme:** Kunden, deren Ausgaben die oberen "Whisker" des Boxplots überschreiten, was als Ausreißer angesehen wird (mehr als 1.5). Dies sind die wertvollsten Kunden, die deutlich mehr als alle anderen ausgeben. Ihr Kaufverhalten könnte mit besonderen Anlässen verbunden sein, wie zum Beispiel Käufe im Rahmen großer Events oder eine hohe persönliche Treue zur Marke.

**Visualisierung der Verteilung der Kunden nach Kaufsummen-Gruppen**

Das dargestellte Histogramm zeigt die Verteilung der H&M-Kunden nach vier Gruppen, die auf der Basis ihrer Kaufsummen im Rahmen der RFM-Analyse gebildet wurden. Die Gruppen sind wie folgt definiert:
- **Gruppe 1:** Kunden mit den höchsten Gesamtausgaben.
- **Gruppe 2:** Kunden mit erheblichen Ausgaben, aber weniger als in der ersten Gruppe.
- **Gruppe 3:** Kunden mit moderaten Ausgaben, die den größten Anteil im Diagramm ausmachen.
- **Gruppe 4:** Kunden mit den geringsten Ausgaben, deren Anzahl deutlich geringer ist im Vergleich zu den anderen Gruppen.

![MonetaryGruppeVerteilung](https://github.com/OlhaAD/RFM_HandM/blob/main/visualisations/MonetaryGruppeHist.png)

### Kundensegmentierung

Die erste Segmentierung der Kunden wird in der folgenden Visualisierung dargestellt. Das Diagramm zeigt die Verteilung der Kunden nach RFM-Segmenten basierend auf ihrem Verhalten. Die Segmente sind nach der Anzahl der Kunden sortiert, was es leicht macht, die größten Gruppen zu identifizieren.

![PrimarySegmentierung](https://github.com/OlhaAD/RFM_HandM/blob/main/visualisations/Prim%C3%A4reRFMAufteilungPlot.png)

Es ist zu beachten, dass sich eine beträchtliche Anzahl von Segmenten mit einer geringen Kundenanzahl gebildet hat. Diese Segmente wurden in eine allgemeine Kategorie — Andere Gruppen — zusammengefasst. In einem nächsten Schritt werden die Segmente zu größeren Gruppen zusammengefasst, und alle kleinen Segmente werden ebenfalls berücksichtigt und in entsprechende Gruppen integriert. Laut der Visualisierung ist das Segment mit der größten Anzahl an Kunden das Segment 444. Dies sind hauptsächlich verlorene Kleinkunden, die ihre letzten Einkäufe vor mehr als einem Jahr getätigt haben, nicht mehr als drei Einkäufe gemacht haben und geringe Beträge (unter 0,09) ausgegeben haben.

**Kombination von Segmenten und Erstellung zusammengefasster Kundengruppen:**

1. **Abwandernde Kleinkunden:** Segmente 444, 434, 443, 433, 424. Diese Kunden haben seit mehr als einem Jahr keine Einkäufe getätigt und entweder wenige oder nur kleine Beträge ausgegeben.

2. **Abwandernde Mittelkunden:** Segmente 423, 442, 432, 422, 413. Diese Kunden haben seit mehr als einem Jahr nichts mehr gekauft, hatten jedoch zuvor durchschnittliche Ausgaben zwischen 0,1 und 1,5.

3. **Abwandernde VIP-Kunden:** Segmente 421, 411, 431, 412. Diese Kunden haben entweder eine große Anzahl von Käufen getätigt (über 28), wie im Segment 412, oder beträchtliche Beträge ausgegeben (über dem dritten Quartil), aber seit mehr als einem Jahr nichts mehr gekauft. Diese Gruppe erfordert besondere Aufmerksamkeit, da sie für das Geschäft von großem Wert ist.

4. **Schlafende Kleinkunden:** Segmente 344, 343, 334, 324, 333. Diese Kunden haben seit mehr als 100 Tagen keine Einkäufe getätigt und hauptsächlich kleine Beträge ausgegeben. Dies sind Kunden mit geringer Aktivität und geringem Umsatzwert für das Unternehmen.

5. **Schlafende Mittelkunden:** Segmente 323, 322, 313, 332, 342. Kunden, die seit mehr als 100 Tagen keine Einkäufe getätigt haben und durchschnittliche Ausgaben haben. Diese Gruppe umfasst Kunden mit moderater Aktivität und mittlerem Umsatzwert.

6. **Schlafende VIP-Kunden:** Segmente 311, 331, 312, 321. Diese Kunden haben seit mehr als 100 Tagen keine Einkäufe getätigt, zeichnen sich jedoch durch sehr hohe Ausgaben oder eine große Anzahl von Käufen (über 28) aus. Diese Kunden haben trotz ihrer kürzlich mangelnden Aktivität einen hohen Wert für das Geschäft.

7. **Aktive Kleinkunden:** Segmente 244, 144, 234, 143, 134, 243, 124, 224, 233, 133. Kunden, die in den letzten 100 Tagen eingekauft haben, jedoch nur kleine Beträge ausgegeben haben.

8. **Regelmäßige Mittelkunden:** Segmente 123, 113, 213, 223, 222, 232, 132. Kunden, die in den letzten 100 Tagen Einkäufe getätigt haben, mit Ausgaben zwischen 0,1 und 1,5.

9. **Regelmäßige Großkunden:** Segmente 212, 112, 122. Kunden, die in den letzten 100 Tagen Einkäufe getätigt haben, wobei die meisten von ihnen mehr als 28 Käufe getätigt und zwischen 0,7 und 1,5 ausgegeben haben.

10. **VIP-Kunden:** Segmente 111, 211, 121, 221, 131, 231. Kunden, die in den letzten 100 Tagen Einkäufe mit sehr großen Beträgen (über 1,5) getätigt haben.

**Visualisierung der Kundenverteilung nach den 10 konsolidierten RFM-Gruppen**

Dieses Kreisdiagramm veranschaulicht die Verteilung der H&M-Kunden auf zehn konsolidierte RFM-Gruppen, die auf der Analyse von Recency, Frequency und Monetary basieren. Diese Gruppen repräsentieren verschiedene Ebenen der Kundenbindung und Aktivität, was es dem Unternehmen ermöglicht, seine Kundenbasis effektiv zu segmentieren und Marketingstrategien gezielt auf die entsprechenden Segmente auszurichten.

![10GruppenRFM](https://github.com/OlhaAD/RFM_HandM/blob/main/visualisations/RFMGroupen.png)
