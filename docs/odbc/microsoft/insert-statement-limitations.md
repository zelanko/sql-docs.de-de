---
title: Einschränkungen der INSERT-Anweisung | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300004"
---
# <a name="insert-statement-limitations"></a>Einschränkungen der INSERT-Anweisung
Eingefügte Daten werden auf der rechten Seite ohne Warnung abgeschnitten, wenn Sie zu lang ist, um in die Spalte zu passen.  
  
 Der Versuch, einen Wert, der außerhalb des Bereichs des Datentyps einer Spalte liegt, einzufügen, bewirkt, dass ein NULL-Wert in die Spalte eingefügt wird.  
  
 Wenn eine dBASE, Microsoft Excel, Paradox oder textdriver verwendet wird, fügt eine Zeichenfolge der Länge 0 (null) in eine Spalte ein, stattdessen wird stattdessen ein NULL-Wert eingefügt.  
  
 Wenn der Microsoft Excel-Treiber verwendet wird und eine leere Zeichenfolge in eine Spalte eingefügt wird, wird die leere Zeichenfolge in einen NULL-Wert konvertiert. eine gesuchte SELECT-Anweisung, die mit einer leeren Zeichenfolge in der WHERE-Klausel ausgeführt wird, ist für diese Spalte nicht erfolgreich.  
  
 Eine Tabelle kann von dem Paradox-Treiber unter zwei Bedingungen nicht aktualisiert werden:  
  
-   Wenn für die Tabelle kein eindeutiger Index definiert ist. Dies gilt nicht für eine leere Tabelle, die mit einer einzelnen Zeile aktualisiert werden kann, auch wenn für die Tabelle kein eindeutiger Index definiert ist. Wenn eine einzelne Zeile in eine leere Tabelle eingefügt wird, die nicht über einen eindeutigen Index verfügt, kann eine Anwendung keinen eindeutigen Index erstellen oder zusätzliche Daten einfügen, nachdem die einzelne Zeile eingefügt wurde.  
  
-   Wenn die Borland-Datenbank-Engine nicht implementiert ist, sind nur die Anweisungen "lesen" und "anfügen" in der Tabelle "Paradox" zulässig.  
  
 Wenn der Text Treiber verwendet wird, werden NULL-Werte in Dateien mit fester Länge durch eine leere, aufgefüllte Zeichenfolge dargestellt, aber in durch Trennzeichen getrennten Dateien ohne Leerzeichen dargestellt. In der folgenden Zeile, die drei Felder enthält, ist das zweite Feld z. b. ein NULL-Wert:  
  
```  
"Smith:,, 123  
```  
  
 Wenn der Text Treiber verwendet wird, können alle Spaltenwerte mit führenden Leerzeichen aufgefüllt werden. Die Länge einer Zeile muss kleiner oder gleich 65.543 Bytes sein.
