---
title: Ausführen von Abfragen (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, executing queries
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
- SQL Server Native Client ODBC driver, queries
- queries [ODBC]
ms.assetid: d935bcba-8ce6-4159-8395-6c86431602ad
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a982d232a16e2b7f3d3692d9293686829910aeec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73779811"
---
# <a name="executing-queries-odbc"></a>Ausführen von Abfragen (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Nachdem eine ODBC-Anwendung ein Verbindungshandle initialisiert und eine Verbindung zu einer Datenquelle hergestellt hat, weist sie dem Verbindungshandle ein oder mehrere Anweisungshandles zu. Die Anwendung kann dann- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anweisungen für das Anweisungs Handle ausführen. Die übliche Reihenfolge bei der Ausführung einer SQL-Anweisung ist:  
  
1.  Festlegen aller erforderlichen Anweisungsattribute.  
  
2.  Erstellen der Anweisung.  
  
3.  Ausführen der Anweisung.  
  
4.  Abrufen der Resultsets.  
  
 Erst nachdem eine Anwendung alle Zeilen in sämtlichen von der SQL-Anweisung zurückgegebenen Resultsets abgerufen hat, kann sie eine weitere Abfrage über dasselbe Anweisungshandle ausführen. Wenn eine Anwendung ermittelt, dass es nicht erforderlich ist, alle Zeilen in einem bestimmten Resultset abzurufen, kann Sie den Rest des Resultsets durch Aufrufen von [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) oder [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)abbrechen.  
  
 Wenn Sie in einer ODBC-Anwendung dieselbe SQL-Anweisung mehrfach mit unterschiedlichen Daten ausführen müssen, verwenden Sie bei der Erstellung der SQL-Anweisung eine Parametermarkierung in Form eines Fragezeichens (?):  
  
```  
INSERT INTO MyTable VALUES (?, ?, ?)  
```  
  
 Jede Parameter Markierung kann dann durch Aufrufen von [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)an eine Programm Variable gebunden werden.  
  
 Nachdem alle SQL-Anweisungen ausgeführt und ihre Resultsets verarbeitet wurden, gibt die Anwendung das Anweisungshandle frei.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt mehrere Anweisungs Handles pro Verbindungs Handle. Transaktionen werden auf Verbindungsebene verwaltet, d. h. alle über sämtliche Anweisungshandles auf einem einzelnen Verbindungshandle ausgeführten Aufgaben werden als Bestandteil derselben Transaktion verwaltet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Zuordnen eines Anweisungshandles](../../relational-databases/native-client-odbc-queries/allocating-a-statement-handle.md)  
  
-   [Erstellen einer SQL-Anweisung &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-queries/constructing-an-sql-statement-odbc.md)  
  
-   [Erstellen von SQL-Anweisungen für Cursor](../../relational-databases/native-client-odbc-queries/constructing-sql-statements-for-cursors.md)  
  
-   [Verwenden von Anweisungsparametern](../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)  
  
-   [Ausführen von Anweisungen &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
-   [Freigeben eines Anweisungshandles](../../relational-databases/native-client-odbc-queries/freeing-a-statement-handle.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC-&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
