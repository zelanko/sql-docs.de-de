---
title: Entfernen einer Spalte aus einer SQL Server-Tabelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- SQL Server Native Client OLE DB provider, columns
ms.assetid: 210811b7-cbd6-421e-bc6e-df9482236768
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cab69ebd55bf14bd20a0fe452aee0ad81f35d1e8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47847138"
---
# <a name="removing-a-column-from-a-sql-server-table"></a>Entfernen einer Spalte aus einer SQL Server-Tabelle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt die **Dropcolumn** Funktion. Mit dieser Funktion können Consumer eine Spalte aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle entfernen.  
  
 Consumer geben den Tabellennamen als Unicode-Zeichenfolge im *pwszName*-Element der *uName*-Vereinigung des *pTableID*-Parameters an. Das *eKind*-Element von *pTableID* muss DBKIND_NAME sein.  
  
 Der Consumer gibt den Namen einer Spalte aus der *PwszName*Mitglied der *uName* -Vereinigung der *pColumnID* Parameter. Der Spaltenname ist eine Unicode-Zeichenfolge. Das *eKind*-Element von *pColumnID* muss DBKIND_NAME sein.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Tabellen und Indizes](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
