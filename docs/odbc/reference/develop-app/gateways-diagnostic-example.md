---
title: Gateways-Diagnosebeispiel | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b18fd78be7be2eb79316339cbdf3d315deb194fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305571"
---
# <a name="gateways-diagnostic-example"></a>Beispiel für die Diagnose von Gateways
In einer Gatewayarchitektur sendet ein Treiber Anforderungen an ein Gateway, das ODBC unterstützt. Das Gateway sendet die Anforderungen an ein DBMS. Da die Komponente mit dem Treiber-Manager in Verbindung steht, formatiert und gibt der Treiber Argumente für **SQLGetDiagRec**zurück.  
  
 Wenn Oracle beispielsweise ein Gateway zu Rdb auf Microsoft Open Data Services basiert und Rdb die Tabelle EMPLOYEE nicht finden konnte, generiert das Gateway möglicherweise diese Diagnosemeldung:  
  
```  
"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "  
   "in schema."  
```  
  
 Da der Fehler in der Datenquelle aufgetreten ist, hat das Gateway der Diagnosemeldung ein Präfix für den Datenquellenbezeichner ([Rdb]) hinzugefügt. Da das Gateway die Komponente war, die mit der Datenquelle verbunden war, fügte es der Diagnosenachricht Präfixe für den Hersteller ([DEC]) und bezeichner ([ODS Gateway] hinzu. Außerdem wurde der SQLSTATE-Wert und der Rdb-Fehlercode am Anfang der Diagnosenachricht hinzugefügt. Dadurch konnte die Semantik der eigenen Nachrichtenstruktur erhalten bleiben und dennoch die ODBC-Diagnoseinformationen an den Treiber übermittelt werden. Der Treiber analysiert die Fehlerinformationen, die vom Gateway an die Fehleranweisung angehängt sind.  
  
 Da der Gatewaytreiber die Komponente ist, die mit dem Treiber-Manager verbunden ist, würde er die vorherige Diagnosemeldung verwenden, um die folgenden Werte aus **SQLGetDiagRec**zu formatieren und zurückzugeben:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "  
                  "defined in schema."  
```
