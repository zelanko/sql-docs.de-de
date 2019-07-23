---
title: Entfernen einer Spalte aus einer SQL Server Tabelle | Microsoft-Dokumentation
description: Entfernen einer Spalte aus einer SQL Server Tabelle mithilfe OLE DB Treibers für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- OLE DB Driver for SQL Server, columns
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 7e367c1b0664b0b43007db3a465dcbec0ffa90d9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993986"
---
# <a name="removing-a-column-from-a-sql-server-table"></a>Entfernen einer Spalte aus einer SQL Server-Tabelle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server macht die **ITableDefinition::D ropcolumn** -Funktion verfügbar. Mit dieser Funktion können Consumer eine Spalte aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle entfernen.  
  
 Consumer geben den Tabellennamen als Unicode-Zeichenfolge im *pwszName*-Element der *uName*-Vereinigung des *pTableID*-Parameters an. Das *eKind*-Element von *pTableID* muss DBKIND_NAME sein.  
  
 Der Consumer gibt einen Spaltennamen im *pwszName*-Element der *uname* -Vereinigung im *pColumnID* -Parameter an. Der Spaltenname ist eine Unicode-Zeichenfolge. Das *eKind*-Element von *pColumnID* muss DBKIND_NAME sein.  
  
## <a name="example"></a>Beispiel  
  
### <a name="code"></a>Code  
  
```  
DBID TableID;  
DBID ColumnID;  
HRESULT hr;  
  
TableID.eKind = DBKIND_NAME;  
TableID.uName.pwszName = L"MyTableName";  
  
ColumnID.eKind = DBKIND_NAME;  
ColumnID.uName.pwszName = L"MyColumnName";  
  
hr = m_pITableDefinition->DropColumn(&TableID, &ColumnID);  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellen und Indizes](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
