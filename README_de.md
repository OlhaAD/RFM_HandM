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
