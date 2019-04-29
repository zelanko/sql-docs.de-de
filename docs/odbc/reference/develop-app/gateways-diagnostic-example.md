---
title: Beispiel für die Diagnose von Gateways | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], examples
- gateway diagnostic [ODBC]
- error messages [ODBC], diagnostic messages
ms.assetid: e0695fac-4593-4b3d-8675-cb8f73dab966
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f4e17074616111ee93ce87c04036d1fc3fd48dd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63062418"
---
# <a name="gateways-diagnostic-example"></a>Beispiel für die Diagnose von Gateways
In einer gatewayarchitektur sendet ein Treiber Anforderungen mit einem Gateway, die ODBC unterstützt. Das Gateway sendet Anforderungen an ein DBMS. Da es sich um die Komponente, die mit dem Treiber-Manager-Schnittstellen ist, formatiert und gibt Argumente für der Treiber **SQLGetDiagRec**.  
  
 Z. B. kann Oracle basierend ein Gateway Rdb auf Microsoft Open Data Services, und wenn Rdb die EMPLOYEE-Tabelle nicht finden konnte, das Gateway diese diagnosemeldung generiert:  
  
```  
"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "  
   "in schema."  
```  
  
 Aufgrund des Fehlers in der Datenquelle, mit das Gateway die diagnosemeldung ein Präfix für die Datenquellen-ID (Rdb) hinzugefügt. Da das Gateway konnte von der Komponente, die mit der Datenquelle verbunden, werden die diagnosemeldung Präfixe für die Hersteller (Dez) und den Bezeichner ([ODS-Gateway]) hinzugefügt. Es hinzugefügt auch der SQLSTATE-Wert und der Rdb-Fehlercode an den Anfang der diagnosemeldung. Dies gestattet es die Semantik der eigene Nachrichtenstruktur beibehalten, und geben Sie immer noch die ODBC-Diagnoseinformationen an den Treiber. Der Treiber analysiert die Fehlerinformationen an die Error-Anweisung angefügt werden, durch das Gateway.  
  
 Da der Gateway-Treiber die Komponente, die mit dem Treiber-Manager-Schnittstellen ist, verwenden sie die vorherige diagnosemeldung zum Formatieren und die folgenden Rückgabewerte von **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "  
                  "defined in schema."  
```
