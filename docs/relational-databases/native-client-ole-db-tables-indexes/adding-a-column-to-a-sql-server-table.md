---
title: Hinzufügen einer Spalte zu einer SQL Server-Tabelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- SQL Server Native Client OLE DB provider, columns
- adding columns
ms.assetid: 22bae18a-bc9d-4617-8660-ed8b17a468d4
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f6d5654db4b86995dcc38833afb514e707969f8d
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012962"
---
# <a name="adding-a-column-to-a-sql-server-table"></a>Hinzufügen einer Spalte zu einer SQL Server-Tabelle
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt die **ITableDefinition:: AddColumn** -Funktion zur Verfügung. Mit dieser Funktion können Consumer einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle eine Spalte hinzufügen.  
  
 Wenn Sie einer Tabelle eine Spalte hinzufügen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird der Consumer des Native Client OLE DB-Anbieters wie folgt eingeschränkt:  
  
-   Wenn DBPROP_COL_AUTOINCREMENT VARIANT_TRUE ist, muss DBPROP_COL_NULLABLE VARIANT_FALSE sein.  
  
-   Wenn die Spalte mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp**-Datentyp definiert wird, muss DBPROP_COL_NULLABLE auf VARIANT_FALSE festgelegt sein.  
  
-   Für alle anderen Spaltendefinitionen muss DBPROP_COL_NULLABLE  VARIANT_TRUE sein.  
  
 Consumer geben den Tabellennamen als Unicode-Zeichenfolge in das *pwszName*-Element der *uName*-Vereinigung des *pTableID*-Parameters ein. Das *eKind*-Element von *pTableID* muss DBKIND_NAME sein.  
  
 Der neue Spaltenname wird als Unicode-Zeichenfolge im *pwszName*-Element der *uName*-Vereinigung des *dbcid*-Elements des DBCOLUMNDESC-Parameters *pColumnDesc* angegeben. Das *eKind*-Element muss DBKIND_NAME sein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellen und Indizes](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  
