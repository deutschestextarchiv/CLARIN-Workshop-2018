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

- Vier Ziele:
  1. Vermittlung technischer Grundlagen
  2. Veranschaulichung der computerlinguitischen Verfahren anhand einfacher Beispiele
  3. Annäherung an die methodischen Herausforderungen der digitalen Hermeneutik
  4. Einstieg in fachlich relevante Fallbeispiele

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

# Textsammlungen

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
    + Auszählen gemeinsamer Vorkommen von Wörtern bzw. Wortgruppen: **distributionelle Semantik**
- vollautomatisch möglich (mit akzeptabler Qualität)
- zwei grundsätzliche Ansätze der Modellierung:
    + auf Basis von Expertenwissen **manuell** erstellte Regeln
    + auf Basis manuell erstellter Beispiele **automatisch** induzierte Regeln

---

# Tokenisierung

- Unterteilung von Fließtext in **Wörter** (bzw. *Tokens*) und **Sätze**
- (Vor-)Klassifizierung der Tokens zur Beschleunigung der morphologischen Analyse
    + Abkürzungen
    + Zahlen
    + Sonderzeichen
    + Fremdalphabete
- Normalisierung der Worttrennung
- Ansatz: Trennung an Leerraum
- im statistischer Ansatz, **überwachtes Lernen**

---

# Tokenisierung

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

# Morphologische Analyse

- Aufgabe
    + Bestimmung der **möglichen** Wortarten eines Wortes
      ```
      grünen ↦ {Verb, Adjektiv}
      Müller ↦ {Substantiv, Eigenname}
      ```
    + Abbildung auf eine kanonische **Grundform** (*Lemma*)
      ```
      grünen  ↦ grün
      Müllers ↦ Müller
      ```
    + Identifikation der beteiligten Wortbildungsprozesse
      ```
      Grünspan ↦ grün<A>#Span<N>
      verirren ↦ ver<p>+irren<V>
      ```

---

# Morphologische Analyse

- Verfahren des maschinellen Lernens nicht geeignet
- Herausfordend für Sprachen mit komplexer Wortbildung
- `Finite State Morphology` (klassischer regelbasierter Ansatz):
    + Man nehme
        * eine **große** Liste einfacher Wörter
        * deren **morphosyntaktische** Eigenschaften
        * Vor- und Nachsilben,
    + packe dies in einen **endlichen Automaten** und
    + bilde dessen **Kleenesche Hülle**
- Bestandteil der meisten Sprachverarbeitungssysteme

---

# Morphologische Analyse

- Illustration
    + Lexikon `{schön<A>,Geist<N>}`
    + Vorsilben `{un<p>,ur<p>}`
    + Nachsilben `{heit<N>,lich<A>}`

.center[.img-orig[![Lexikon](figures/morph_ex.svg)]]

---

count: false

# Morphologische Analyse

- Illustration
    + Lexikon `{schön<A>,Geist<N>}`
    + Vorsilben `{un<p>,ur<p>}`
    + Nachsilben `{heit<N>,lich<A>}`

.center[.img-orig[![Lexikon](figures/morph_ex2.svg)]]

---

count: false

# Morphologische Analyse

- Illustration
    + Lexikon `{schön<A>,Geist<N>}`
    + Vorsilben `{un<p>,ur<p>}`
    + Nachsilben `{heit<N>,lich<A>}`

<center><img src="figures/morph_ex3.svg" width="650" /></center>

---

count: false

# Morphologische Analyse

- Illustration
    + Lexikon `{schön<A>,Geist<N>}`
    + Vorsilben `{un<p>,ur<p>}`
    + Nachsilben `{heit<N>,lich<A>}`

<center><img src="figures/morph_ex4.svg" width="880" /></center>

---

count: false

# Morphologische Analyse

- Illustration
    + Lexikon `{schön<A>,Geist<N>}`
    + Vorsilben `{un<p>,ur<p>}`
    + Nachsilben `{heit<N>,lich<A>}`

<center><img src="figures/morph_ex6.svg" width="880" /></center>

---

count: false

# Morphologische Analyse

- Illustration
    + Lexikon `{schön<A>,Geist<N>}`
    + Vorsilben `{un<p>,ur<p>}`
    + Nachsilben `{heit<N>,lich<A>}`

<center><img src="figures/morph_ex5.svg" width="880" /></center>

---

# PoS-Tagging

- Auswahl der **wahrscheinlichsten Wortart** im konkreten Satzkontext aus der Menge der **möglichen** Wortarten eines
Wortes
- statistischer Ansatz, trainiert auf **manuell kategorisierten** Daten
    + Modell über Trigramme aus Wörtern und Kategoriemengen (i.e. Wortklasse)
    + Bestimmung der wahrscheinlichsten Kategoriesequenz für einen Satz
    + heuristische Auswahl der »einfachsten« **Grundform**
    + angepasste Modelle für historische Sprache, gesprochene Sprache, Kindersprache etc.
- `TreeTagger` als bekanntestes, frei verfügbares Werkzeug

---

# PoS-Tagging

.center[<img src="figures/kohl1.svg" style="width:800px"/>]

---

count: false

# PoS-Tagging

.center[<img src="figures/kohl.svg" style="width:800px"/>]

---

# Wortverlaufskurven

+ **Häufigkeit eines Wort über einen zeitlichen Verlauf**
+ nutzen Textsammlungen als Basis; z.B.:
    - Zeitungen (1945 bis heute)
    - Deutsches Textarchiv und DWDS-Kernkorpus (1600&ndash;2000)
+ Metadaten für jeden Text:
    - *Datum* (Jahr)
    - *Textklasse* (Belletristik, Gebrauchsliteratur, Wissenschaft, Zeitung)
    - und viele weitere (i.e. beliebige DDC-Abfragen)
+ Darstellung:
    - relativ (Vorkommen pro Million)
        + 
.red[Achtung!] Kurven werden häufig geglättet, da nicht für jedes Jahr ausreichend und gleich viele Daten verfügbar sind
    - in absoluten Zahlen

---

# Wortverlaufskurven

.center[<img src="figures/stress.svg" style="width:800px"/>]

---

# Wortverlaufskurven

.center[<img src="figures/flugzeug_vs_eisenbahn.svg" style="width:800px"/>]

---

# Wortverlaufskurven

.center[<img src="figures/kanzler_vs_kanzlerin.svg" style="width:800px"/>]

---

# Typische Verbindungen

- **DWDS-Wortprofil**
    + statistisch signifikante und damit typische Wortverbindungen
    + als Schlagwortwolke (Tagcloud) oder als Tabelle
    + kombiniert distributionelle Semantik mit Dependenzparsing

.center[.img-orig[![Stress](figures/wp_kaffee_objekt.png)]]

---

# Typische Verbindungen

.center[<img src="figures/wp_kaffee.png" style="width:700px"/>]

---

# Distributionelle Semantik

- Semantik: Theorie von der sprachlichen Bedeutung
    + **lexikalische** Semantik: Wortbedeutungen
    + **kompositionelle** Semantik: Phrasen- und Satzbedeutung
    * **ontologische** Beziehungen: Synonyme, Hyponyme, Hyperonyme
- mit automatischen Verfahren sehr schwer zu erfassen
- distributionelle Ähnlichkeit: gleiche Kontexte ⇒ ähnliche Bedeutung
- <span style="font-variant:small-caps;">John Rupert Firth</span> (1890&ndash;1960)
    + »You shall know a word by the company it keeps« (1957)
    + `Er versenkte den .... im Tor.`

---

count: false

# Distributionelle Semantik

- Semantik: Theorie von der sprachlichen Bedeutung
    + **lexikalische** Semantik: Wortbedeutungen
    + **kompositionelle** Semantik: Phrasen- und Satzbedeutung
    * **ontologische** Beziehungen: Synonyme, Hyponyme, Hyperonyme
- mit automatischen Verfahren sehr schwer zu erfassen
- distributionelle Ähnlichkeit: gleiche Kontexte ⇒ ähnliche Bedeutung
- <span style="font-variant:small-caps;">John Rupert Firth</span> (1890&ndash;1960)
    + »You shall know a word by the company it keeps« (1957)
    + `Er versenkte den Ball im Tor.`

---

# Distributionelle Semantik

- Vorgehen:
    + Man definiere einen **Kontext** (z.&#x202f;B. Satz) und **interessante** Wörter,
    + werfe für jedes Zielwort alle interessanten Wörter (z.&#x202f;B. *Nomen* und *Verben*) aus dem Kontext in einen Topf (*Bag of Words*),
    + repräsentiere den Topf als **hochdimensionalen Vektorraum** und
    + vergleiche die Vektoren miteinander.
- Illustration:
    + `Der Säufer randalierte in der Kneipe. Die Polizei sperrte den Säufer ein, weil er randalierte.`
.right[<img src="figures/distr.svg" style="width:180px"/>]

---

# Dependenzparsing

- Bestimmung der **strukturellen** Beziehungen zwischen Wörtern im Satz
- **regelbasierter** Ansatz
    + handgeschriebene Grammatik
    + Grundform, Kategorie und morphosyntaktische Merkmale als Beschreibungseinheit
    + Implementierung mit Hilfe endlicher, gewichteter Automaten
(schnell!)

---

# Dependenzparsing

.center[<img src="figures/dependency_ex.svg" style="width:800px"/>]

---

# Typische Verbindungen

+ Wortvergleiche: Gemeinsamkeiten und Unterschiede

.center[<span style="color:#5B7BB6;font-weight:bold">verkünden</span> und <span style="color:#c30c60;font-weight:bold">bekanntgeben</span>]

.center[<img src="figures/wp_vergleich.png" style="height:400px"/>]

---

# Spiel: Profilardy

.center[[**Klick mich!**](https://docs.google.com/presentation/d/1qPfvBRmpPNAV6Y3zHGoYXAj-MuKy84E1ZJPvgMjwezA)]

---

class: title-slide

# Digitale Hermeneutik

---

# Operationalisierung digitaler Tools
Wie geht der Forscher mit quantitativen Ergebnissen um?
- Grundvoraussetzung ist Kenntnis über die Arbeitsweise digitaler Tools
- Vorgehen: Integration von **Distant Reading**-Methoden und klassischen **Close Reading**-Ansätzen
- Ziel: Etablierung einer neuen hermeneutischen Methode: **Digitale Hermeneutik**

---


# Distant Reading

- Definition:
  * ...
- Verfahren:
  1. Volltextsuche
  2. Lexikometrie und Korpusstatistik
  3. Methoden maschinellen Lernens/ Topic modelling
  4. Netzwerkanalysen
- **Wichtig:** Voraussetzung hierfür sind immer entsprechend annotierte Text-Korpora


---

# Der Weg zur Digitalen Hermeneutik?

Fünf neue Basisfertigkeiten nach Andreas Fickers (Luxemburg):
- Algorithmuskritik
- Datenkritik
- Werkzeugkritik
- Interface-Kritik
- Simulationskritik

---

# Close + Distant = Blended Reading?

> *„Unter dem Begriff des ‚blended reading‘ schlagen wir eine Strategie im Sinne einer Best Practise vor, die semiautomatische Analyseverfahren mit klassischer Textlektüre so integriert, dass sozialwissenschaftliche Erkenntnispotenziale, die sich auf die Auswertung großer Textdatenmengen stützen, optimal ausgeschöpft werden.“*<br />
> Stulpe/Lemke (Textmining in den Sozialwissenschaften, 2016, S. 21)

---

class: title-slide

# Blended Reading und die Kollokationsanalyse mit DiaCollo

---

# Definition: Kollokation

- *Kollokation* bezeichnet häufiges gemeinsames Auftreten zweier Wörter in vordefiniertem Kontext (Satz, Absatz etc.)
  + enge semantische Beziehungen (Schüler-Lehrer) 
  + Sachverhalte (Schule-Reform) 
  + feste Phrasen (Hänschen-Hans)
- **Grundidee:**
  + Ermittlung aller Kollokationen eines Eingabebegriffes
  + Ordnung nach deren Assoziationsgrad zum Eingabebegriff
  + Beispiel [Begriff](http://kaskade.dwds.de/dstar/dta/diacollo/?query=Begriff&date=&slice=50&score=ld&kbest=20&cutoff=&profile=2&format=cloud&groupby=&eps=0) im DTA

---

# Diachrone Kollokationsanalyse

> *„Die Bedeutung eines Wortes ist sein Gebrauch in der Sprache“*<br />
> Ludwig Wittgenstein (Philosophische Untersuchungen)

- DiaCollo ermöglicht die Analyse von Sprachwandel indem es die historische (Zeit-)Dimension in großen digitalen Textkorpora visualisiert
  + Untersuchungszeiträume frei skalierbar (jahresweise, dekadenweise etc.)
  + Visualisierungsoptionen für Abfrageergebnisse (Wordclouds, Bubble, Gmotion, Html‐Lists)
- getestet an großen und mittelgroßen Korpora, darunter die *Grenzboten* und *DDR-Presseportal*

---

# Weitere Informationen unter:

[http://kaskade.dwds.de/dstar/dta/diacollo/](http://kaskade.dwds.de/dstar/dta/diacollo/)
[http://kaskade.dwds.de/diacollo‐tutorial/#introduction.html](http://kaskade.dwds.de/diacollo‐tutorial/#introduction.html)
[https://clarin‐d.net/de/kollokationsanalyse‐in‐diachroner‐perspektive](https://clarin‐d.net/de/kollokationsanalyse‐in‐diachroner‐perspektive)

![DiaCollo](https://i.imgur.com/hcCsIUN.jpg)

---

class: title-slide

# Fallbeispiele

---

# Fallbeispiele - Vorgehenweise

- *Explorativ*
  + Wordstatistiken und Verlaufskurven
  + signifikante Veränderungen im Inhaltswortbereich
  + Hinweise auf Bedeutungsverschiebung bzw. Bezeichnungswandel

- *Hypothesengeleitet*
  + spezifische Korpusrecherchen zur efizienten Belegauswahl
  + Belegauswertung
  + quantitatives „Untermauern“

---

# Fallbeispiel 1: Antisemitismus

![](https://i.imgur.com/cjApfpk.jpg)

- Nationalliberale Zeitschrift „Die Grenzboten“
  + Erscheinungszeitraum 1841 bis 1922 wöchentlich, zeitweise zweiwöchentlich.
  + Insgesamt ca. 270 Bände (ca. 187.000 Seiten)
- Digitalisierung an der SuUB Bremen im Rahmen zweier DFG-Projekte
  + Erschließung von Volltext **und** Struktur 
  + seit 2017 auch in CLARIN-D integriert
