# Bachelorthesis LATEX-Vorlage

Bachelorthesis nach dem geforderten Format der FH Münster, des Fachbereichs Wirtschaft, Studiengang Wirtschaftsinformatik. Einfach anzupassen. Keine unnötigen Dependencies.

## Vorbereitungen

`brew cask install mactex`

## Benutzung

Nach dem clonen einfach: `pdflatex thesis && biber thesis && pdflatex thesis` ausführen und glücklich sein.

## Empfehlungen

- Literaturverwaltungsprogramm **JabRef**, welches das Hinzufügen von neuen Büchern mittels ISBN vereinfacht. Dennoch müssen manchmal manuell Änderungen vorgenommen werden. Einfach die Datei `literatur.bib` öffnen und mittels *Library → New Entry → ID-Type: ISBN → Generate* neue Bücher hinzufügen. Installation durch `brew cask install jabref`
- VS Code Addon: <a href="https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop">LaTeX Workshop von James Yu</a>

Wenn die settings.json wie nachfolgend angepasst wird, wird das Latex Dokument damit beim Speichern automatisch kompilliert und kann in Visual Studio Code angezeigt werden:

```
{
    "telemetry.enableTelemetry": false,
    "latex-workshop.view.pdf.viewer": "tab",
    "latex-workshop.latex.recipes":[
        {
            "name": "pdflatex ➞ biber ➞ pdflatex",
            "tools": [
                "pdflatex",
                "biber",
                "pdflatex"
            ]
        }
    ],
    "latex-workshop.latex.tools":[
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
            ],
            "env": {}
        },
        {
            "name": "biber",
            "command": "biber",
            "args": [
                "%DOCFILE%"
            ],
            "env": {}
        }
    ]
}
```

## Latex Hilfen

### Abbildung
```
\begin{figure}[h]
    \centering
    \includegraphics[width=\textwidth]{<Verzeichnis>/<Dateiname ohne Dateiendung>}
    \caption[<Abbildungsbeschriftung>]{<Abbildungsbeschriftung> \cite[S.<Seitennr>]{<Author>:<Titelkürzel>}}
\end{figure}
```
### Tabelle
```
\begin{table}[h]
    \centering
    \caption[<Tabellenbeschriftung>]{Tabellenbeschriftung \cite[S.<Seitennr>]{<Author>:<Titelkürzel>}}
    \begin{tabular}[t]{lcc}
        \hline
        &<Überschrift 1>&<Überschrift 2>\\
        \hline
        <Zeile 1, Spalte 1>&<Zeile 1, Spalte 2>&<Zeile 1, Spalte 3>\\
        <Zeile 2, Spalte 1>&<Zeile 2, Spalte 2>&<Zeile 2, Spalte 3>\\
        <Zeile 3, Spalte 1>&<Zeile 3, Spalte 2>&<Zeile 3, Spalte 3>\\
        \hline
    \end{tabular}
\end{table}%
```
### Literaturverweis

`\cite[S.<Seitennr>]{<Author>:<Titelkürzel>}`