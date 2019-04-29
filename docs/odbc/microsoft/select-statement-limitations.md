---
title: Einschränkungen der SELECT-Anweisung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, SELECT statement limitations
- SELECT statement limitations [ODBC]
ms.assetid: c6b05955-f8fd-4706-a1a7-a8dbd74870c2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26bf17596dbd3279498df2edcee7636db95ae139
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63127855"
---
# <a name="select-statement-limitations"></a>Einschränkungen der SELECT-Anweisung
Eine Aggregatfunktion Spalte kann nicht mit einer nicht-Aggregatspalte in einer SELECT-Anweisung kombiniert werden.  
  
 Die Auswahlliste einer SELECT-Anweisung, die eine GROUP BY-Klausel kann nur Ausdrücke aus der GROUP BY-Klausel haben oder Funktionen festlegen.  
  
 Die Verwendung der ein Sternchen (um alle Spalten auswählen) in einer SELECT-Anweisung mit einer GROUP BY-Klausel wird nicht unterstützt. Die Namen der Spalten ausgewählt werden, müssen angegeben werden.  
  
 Die Verwendung eines vertikalen Balkens in einer SELECT-Anweisung wird nicht unterstützt. Verwenden Sie einen Parameter in der SELECT-Anweisung, wenn Sie müssen auf einen Datenwert verweisen, einen senkrechter Strich enthält.  
  
 Wenn Sie einen Spaltenalias in einer SELECT-Anweisung verwenden zu können, muss für das Wort "as" den Alias vorangestellt sein. Z. B. "SELECT" col1 "als einer von b." Ohne das "wie" wird die Anweisung einen Fehler zurück.  
  
 Wenn ein falsche Spaltennamen in einer SELECT-Anweisung eingegeben wird, wird ein SQLSTATE 07001-Fehler "Falsche Anzahl von Parametern," zurückgegeben statt eines Fehlers SQLSTATE S0022 "-Spalte nicht gefunden."  
  
 Wenn der Microsoft Excel-Treiber, verwendet wird Wenn eine leere Zeichenfolge in eine Spalte eingefügt wird, wird die leere Zeichenfolge in NULL konvertiert. eine komplexe SELECT-Anweisung, die mit einer leeren Zeichenfolge in der WHERE-Klausel ausgeführt wird, ist für die betreffende Spalte nicht erfolgreich.
