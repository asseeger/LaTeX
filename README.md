# LaTeX 101

Autor: Andreas Seeger, asseeger@mac.com

Dieses Dokument dient nicht als vollständige Referenz sondern vielmehr als Nachschlagewerk für Lessons Learnt im Umgang mit LaTeX. Auch handelt sich um ein Dokument, das sich ständig verändert, sobald sich mir neue Erkenntnisse ergeben.

In erster Linie für mich selbst geschrieben, kann es dem einen oder anderen vielleicht auch helfen, allerdings gebe ich keine Gewähr auf Vollständigkeit, Richtigkeit oder Aktualität.

Inhalt:

- [Voraussetzungen](#voraussetzungen)
- [Aufbau](#aufbau)
- [Aufzählungen](#aufzaehlungen)
- [Abbildungen](#abbildungen)
- [Umlaute](#umlaute)



<a name="voraussetzungen"/>

## Voraussetzungen

### TeX-Umgebung

Für das Kompilieren von LaTeX-Dokumenten muss eine TeX-Umgebung installiert werden, für macOS bspw. MacTeX.
### IDE für LaTeX
Gute Erfahrungen habe ich mit dem Programm `texmaker` gemacht, welches für verschiedene Betriebssysteme zur Verfügung steht.

<a name="aufbau"/>

## Grundsätzlicher Aufbau eines LaTeX-Dokuments

### Präambel
Zu Beginn des Quellcode-Dokuments befindet sich die sog. Preamble bzw. Präambel. Hierin befinden sich u.a. Informationen zur Art des Dokuments, es werden nötige Packete eingebunden usw.
### Das Dokument
Das eigentliche Dokument wird eingeleitet durch `\begin{document}` und beendet durch `\end{document}`.
### Seitengrösse und Seitenränder


## LaTeX Dokumentklassen
Es gibt verschiedene Dokumentklassen für verschiedene Dokumentarten. Die besten Ergebnisse habe ich bis dato mit dem Dokumenttyp `scrartcl` gemacht.

Für Präsentationen bietet sich der Dokumenttyp `seminar` an.


## Kommentare
Kommentare in LaTeX werden mit `%`am Zeilenanfang deklariert:
```
%LaTeX-Kommentar
```

<a name="umlaute"/>

## Umlaute

Es ist möglich, verschiedene Packete zu verwenden.

Was jedoch grundsätzlich immer, auch ohne Einbindung von Packeten, funktioniert, ist eine direkte Anweisung, z.B.

- `\"u` für in ü usw.

## Erstellung eines Titels mit Bild
Erstellung des Titelblatts inkl. Bild
```
\title{Mein Title}
\titlehead{\centering\includegraphics[width=10cm]{Bild}}
\author{Autoren: Die Autoren}
\date{Ort, den \today{}}
```
Das so erstellte Titelblatt wird durch aufrufen von `\maketitle` in das Dokument eingefügt.

<a name="aufzaehlungen"/>

## Aufzählungen

### Nicht-nummerierte Listen
```latex
\begin{itemize}
	\item Hier kommt der Text
    \item ...
    ...
\end{itemize}
```

### Nummerierte Listen

```latex
\begin{enumerate}
	\item Hier kommt der Text
    \item ...
    ...
\end{enumerate}
```

## Zeilenumbruch nach einem `\paragraph{Paragraphbezeichnung}`
Um nach einem `\paragraph` einen Zeilenumbruch zu erzwingen, muss ein Leerzeichen durch `\mbox{}` hinzugefügt werden. Hiernach kann durch ein reguläres `\\` in einer neuen Zeile weitergeschrieben werden.

## Anführungszeichen
Für die im deutschen gebräuchlichen An- bzw. Abführungszeichen stehen in Latex eigene Befehle zur Verfügung:
- Anführungszeichen unten: ``"` ``
- Abführungszeichen oben: `"'`

<a name="abbildungen" />

## Abbildungen

### Abbildungen hinzufügen
```latex
\begin{figure}[h]
	\centering
	\includegraphics[scale=.5]{../path/to/pic}
	\caption{Beschreibung}
	\label{Verknüpfung}
\end{figure}
```
Hierbei steht der Schalter `h`für die Einbindung der Figur an der im Quelltext definierten Stelle. Wird es weggelassen, erscheint die Figur an unerwarteter Stelle.

#### Grösse der Abbildung

In der Regel bietet es sich an, die Breite der Abbildung der Textbreite anzupassen, etwa durch

```latex
\includegraphics[width=\textwidth]{patch/to/pic}
```



### Abblildungsverzeichnis anzeigen
Um eine Liste aller Abbildungen im Dokument anzuzeigen, muss der Bedehl `\listoffigures` verwendet werden.

## Quellcode anzeigen: lstlisting
Über das Einbinden des Packets `\usepackage{listings}` kann Quellcode eingebunden werden.

Damit lässt sich Quellcode über mehrere Zeilen über `\begin` und `\end` einbinden:

```latex
\begin{lstlisting}
Some sourcecode...
...
\end{lstlisting}
```

Je nach Art des Quellcodes kann auch Syntax-Highlighting definiert werden, um dies z.B. für Java zu erreichen, müssen die folgenden Zeilen in der Präambel hinzugefügt werden:

```latex
% Java Syntax highlighting Begin

\usepackage{color}

\definecolor{javared}{rgb}{0.6,0,0} % for strings

\definecolor{javagreen}{rgb}{0.25,0.5,0.35} % comments

\definecolor{javapurple}{rgb}{0.5,0,0.35} % keywords

\definecolor{javadocblue}{rgb}{0.25,0.35,0.75} % javadoc

\lstset{language=Java,

basicstyle=\ttfamily,

keywordstyle=\color{javapurple}\bfseries,

stringstyle=\color{javared},

commentstyle=\color{javagreen},

morecomment=s{/*}{/},

numbers=left,

numberstyle=\tiny\color{black},

stepnumber=1,

numbersep=10pt,

tabsize=4,

showspaces=false,

showstringspaces=false}

% Java Syntax highlighting End

```

### Verzeichnis von Listings darstellen
Ein Verzeichnis mit allen Listings im Dokument lässt sich erstellen mit `\lstlistoflistings`

## Glossar
### Das Paket `glossaries`
Fachbegriffe und Akronyme im Text lassen sich durch das Paket `glossaries` definieren:

`\usepackage[numberedsection]{glossaries}`

Der Schalter `numberedselections` führt das Glossar hierbei als nummerierte Sektion ein.

### Einen Glossareintrag definieren
Ein Glossareintrag wird grundsätzlich in der Präambel definiert:

`\newglossaryentry{umlaut}{name={Umlaut},description={Die Buchstaben ä, ö, ü}}`

### Ein Akronym definieren
Ein Akronym muss ebenfalls in der Präambel definiert werden. Hierbei lässt sich zuvor einstellen, in welcher Weise das Akronym im Text verwendet werden soll.

Die Einführung des Akronyms im Lauftext durch Ausschreiben des Begriffs, der direkt angefügten Nennung der Abkürzung in Klammern und anschliessende Nutzung der so eingeführten Abkürzung im weiteren Lauftext wird bspw. so ermöglicht:

`\setacronymstyle{long-short}`

Die eigentliche Definition des Akronyms sieht dann aus wie folgt:

```latex
\newacronym[description={Laufzeitumgebung für Java-Applikationen}]{jvm}{JVM}{Java Virtual Machine}
```
Hierbei ist `jvm` die Bezeichnung des Akronyms für die Verwendung, `JVM` die im Text genannte Abkürzung und `Java Virtual Machine` der ausgeschriebene Begriff. Als Option kann zuvorderst noch eine Beschreibung erstellt werden, dies ist jedoch optional.

Die Verwendung des Akronyms im Lauftext passiert hiernach über

`\gls{jvm}`

### Einen Glossareintrag oder ein Akronym verwenden
Einen Glossarbegriff oder ein Akronym lässt sich im Lauftext wie folgt verwenden (wie bereits oben erwähnt):

```latex
\gls{name_des_eintrags}
```
### Das Glossarverzeichnis
Das Glossarverzeichnis lässt sich an beliebiger Stelle im Dokument einbinden über den Befehl

```latex
 \printglossaries

 % bzw.

 \printnoidxglossaries
```
## Tabellen
Die einfachste Variante, eine Tabelle zu erstellen, ist es, einen Onlinegenerator hierzu zu verwenden, z.B. [www.tablesgenerator.com](http://www.tablesgenerator.com/).
### Tabellenbreite beeinflussen
Um eine Tabelle auf die ganze Seitenbreite auszudehnen, kann das Package Tabularx mit `\usepackage{tabularx}` in der Präambel eingebunden werden.
Anstelle der Zellenanweisung `l` für linksbündig, `c` für mittig oder `r` für rechtsbündig kann dann eine Zelle mit `X` definiert werden. Diese Spalte nutzt dann die verfügbare Seitenbreite aus, während die anderen Spalten so breit wie der maximale Inhalt sind.
### Zeilenumbruch in einzelner Zelle
Einen Zeilenumbruch in einer einzelnen Zelle kann über den Befehl `\newline`erreicht werden.
### Aufzählungen in Tabellen
Für Aufzählungen in Tabellen kann das Paket `booktabs` eingebunden werden, welches den Befehl `\tabitem` definieren lässt. Hierzu folgenden Code in die Präambel einfügen:

```latex
\usepackage{booktabs} %http://ctan.org/pkg/booktabs

\newcommand{\tabitem}{\llap{\textbullet}}
```
## To Do-Notizen
Mithilfe des Pakets `todonotes` können Notizen im Dokument angelegt werden, welche dann prominent erscheinen.
Über den Befehl  `\listoftodos` kann an beliebiger Stelle im Dokument eine Übersicht der To Dos eingeblendet werden.
Siehe http://www.pirbot.com/mirrors/ctan/macros/latex/contrib/todonotes/todonotes.pdf
