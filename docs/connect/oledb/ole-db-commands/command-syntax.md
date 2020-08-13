---
title: Befehlssyntax (OLE DB-Treiber) | Microsoft-Dokumentation
description: Befehlssyntax und gespeicherte Prozeduren
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, commands
- commands [OLE DB]
- OLE DB Driver for SQL Server, stored procedures
- stored procedures [OLE DB], command syntax
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 06516c7ac352ced53ba56241d8845aafaf236139
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942760"
---
# <a name="command-syntax"></a>Befehlsyntax
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server erkennt vom Makro DBGUID_SQL angegebene Befehlssyntax. Für den OLE DB-Treiber für SQL Server gibt der Bezeichner an, dass ein Zusammenschluss von ODBC SQL, ISO und [!INCLUDE[tsql](../../../includes/tsql-md.md)] eine gültige Syntax ist. Die folgende SQL-Anweisung beispielsweise verwendet eine ODBC SQL-Escapesequenz, um die LCASE-Zeichenfolgenfunktion anzugeben:  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 LCASE gibt eine Zeichenfolge zurück und konvertiert alle Großbuchstaben in ihre kleingeschriebenen Entsprechungen. Die ISO-Zeichenfolgenfunktion LOWER führt denselben Vorgang durch, daher ist die folgende SQL-Anweisung eine ISO-Entsprechung der oben aufgeführten ODBC-Anweisung:  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 Der OLE DB-Treiber für SQL Server verarbeitet beide Formen der Anweisung erfolgreich, wenn sie für einen Befehl als Text angegeben wird.  
  
## <a name="stored-procedures"></a>Gespeicherte Prozeduren  
 Wenn eine in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gespeicherte Prozedur mit einem Befehl des OLE DB-Treibers für SQL Server ausgeführt wird, verwenden Sie die ODBC CALL-Escapesequenz im Befehlstext. Der OLE DB-Treiber für SQL Server verwendet dann den Aufrufmechanismus für Remoteprozeduren von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], um die Befehlsverarbeitung zu optimieren. Zum Beispiel ist die folgende ODBC SQL-Anweisung bevorzugter Befehlstext über das [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Formular:  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehle](../../oledb/ole-db-commands/commands.md)  
  
  
