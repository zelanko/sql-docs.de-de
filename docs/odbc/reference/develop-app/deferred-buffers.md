---
title: Verzögerte Puffer | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f34c6d3d886a0a75c309dc4f5c71f5c7ba3df447
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305981"
---
# <a name="deferred-buffers"></a>Zurückgestellte Puffer
Ein *verzögerter Puffer* ist ein Puffer, dessen Wert zu einem bestimmten Zeitpunkt verwendet wird, *nachdem* er in einem Funktionsaufruf angegeben wurde. **SQLBindParameter** wird beispielsweise verwendet, um einem Parameter in einer SQL-Anweisung einen Datenpuffer zuzuordnen oder zu *binden.* Die Anwendung gibt die Nummer des Parameters an und übergibt die Adresse, die Bytelänge und den Typ des Puffers. Der Treiber speichert diese Informationen, untersucht jedoch nicht den Inhalt des Puffers. Später, wenn die Anwendung die Anweisung ausführt, ruft der Treiber die Informationen ab und verwendet sie, um die Parameterdaten abzurufen und an die Datenquelle zu senden. Daher wird die Eingabe von Daten in den Puffer zurückgestellt. Da verzögerte Puffer in einer Funktion angegeben und in einer anderen verwendet werden, ist es ein Anwendungsprogrammierfehler, um einen verzögerten Puffer freizugeben, während der Treiber weiterhin erwartet, dass er vorhanden ist. Weitere Informationen finden Sie weiter unten in diesem Abschnitt unter [Zuweisen und Verteilen von Puffern](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Sowohl Ein- als auch Ausgabepuffer können zurückgestellt werden. Die folgende Tabelle fasst die Verwendung von verzögerten Puffern zusammen. Beachten Sie, dass an Ergebnissatzspalten gebundene verzögerte Puffer mit **SQLBindCol**angegeben werden und zurückgestellte Puffer, die an SQL-Anweisungsparameter gebunden sind, mit **SQLBindParameter**angegeben werden.  
  
|Pufferverwendung|type|Angegeben mit|Verwendet von|  
|----------------|----------|--------------------|-------------|  
|Senden von Daten für Eingabeparameter|Verzögerte Eingabe|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|Senden von Daten zum Aktualisieren oder Einfügen einer Zeile in ein Resultset|Verzögerte Eingabe|**SQLBindCol**|**SQLSetPos**|  
|Zurückgeben von Daten für Ausgabe- und Ein-/Ausgabeparameter|Verzögerte Ausgabe|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|Zurückgeben von Resultset-Daten|Verzögerte Ausgabe|**SQLBindCol**|**SQLFetch**<br /> **SQLFetchScroll SQLSetPos**|
