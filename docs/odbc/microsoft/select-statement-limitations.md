---
title: EINSCHRÄNKUNGEN der SELECT-Anweisung | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d91e93076a67287cbbd2b64b2ad0d6414a0aea6d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300920"
---
# <a name="select-statement-limitations"></a>Einschränkungen der SELECT-Anweisung
Eine Aggregat-Funktionsspalte kann nicht mit einer nicht aggregierten Spalte in einer SELECT-Anweisung gemischt werden.  
  
 Die Auswahlliste einer SELECT-Anweisung mit einer GROUP BY-Klausel kann nur Ausdrücke aus der GROUP BY-Klausel oder Set-Funktionen enthalten.  
  
 Die Verwendung eines Sternchens (zum Auswählen aller Spalten) in einer SELECT-Anweisung, die eine GROUP BY-Klausel enthält, wird nicht unterstützt. Die Namen der auszuwählenden Spalten müssen angegeben werden.  
  
 Die Verwendung einer vertikalen Leiste in einer SELECT-Anweisung wird nicht unterstützt. Verwenden Sie einen Parameter in der SELECT-Anweisung, wenn Sie auf einen Datenwert verweisen müssen, der einen vertikalen Balken enthält.  
  
 Wenn Sie einen Spaltenalias in einer SELECT-Anweisung verwenden, muss das Wort "as" dem Alias vorausgehen. Beispiel: "SELECT col1 as a from b." Ohne das "as" gibt die Anweisung einen Fehler zurück.  
  
 Wenn ein falscher Spaltenname in eine SELECT-Anweisung eingegeben wird, wird anstelle des SQLSTATE S0022-Fehlers "Spalte nicht gefunden" der SQLSTATE 07001-Fehler "Falsche Anzahl von Parametern" zurückgegeben.  
  
 Wenn der Microsoft Excel-Treiber verwendet wird und eine leere Zeichenfolge in eine Spalte eingefügt wird, wird die leere Zeichenfolge in einen NULL-Wert konvertiert. Eine durchsuchte SELECT-Anweisung, die mit einer leeren Zeichenfolge in der WHERE-Klausel ausgeführt wird, ist für diese Spalte nicht erfolgreich.
