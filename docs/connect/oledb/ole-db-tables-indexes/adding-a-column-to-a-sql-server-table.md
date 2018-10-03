---
title: Hinzufügen einer Spalte zu einer SQL Server-Tabelle | Microsoft-Dokumentation
description: Hinzufügen einer Spalte in einer SQL Server-Tabelle, die mithilfe von OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- OLE DB Driver for SQL Server, columns
- adding columns
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 43e279a80bdddd8b34e570116dace51aac60c9ee
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47684718"
---
# <a name="adding-a-column-to-a-sql-server-table"></a>Hinzufügen einer Spalte zu einer SQL Server-Tabelle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server macht die **addColumn** Funktion. Mit dieser Funktion können Consumer einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle eine Spalte hinzufügen.  
  
 Beim Hinzufügen einer Spalteninhalts in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tabelle, die OLE DB-Treiber für SQL Server-Consumer wie folgt beschränkt ist:  
  
-   Wenn DBPROP_COL_AUTOINCREMENT VARIANT_TRUE ist, muss DBPROP_COL_NULLABLE VARIANT_FALSE sein.  
  
-   Wenn die Spalte mit dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **timestamp**-Datentyp definiert wird, muss DBPROP_COL_NULLABLE auf VARIANT_FALSE festgelegt sein.  
  
-   Für alle anderen Spaltendefinitionen muss DBPROP_COL_NULLABLE  VARIANT_TRUE sein.  
  
 Consumer geben den Tabellennamen als Unicode-Zeichenfolge in das *pwszName*-Element der *uName*-Vereinigung des *pTableID*-Parameters ein. Das *eKind*-Element von *pTableID* muss DBKIND_NAME sein.  
  
 Der neue Spaltenname wird als Unicode-Zeichenfolge im *pwszName*-Element der *uName*-Vereinigung des *dbcid*-Elements des DBCOLUMNDESC-Parameters *pColumnDesc* angegeben. Das *eKind*-Element muss DBKIND_NAME sein.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Tabellen und Indizes](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)  
  
  
