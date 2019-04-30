---
title: CREATE INDEX für Paradox | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX [ODBC]
- Paradox driver [ODBC], create index
ms.assetid: 6472bd69-b931-4bc2-a9bf-f1873ed4cdfe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 15e16fb311bf3c9acb2823772247e0fc16eabeef
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63232302"
---
# <a name="create-index-for-paradox"></a>CREATE INDEX für Paradox
Die Syntax der CREATE INDEX-Anweisung für den ODBC-Paradox-Treiber ist:  
  
 **Erstellen Sie** [**UNIQUE**] **INDEX** *Indexname*  
  
 **ON** *Tabellenname*  
  
 **(** *Spaltenbezeichner* [**ASC**]  
  
 [**,** *Spaltenbezeichner* [**ASC**]...] **)**  
  
 Die ODBC-Paradox-Treiber unterstützt nicht die **DESC** Schlüsselwort in der ODBC-SQL-Grammatik für die CREATE INDEX-Anweisung. Die *Tabellenname* -Argument kann den vollständigen Pfad der Tabelle angeben.  
  
 Wenn das Schlüsselwort **UNIQUE** angegeben ist, wird die ODBC-Paradox-Treiber wird einen eindeutigen Index erstellt. Der erste eindeutige Index wird als primären Index erstellt. Paradox primary Key-Datei mit dem Namen *Tabellenname*. PX. Primäre Indizes werden jedoch mit folgenden Einschränkungen:  
  
-   Der primäre Index muss erstellt werden, bevor alle Zeilen der Tabelle hinzugefügt werden.  
  
-   Ein primärer Index muss bei der ersten "n"-Spalten in einer Tabelle definiert werden.  
  
-   Es ist nur ein primärer Index pro Tabelle zulässig.  
  
-   Eine Tabelle kann nicht vom Paradox-Treiber aktualisiert werden, wenn ein primärer Index nicht für die Tabelle definiert ist. (Beachten Sie, dass dies nicht "true" für eine leere Tabelle, die aktualisiert werden kann, auch wenn Sie ein eindeutiger Index nicht für die Tabelle definiert ist.)  
  
-   Die *Indexname* Argument für einen primären Index muss identisch mit dem Basisnamen der Tabelle nach Bedarf Paradox.  
  
 Wenn das Schlüsselwort **UNIQUE** wird weggelassen, wird die ODBC-Paradox-Treiber einen nicht eindeutiger Index erstellt. Dies besteht aus zwei Paradox-sekundären Index-Dateien, die mit dem Namen *Tabellenname*. X*Nn* und *Tabellenname*. Y*Nn*, wobei *Nn* ist die Nummer der Spalte in der Tabelle. Nicht eindeutige Indizes sind jedoch mit folgenden Einschränkungen:  
  
-   Bevor ein nicht eindeutiger Index für eine Tabelle erstellt werden kann, muss ein primärer Index für die Tabelle vorhanden sein.  
  
-   Für Paradox 3. *x*, *Indexname* Argument für jeden Index als primären Index (eindeutigen oder nicht eindeutig) muss den Namen der Spalte identisch sein. Für Paradox 4. *x* und 5. *X*, der Namen des solchen Index kann sein, aber nicht den Namen der Spalte identisch sein.  
  
-   Nur eine Spalte kann für ein nicht eindeutiger Index angegeben werden.  
  
 Spalten können nicht hinzugefügt werden, nachdem ein Index für eine Tabelle definiert wurde. Wenn die erste Spalte der Argumentliste einer CREATE TABLE-Anweisung einen Index erstellt wird, kann keine zweite Spalte in der Argumentliste enthalten sein.  
  
 Verwenden Sie z. B. die Verkaufsauftragsnummer und Zahlenspalten als eindeutiger Index für die Tabelle SO_LINES Zeile, die Anweisung ein:  
  
```  
CREATE UNIQUE INDEX SO_LINES  
 ON SO_LINES (SONum, LineNum)  
```  
  
 Um die Spalte Teil als ein nicht eindeutiger Index für die Tabelle SO_LINES verwenden möchten, verwenden Sie die Anweisung ein:  
  
```  
CREATE INDEX PartNum  
 ON SO_LINES (PartNum)  
```  
  
 Beachten Sie, wenn zwei CREATE INDEX-Anweisungen ausgeführt werden, die erste Anweisung einen primären Index immer mit dem gleichen Namen wie die Tabelle erstellt und die zweite Anweisung einen nicht eindeutigen Index immer mit dem gleichen Namen wie die Spalte erstellt an. Diese Indizes werden auf diese Weise benannt werden, auch wenn unterschiedliche Namen in der CREATE INDEX-Anweisungen eingegeben werden, und selbst wenn der Index eindeutig in der zweiten CREATE INDEX-Anweisung mit der Bezeichnung.  
  
> [!NOTE]  
>  Anweisungen sind zulässig, wenn Sie die Paradox-Treiber verwenden, ohne die Implementierung der Borland-Datenbank-Engine nur lesen und anfügen.
