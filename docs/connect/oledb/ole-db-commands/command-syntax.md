---
title: -Befehlssyntax | Microsoft Docs
description: Befehl Syntax und gespeicherte Prozeduren
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, commands
- commands [OLE DB]
- OLE DB Driver for SQL Server, stored procedures
- stored procedures [OLE DB], command syntax
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: a3ea215d3596842503517a9485187ba2b1368059
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2018
ms.locfileid: "35665750"
---
# <a name="command-syntax"></a>Befehlsyntax
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server erkennt vom Makro DBGUID_SQL angegebene Befehlssyntax. Für den OLE DB-Treiber für SQL Server, der Bezeichner gibt an, dass ein Zusammenschluss von ODBC SQL, ISO und [!INCLUDE[tsql](../../../includes/tsql-md.md)] gültige Syntax. Die folgende SQL-Anweisung beispielsweise verwendet eine ODBC SQL-Escapesequenz, um die LCASE-Zeichenfolgenfunktion anzugeben:  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 LCASE gibt eine Zeichenfolge zurück und konvertiert alle Großbuchstaben in ihre kleingeschriebenen Entsprechungen. Die ISO-Zeichenfolgenfunktion LOWER führt denselben Vorgang durch, daher ist die folgende SQL-Anweisung eine ISO-Entsprechung der oben aufgeführten ODBC-Anweisung:  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 Der OLE DB-Treiber für SQL Server verarbeitet beide Formen der Anweisung erfolgreich, wenn Sie als Text für einen Befehl angegeben.  
  
## <a name="stored-procedures"></a>Gespeicherte Prozeduren  
 Beim Ausführen einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gespeicherte Prozedur mit einer OLE DB-Treiber für SQL Server-Befehl verwendet die ODBC CALL-Escapesequenz im Befehlstext. Der OLE DB-Treiber für SQL Server verwendet dann den remoteprozeduraufrufsmechanismus von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] um die befehlsverarbeitung zu optimieren. Zum Beispiel ist die folgende ODBC SQL-Anweisung bevorzugter Befehlstext über das [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Formular:  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle](../../oledb/ole-db-commands/commands.md)  
  
  
