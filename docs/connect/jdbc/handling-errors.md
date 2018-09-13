---
title: Behandeln von Fehlern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eee315022a94795dd27ae8ae7fee6cc784912bec
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784041"
---
# <a name="handling-errors"></a>Behandlung von Fehlern
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Wenn Sie [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] verwenden, werden alle Datenbankfehlerbedingungen mit der [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md)-Klasse als Ausnahmen an die Java-Anwendung übergeben. Die folgenden Methoden der SQLServerException-Klasse werden von „java.sql.SQLException“ und „java.lang.Throwable“ geerbt. Mit ihnen können spezielle Informationen zum aufgetretenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehler zurückgegeben werden:  
  
-   getSQLState gibt den normalen X/Open- oder SQL99-Statuscode der Ausnahme zurück.  
  
-   getErrorCode gibt die jeweilige Datenbankfehlernummer zurück.  
  
-   getMessage gibt den vollständigen Text der Ausnahme zurück. Der Text der Fehlermeldung beschreibt das Problem und enthält häufig Platzhalter für Informationen wie Objektnamen, die in die angezeigte Fehlermeldung eingefügt werden.  
  
-   GetNextException gibt zurück, der nächste SQLServerException-Objekt oder Null, wenn keine weiteren Ausnahmeobjekte zurückzugebenden vorhanden sind.  
  
 Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben und eine fehlerhafte SQL-Anweisung ohne FROM-Klausel erstellt. Anschließend werden die Anweisung ausgeführt und eine SQL-Ausnahme verarbeitet.  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Diagnostizieren von Problemen mit dem JDBC-Treiber](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
