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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1676af6216ac703e9a8976951ec2888b9e940b67
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085521"
---
# <a name="insert-statement-limitations"></a>Einschränkungen der INSERT-Anweisung
Eingefügte Daten ist auf der rechten Seite ohne Warnung abgeschnitten, wenn sie in der Spalte passt zu lang ist.  
  
 Es wird versucht, einen Wert einzufügen, der außerhalb des Bereichs des Datentyps einer Spalte bewirkt, dass NULL in der Spalte eingefügt werden soll.  
  
 Wenn eine dBASE, Microsoft Excel, Paradox oder Textdriver verwendet wird, fügt eine Zeichenfolge der Länge 0 (null) in eine Spalte einfügen tatsächlich ein NULL-Wert stattdessen.  
  
 Wenn der Microsoft Excel-Treiber, verwendet wird Wenn eine leere Zeichenfolge in eine Spalte eingefügt wird, wird die leere Zeichenfolge in NULL konvertiert. eine komplexe SELECT-Anweisung, die mit einer leeren Zeichenfolge in der WHERE-Klausel ausgeführt wird, ist für die betreffende Spalte nicht erfolgreich.  
  
 Eine Tabelle kann nicht aktualisiert, durch die Paradox-Treiber unter zwei Bedingungen:  
  
-   Wenn ein eindeutiger Index nicht für die Tabelle definiert ist. Dies gilt nicht für eine leere Tabelle, die mit einer einzelnen Zeile aktualisiert werden kann, auch wenn Sie ein eindeutiger Index nicht für die Tabelle definiert ist. Wenn eine einzelne Zeile in eine leere Tabelle, die nicht über einen eindeutigen Index verfügt eingefügt wird, kann eine Anwendung kann keinen eindeutigen Index erstellen oder fügen Sie zusätzliche Daten, nachdem die einzelne Zeile eingefügt wurde.  
  
-   Wenn die Datenbank-Engine für Borland nicht implementiert wird, nur lesen, und fügen Sie Anweisungen für die Paradox-Tabelle zulässig sind.  
  
 Wenn der Text-Treiber verwendet wird, wird NULL-Werte werden durch eine Zeichenfolge mit Leerzeichen aufgefüllt, in Dateien mit fester Länge dargestellt, aber durch keine Leerzeichen im durch Trennzeichen getrennte Dateien dargestellt werden. Beispielsweise ist in der folgenden Zeile, die drei Felder enthält, das zweite Feld einen NULL-Wert auf:  
  
```  
"Smith:,, 123  
```  
  
 Wenn der Text-Treiber verwendet wird, können alle Spaltenwerte werden mit führenden Leerzeichen aufgefüllt. Die Länge einer Zeile muss kleiner als oder gleich 65,543 Bytes sein.
