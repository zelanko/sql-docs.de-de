---
description: CREATE INDEX für Paradox
title: Create Index for Paradox | Microsoft-Dokumentation
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
ms.openlocfilehash: c0274f3f7cfdb79bf64e3616b16b7f3383063e07
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483643"
---
# <a name="create-index-for-paradox"></a>CREATE INDEX für Paradox
Die Syntax der CREATE INDEX-Anweisung für den ODBC-Paradox-Treiber lautet wie folgt:  
  
 **Create** [**Unique**] *INDEXIndexname* **INDEX**  
  
 **Bei** *Tabellennamen*  
  
 **(** *Spalten Bezeichner* [**ASC**]  
  
 [**,** *Spalten Bezeichner* [**ASC**]...] **)**  
  
 Der ODBC-Paradox-Treiber unterstützt das **DESC** -Schlüsselwort in der ODBC-SQL-Grammatik für die CREATE INDEX-Anweisung nicht. Das Argument *Table-Name* kann den vollständigen Pfad der Tabelle angeben.  
  
 Wenn das **Unique** -Schlüsselwort angegeben ist, erstellt der ODBC-Paradox-Treiber einen eindeutigen Index. Der erste eindeutige Index wird als primärer Index erstellt. Dies ist eine Paradox-Primärschlüssel Datei mit dem Namen " *Table-Name*". Entworfen. Primäre Indizes unterliegen den folgenden Einschränkungen:  
  
-   Der primäre Index muss erstellt werden, bevor der Tabelle Zeilen hinzugefügt werden.  
  
-   Ein primärer Index muss auf den ersten n-Spalten in einer Tabelle definiert werden.  
  
-   Pro Tabelle ist nur ein primärer Index zulässig.  
  
-   Eine Tabelle kann nicht vom Paradox-Treiber aktualisiert werden, wenn kein primärer Index in der Tabelle definiert ist. (Beachten Sie, dass dies für eine leere Tabelle nicht zutrifft, die auch dann aktualisiert werden kann, wenn für die Tabelle kein eindeutiger Index definiert ist.)  
  
-   Das *Index-Name-* Argument für einen primären Index muss mit dem Basisnamen der Tabelle übereinstimmen, wie von Paradox verlangt.  
  
 Wenn das Schlüsselwort **Unique** weggelassen wird, erstellt der ODBC-Paradox-Treiber einen nicht eindeutigen Index. Diese besteht aus zwei sekundären Paradox-Indexdateien namens " *Table-Name*". X*NN* und *Tabellenname*. J*NN*, wobei *NN* die Nummer der Spalte in der Tabelle ist. Nicht eindeutige Indizes unterliegen den folgenden Einschränkungen:  
  
-   Bevor ein nicht eindeutiger Index für eine Tabelle erstellt werden kann, muss ein primärer Index für diese Tabelle vorhanden sein.  
  
-   Für Paradox 3. *x*, das *Indexnamen* Argument für jeden anderen Index als einen primären Index (eindeutig oder nicht eindeutig) muss mit dem Spaltennamen identisch sein. Für Paradox 4. *x* und 5. *x*, der Name eines solchen Indexes kann sein, muss jedoch nicht mit dem Spaltennamen identisch sein.  
  
-   Für einen nicht eindeutigen Index kann nur eine Spalte angegeben werden.  
  
 Spalten können nicht hinzugefügt werden, nachdem ein Index für eine Tabelle definiert wurde. Wenn die erste Spalte der Argumentliste einer CREATE TABLE-Anweisung einen Index erstellt, kann keine zweite Spalte in der Argumentliste enthalten sein.  
  
 Wenn Sie z. b. die Spalten Sales Order Number und line number als eindeutigen Index für die SO_LINES Tabelle verwenden möchten, verwenden Sie die-Anweisung:  
  
```  
CREATE UNIQUE INDEX SO_LINES  
 ON SO_LINES (SONum, LineNum)  
```  
  
 Verwenden Sie die-Anweisung, um die Teilenummern Spalte als einen nicht eindeutigen Index für die SO_LINES Tabelle zu verwenden:  
  
```  
CREATE INDEX PartNum  
 ON SO_LINES (PartNum)  
```  
  
 Beachten Sie Folgendes: Wenn zwei CREATE INDEX-Anweisungen ausgeführt werden, erstellt die erste Anweisung immer einen primären Index mit dem gleichen Namen wie die Tabelle, und die zweite Anweisung erstellt immer einen nicht eindeutigen Index mit dem gleichen Namen wie die Spalte. Diese Indizes werden auf diese Weise benannt, auch wenn in den CREATE INDEX-Anweisungen verschiedene Namen eingegeben werden und der Index in der zweiten CREATE INDEX-Anweisung eindeutig bezeichnet wird.  
  
> [!NOTE]  
>  Wenn Sie den Paradox-Treiber verwenden, ohne den Borland-Datenbank-Engine zu implementieren, sind nur Lese-und Anfügen-Anweisungen zulässig.
