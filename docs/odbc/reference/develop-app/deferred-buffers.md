---
title: Verzögerte Puffer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- buffers [ODBC], deferred
- deferred buffers [ODBC]
ms.assetid: 02c9a75c-2103-4f68-a1db-e31f7e0f1f03
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1f7c90dacc375877b4e449b8d59533ce75ff8a4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076835"
---
# <a name="deferred-buffers"></a>Zurückgestellte Puffer
Ein *verzögerter Puffer* ist ein Puffer, dessen Wert zu einem bestimmten Zeitpunkt *nach* dem angeben in einem Funktionsaufruf verwendet wird. Beispielsweise wird **SQLBindParameter** verwendet, um einen Datenpuffer mit einem Parameter in einer SQL-Anweisung zuzuordnen oder zu *binden* . Die Anwendung gibt die Nummer des Parameters an und übergibt die Adresse, die Byte Länge und den Typ des Puffers. Der Treiber speichert diese Informationen, untersucht jedoch nicht den Inhalt des Puffers. Wenn die Anwendung später die-Anweisung ausführt, ruft der Treiber die Informationen ab und verwendet Sie, um die Parameterdaten abzurufen und an die Datenquelle zu senden. Daher wird die Eingabe von Daten im Puffer verzögert. Da verzögerte Puffer in einer Funktion angegeben und in einer anderen Funktion verwendet werden, handelt es sich um einen Anwendungs Programmierfehler, der einen verzögerten Puffer freigibt, während der Treiber weiterhin erwartet, dass er vorhanden ist. Weitere Informationen finden Sie weiter unten in diesem Abschnitt unter [zuordnen und Freigeben von Puffern](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Sowohl Eingabe-als auch Ausgabepuffer können zurückgestellt werden. In der folgenden Tabelle werden die Verwendungen verzögerter Puffer zusammengefasst. Beachten Sie, dass verzögerte Puffer, die an Resultsetspalten gebunden sind, mit **SQLBindCol**angegeben werden und verzögerte Puffer, die an SQL-Anweisungs Parameter gebunden sind, mit **SQLBindParameter**angegeben werden  
  
|Puffer Verwendung|type|Angegeben mit|Verwendet von|  
|----------------|----------|--------------------|-------------|  
|Senden von Daten für Eingabeparameter|Verzögerte Eingabe|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|Senden von Daten zum Aktualisieren oder Einfügen einer Zeile in einem Resultset|Verzögerte Eingabe|**SQLBindCol**|**SQLSetPos**|  
|Rückgabe von Daten für Ausgabe-und Eingabe-/Ausgabeparameter|Verzögerte Ausgabe|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|Zurückgeben von Resultsetdaten|Verzögerte Ausgabe|**SQLBindCol**|**SQLFetch**<br /> **SQLFetchScroll SQLSetPos**|
