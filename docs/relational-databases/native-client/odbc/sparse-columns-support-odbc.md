---
title: Unterstützung für Spalten mit geringer Dichte (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|ODBC
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 11ae959f-2fb6-4b85-ac5d-1476a82136d4
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 649656eb90aa4431d3d34bcbd6a3c28f069d30e4
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37409129"
---
# <a name="sparse-columns-support-odbc"></a>Unterstützung für Spalten mit geringer Dichte (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  In diesem Thema wird beschrieben, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Unterstützung für Spalten mit geringer Dichte. Ein Beispiel, ODBC-Unterstützung für sparsespalten veranschaulicht, finden Sie unter [Aufrufen von SQLColumns für eine Tabelle mit Spalten mit geringer Dichte](../../../relational-databases/native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md). Weitere Informationen zu Sparsespalten finden Sie unter [Sparse Columns Support in SQL Server Native Client](../../../relational-databases/native-client/features/sparse-columns-support-in-sql-server-native-client.md).  
  
## <a name="statement-metadata"></a>Anweisungsmetadaten  
 Das Deskriptorfeld für den Anwendungsparameterdeskriptor (APD) und das SQL_SOPT_SS_NAME_SCOPE-Anweisungsattribut akzeptieren die zusätzlichen Werte SQL_SS_NAME_SCOPE_EXTENDED und SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET. Diese Werte angeben, welche Spalten im Resultset zurückgegebenes enthalten sind [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md). Weitere Informationen zu SQL_SOPT_SS_NAME_SCOPE finden Sie unter [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Mithilfe eines neuen Implementierungszeilendeskriptors (IRD), ein schreibgeschütztes SQLSMALLINT-Feld namens SQL_CA_SS_IS_COLUMN_SET, kann bestimmt werden, ob eine Spalte einen XML **column_set** -Wert darstellt. SQL_CA_SS_IS_COLUMN_SET akzeptiert die Werte SQL_TRUE und SQL_FALSE.  
  
## <a name="catalog-metadata"></a>Katalogmetadaten  
 Zwei [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -spezifische Spalten (SS_IS_SPARSE and SS_IS_COLUMN_SET) wurden hinzugefügt, um das Resultset für [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md).  
  
## <a name="odbc-function-support-for-sparse-columns"></a>ODBC-Funktionsunterstützung für Spalten mit geringer Dichte  
 Die folgenden ODBC-Funktionen wurden aktualisiert, um Sparsespalten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client zu unterstützen:  
  
-   [SQLColAttribute](../../../relational-databases/native-client-odbc-api/sqlcolattribute.md)  
  
-   [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)  
  
-   [SQLGetDescField](../../../relational-databases/native-client-odbc-api/sqlgetdescfield.md)  
  
-   [SQLSetDescField](../../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)  
  
-   [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
