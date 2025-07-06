# PDF-Erstellung und Druck

Dieses Dokument erklärt, wie Sie die Inhalte dieses Repositories als PDF oder gedruckte Version erstellen können.

## Option 1: Über GitHub Pages (empfohlen)

Die einfachste Methode, um eine PDF-Version zu erstellen:

1. Besuchen Sie die GitHub Pages-Version des Projekts: `https://[IhrUsername].github.io/Autismus/de/`
2. Drücken Sie `Strg+P` (Windows/Linux) oder `Cmd+P` (Mac)
3. Wählen Sie "Als PDF speichern" im Druckdialog
4. Passen Sie die Einstellungen wie gewünscht an (Randeinstellungen, Hintergrundgrafiken aktivieren)
5. Klicken Sie auf "Speichern"

## Option 2: Mit VS Code und Pandoc (für Entwickler)

Für fortgeschrittene Anwender mit installiertem [Pandoc](https://pandoc.org/):

1. Verwenden Sie die integrierten VS Code-Tasks:
   - Öffnen Sie die zu konvertierende Markdown-Datei
   - Drücken Sie `Strg+Shift+P` (Windows/Linux) oder `Cmd+Shift+P` (Mac)
   - Wählen Sie "Tasks: Run Task" und dann:
      - "Markdown to PDF" für PDF-Ausgabe
      - "Markdown to Word" für DOCX-Ausgabe

2. Alternativ können Sie die folgenden Befehle in der Powershell ausführen:

```powershell
# Für PDF
pandoc "d:\Entwicklung\Autismus\docs\de\index.md" -o "d:\Entwicklung\Autismus\export\Autismus-Sensorik-Modell.pdf"

# Für Word-Dokument
pandoc "d:\Entwicklung\Autismus\docs\de\index.md" -o "d:\Entwicklung\Autismus\export\Autismus-Sensorik-Modell.docx"
```

## Option 3: Zusammengeführte PDF-Version aller Kapitel

Um eine zusammengeführte PDF-Version aus den einzelnen Kapiteldateien zu erstellen:

```powershell
$chapters = @(
    "d:\Entwicklung\Autismus\docs\de\chapters\01-einleitung.md",
    "d:\Entwicklung\Autismus\docs\de\chapters\02-diagnostik.md",
    "d:\Entwicklung\Autismus\docs\de\chapters\03-sensorik.md",
    "d:\Entwicklung\Autismus\docs\de\chapters\04-emergenz.md",
    "d:\Entwicklung\Autismus\docs\de\chapters\05-forschung.md",
    "d:\Entwicklung\Autismus\docs\de\chapters\06-modell.md",
    "d:\Entwicklung\Autismus\docs\de\chapters\07-schluss.md"
)

pandoc $chapters -o "d:\Entwicklung\Autismus\export\Autismus-Sensorik-Modell-Kapitel.pdf"
```

## Hinweise zur Formatierung

- Die Kapitellinks in den PDF-Versionen werden nicht funktionieren
- Für die beste Formatierung können Sie eine CSS-Datei erstellen und mit `-c style.css` beim Pandoc-Befehl verwenden
- Für anspruchsvollere Formatierung können Sie LaTeX-Vorlagen verwenden
