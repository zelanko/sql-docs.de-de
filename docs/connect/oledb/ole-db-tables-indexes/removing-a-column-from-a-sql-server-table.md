---
title: Entfernen einer Spalte aus einer SQL Server-Tabelle (OLE DB-Treiber)
description: Der OLE DB-Treiber für SQL Server macht die ITableDefinition::DropColumn-Funktion verfügbar, mit der Consumer eine Spalte aus einer SQL Server-Tabelle entfernen können.
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0672669e6d724e7dfcb5338c76694473f078da10
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88859461"
---
# <a name="removing-a-column-from-a-sql-server-table"></a>Entfernen einer Spalte aus einer SQL Server-Tabelle
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server stellt die **ITableDefinition::DropColumn**-Funktion zur Verfügung. Mit dieser Funktion können Consumer eine Spalte aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle entfernen.  
  
 Consumer geben den Tabellennamen als Unicode-Zeichenfolge im *pwszName*-Element der *uName*-Vereinigung des *pTableID*-Parameters an. Das *eKind*-Element von *pTableID* muss DBKIND_NAME sein.  
  
 Der Consumer gibt einen Spaltennamen im *pwszName*-Element der *uName*-Vereinigung des *pColumnID*-Parameters an. Der Spaltenname ist eine Unicode-Zeichenfolge. Das *eKind*-Element von *pColumnID* muss DBKIND_NAME sein.  
  
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
  
  
