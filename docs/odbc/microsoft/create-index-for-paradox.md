---
title: CREATE INDEX für Paradox | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2e68484efdc5194f93f2acab31973377d9c66f1c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280910"
---
# <a name="create-index-for-paradox"></a>CREATE INDEX für Paradox
Die Syntax der CREATE INDEX-Anweisung für den ODBC Paradox-Treiber lautet:  
  
 **CREATE** [**UNIQUE**] **INDEX** *Indexname*  
  
 **ON** *ON-Tabellenname*  
  
 **(** *Spaltenbezeichner* [**ASC**]  
  
 [**,** *Spaltenbezeichner* [**ASC**]...] **)**  
  
 Der ODBC Paradox-Treiber unterstützt das **DESC-Schlüsselwort** in der ODBC SQL-Grammatik für die CREATE INDEX-Anweisung nicht. Das *Argument "Tabellenname"* kann den vollständigen Pfad der Tabelle angeben.  
  
 Wenn das Schlüsselwort **UNIQUE** angegeben ist, erstellt der ODBC Paradox-Treiber einen eindeutigen Index. Der erste eindeutige Index wird als primärer Index erstellt. Dies ist eine Paradox Primärschlüsseldatei mit dem Namen *"Tabellenname """"* Pixel. Primäre Indizes unterliegen den folgenden Einschränkungen:  
  
-   Der primäre Index muss erstellt werden, bevor der Tabelle Zeilen hinzugefügt werden.  
  
-   Ein primärer Index muss für die ersten "n"-Spalten in einer Tabelle definiert werden.  
  
-   Pro Tabelle ist nur ein Primärindex zulässig.  
  
-   Eine Tabelle kann vom Paradox-Treiber nicht aktualisiert werden, wenn kein primärer Index für die Tabelle definiert ist. (Beachten Sie, dass dies nicht für eine leere Tabelle gilt, die aktualisiert werden kann, auch wenn ein eindeutiger Index nicht für die Tabelle definiert ist.)  
  
-   Das *Indexnamenargument* für einen primären Index muss mit dem Basisnamen der Tabelle identisch sein, wie von Paradox gefordert.  
  
 Wenn das Schlüsselwort **UNIQUE** weggelassen wird, erstellt der ODBC Paradox-Treiber einen nicht eindeutigen Index. Diese besteht aus zwei sekundären Paradox-Indexdateien mit dem Namen *table-name*. X*nn* und *Tabellenname*. Y*nn*, wobei *nn* die Nummer der Spalte in der Tabelle ist. Nicht eindeutige Indizes unterliegen den folgenden Einschränkungen:  
  
-   Bevor ein nicht eindeutiger Index für eine Tabelle erstellt werden kann, muss für diese Tabelle ein primärer Index vorhanden sein.  
  
-   Für Paradox 3. *x*muss das *Indexnamenargument* für einen anderen Index als einen primären Index (eindeutig oder nicht eindeutig) mit dem Spaltennamen identisch sein. Für Paradox 4. *x* und 5. *x*, der Name eines solchen Indexes kann, muss aber nicht derselbe sein wie der Spaltenname.  
  
-   Für einen nicht eindeutigen Index kann nur eine Spalte angegeben werden.  
  
 Spalten können nicht hinzugefügt werden, nachdem ein Index für eine Tabelle definiert wurde. Wenn die erste Spalte der Argumentliste einer CREATE TABLE-Anweisung einen Index erstellt, kann eine zweite Spalte nicht in die Argumentliste aufgenommen werden.  
  
 Verwenden Sie beispielsweise die Anweisung, um die Spalten Auftragsnummer und Zeilennummer als eindeutigen Index für die Tabelle SO_LINES zu verwenden:  
  
```  
CREATE UNIQUE INDEX SO_LINES  
 ON SO_LINES (SONum, LineNum)  
```  
  
 Um die Spalte "Teilenummer" als nicht eindeutigen Index für die SO_LINES-Tabelle zu verwenden, verwenden Sie die Anweisung:  
  
```  
CREATE INDEX PartNum  
 ON SO_LINES (PartNum)  
```  
  
 Beachten Sie, dass bei der Ausgeführtwerden zweiER CREATE INDEX-Anweisungen immer ein primärer Index mit demselben Namen wie die Tabelle erstellt wird und die zweite Anweisung immer einen nicht eindeutigen Index mit demselben Namen wie die Spalte erstellt. Diese Indizes werden auf diese Weise benannt, auch wenn in den CREATE INDEX-Anweisungen unterschiedliche Namen eingegeben werden und der Index in der zweiten CREATE INDEX-Anweisung als UNIQUE bezeichnet wird.  
  
> [!NOTE]  
>  Wenn Sie den Paradox-Treiber verwenden, ohne die Borland Database Engine zu implementieren, sind nur Lese- und Anhängensanweisungen zulässig.
