---
title: INSERT-Anweisungsbeschränkungen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, INSERT statement limitations
- INSERT statement limitations [ODBC]
- truncation of data [ODBC]
ms.assetid: dea05698-527a-41ab-8729-bbed85556185
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f903f15ec13baa28a789891c1527dc742daa68ac
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300004"
---
# <a name="insert-statement-limitations"></a>Einschränkungen der INSERT-Anweisung
Eingefügte Daten werden auf der rechten Seite ohne Warnung abgeschnitten, wenn sie zu lang sind, um in die Spalte zu passen.  
  
 Wenn Versucht wird, einen Wert einzufügen, der aneben aneben ist, um den Datentyp einer Spalte zu erreichen, wird ein NULL in die Spalte eingefügt.  
  
 Wenn ein dBASE, Microsoft Excel, Paradox oder Textdriver verwendet wird, fügt das Einfügen einer Zeichenfolge mit null Länge in eine Spalte stattdessen einen NULL-Wert ein.  
  
 Wenn der Microsoft Excel-Treiber verwendet wird und eine leere Zeichenfolge in eine Spalte eingefügt wird, wird die leere Zeichenfolge in einen NULL-Wert konvertiert. Eine durchsuchte SELECT-Anweisung, die mit einer leeren Zeichenfolge in der WHERE-Klausel ausgeführt wird, ist für diese Spalte nicht erfolgreich.  
  
 Eine Tabelle ist vom Paradox-Treiber unter zwei Bedingungen nicht aufrüstbar:  
  
-   Wenn ein eindeutiger Index in der Tabelle nicht definiert ist. Dies gilt nicht für eine leere Tabelle, die mit einer einzelnen Zeile aktualisiert werden kann, auch wenn kein eindeutiger Index für die Tabelle definiert ist. Wenn eine einzelne Zeile in eine leere Tabelle eingefügt wird, die keinen eindeutigen Index hat, kann eine Anwendung keinen eindeutigen Index erstellen oder zusätzliche Daten einfügen, nachdem die einzelne Zeile eingefügt wurde.  
  
-   Wenn die Borland Database Engine nicht implementiert ist, sind nur Lese- und Anfügenanweisungen in der Paradox-Tabelle zulässig.  
  
 Wenn der Texttreiber verwendet wird, werden NULL-Werte durch eine Zeichenfolge mit leerer Aufgeponen in Dateien mit fester Länge dargestellt, aber durch keine Leerzeichen in durchTrennkörper getrennten Dateien dargestellt. In der folgenden Zeile, die drei Felder enthält, ist das zweite Feld beispielsweise ein NULL-Wert:  
  
```  
"Smith:,, 123  
```  
  
 Wenn der Texttreiber verwendet wird, können alle Spaltenwerte mit führenden Leerzeichen aufgepolstert werden. Die Länge einer Zeile muss kleiner oder gleich 65.543 Bytes sein.
