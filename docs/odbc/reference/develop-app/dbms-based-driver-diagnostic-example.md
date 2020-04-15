---
title: DBMS-basiertes Treiberdiagnosebeispiel | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBMS-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: a80d54b0-43ff-4dfd-b6cb-f4694a5ed765
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 117f43548d2b57233dea6f7423e6bad67b6233b0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304351"
---
# <a name="dbms-based-driver-diagnostic-example"></a>Beispiel für die Diagnose des DBMS-basierten Treibers
Ein DBMS-basierter Treiber sendet Anforderungen an ein DBMS und gibt Informationen über den Treiber-Manager an die Anwendung zurück. Da der Treiber die Komponente ist, die mit dem Treiber-Manager in Verbindung steht, formatiert und gibt er Argumente für **SQLGetDiagRec**zurück.  
  
 Wenn z. B. ein Microsoft-Treiber für Oracle Rdb mithilfe von SQL/Services auf einen ungültigen Cursornamen gestoßen ist, gibt er möglicherweise die folgenden Werte aus **SQLGetDiagRec**zurück:  
  
```  
SQLSTATE:         "34000"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."  
```  
  
 Da der Fehler im Treiber aufgetreten ist, wurden der Diagnosenachricht für den Hersteller ([Microsoft]) und den Treiber ([ODBC Rdb Driver]) Präfixe hinzugefügt.  
  
 Wenn das DBMS die Tabelle EMPLOYEE nicht finden konnte, formatiert und gibt der Treiber möglicherweise die folgenden Werte aus **SQLGetDiagRec**zurück:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "  
                  "is not defined in schema."  
```  
  
 Da der Fehler in der Datenquelle aufgetreten ist, hat der Treiber der Diagnosemeldung ein Präfix für den Datenquellenbezeichner ([Rdb]) hinzugefügt. Da der Treiber die Komponente war, die mit der Datenquelle in Verbindung stand, fügte er der Diagnosemeldung Präfixe für den Hersteller ([Microsoft]) und den Bezeichner ([ODBC Rdb Driver]) hinzu.
