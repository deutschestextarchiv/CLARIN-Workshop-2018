layout: true
  
<div class="my-header"></div>

<div class="my-footer">
  <table>
    <tr>
      <td>CLARIN-D &ndash; Common Language Resources and Technology Infrastructure</td>
      <td style="text-align:right"><a href="https://www.clarin-d.net/">www.clarin-d.net</a></td>
    </tr>
  </table>
</div>

---

class: title-slide

# Digitale Werkzeuge für die Zeitgeschichte:
## Eine Einführung in die digitale Hermeneutik und das Textmining

| Thomas Werneke  | Kay-Michael Würzner |
|:---------------:|:-------------------:|
| [werneke@zzf-potsdam.de](mailto:werneke@zzf-potsdam.de) | [wuerzner@bbaw.de](mailto:wuerzner@bbaw.de) |

---

# Überblick

---

# Digital turn?

- *Was sind Digitale Geisteswissenschaften?*
    + Neue Arbeitsweisen?
    + Neue Methodiken?
    + Eine neue Disziplin?

- *Alle arbeiten bereits „digital“*
    + mit Smartboards, Lernplattformen und digitalen Bildungsmedien
    + mit Online‐Katalogen der Bibliotheken und fachlichen Onlineportalen (z.B. HSozKult)
    + mit digitalen Werkzeugen (wie Googles „Ngram‐Viewer“)

---

# Google _Ngram_ – Fluch oder Segen?

:::info
Fallbeispiel: `love=>*_noun` im „English“-Korpus 
(10 häufigtsten Nomen in der Nähe von „love“)
:::


![](https://i.imgur.com/zq6Rr0T.jpg)

---

class: title-slide

# Linguistische Annotation

---

# Linguistische Annotation

- Zum Begriff der Linguistischen Annotation
    + Auszeichnung bestimmter linguistischer Eigenschaften
    + Bezug zu einer Einheit des Textes:
        * **Wort**: Silbenstruktur, morphologische Zerlegung, lexikalische
Semantik etc.
        * *Wortgruppe*: Mehrwortausdrücke, Namen, Kollokationen etc.
        * *Phrase*: syntaktische Kategorie, syntaktische Funktion
        * *Satz*: syntaktische Struktur, Satzsemantik, Funktion im Text (?)
    + *manuelle* vs. *automatische* Annotation
- Annotation von Korpora
    + Strukturierung und Anreicherung der Rohtexte zum Zwecke
        * besserer Durchsuchbarkeit
        * einfacherer Belegidentifikation
        * moderner Korpuspräsentationsformen
        * quantitativer Auswertungen
    + Korpusumfang bedingt vollautomatische Analysekette

---

# Linguistische Annotation

- Beispiel:

---

# Linguistische Annotation

- Analysekette:
    + Zerlegung des Fließtextes in Wörter und Sätze: **Tokenisierung**
    + Bestimmung der Grundform der Wörter: **Lemmatisierung**
    + Bestimmung der tatsächlichen Wortart eines Wortes: **PoS-Tagging**
    + Klassifizierung der Beziehungen der Wörter untereinander: **Dependenzparsing**
- vollautomatisch möglich (mit akzeptabler Qualität)
- zwei grundsätzliche Ansätze der Modellierung:
    + auf Basis von Expertenwissen **manuell** erstellte Regeln
    + auf Basis manuell erstellter Beispiele **automatisch** induzierte Regeln

---

# NLP: Tokenisierung

- Unterteilung von Fließtext in **Wörter** (bzw. *Tokens*) und **Sätze**
- (Vor-)Klassifizierung der Tokens zur Beschleunigung der morphologischen Analyse
    + Abkürzungen
    + Zahlen
    + Sonderzeichen
    + Fremdalphabete
- Normalisierung der Worttrennung
- Ansatz: Trennung an Leerraum
- im DWDS: statistischer Ansatz, **überwachtes Lernen**

---

# NLP: Tokenisierung

Problembereich *Satz*
```
Nach einer Schätzung des Industrieministeriums sind es mehr als 800.
»Österreich wurde alleingelassen in Europa«, beschwerte sich SPÖ-
Zentralsekretär Josef Cap.
SZ: Auf die Wahlerfolge der rechtsradikalen Parteien ...
```
Problembereich *Token*
```
Kaiser's-Netz → Kaiser 's-Netz
Jeanne d'Arc → Jeanne d' Arc
mm. → mm. [ORD]
CDU/CSU → CDU / CSU
(Verwaltungs-)Personal → ( Verwaltungs- ) Personal
```

---
