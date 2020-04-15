---
title: Dateibasiertes Treiberdiagnosebeispiel | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- file-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: 0575fccd-4641-478d-a3cc-5a764e35bae2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6f09e4f4758b6276836b08f02b24fb31dd1fadc7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305638"
---
# <a name="file-based-driver-diagnostic-example"></a>Beispiel für die Diagnose des dateibasierten Treibers
Ein dateibasierter Treiber fungiert sowohl als ODBC-Treiber als auch als Datenquelle. Es kann daher Fehler und Warnungen sowohl als Komponente in einer ODBC-Verbindung als auch als Datenquelle generieren. Da es auch die Komponente ist, die mit dem Treiber-Manager verbindet, formatiert und gibt sie Argumente für **SQLGetDiagRec**zurück.  
  
 Wenn z. B. ein Microsoft®-Treiber für dBASE nicht genügend Arbeitsspeicher zuweisen konnte, gibt er möglicherweise die folgenden Werte aus **SQLGetDiagRec**zurück:  
  
```  
SQLSTATE:         "HY001"  
Native Error:      42052  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver]Unable to allocate sufficient memory."  
```  
  
 Da dieser Fehler nicht mit der Datenquelle zusammenhängt, fügte der Treiber der Diagnosenachricht für den Hersteller ([Microsoft]) und den Treiber ([ODBC dBASE Driver]) nur Präfixe hinzu.  
  
 Wenn der Treiber die Datei Employee.dbf nicht finden konnte, gibt er möglicherweise die folgenden Werte aus **SQLGetDiagRec**zurück:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1305  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver][dBASE]No such table or object"  
```  
  
 Da dieser Fehler mit der Datenquelle zusammenhängt, hat der Treiber das Dateiformat der Datenquelle ([dBASE]) als Präfix zur Diagnosemeldung hinzugefügt. Da der Treiber auch die Komponente war, die mit der Datenquelle in Verbindung stand, fügte er Präfixe für den Hersteller ([Microsoft]) und den Treiber ([ODBC dBASE Driver]) hinzu.
