---
title: SQLEndTran | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a668d69434d78dab1a1494a785023e84736e32af
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85789312"
---
# <a name="sqlendtran"></a>SQLEndTran
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  In der Standardeinstellung schließt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber den mit einer Anweisung verknüpften Cursor, wenn **SQLEndTran** für einen Vorgang ein Commit oder Rollback ausführt. Servercursor werden nicht geschlossen, wenn sie statisch sind. Wenn **SQLEndTran** für einen Vorgang ein Commit oder Rollback ausführt, wird das Verhalten des mit der Anweisung verknüpften Cursors vom Wert des treiberspezifischen ODBC-Verbindungsattributs SQL_COPT_SS_PRESERVE_CURSORS bestimmt, das von [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)festgelegt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Details zur ODBC-API-Implementierung](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SQLEndTran-Funktion](https://go.microsoft.com/fwlink/?LinkId=59342)  
  
  
