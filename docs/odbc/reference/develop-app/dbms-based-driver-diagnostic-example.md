---
title: Beispiel für die Diagnose von DBMS-basierten Treibers | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0485ecf720cb84580c17c77b31fc6816de2e679a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62641039"
---
# <a name="dbms-based-driver-diagnostic-example"></a>Beispiel für die Diagnose des DBMS-basierten Treibers
Ein DBMS-basierten Treiber sendet Anforderungen an ein DBMS und gibt Informationen an die Anwendung über den Treiber-Manager. Da der Treiber die Komponente, die mit dem Treiber-Manager-Schnittstellen ist, formatiert und gibt die Argumente für **SQLGetDiagRec**.  
  
 Z. B. wenn, SQL und-Dienste auf und ein Microsoft-Treiber für Oracle Rdb einen Ungültiger Cursorname gefunden, es kann die folgenden Werte zurückgeben von **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "34000"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."  
```  
  
 Da der Fehler im Treiber hinzugefügt Präfixe der diagnosemeldung für den Anbieter ([Microsoft]) und der Treiber ([ODBC-Treiber Rdb]).  
  
 Wenn das DBMS die EMPLOYEE-Tabelle nicht finden konnte, der Treiber formatieren und die folgenden Rückgabewerte von möglicherweise **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "  
                  "is not defined in schema."  
```  
  
 Da der Fehler in der Datenquelle, mit der Treiber die diagnosemeldung ein Präfix für die Datenquellen-ID (Rdb) hinzugefügt. Da der Treiber konnte von der Komponente, die mit der Datenquelle verbunden, werden die diagnosemeldung Präfixe für die Anbieter ([Microsoft]) und den Bezeichner ([ODBC-Treiber Rdb]) hinzugefügt.
