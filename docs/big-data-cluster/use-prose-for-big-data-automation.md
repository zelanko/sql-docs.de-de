---
title: Generieren von Code für Data Wrangling-Aufgaben
titleSuffix: Azure Data Studio
description: In diesem Artikel wird beschrieben, wie Sie den PROSE Code Accelerator in Azure Data Studio verwenden, um automatisch Code für allgemeine Data Wrangling-Aufgaben zu generieren.
author: dphansen
ms.author: davidph
ms.reviewer: mihaelab
ms.date: 10/12/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning-bdc
ms.openlocfilehash: 3357757c0cca35be0b3410795cfd89ca75f34dc3
ms.sourcegitcommit: 544706f6725ec6cdca59da3a0ead12b99accb2cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638973"
---
# <a name="data-wrangling-using-prose-code-accelerator"></a>Data Wrangling mithilfe von PROSE Code Accelerator

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Der PROSE Code Accelerator generiert lesbaren Python-Code für Ihre Data Wrangling-Aufgaben. Sie können den generierten Code mit dem handgeschriebenen Code mischen, während Sie in Azure Data Studio in einem Notebook arbeiten.

Dieser Artikel bietet eine Übersicht darüber, wie Sie den Code Accelerator verwenden können.

 > [!NOTE]
 > „Program Synthesis using Examples“ oder PROSE ist eine Microsoft-Technologie, die mithilfe von KI visuell lesbaren Code generiert. PROSE analysiert die Absicht und die Daten eines Benutzers, generiert verschiedene Kandidatenprogramme und wählt anhand von Algorithmen zur Ermittlung von Rangfolgen das beste Programm aus. Weitere Informationen zur PROSE-Technologie finden Sie auf der [PROSE-Homepage](https://microsoft.github.io/prose/).

Der Code Accelerator ist in Azure Data Studio vorinstalliert. Sie können ihn wie jedes andere Python-Paket in das Notebook importieren. Gemäß Konvention importieren wir ihn in der Kurzform „cx“.

```python
import prose.codeaccelerator as cx
```

Im aktuellen Release kann der Code Accelerator auf intelligente Weise Python-Code für die folgenden Aufgaben generieren:

- Lesen von Datendateien in einen Pandas- oder Pyspark-Dataframe
- Korrigieren von Datentypen in einem Dataframe
- Suchen nach regulären Ausdrücken, die Muster darstellen, in einer Liste mit Zeichenfolgen

Eine allgemeine Übersicht über die Code Accelerator-Methoden finden Sie in der [Dokumentation](/python/api/overview/azure/prose/intro).

## <a name="reading-data-from-a-file-to-a-dataframe"></a>Lesen von Daten aus einer Datei in einen Dataframe

Das Lesen von Dateien in einen Dataframe umfasst eine Untersuchung des Inhalts, um die richtigen Parameter zu ermitteln, die an eine Bibliothek zum Laden der Daten übergeben werden müssen.

Je nach Komplexität der Datei sind zur Identifizierung der richtigen Parameter mehrere Iterationen erforderlich.

Der PROSE Code Accelerator löst dieses Problem, indem die Struktur der Datendatei analysiert und der Code zum Laden der Datei automatisch generiert wird. Normalerweise analysiert der generierte Code die Daten richtig. Ein einigen wenigen Fällen müssen Sie den Code möglicherweise anpassen, um Ihre Anforderungen zu erfüllen.

Betrachten Sie das folgenden Beispiel:

 ```python
import prose.codeaccelerator as cx

# Call the ReadCsvBuilder builder to analyze the file content and generate code to load it
builder = cx.ReadCsvBuilder(r'C:/911.txt')

#Set target to pyspark if generating code to use pyspark library
#builder.Target = "pyspark"

#Get the code generated to fix the data types
builder.learn().code()
 ```

Der obige Codeblock gibt den folgenden Python-Code aus, um eine durch Trennzeichen getrennte Datei zu lesen. Beachten Sie, wie PROSE automatisch die Anzahl zu überspringender Zeilen, Kopfzeilen, Anführungszeichen, Trennzeichen usw. ermittelt.

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

Code Accelerator kann Code generieren, um durch Trennzeichen getrennte Dateien, JSON-Dateien sowie Dateien mit fester Breite in einen Dataframe zu laden. Zum Lesen von Dateien mit fester Breite verwendet der `ReadFwfBuilder` optional eine visuell lesbare Schemadatei, die analysiert werden kann, um die Spaltenpositionen abzurufen. Weitere Informationen finden Sie in der [Dokumentation](/python/api/overview/azure/prose/intro).

## <a name="fixing-data-types-in-a-dataframe"></a>Korrigieren von Datentypen in einem Dataframe

Pandas- oder Pyspark-Dataframes mit falschem Datentyp kommen häufiger vor. Der falsche Datentyp hat seine Ursache in einigen nicht konformen Werten in einer Spalte. Die Folge ist, dass Integer-Typen als Float- oder String-Typen oder Date-Typen als String-Typen gelesen werden. Der Aufwand für die manuelle Korrektur der Datentypen ist proportional zur Anzahl von Spalten.

In solchen Situationen können Sie den `DetectTypesBuilder` verwenden. Er analysiert die Daten und generiert Code, um die Datentypen zu korrigieren. Der Code dient als Ausgangspunkt. Sie können diesen überprüfen, verwenden oder nach Bedarf ändern.

```python
import prose.codeaccelerator as cx

builder = cx.DetectTypesBuilder(df)

#Set target to pyspark if working with pyspark
#builder.Target = "pyspark"

#Get the code generated to fix the data types
builder.learn().code()
```

Weitere Informationen finden Sie in der [Dokumentation](/python/api/overview/azure/prose/fixdatatypes).

## <a name="identifying-patterns-in-strings"></a>Identifizieren von Mustern in Zeichenfolgen

p.


|Zeile|Name                      |BirthDate      |
|--:|:-------------------------|:--------------|
| 0 |Bertram du Plessis        |1995           |
| 1 |Naiara Moravcikova        |Unknown        |
| 2 |Jihoo Spel                |2014           |
| 3 |Viachaslau Gordan Hilario |22-Apr-67      |
| 4 |Maya de Villiers          |19-Mar-60      |

Je nach Umfang und Vielfalt der Daten kann das Schreiben von regulären Ausdrücken für verschiedene Muster in der Spalte eine sehr zeitaufwendige Arbeit sein. Der `FindPatternsBuilder` ist ein leistungsstarkes Tool für die Codebeschleunigung, das das oben genannte Problem löst, indem es reguläre Ausdrücke für eine Liste von Zeichenfolgen generiert.

```python
import prose.codeaccelerator as cx

builder = cx.FindPatternsBuilder(df['BirthDate'])

#Set target to pyspark if working with pyspark
#builder.Target = "pyspark"

builder.learn().regexes
```

Für die oben genannten Daten generiert der `FindPatternsBuilder` die folgenden regulären Ausdrücke.

```
^[0-9]{2}-[A-Z][a-z]+-[0-9]{2}$
^[0-9]{2}[\s][A-Z][a-z]+[\s][0-9]{4}$
^[0-9]{4}$
^Unknown$
```

Abgesehen vom Generieren regulärer Ausdrücke kann der `FindPatternsBuilder` auch Code generieren, mit dem die Werte basierend auf den generierten regulären Ausdrücken gruppiert werden. Das Tool kann auch bestätigen, dass alle Werte in einer Spalte den generierten regulären Ausdrücken entsprechen. Weitere Informationen und andere nützliche Szenarien finden Sie in der [Dokumentation](/python/api/overview/azure/prose/findpatterns).