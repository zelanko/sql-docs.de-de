---
title: Beispiel für die Diagnose von DBMS-basierten Treibern | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304351"
---
# <a name="dbms-based-driver-diagnostic-example"></a>Beispiel für die Diagnose des DBMS-basierten Treibers
Ein DBMS-basierter Treiber sendet Anforderungen an ein DBMS und gibt über den Treiber-Manager Informationen an die Anwendung zurück. Da der Treiber die Komponente ist, die mit dem Treiber-Manager eine Schnittstelle besteht, werden Argumente für **SQLGetDiagRec**formatiert und zurückgegeben.  
  
 Wenn beispielsweise bei Verwendung von SQL/Services ein Microsoft-Treiber für Oracle RDB einen ungültigen Cursor Namen feststellt, werden möglicherweise die folgenden Werte von **SQLGetDiagRec**zurückgegeben:  
  
```  
SQLSTATE:         "34000"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."  
```  
  
 Da der Fehler im Treiber aufgetreten ist, wurden der Diagnose Meldung für den Hersteller ([Microsoft]) und den Treiber ([ODBC RDB-Treiber]) Präfixe hinzugefügt.  
  
 Wenn das DBMS den Tabellen Mitarbeiter nicht finden konnte, kann der Treiber die folgenden Werte von **SQLGetDiagRec**formatieren und zurückgeben:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "  
                  "is not defined in schema."  
```  
  
 Da der Fehler in der Datenquelle aufgetreten ist, hat der Treiber der Diagnose Nachricht ein Präfix für den Datenquellen Bezeichner ([RDB]) hinzugefügt. Da der Treiber die Komponente war, die mit der Datenquelle interstand, wurden der Diagnose Meldung Präfixe für den Hersteller ([Microsoft]) und den Bezeichner ([ODBC RDB-Treiber]) hinzugefügt.
