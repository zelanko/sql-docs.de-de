---
title: Einschränkungen für die SELECT-Anweisung | Microsoft-Dokumentation
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
ms.openlocfilehash: 0cde0158e72d1e24c112c8e7955f0d6b317bd729
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67987853"
---
# <a name="select-statement-limitations"></a>Einschränkungen der SELECT-Anweisung
Eine Aggregat Funktions Spalte kann nicht mit einer nicht aggregierten Spalte in einer SELECT-Anweisung gemischt werden.  
  
 Die SELECT-Liste einer SELECT-Anweisung mit einer Group By-Klausel kann nur Ausdrücke aus der Group By-Klausel oder Set-Funktionen enthalten.  
  
 Die Verwendung eines Sternchen (zum Auswählen aller Spalten) in einer SELECT-Anweisung, die eine Group By-Klausel enthält, wird nicht unterstützt. Die Namen der auszuwählenden Spalten müssen angegeben werden.  
  
 Die Verwendung eines vertikalen Balkens in einer SELECT-Anweisung wird nicht unterstützt. Verwenden Sie einen Parameter in der SELECT-Anweisung, wenn Sie auf einen Datenwert verweisen müssen, der einen senkrechten Strich enthält.  
  
 Wenn ein Spaltenalias in einer SELECT-Anweisung verwendet wird, muss das Wort "as" dem Alias vorangestellt sein. Beispiel: "SELECT Col1 as a from b". Ohne das "as" gibt die Anweisung einen Fehler zurück.  
  
 Wenn ein falscher Spaltenname in eine SELECT-Anweisung eingegeben wird, wird der SQLSTATE 07001-Fehler "falsche Anzahl von Parametern" anstelle eines SQLSTATE-S0022-Fehlers zurückgegeben, "Spalte nicht gefunden".  
  
 Wenn der Microsoft Excel-Treiber verwendet wird und eine leere Zeichenfolge in eine Spalte eingefügt wird, wird die leere Zeichenfolge in einen NULL-Wert konvertiert. eine gesuchte SELECT-Anweisung, die mit einer leeren Zeichenfolge in der WHERE-Klausel ausgeführt wird, ist für diese Spalte nicht erfolgreich.
