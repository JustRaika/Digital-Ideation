# Astat (Applied Statistics for Data Science)
This folder contains all the assets from the Astat module. It has some content covered by Yanis's summary found [here](https://yanisdeplazes.github.io/Digital-Ideation/24HS/ASTAT/astat-summary.pdf). I have my own summary which contains my lecture notes and my preperation for the final exam. It can be accessed [here](https://github.com/JustRaika/Digital-Ideation/blob/main/static-wiki/docs/ASTAT-compressed.pdf). 


**Men4:** The aim of this learning portfolio is to prepare me for the exam as I failed the admission last semester. The mentoring helps me to make time for ASTAT every week and to familiarise myself with the lectures in greater depth (and also to work through them). My mentor accompanies me in this process, guides me upon questions and gives me confidence in my abilities. The "Aufgabe zum Verständnis der Vorlesung" is picked out of a few and just representative.

## Content
- [Woche 1 - Einführung in R](#woche-1---einführung-in-r)
- [Woche 2 - Eindimensionale deskriptive Statistik](#woche-2---eindimensionale-diskriptive-statistik)
- [Woche 3 - Histogramm & zweidimensionale Statistik](#woche-3---histogramm--zweidimensionale-statistik)
- [Woche 4 - Korrelation, Wahrscheinlichkeitsmodelle](#woche-4---korrelation-wahrscheinlichkeitsmodelle)
- [Woche 5 - Zufallsvariable & Wahrscheinlichkeitsverteilung](#woche-5---zufallsvariable--wahrscheinlichkeitsverteilung)
- [Woche 6 - Bedingte Wahrscheinlichkeit](#woche-6---bedingte-wahrscheinlichkeit)
- [Woche 7 - Normalverteilung](#woche-7---normalverteilung)
- [Woche 8 - Gesetz der großen Zahlen](#woche-8---gesetz-der-grossen-zahlen)
- [Woche 9 - Hypothesentest](#woche-9---hypothesentest)
- [Woche 10 - Vertrauenstest & Wilcoxontest](#woche-10---vertrauenstest--wilcoxontest)
- [Woche 11 - Lineare Regression](#woche-11---lineare-regression)
- [Woche 12 - Multiple lineare Regression](#woche-12---multiple-lineare-regression)


## Woche 1 - Einführung in R
### Vorlesung
1) Einen Vektor mit den Zahlen 4,2,1,3,3,5,7 bilden: `x <- c(4,2,1,3,3,5,7)`
2) Den dritten Wert aus diesem Vektor wählen: `x[3]`
3) Den ersten & vierten Wert auswählen: `x[c(1,4)]`
4) Die Länge des Vektors x bestimmen: `length(x)`
5) +2 zu jedem Wert im Vektor addieren: `x+2`
6) Gesamtsumme des Vektors ausgeben nachdem +2 gemacht wurde: `sum(x+2)`

***
### Ilias-Fragen
<img src="https://github.com/user-attachments/assets/292438da-2643-408c-aefb-45c715f6cecc" width="500">
<img src="https://github.com/user-attachments/assets/e418c156-2a39-4835-871b-109cb18faedf" width="500">
<img src="https://github.com/user-attachments/assets/74cc2834-4863-4f80-88e6-8820a7db5dc8" width="500">

***
### Aufgabe zum Verständnis der Vorlesung
Es gibt 6 Personen mit Kilogramm: 60, 72, 57, 90, 95, 72 und Meter: 1.75, 1.80, 1.65, 1.90, 1.74, 1.91. Berechne den BMI mit folgender Formel:

 _Gewicht/Grösse^2_

```r
# Lösung
weight <- c(60, 72, 57, 90, 95, 72)
height <- c(1.75, 1.80, 1.65, 1.90, 1.74, 1.91)
bmi <- weight/height^2
bmi
```

## Woche 2 - Eindimensionale diskriptive Statistik
### Vorlesung
* `Eindimensional` = eine Form von einem Datensatz (z.B nur Körpergrösse oder nur Gewicht).
* `Zweidimensional` = z.B Gewicht und Grösse gemeinsam. Meistens in Form einer Tabelle.
* `Deskriptiv` = Daten zusammenfassen und grafische Darstellung dieser Daten.
* `Arithmetisches Mittel (Mittelwert, Durchschnitt)` = Wo ist die Mitte der Daten?

<img src="https://github.com/user-attachments/assets/4f8889eb-4a22-4ff8-9414-96b259cab584" width="700">

```r
# Arithmetisches Mittel
waageA <- c(79.98, 80.04, 80.02, 80.04, 80.03, 80.03, 80.04, 79.97, 80.05, 80.03, 80.02, 80.00, 80.02)

mean(waageA)
## [1] 0.02396579
```

* `Empirische Varianz und Standartabweichung` = Ist die emprische Varianz (und damit die Standartabweichung) gross, so ist die Streung der Messwerte um das arithmetische Mittel gross.

<img src="https://github.com/user-attachments/assets/5c6876db-ac8d-4f63-92bf-904bb1e123d2" width="700">

```r
# Empirische Varianz und Standartabweichung
var(waageA)
## [1] 0.000574359

sd(waageA)
## [1] 0.02396579
```

* `Median (mittlerer Wert)` = Wert, bei dem die Hälfte der Messwerte unter oder gleich diesem Wert sind. Die andere Hälfte ist gleich diesem Messwert oder darüber.

```r
# Median
median(waageA)
## [1] 80.03
waageB <- c(80.02, 79.94, 79.98, 79.97, 79.97, 80.03, 79.95, 79.97)

median(waageB)
## [1] 79.97
```

* `Unteres Quartil` = Wert, wo 25% aller Beobachtungen kleiner oder gleich und 75% grösser oder gleich sind wie dieser Wert. Man wählt den nächstgrösseren Wert als unteres Quartil.
* `Oberes Quartil` = Wert, wo 75% aller Beobachtungen kleiner oder gleich und 25% grösser oder gleich sind wie dieser Wert. Man wählt den nächstgrösseren Wert als oberes Quartil.

```r
# Syntax für das untere Quartil: p=0.25

quantile(waageA, p=0.25, type =2)
## 25%
## 80.02

quantile(waageB, p=0.25, type =2)
## 25%
## 79.96

# Syntax für das obere Quartil: p=0.75

## 75%
## 80.04
```

* `Quartilsdifferenz` = Ist ein Streuungsmass für die Daten (oberes Quartil − unteres Quartil). Es misst die Länge des Intervalls, das etwa die Hälfte der mittleren Beobachtungen enthält. Je kleiner dieses Mass, umso näher liegt die Hälfte aller Werte um den Median und umso kleiner ist die Streuung.

```r
# Hälfte der Lernenden liegen innerhalb von 1.55 Noten, nämlich zwischen 3.8 und 5.35 25 % der Klasse 3.8 oder weniger; rund 25 % der Klasse 5.35 und mehr.

quantile(noten, p= c(0.25, 0.75), type = 2)
## 25% 75%
## 3.80 5.35

IQR(noten, type = 2)
## [1] 1.55
```

* `Quantile` = Quantile sind Quartile auf jede andere Prozentzahl verallgemeinert. Nachfolgend 10% und 70%-Quantil:

```r
# Knapp 10 % der Messwerte sind kleiner oder gleich 79.97. Entsprechend: Knapp 70 % der Messwerte kleiner oder gleich 80.04

quantile(waageA, p = .1, type = 2)
## 10%
## 79.98

quantile(waageA, p = .7, type = 2)
## 70%
## 80.04
```


* `Boxplot` = In einem Boxplot werden numerische Daten in Quartile unterteilt, und zwischen den ersten und dritten Quartilen wird ein Feld gezeichnet, wobei eine zusätzliche Linie entlang des zweiten Quartils
gezeichnet wird, um den Median zu kennzeichnen.

<img src="https://github.com/user-attachments/assets/16505430-4636-4f59-bafb-2a6357481f6c" width="900">

```r
# Boxplot: Darstellungen von verschiedenen Gruppen
boxplot(waageA, col = "darkseagreen3")

boxplot(waageA, waageB, xlab = "Waage", col = c("orange", "lightblue")

axis(side = 1, at = c(1,2), labels = c("A", "B"))
```

***
### Ilias-Fragen
<img src="https://github.com/user-attachments/assets/cb1f2b3d-50b1-4191-8529-e32942b651fd" width="500">
<img src="https://github.com/user-attachments/assets/f9af140f-c6f5-441c-b185-d4f2129ff21f" width="500">
<img src="https://github.com/user-attachments/assets/05f906a3-fcb0-449b-ac0f-035b80d8d94b" width="500">

***
### Aufgabe zum Verständnis der Vorlesung
In der Datei Diet.csv sind 76 Personen aufgelistet, die jeweils einer der Diäten 1,2 oder 3 für 6 Wochen machten.

<img src="https://github.com/user-attachments/assets/b6428196-642c-4f61-b15a-e8d7f4ca3a04" width="900">
In der Datei ist das Gewicht `pre.weight` vor der Diät und das Gewicht `weight6weeks` nach 6 Wochen aufgeführt. Wir interessieren uns für den Gewichtsverlust. Dazu führen wir zu der Datei eine Spalte `weight.loss` hinzu. Das geht folgendermassen:

<img src="https://github.com/user-attachments/assets/39f739e2-2f94-44c2-ac7f-c27e56451b55" width="900">

`R` versteht `diet$weight.loss` automatisch als neue Spalte und fügt die der Tabelle
hinzu. Nun soll dasselbe für die Teilaufgaben `weight.loss` und `Diet` durchgeführt werden. Die Resultate sollten jeweils interpretiert werden.

```r
# Gruppenmittel:
tapply(diet$weight.loss, diet$Diet, mean)

##     1         2         3
## -3.300000 -3.025926 -5.148148

# Resultat: Die Diäten 1 und 2 führen zu einem durchschnittlichen Gewichtsverlust von 3kg. Bei Diät 3 sind es durchschnittlich 5kg.
```

## Woche 3 - Histogramm & zweidimensionale Statistik
### Vorlesung
* `Histogramm` = Grafischer Überblick über auftretende Werte. Aufteilung des Wertebereichs in `k` Klassen (Intervalle). Wahl der Anzahl Balken ist relevant für die Aussagekraft eines Histogrammes. Zu viel -> Muster schwer erkennbar. Zu wenig -> zu ungenau.

<img src="https://github.com/user-attachments/assets/aa5bb31b-2381-4fa7-ab42-8cd3c9566703" width="900">
<img src="https://github.com/user-attachments/assets/8a27d9e6-88c1-4461-b0d0-f42ed9b39b56" width="900">


* `Zweidimensionale Deskriptive Statistik` = Zweidimensionale Daten. An einem Versuchsobjekt werden jeweils zwei verschiedene Grössen gemessen.

* `Streudiagramm plot(x,y)` = Grafische Darstellung zweidimensionaler Daten. Auf der x-Achse wird die erste Grösse und auf der y-Achse die zweite Grösse abgetragen. Die Punkte im Streudiagramm sind die Messwerte. 

```r
# Streudiagramm für Weinkonsum und Mortalität (Beispiel)
wein <- c(2.8, 3.2, 3.2, 3.4, 4.3, 4.9, 5.1, 5.2, 5.9, 5.9, 6.6, 8.3, 12.6, 15.1, 25.1, 33.1, 75.9, 75.9)

mort <- c(6.2, 9.0, 7.1, 6.8, 10.2, 7.8, 9.3, 5.9, 8.9, 5.5, 7.1, 9.1, 5.1, 4.7, 3.1, 3.2, 2.1)

plot(wein, mort, 
     xlab = "Weinkonsum (Lier pro Jahr)", 
     ylab = "Mortalität",
     col = "blue",
     pch = 20
)
```
<img src="https://github.com/user-attachments/assets/3dc05ccc-5c5d-4e19-93c0-7dfeb424c1bd" width="700">


* `Regressionsgerade lm(y ~ x) + abline (lm(y ~ x))` = Die Regressionsgerade ist eine Gerade, die die Beziehung zwischen zwei Variablen beschreibt. Sie wird durch die Methode der kleinsten Quadrate geschätzt. Die Regressionsgerade wird in einem Streudiagramm eingezeichnet, um den Trend der Daten zu verdeutlichen.

```r
# Regressionsgerade für die Beziehung zwischen Seiten und Preis eines Buches
seiten <- seq(50, 500, 50)

preis <- c(6.4, 9.5, 15.6, 17.8, 23.4, 23.4, 22.5, 26.1, 29.1)

lm(preis ~ seiten)

## 
## Call:
## lm(formula = preis ~ seiten)
##
## Coefficients:
## (Intercept)      seiten
##     6.04000     0.04673

## Der Grundpreis ohne Seiten liegt bei 6.04. Pro zusätzliche Seite steigt der Preis um 0.04673.
```
<img src="https://github.com/user-attachments/assets/9554c0eb-7667-4f45-81ac-4bde725bf144" width="700">

***
### Ilias-Fragen
<img src="https://github.com/user-attachments/assets/e3e3587c-2d4e-4910-a2b2-b9e1c1ae1bc8" width="500">

***
### Aufgabe zum Verständnis der Vorlesung
In dieser Aufgabe werden 4 Datensätze betrachtet, die von Anscombe konstruiert wurden. In jedem der Datensätze gibt es eine Zielvariable y und eine erklärende Variable x. Die Datei ist `R` schon enthalten.

<img src="https://github.com/user-attachments/assets/88ee19fb-64df-4023-9ede-aea434713771" width="900">

Stelle jeden der 4 Datensätze als Streudiagramm dar, zeichnen die Regressionsgerade ein und kommentieren die Ergebnisse.

<img src="https://github.com/user-attachments/assets/69f4d29b-5f38-44d3-b9a5-0cc8ee91dbb3" width="900">

Mit `par(mfrow=c(2,2))` wird das Grafikfenster so eingeteilt, dass alle 4 Bilder nebeneinander passen.

```r
# Betrachtet man die vier Streudiagramme, so sieht man, dass nur im ersten Fall eine lineare Regression korrekt ist. Im zweiten Fall ist die Beziehung zwischen X und Y nicht linear, sondern quadratisch. Im dritten Fall gibt es einen Ausreisser, welcher die geschätzten Parameter stark beeinflusst. Im vierten Fall wird die Regressionsgerade durch einen einzigen Punkt bestimmt.

data(anscombe)
reg <- lm(anscombe$y1 ~ anscombe$x1)
reg2 <- lm(anscombe$y2 ~ anscombe$x2)
reg3 <- lm(anscombe$y3 ~ anscombe$x3)
reg4 <- lm(anscombe$y4 ~ anscombe$x4)
par(mfrow=c(2,2))
plot(anscombe$x1, anscombe$y1, ylab = "Y1", xlab = "X1")
abline(reg)
plot(anscombe$x2, anscombe$y2, ylab = "Y2", xlab = "X2")
abline(reg2)
plot(anscombe$x3, anscombe$y3, ylab = "Y3", xlab = "X3")
abline(reg3)
plot(anscombe$x4, anscombe$y4, ylab= "Y4", xlab= "X4" )
abline(reg4)
```

<img src="https://github.com/user-attachments/assets/d85a281b-6e58-4c6a-a280-f709b493956c" width="900">


## Woche 4 - Korrelation, Wahrscheinlichkeitsmodelle
### Vorlesung
* `Korrelation` = Dimensionslose Zahl zwischen −1 und +1. Korrelationskoeffizient erkennt nur lineare Zusammenhänge. Wie kann man feststellen, ob ein linearer Zusammenhang der Daten besteht oder nicht? Wert sehr nahe bei 1: Starker linearer Zusammenhang (je mehr, desto mehr).

```r
# Korrelation zwischen Seiten und Preis eines Buches
cor(seiten, preis)

## [1] 0.9681122
```
<img src="https://github.com/user-attachments/assets/afb26af8-6d22-4cb2-a703-47eb167a11d4" width="700">
<img src="https://github.com/user-attachments/assets/a18d367e-2ae8-4bcc-9d8d-820a5dc7b7e7" width="700">
<img src="https://github.com/user-attachments/assets/a5a5ec9b-c1fb-422a-b1d8-f100676b8b54" width="700">
<img src="https://github.com/user-attachments/assets/adf56656-41c9-4985-bf03-d3dbaaaeb6b5" width="700">
<img src="https://github.com/user-attachments/assets/857568bd-36cb-494f-9eaf-60a8a0b9c98b" width="700">


#### Wahrscheinlichkeit
* `Wahrscheinlichkeitsmodell` = Wahrscheinlichkeitsmodelle sind formale mathematische Beziehungen, die den möglichen Resultaten eines zufälligen Experiments ihre jeweiligen Wahrscheinlichkeiten zuordnen.
* `Grundraum Ω` = Enthält alle möglichen Elementarereignisse {ω}.
* `Ereignisse A, B, C` = Teilmengen des Grundraums
* `Wahrscheinlichkeit P` = gehören zu A, B, C
* `Grundraum (die möglichen Ergebnisse)` = z.B beim Würfel: Ω={1,2,3,4,5,6}
* `Element ω` = z.B beim Würfel: 2 ist ein Elementareregnis
* `Kein Elementarereignis` = z.B beim Würfel: 7 ist kein Elementareregnis, weil nicht im Grundraum Ω.
* `Elementarereignis` = Ein Elementarereignis ist das kleinste mögliche Ergebnis eines Zufallsexperiments. Beispiel:  Beim Würfeln ist 1 ein Elementarereignis.


#### Mengenlehre
<img src="https://github.com/user-attachments/assets/595bd512-39c5-41e0-83fa-ab69bd9a9306" width="700">
<img src="https://github.com/user-attachments/assets/6b3c82c0-da4a-42c2-88ae-9aec38174aeb" width="700">
<img src="https://github.com/user-attachments/assets/97f30bee-8383-4438-a9ba-db2db19fb1f1" width="700">


* `Stochastische Unabhängigkeit` = Die stochastische Unabhängikeit von Ereignissen impliziert, dass das Eintreten des Einen keine Auswirkung auf die Wahrscheinlichkeit des Eintretens des anderen Ereignisses hat.

<img src="https://github.com/user-attachments/assets/25376214-34d1-446c-8ecf-d5b517da4576" width="700">
<img src="https://github.com/user-attachments/assets/87b12d4c-786e-4d0b-b0fd-020768bfeaa5" width="700">

```r
## Beispiel
Ereignis A: Mit fairem Würfel eine 1 oder 2 werfen
Ereignis B: Kopf beim Werfen einer fairen Münze
Werfen einer Münze keinen Einfluss auf das Resultat beim Würfelwurf
Formel oben verwenden: P(A⋂B) = P(A) * P(B) = 1/3 * 1/2 = 1/6

## Beispiel Laplace Modell
Es werden zwei verschiedene (blau und rot) Würfel geworfen. 
Wie gross ist die Wahrschienlichkeit, dass die Augensumme 7 ergibt?
Elementarereignis beschreibt die AUgenzahlen auf beiden Würfeln.
Ergebnis in der Form 1 4 schreiben
Ergebnis 1 4 ist nicht = 4 1
Elementarereignisse: Ω = {11,12,..., 65,66}
Anzahl Elementareregnisse: |Ω| = 36
Ereignis E: Augensumme 7 wird gewürfelt
Es gibt davon 6 Elementarereignisse: E = {16, 25, 34, 43, 52, 61}
Alle Elementarereignisse gleich wahrscheinlich: Wahrscheinlihckeit für Ereignis E: P(E) = |E|/|Ω| = 6/36 = 1/6
```

* `GLeichverteilung (Modell von Laplace)`

<img src="https://github.com/user-attachments/assets/1ea18876-95e1-4b55-b783-4a81d74f7984" width="700">

***
### Ilias-Fragen
<img src="https://github.com/user-attachments/assets/3111cb82-2aba-466b-8e26-1c8109caf952" width="500">
<img src="https://github.com/user-attachments/assets/f28ffc07-f444-4dea-a44a-e97a25f4ccfd" width="500">
<img src="https://github.com/user-attachments/assets/d5c15805-e840-4b84-8613-bc92a6a0d3a5" width="500">
<img src="https://github.com/user-attachments/assets/beb4bc23-c299-4d8e-86c6-ff8b3c5d99df" width="500">

***
### Aufgabe zum Verständnis der Vorlesung
Erzeuge den Vektor `t.x` mit den Werten −10, −9, . . . , 9, 10 und den Vektor `t.x1` mit den Werten 0, 1, . . . , 9, 10. Erzeuge dann die Vektoren `t.y` und `t.y1`, deren Elemente die Quadratwerte der entsprechenden Elemente von `t.x` bzw. `t.x1` enthalten.

```r
t.x <- (-10):10
t.x1 <- 0:10
t.y <- t.x^2
t.y1 <- t.x1^2
```

Zeichne die Streudiagramme `t.y` vs. `t.x` und `t.y1` vs `t.x1`. Benutze die R-Funktion `plot()`.

```r
par(mfrow=c(1,2)) # zwei Grafiken im Grafikfenster
plot(t.x, t.y, col = "darkseagreen4", pch = 19)
plot(t.x1, t.y1, col = "darkseagreen4", pch = 19)
```

<img src="https://github.com/user-attachments/assets/86e75a9e-5009-47a8-a0d2-f50c2cedd681" width="700">

Berechne die Korrelationskoeffizienten zwischen `t.x` und `t.y` bzw. zwischen `t.x1` und `t.y1`. Benutze die R-Funktion `cor()`. Warum sind die beiden Korrelationen so verschieden?

```r
cor(t.x,t.y)
## [1] 0

cor(t.x1,t.y1)
## [1] 0.9631427

## Die Korrelation zwischen t.x und t.y ist 0, weil die Daten symmetrisch zur y-Achse liegen. Im zweiten Fall ist die Korrelation hoch (0.96), obwohl die Daten keine lineare Beziehung aufweisen. Der Grund dafür ist, dass x und y monoton steigen.
```

## Woche 5 - Zufallsvariable & Wahrscheinlichkeitsverteilung
### Vorlesung
* `Wahrscheinlichkeitsverteilung` = Eine Wahrscheinlichkeitsverteilung ist eine mathematische Funktion, bei der jedem möglichen Wert eines Zufallsexperiments eine bestimmte Wahrscheinlichkeit zugeordnet wird.

<img src="https://github.com/user-attachments/assets/88ddacdc-a85b-4f42-be36-396bacc10060" width="700">

* `Kennzahlen einer Verteilung`

<img src="https://github.com/user-attachments/assets/ce06fcbd-2eb0-4575-b3f3-38cf98154ac7" width="700">


#### Empirische und theoretische Kennzahlen
* `Das arithmetisches Mittel` x nähert sich für immer mehr Versuche dem theoretischen Wert μX = E(x) an, sofern die Daten der Wahrscheinlichkeitsverteilung von X folgen.

<img src="https://github.com/user-attachments/assets/2de57b0e-478e-4427-819f-52aef1424924" width="700">


* `Die empirische Standardabweichung` sX nähert sich für immer mehr Versuche dem theoretischen Wert σX an, falls die Daten der Wahrscheinlichkeitsverteilung von X folgen.

<img src="https://github.com/user-attachments/assets/e9d1656d-7da7-4840-8c31-5f1f1f600979">

***
### Ilias-Fragen
<img src="https://github.com/user-attachments/assets/f72de135-429b-4779-be6b-0e1ca7071061" width="500">
<img src="https://github.com/user-attachments/assets/a727eff8-2e76-441d-8fce-c186feaf834d" width="500">
<img src="https://github.com/user-attachments/assets/83abf4e2-0e35-4c3b-b329-25485fee4fcb" width="500">

***
### Aufgabe zum Verständnis der Vorlesung
Die Zufallsvariable X beschreibt die Anzahl der Haushaltsmitglieder bei einer Stichprobe und haben die Verteilung:

```r
    k   |  1   2   3   4   5
P(X = k)| 0.4 0.2 0.2 0.1 0.1
```

Beschreibe die von b) – e) gesuchten Wahrscheinlichkeiten in der Form P(...), z.B. _P(X ≤ 5) oder P(3 ≤ X ≤ 5)._

```r
a) Handelt es sich hier um eine Wahrscheinlichkeitsverteilung? 

## Ja, denn wie Wahrscheinlichkeiten ergeben aufaddiert 1. 0.4 + 0.2 + 0.2 + 0.1 + 0.1 = 1
```

```r
b) Berechne die Wahrscheinlichkeit, bei zufälliger Auswahl einen Haushalt zu erhalten, der zwischen 2 und 4 Mitglieder hat.

## P(2 ≤ X ≤ 4) = P(X = 2) + P(X = 3) + P(X = 4) = 0.2 + 0.2 + 0, 1 = 0.5
```

```r
c) Berechne die Wahrscheinlichkeit, bei zufälliger Auswahl einen Haushalt zu erhalten, der mehr als 2 Mitglieder hat.

## P(X > 2) = P(X ≥ 3) = P(X = 3) + P(X = 4) + P(X = 5) = 0.2+0.1+0.1 = 0.4
```

```r
d) Berechne die Wahrscheinlichkeit, bei zufälliger Auswahl einen Haushalt zu erhalten, der höchstens 4 Mitglieder hat.

## P(X ≤ 4) = 1 − P(X = 5) = 1 − 0.1 = 0.9
```

```r
e) Berechne die Wahrscheinlichkeit, bei zufälliger Auswahl einen Mehrpersonenhaushalt zu erhalten.

## P(X ≥ 2) = 1 − P(X = 1) = 1 − 0.4 = 0.6
```

## Woche 6 - Bedingte Wahrscheinlichkeit
### Vorlesung
* `Bedingte Wahrscheinlichkeit` = Wahrscheinlichkeit des Eintreten eines Ereignisses unter der Bedingung, dass das Eintreten eines anderen Ereignisses bereits bekannt ist.

<img src="https://github.com/user-attachments/assets/ba19c5f9-846f-48bc-ae9e-f7615cc708e8" width="700">


* `Satz von Bayes` = Wenn A und B zwei Ereignisse sind und die Wahrscheinlichkeit P(A|B) gegeben ist, kann man P(B|A) berechnen.

<img src="https://github.com/user-attachments/assets/c360e4cc-8dea-47e9-98fc-ee64ec1219b2" width="700">

```r
# Beispiel

1000 Personen haben die Krankheit (1%)
90% dieser Personen werden positiv getestet: 900 Personen
99'000 haben die Krankheit nicht
10% dieser Personen werden positiv getestet 9900
Anzahl positiv Getesteter 900+ 9900 = 10'800
Unter diesem positiv getestetem sind aber bei weitem mehr Gesunde, die fälschlicherweise postiv getestet wurden
Wahrscheinlichkeit, dass eine positiv getestete Person auch wirklich krank ist: 900/10'800 = 0.833

## Beispiel mit Bayes Theorem
P(D|+) = [P(+|D)*P(D)]/P(+) = 0.9*(0.009 + 0.001)/0.009 + 0.099 = 0.009/0.009 + 0.099 = 0.08

```

***
### Ilias-Fragen
<img src="https://github.com/user-attachments/assets/cc99e94f-f829-448e-8ebb-95c3323e0588" width="500">
<img src="https://github.com/user-attachments/assets/6f6c0982-98ce-4d74-b4a5-60c032e3e171" width="500">
<img src="https://github.com/user-attachments/assets/6c59f279-9680-4204-b458-4c49a8a904b5" width="500">

***
### Aufgabe zum Verständnis der Vorlesung
Bei einer Sportveranstaltung wird ein Dopingtest durchgeführt. Wenn ein Sportler gedopt hat, dann fällt der Test zu 99 % positiv aus. Hat ein Sportler aber nicht gedopt, zeigt der Test trotzdem zu 5 % ein positives Ergebnis an. Aus Erfahrung weiss man, dass 20 % der Sportler gedopt sind.

Bezeichnungen: D = gedopt, T = positiv getestet


P(D) = 0.2, P(T|D) = 0.99, P(T|D) = 0.05

a) Wie gross ist die Wahrscheinlichkeit, dass eine Dopingprobe positiv ausfällt?

```r
Gesucht: P(T).

## P(T) = P(T|D) · P(D) + P(T|¬D) · P(¬D)
## = P(T|D) · P(D) + P(T|¬D) · (1 − P(D))
## = 0.99 · 0.2 + 0.05 · 0.8
## = 0.238 = 23.8% 
``` 

b) Wie gross ist die Wahrscheinlichkeit, dass der Test negativ ausfällt, obwohl der Sportler gedopt hat?

```r
Gesucht: P(T|D)

## P(T|D) = 1 − P(¬T|D) = 1 − 0.99 = 0.01
```

c) Wie gross ist die Wahrscheinlichkeit, dass ein Sportler gedopt hat, falls seine Dopingprobe negativ ausgefallen ist.

```r
Gesucht: P(D|¬T)

## P(D|¬T) = P(¬T|D) · P(D)/P(¬T)
## = (0.01 · 0.2)/1 − 0.238
## = 0.00262 = 0.262%

```


## Woche 7 - Normalverteilung
### Vorlesung
* `Punktwahrscheinlichkeit` = Wahrscheinlichkeit, dass genau
eine Körpergrösse gemessen wird.

* `Wahrscheinlichkeitsdichte` = Wahrscheinlichkeit, dass ein Messwert in einem bestimmten Bereich liegt. Wahrscheinlichkeit entspricht der Fläche zwischen a und b.

<img src="https://github.com/user-attachments/assets/6f5bc973-ab58-43b3-afb1-c9d3a61fe2ed" width="700">

* `Gaussverteilung` = Anderes Wort für die Normalverteilung. 
<img src="https://github.com/user-attachments/assets/01cedd3a-1703-4631-89db-c94607e4acf6" width="200">

<img src="https://github.com/user-attachments/assets/fb8160bb-1628-429e-a174-fd91ff760d53" width="700">

***
### Ilias-Fragen
<img src="https://github.com/user-attachments/assets/cdb2a870-dcd2-4a10-8207-fa4b98b4da29" width="500">
<img src="https://github.com/user-attachments/assets/1066ece9-f281-445f-a185-3548f38a150e" width="500">

***
### Aufgabe zum Verständnis der Vorlesung
In einem Ort gibt es einige Karpfenteiche. Die Masse der Karpfen ist normalverteilt mit dem Erwartungswert µ = 4 kg und der Standardabweichung 1.25 kg.

a) Wie gross ist die Wahrscheinlichkeit, einen Karpfen zu fangen, der höchstens 2.5 kg bzw. mindestens 5 kg wiegt?

```r
Die Zufallvariable X misst das Gewicht der Karpfen. X ist dann wie folgt verteilt: X ∼ N (4,1.252^2).

Gesucht ist P(X ≤ 2.5) = 0.115.
Etwa 11 % der Karpfen wiegen weniger als 2.5 kg.

pnorm(q = 2.5, mean = 4, sd = 1.25)
## [1] 0.1150697

Gesucht ist P(X ≥ 5) = 0.212
Etwa 21 % der Karpfen wiegen mehr als 5 kg.

1 - pnorm(q = 5, mean = 4, sd = 1.25)
## [1] 0.2118554
```

b) Wie viel Prozent aller Karpfen wiegen zwischen 3 kg und 4.5 kg?

```r
Gesucht ist P(3 ≤ X ≤ 4.5) = 0.4436.
Etwa 44 % der Karpfen wiegen zwischen 3 kg und 4.5 kg.

pnorm(q = 4.5, mean = 4, sd = 1.25) - pnorm(3, 4, 1.25)
## [1] 0.4435663
```


## Woche 8 - Gesetz der grossen Zahlen
### Vorlesung
<img src="https://github.com/user-attachments/assets/58560f3e-1898-40d9-a71c-f442334f97ed" width="700">

<img src="https://github.com/user-attachments/assets/13309476-b5de-43c4-9b09-e4e0a3b88a5c" width="700">

* `Zentraler Grenzwertsatz` = Verteilung der Mittelwerte/Summen nähert sich mit wachsendem n einer Normalverteilung an. Besagt, dass sich
der Mittelwert und die Summe unabhängig und identisch verteilter Zufallsvariablen bei einer beliebigen Verteilung mit zunehmenden Stichprobenumfang der Normalverteilung annähern.

<img src="https://github.com/user-attachments/assets/52a63fb8-0c5b-4018-9797-1088f865d5e7" width="700">

<img src="https://github.com/user-attachments/assets/ac5800ee-1177-4a0a-ae31-9833ad5f25b0" width="700">

***
### Ilias-Fragen
<img src="https://github.com/user-attachments/assets/15733e7b-08aa-4f42-b4ab-6c934ea47ee3" width="500">
<img src="https://github.com/user-attachments/assets/8c2904f6-f358-4ffd-a4de-5972d380149f" width="500">
<img src="https://github.com/user-attachments/assets/0a8a5237-5127-4307-90b1-a440086fd47d" width="500">
<img src="https://github.com/user-attachments/assets/ea1e28a6-9345-4396-b978-2c6833b6f94f" width="500">

***
### Aufgabe zum Verständnis der Vorlesung
Die Zeit, die ein Passagier an einem Flughafen Check-in Schalter verbringt ist eine Zufallsvariable mit Mittelwert 8.2 Minuten und Standardabweichung 6 Minuten. Wir beobachten zufällig 36 Passgiere.

Xi ist die Zufallsvariable der Wartezeit für den i-ten Passagier. Es gilt µ = 8.2 und
σX = 6. Wir betrachten die durchschnittliche Wartezeit X36.

a) Berechnen Sie die Wahrscheinlichkeit, dass die durchschnittliche Wartezeit dieser Passagiere weniger als 10 Minuten beträgt. 
```r 
Gesucht ist: P(X36 ≤ 10) = 0.9640697

pnorm(q = 10, mean = 8.2, sd = 1)

## [1] 0.9640697
```

b) Berechnen Sie die Wahrscheinlichkeit, dass die durchschnittliche Wartezeit dieser Passagiere zwischen 5 und 10 Minuten beträgt.
```r
Gesucht ist: P(5 ≤ X36 ≤ 10) = 0.9633825

pnorm(q = 10, mean = 8,2, sd = 1) - pnorm(q = 5, 8.2, 1)

## [1] 0.9633825
```

c) Berechnen Sie die Wahrscheinlichkeit, dass die durchschnittliche Wartezeit dieser Passagiere mehr als 20 Minuten beträgt.
```r
Gesucht ist: P(X36 ≥ 20) ≈ 0

1 - pnorm(q = 20, mean = 8.2, sd = 1)

## [1] 0

## Hier wird die W’keit 0 angegeben, aber dies ist sie nicht. Sie ist nur so klein, dass sie mit 0 dargestellt wird.
```

d) Alle haben wohl schon die Erfahrung gemacht, dass man länger beim Check-in
gewartet hat. Warum ist die Wahrscheinlichkeit von c) dann so klein?
```r
## Die Wahrscheinlichkeit, dass man selber mehr als 20 Minuten warten kann, ist viel grösser.

## Die Wahrscheinlichkeit in c) beschreibt die Wahrscheinlichkeit, dass 36 zufällig beobachtete Personen durchschnittlich mehr warteten und diese ist fast 0. 

## Dass viele Personen durchschnittlich mehr als 20 Minuten warten müssen, ist kleiner als die Wahrscheinlichkeit, dass eine Person mehr als 20 Minuten warten muss.
```

## Woche 9 - Hypothesentest
### Vorlesung
* `Hypothesentest` = Wichtiges statistisches Mittel, um zu entscheiden, ob der Mittelwert einer Messreihe zu einem bestimmten wahren Mittelwert passt oder nicht.

<img src="https://github.com/user-attachments/assets/7298d6ce-354c-409c-a91b-b3ede4e78e97" width="700">

<img src="https://github.com/user-attachments/assets/6a306bb9-2559-4bdd-a71e-9f92f00bfeba" width="700">

* `z-Test` = Beim z-Test ist die Standardabweichung im Voraus bekannt.
1. Null- und Alternativhypothese aufstellen
2. Verwerfungsbereich bestimmen
3. p-Wert mit Messreihe berechnen
4. Testentscheid fällen

<img src="https://github.com/user-attachments/assets/2717c128-6810-43b7-80ca-cb3f149d5682" width="700">

```r
## Beispiel

Das Bundesamt für Statistik behauptet, dass die durchschnittliche Körpergrösse der erwachsenen Frauen in der Schweiz bei 180cm mit einer Standardabweichung von 10cm liegt. -> Einseitiger Test

Der p-Wert ist unter dem Signifikanzniveau von 0.05. Die Nullhypothese wird somit verworfen und die Alternativhypothese angenommen.
```

* `t-Test` = Beim t-Test ist die Standardabweichung im Voraus unbekannt. 

```r
## Beispiel

Es folgt eine zusätzliche Unsicherheit. Die t-Verteilung ist ähnlich der Normalverteilung, aber flacher, aufgrund der grösseren Unsicherheit.
Das Bundesamt für Statistik behauptet, dass die durchschnittliche Körpergrösse der erwachsenen Frauen in der Schweiz bei 180cm liegt. -> Einseitiger Test. 
```

<img src="https://github.com/user-attachments/assets/416b1fcb-6638-46ae-80da-dbfb155639f2" width="700">

```r
## Beispiel

Wählen zufällig 10 Frauen aus und messen deren Körpergrösse. Der p-Wert ist unter dem Signifikanzniveau von 0.05. Die Nullhypothese und wird somit verworfen und die Alternativhypothese angenommen.
```

***
### Ilias-Fragen
<img src="https://github.com/user-attachments/assets/71d204db-8027-4d8e-b2f1-8763c5ead940" width="500">
<img src="https://github.com/user-attachments/assets/e826c8e6-4b3c-40f7-a231-09ed20a09a56" width="500">

***
### Aufgabe zum Verständnis der Vorlesung
Ein Weinhändler behauptet, dass die von ihm gefüllten Weinflaschen 70 Zentiliter enthalten. Ein skeptischer Konsument vermutet aber, dass der Weinhändler zu wenig Wein abfüllt und will diese Behauptung überprüfen. Deshalb kauft er 12 Weinflaschen und misst ihren Inhalt. Er findet:

71, 69, 67, 68, 73, 72, 71, 71, 68, 72, 69, 72 (in Zentiliter)

Nehmen wir zunächst an, dass die Standardabweichung der Abfüllung im Voraus
bekannt ist. Sie beträgt σ = 1.5 Zentiliter. Da die Standardabweichung der Messungen bekannt ist, können wir einen z-Test durchführen. Führe den (einseitigen; in welche Richtung?) Test auf dem 5 %- Signifikanzniveau durch. Gebe die Modellannahmen, H0, HA, den Verwerfungsbereich, den Wert der Teststatistik und das Testergebnis explizit an. Formuliere in einem Satz die Schlussfolgerung für den kritischen Konsumenten.

<img src="https://github.com/user-attachments/assets/420f21b7-113f-4a27-956f-a1f4a2300105" width="700">

(Musterlösung. Bei einem Test nach unten zu x12 ist es schon grösser als 70.)


## Woche 10 - Vertrauenstest & Wilcoxontest
### Vorlesung
* `Wilcoxontest` = Beim Wilcoxon-Test müssen die Daten nicht normalverteilt sein. Er ist eine Alternative zum t-Test mit weniger Voraussetzungen.
Lediglich die Verteilung unter der Nullhypothese muss symmetrisch sein.

<img src="https://github.com/user-attachments/assets/f31c0d72-50cc-4a3c-91ac-ae503e81e266" width="700">

<img src="https://github.com/user-attachments/assets/e2977488-1e02-46c7-a306-7c32046c9612" width="700">

***
### Ilias-Fragen
<img src="https://github.com/user-attachments/assets/05edd222-c19a-4a17-93da-03772f561978" width="500">
<img src="https://github.com/user-attachments/assets/74ab47d1-1654-4daa-a6cc-80d4b930fb01" width="500">

***
### Aufgabe zum Verständnis der Vorlesung
Die Aufgaben für diese Wochen waren zu gross, um sie hier abzutippen, als auch eine Kombination mit den Aufgaben aus den vorherigen Wochen.

## Woche 11 - Lineare Regression
### Vorlesung
* `Lineare Regression` = Auf Basis von erklärenden Variablen (Prädiktoren) eine passende Outputvariable (Zielgrösse) finden. Durch das hinzufügen eines Fehlerterms ε (Residuen), welcher unabhängig von den Prädikatoren ist, wird das Modell zu einer Gleichung.

* `Einfache lineare Regression` = Einfaches Verfahren, um einen quantitativen Output Y auf der Basis einer einzigen Inputvariable X vorherzusagen.

```r
# Beispiel:

Für zusätzliche CHF 1’000 Werbeausgaben werden 47.5 zusätzliche Einheiten des Produktes verkauft.
Die Nullhypothese wird mit p-Wert 2*10-16 verworfen. 
Somit gibt es einen klaren Zusammenhang.
Die R2-Statistik erklärt 61.19% der Varianz durch das Modell. 
Das Modell ist somit zu 2/3 akurat.

confint(lm(Verkauf ~ TV), level = 0.95)
##                    2.5%        97.5%
## (Intercept)   6.12971927  7.93546783
## TV            0.04223072  0.05284256

Verkauf liegt ohne Werbung zwischen 6’130 und 7’935 Einheiten.
Für zusätzliche CHF 1’000 für TV-Werbung, werden durchschnittlich zwischen 42 und 53 Einheiten mehr verkauft.
```

<img src="https://github.com/user-attachments/assets/79a9971b-16df-4c61-ae39-6a344dfb93da" width="700">

***
### Ilias-Fragen
<img src="https://github.com/user-attachments/assets/14e67823-b803-4860-8cc7-9a25ae21f6b9" width="500">
<img src="https://github.com/user-attachments/assets/508880cd-71a3-4bd3-a463-09fc8ee18764" width="500">

***
### Aufgabe zum Verständnis der Vorlesung
In dieser Aufgabe verwenden wir den Datensatz `Auto`, der in der Bibliothek `ISLR` enthalten ist.
```r
library(ISLR)
Bei Fehlermeldung: install.packages("ISLR")
```
a) Untersuchen Sie den Datensatz mit `head(Auto)` und `?Auto`.

<img src="https://github.com/user-attachments/assets/e69f5cb2-59a9-40aa-8638-076078521f80" width="700">

b) Stellen Sie das Modell für eine einfache lineare Regression mit `mpg` als Zielvariable und `horsepower` als Prädiktor auf.

`mpg = β0 + β1 · horsepower`

c) Verwende den `lm()`-Befehl um die Regression durchzuführen.
Verwende den `summary()`-Befehl um die Resultate auszudrucken. Kommentiere diese Fragen:

i) Gibt es einen Zusammenhang zwischen der Zielgrösse und dem Prädiktor?

ii) Wie interpretieren sich die Koeffizienten `(intercept)` und `horsepower`?
Ist der Zusammenhang positiv oder negativ?

iii) Bestimme die Vertrauensintervalle (mit `confint()`) und interpretieren diese?

iv) Interpretiere den R^2-Wert.

<img src="https://github.com/user-attachments/assets/96cc8ea4-2cd2-4c75-a14f-40231b75b7bf" width="700">

<img src="https://github.com/user-attachments/assets/ad9399ad-32ca-4a54-a003-0bdef7c50654" width="700">

<img src="https://github.com/user-attachments/assets/303bc8fc-219c-45a8-9ad2-40122694d80c" width="700">

d) Plotte die Zielvariable und den Prädiktor mit der Regressionsgeraden `(abline)`.
Wie lässt sich dieser Plot im Vergleich zum `summary()`-Output interpretieren?

```r
plot(Auto$horsepower, Auto$mpg, pch = 16, col = "lightskyblue")
abline(lm(Auto$mpg ~ Auto$horsepower), col = "orange")
```

<img src="https://github.com/user-attachments/assets/27a43829-6d84-4e6b-86a8-67be358828d2" width="700">

Die sinkende Tendenz ist deutlich sichtbar, deshalb der tiefe p-Wert. Allerdings
fällt die Punktwolke nicht linear (schwacher R^2-Wert).

## Woche 12 - Multiple lineare Regression
### Vorlesung
* `Multiple lineare Regression` = Das multiple lineare Modell verallgemeinert das einfache lineare Modell. Jeder erklärenden Variable wird ein eigener Steigungskoeffizient in einer Gleichung zugeordnet. Graphische Darstellung nur bis zwei erklärende Variablen möglich (Ebene).
βi: Durchschnittliche Änderung der Zielgrösse bei Änderung von Xi um eine Einheit, wenn alle anderen erklärenden Variablen gleichbleiben.

<img src="https://github.com/user-attachments/assets/605970ba-9720-4c60-becd-fcdb80de386a" width="700">

```r
# Beispiel:

Steigung für Zeitung beschreibt die Änderung der Zielgrösse Verkauf,  wenn man CHF 1’000 mehr für Zeitungswerbung ausgibt, wobei die anderen erklärenden Variablen TV und Radio gleichbleiben. R2 erhöht sich, je mehr erklärende Variablen berücksichtigt werden.

cor(data.frame(TV, Radio, Zeitung, Verkauf))
##                     TV      Radio     Zeitung    Verkauf
## TV          1.00000000  0.05480866  0.05664787  0.7822244 
## Radio       0.05480866  1.00000000  0.35410375  0.5762226
## Zeitung     0.04223072  0.35410375  1.00000000  0.2282990
## Verkauf     0.78222442  0.57622257  0.22829903  1.0000000

In Märkten, wo mehr in die Werbung fürs Radio investiert wird, ist auch die Werbung für die Zeitung grösser, aufgrund des Korrelationskoeffizienten von 0.35. Aber Zeitungswerbung beeinfluss Verkäufe nicht. Zeitung schmückt sich hier mit fremden Lorbeeren, nämlich dem Erfolg von Radio auf Verkauf.
Zuerst entscheiden, ob die erklärenden Variablen Einfluss auf die Zielgrösse haben und dann ein Modell aufstellen, welches nur diese Variablen enthält. 

Interaktionseffekt: lm(medv~lstat*age)
```

<img src="https://github.com/user-attachments/assets/40be2365-5240-439f-a5bf-6d3df0d6bf9d" width="700">

***
### Ilias-Fragen
<img src="https://github.com/user-attachments/assets/b5d3b690-6538-425e-a31e-669dbd6c224d" width="500">
<img src="https://github.com/user-attachments/assets/ecdfec14-552c-4179-a9b2-44cee0127253" width="500">

***
### Aufgabe zum Verständnis der Vorlesung
Wir führen noch eine multiple lineare Regression für Auto aus der letzten Übung durch.

a) Produziere mit pairs Streudiagramme, die alle Variablen des Datensatzes
enthält.
```r
pairs(Auto.1, col = "darkseagreen")
```

<img src="https://github.com/user-attachments/assets/e7a71766-a6c8-4269-8fe3-70f81781ae54" width="700">


b) Berechne die Korrelationsmatrix zwischen den Variablen mit cor(). Dazu müssen wir zuerst die Variable `name` entfernen, da diese qualitativ ist und vor allem kaum einen Einfluss auf den Verbrauch hat. Interpretiere die Werte für `horsepower` und `displacement` mit den Streudiagrammen oben.

<img src="https://github.com/user-attachments/assets/47984c14-a611-4313-9c8d-0a159bf3611c" width="700">

```r
round(cor(Auto.1), 2)
```

<img src="https://github.com/user-attachments/assets/cf873aff-7147-49ba-b429-014bb582dfb0" width="700">

Der Korrelationskoeffizient ist 0.9. Das heisst, je grösser horsepower ist, umso grösser ist displacement. Die beiden Variablen korrelieren also. Dies ist auch aus a) ersichtlich. Das Streudiagramm zeigt deutlich einen positiven linearen Zusammenhang.
