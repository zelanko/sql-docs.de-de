---
description: Beispiel für die Diagnose von Gateways
title: Beispiel für Gateways-Diagnose | Microsoft-Dokumentation
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
ms.openlocfilehash: 17e32f0ccdc1b2fbbebb1969083e216ed3371688
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465782"
---
# <a name="gateways-diagnostic-example"></a>Beispiel für die Diagnose von Gateways
In einer gatewayarchitektur sendet ein Treiber Anforderungen an ein Gateway, das ODBC unterstützt. Das Gateway sendet die Anforderungen an ein DBMS. Da es sich um die Komponente handelt, die eine Schnittstelle mit dem Treiber-Manager hat, formatiert und gibt der Treiber Argumente für **SQLGetDiagRec**aus.  
  
 Wenn Oracle z. b. ein Gateway für RDB unter Microsoft geöffnet Data Services und RDB den Tabellen Mitarbeiter nicht finden konnte, generiert das Gateway möglicherweise die folgende Diagnose Meldung:  
  
```  
"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "  
   "in schema."  
```  
  
 Da der Fehler in der Datenquelle aufgetreten ist, hat das Gateway der Diagnose Nachricht ein Präfix für den Datenquellen Bezeichner ([RDB]) hinzugefügt. Da das Gateway die Komponente war, die mit der Datenquelle interstand, wurden der Diagnose Nachricht Präfixe für den Hersteller ([Dec]) und den Bezeichner ([ODS Gateway]) hinzugefügt. Außerdem wurde der SQLSTATE-Wert und der RDB-Fehlercode am Anfang der Diagnose Nachricht hinzugefügt. Dadurch konnte die Semantik Ihrer eigenen Nachrichtenstruktur beibehalten werden, und die ODBC-Diagnoseinformationen werden dem Treiber weiterhin bereitgestellt. Der Treiber analysiert die Fehlerinformationen, die vom Gateway an die Fehler Anweisung angehängt werden.  
  
 Da der gatewaytreiber die Komponente ist, die mit dem Treiber-Manager über eine Schnittstelle verfügt, wird die vorhergehende Diagnose Meldung verwendet, um die folgenden Werte von **SQLGetDiagRec**zu formatieren und zurückzugeben:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "  
                  "defined in schema."  
```
