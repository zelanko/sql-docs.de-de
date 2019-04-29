---
title: Beispiel für die Diagnose von dateibasierten Treibers | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: decb09098cee4b9ab6473e3c622b9917a89e9b09
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63061528"
---
# <a name="file-based-driver-diagnostic-example"></a>Beispiel für die Diagnose des dateibasierten Treibers
Einen dateibasierten Treibers fungiert sowohl als einen ODBC-Treiber als auch als Datenquelle. Sie können daher Fehler und Warnungen, die sowohl als Komponente in eine ODBC-Verbindung und als Datenquelle generieren. Da es auch die Komponente, die mit dem Treiber-Manager-Schnittstellen, formatiert und gibt die Argumente für **SQLGetDiagRec**.  
  
 Z. B. wenn ein Treiber Microsoft® dBASE-nicht genügend Arbeitsspeicher reservieren kann, es kann die folgenden Werte zurückgeben aus **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY001"  
Native Error:      42052  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver]Unable to allocate sufficient memory."  
```  
  
 Da dieser Fehler nicht mit der Datenquelle verbunden war, hinzugefügt der Treiber nur Präfixe der diagnosemeldung für den Anbieter ([Microsoft]) und der Treiber ([ODBC dBASE-Treiber]).  
  
 Wenn der Treiber nicht die Datei nützlich finden konnte, kann es die folgenden Werte aus zurückgeben **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1305  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver][dBASE]No such table or object"  
```  
  
 Da dieser Fehler mit der Datenquelle verbunden war, hinzugefügt der Treiber das Dateiformat der Datenquelle (dBASE) als Präfix an die diagnosemeldung. Da der Treiber auch konnte von der Komponente, die mit der Datenquelle verbunden, hinzugefügt Präfixe für den Anbieter ([Microsoft]) und der Treiber ([ODBC dBASE-Treiber]).
