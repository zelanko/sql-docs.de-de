---
title: Generieren von Code für die Data wrangling-Aufgaben
titleSuffix: Azure Data Studio
description: Dieser Artikel beschreibt, wie Sie den Code-Accelerator PROSE in Studio für Azure Data zu verwenden, zum automatischen Generieren von Code für common Data wrangling-Aufgaben.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 4d13d200bf331771b0f2f8735bf2c76c1f227979
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241651"
---
# <a name="data-wrangling-using-prose-code-accelerator"></a>Daten-Wrangling mit PROSE Code Accelerator

PROSE Code Accelerator generiert lesbaren Python-Code für Ihre Data wrangling-Aufgaben. Sie können den generierten Code mit Ihrem handgeschriebenem Code auf nahtlose Weise kombinieren, bei der Arbeit in einem Notizbuch in Studio für Azure Data. Dieser Artikel enthält einen Überblick darüber, wie Sie den Code-Accelerator verwenden können.

 > [!NOTE]
 > Synthesis using Examples programmieren, auch bekannt als PROSE, ist eine Microsoft-Technologie, die lesbaren Code, die Verwendung von AI generiert. Dies erfolgt durch Analysieren eines Benutzers Absicht als auch Daten, mehrere Kandidaten-Programme zu generieren und das beste Programm mit Rangfolge Algorithmen auswählen. Um mehr über das PROSE-Technologie zu erfahren, besuchen Sie die [PROSE Homepage](https://microsoft.github.io/prose/).

Die Zugriffstaste Code ist vorinstalliert mit Azure Data Studio. Sie können es wie jedes andere Python-Paket im Notebook importieren. Gemäß der Konvention importieren wir sie als Cx kurz an.

```python
import prose.codeaccelerator as cx
```

In der aktuellen Version können den Code-Accelerator auf intelligente Weise Python-Code für die folgenden Aufgaben generieren:

- Lesen von Datendateien auf einen Pandas oder Pyspark-Dataframe.
- Beheben von Datentypen in einen Datenrahmen.
- Suchen von regulären Ausdrücken, die Muster in einer Liste von Zeichenfolgen darstellt.

Eine allgemeine Übersicht über Code Accelerator-Methoden finden Sie unter den [Dokumentation](https://aka.ms/prose-codeaccelerator-overview).

## <a name="reading-data-from-a-file-to-a-dataframe"></a>Lesen von Daten aus einer Datei in einen dataframe

Häufig umfasst das Lesen von Dateien in einen Dataframe Blick auf den Inhalt der Datei, und bestimmen die richtigen Parameter an eine Bibliothek Laden von Daten übergeben. Je nach Komplexität der Datei erfordern identifizieren die richtigen Parameter mehrere Iterationen.

PROSE Code Accelerator löst dieses Problem durch Analysieren der Struktur der Datendatei und die automatische Generierung von Code aus, um die Datei zu laden. Der generierte Code analysiert die Daten in den meisten Fällen korrekt aus. In einigen Fällen müssen Sie den Code, um Ihre Anforderungen anpassen.

Betrachten Sie das folgende Beispiel:

 ```python
import prose.codeaccelerator as cx

# Call the ReadCsvBuilder builder to analyze the file content and generate code to load it
builder = cx.ReadCsvBuilder(r'C:/911.txt')

#Set target to pyspark if generating code to use pyspark library
#builder.Target = "pyspark"

#Get the code generated to fix the data types
builder.learn().code()
 ```

Im vorherigen Codeblock gibt den folgenden Python-Code zum Lesen einer durch Trennzeichen getrennten Datei aus. Beachten Sie, wie Text, der die Anzahl der Zeilen, die zu überspringen, Header, Quotechars, Trennzeichen usw. automatisch ermittelt.

 ```python
import pandas as pd

def read_file(file):
    names = ["lat",
             "lng",
             "desc",
             "zip",
             "title"]

    df = pd.read_csv(file,
        skiprows = 11,
        header = None,
        names = names,
        quotechar = "\"",
        delimiter = "|",
        index_col = False,
        dtype = str,
        na_values = [],
        keep_default_na = False,
        skipinitialspace = True)
    return df
 ```

Code-Accelerator kann Code zum Laden, die als Trennzeichen und JSON-Dateien mit fester Breite in einen Dataframe generiert. Für das Lesen von Dateien mit fester Breite, die `ReadFwfBuilder` optional kann eine lesbare Schemadatei, die sie analysieren können, um die Position der Spalte abzurufen. Weitere Informationen finden Sie unter den [Dokumentation](https://aka.ms/prose-codeaccelerator-docs).

## <a name="fixing-data-types-in-a-dataframe"></a>Beheben von Datentypen in einen Datenrahmen

Es ist üblich, die ein Pandas haben oder Pyspark-Datenrahmen mit falschen Datentypen. Häufig dies geschieht aufgrund von ein Paar nicht konforme Werte in einer Spalte. Daher werden ganze Zahlen als "float" oder Zeichenfolgen gelesen und Datumsangaben als Zeichenfolgen gelesen werden. Der Aufwand zur manuell korrigieren, die Datentypen ist proportional zur Anzahl der Spalten.

Sie können die `DetectTypesBuilder` in diesen Situationen. Es analysiert die Daten, und anstatt die Datentypen in einer Weise Black-Box-, generiert Code für die Datentypen beheben. Der Code dient als Ausgangspunkt. Sie können überprüfen, verwenden oder ändern ihn nach Bedarf.

```python
import prose.codeaccelerator as cx

builder = cx.DetectTypesBuilder(df)

#Set target to pyspark if working with pyspark
#builder.Target = "pyspark"

#Get the code generated to fix the data types
builder.learn().code()
```

Weitere Informationen finden Sie unter den [Dokumentation](https://aka.ms/prose-codeaccelerator-fixtypes).

## <a name="identifying-patterns-in-strings"></a>Identifizieren von Mustern in Zeichenfolgen

Ein weiteres gängiges Szenario ist zum Erkennen von Mustern in einer Zeichenfolgenspalte zum Bereinigen oder gruppieren. Angenommen, Sie eine Datumsspalte mit Datumsangaben in mehreren verschiedenen Formaten möglicherweise. Um die Werte zu standardisieren, empfiehlt es sich beim Schreiben von bedingten Anweisungen, die mithilfe von regulären Ausdrücken.


|   |Name                      |BirthDate      |
|---|:-------------------------|:--------------|
| 0 |Bertram du Plessis        |1995           |
| 1 |Naiara Moravcikova        |Unknown        |
| 2 |Jihoo Spel                |2014           |
| 3 |Viachaslau Gordan Hilario |22-Apr-67      |
| 4 |Maya de Villiers          |19-Mar-60      |

Je nach Volume und Vielfalt in Daten kann das Schreiben von regulären Ausdrücken, die für verschiedene Muster in der Spalte eine sehr viel Zeit beanspruchen Aufgabe sein. Die `FindPatternsBuilder` ist ein Tool, Beschleunigung von Code, die das oben genannte Problem löst, indem Sie reguläre Ausdrücke für eine Liste von Zeichenfolgen generieren.

```python
import prose.codeaccelerator as cx

builder = cx.FindPatternsBuilder(df['BirthDate'])

#Set target to pyspark if working with pyspark
#builder.Target = "pyspark"

builder.learn().regexes
```

Hier sind die regulären Ausdrücke, die von generiert die `FindPatternsBuilder` für die zuvor genannten Daten.

```
^[0-9]{2}-[A-Z][a-z]+-[0-9]{2}$
^[0-9]{2}[\s][A-Z][a-z]+[\s][0-9]{4}$
^[0-9]{4}$
^Unknown$
```

Abgesehen von regulären Ausdrücken, generieren `FindPatternsBuilder` können auch Code für das clustering die Werte, die basierend auf den generierten Regexes generieren. Sie können auch bestätigen, dass alle Werte in einer Spalte in der generierten reguläre Ausdrücke entsprechen. Erfahren mehr, und finden Sie unter anderen Szenarios nützlich, finden Sie unter den [Dokumentation](https://aka.ms/prose-codeaccelerator-findpatterns).
