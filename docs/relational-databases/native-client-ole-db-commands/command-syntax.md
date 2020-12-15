---
description: Befehlssyntax (Native Client OLE DB-Anbieter)
title: Befehlssyntax (Native Client OLE DB-Anbieter) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, commands
- commands [OLE DB]
- SQL Server Native Client OLE DB provider, stored procedures
- stored procedures [OLE DB], command syntax
ms.assetid: d463d3d7-e5cb-426d-8e92-aa29980356b6
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8820b5df55687018c010b9a920014920a36234cb
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97439911"
---
# <a name="sql-server-native-client-command-syntax"></a>SQL Server Native Client Befehls Syntax
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erkennt die vom DBGUID_SQL-Makro angegebene Befehlssyntax. Für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieter gibt der Spezifizierer an, dass ein Amalgam von ODBC SQL, ISO und eine [!INCLUDE[tsql](../../includes/tsql-md.md)] gültige Syntax ist. Die folgende SQL-Anweisung beispielsweise verwendet eine ODBC SQL-Escapesequenz, um die LCASE-Zeichenfolgenfunktion anzugeben:  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 LCASE gibt eine Zeichenfolge zurück und konvertiert alle Großbuchstaben in ihre kleingeschriebenen Entsprechungen. Die ISO-Zeichenfolgenfunktion LOWER führt denselben Vorgang durch, daher ist die folgende SQL-Anweisung eine ISO-Entsprechung der oben aufgeführten ODBC-Anweisung:  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verarbeitet beide Formen der Anweisung erfolgreich, wenn er als Text für einen Befehl angegeben wird.  
  
## <a name="stored-procedures"></a>Gespeicherte Prozeduren  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verwenden Sie die ODBC-Escapesequenz im Befehls Text, wenn Sie eine gespeicherte Prozedur mit einem Native Client OLE DB Provider-Befehl ausführen. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verwendet dann den Remote Prozedur aufrufsmechanismus von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um die Befehls Verarbeitung zu optimieren. Zum Beispiel ist die folgende ODBC SQL-Anweisung bevorzugter Befehlstext über das [!INCLUDE[tsql](../../includes/tsql-md.md)]-Formular:  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehle](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
