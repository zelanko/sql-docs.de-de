---
title: GetLevel (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- GetLevel
- GetLevel_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetLevel [Database Engine]
ms.assetid: 81577d7e-8ff6-4e73-b7f4-94c03d4921e7
caps.latest.revision: 17
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0ec459f411e31794a2672b7f856f330132cf7a1f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432339"
---
# <a name="getlevel-database-engine"></a>GetLevel (Datenbank-Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt einen Integer zurück, der die Tiefe des Knotens *this* in der Struktur darstellt.
  
## <a name="syntax"></a>Syntax  
  
```sql
-- Transact-SQL syntax  
node.GetLevel ( )   
```  
  
```sql
-- CLR syntax  
SqlInt16 GetLevel ( )   
```  
  
## <a name="return-types"></a>Rückgabetypen  
**SQL Server-Rückgabetyp: smallint**
  
**CLR-Rückgabetyp: SqlInt16**
  
## <a name="remarks"></a>Remarks  
Wird zur Bestimmung der Ebene eines oder mehrerer Knoten oder zur Filterung der Knoten nach Elementen einer bestimmten Ebene verwendet. Der Stamm der Hierarchie ist Ebene 0.
  
GetLevel ist sehr nützlich für Breitensuchindizes. Weitere Informationen finden Sie unter [Hierarchische Daten &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md).
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-the-hierarchy-level-as-a-column"></a>A. Zurückgeben der Hierarchieebene als Spalte  
Im folgenden Beispiel wird eine Textdarstellung von **hierarchyid** und anschließend die Hierarchieebene als **EmpLevel**-Spalte für alle Zeilen in der Tabelle zurückgegeben:
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode,   
OrgNode.GetLevel() AS EmpLevel, *  
FROM HumanResources.EmployeeDemo;  
```  
  
### <a name="b-returning-all-members-of-a-hierarchy-level"></a>B. Zurückgeben aller Elemente einer Hierarchieebene  
Im folgenden Beispiel werden alle Zeilen in der Tabelle auf Hierarchieebene 2 zurückgegeben:
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode,   
OrgNode.GetLevel() AS EmpLevel, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetLevel() = 2;  
```  
  
### <a name="c-returning-the-root-of-the-hierarchy"></a>C. Zurückgeben des Stamms der Hierarchie  
Im folgenden Beispiel wird der Stamm der Hierarchieebene zurückgegeben.
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode,   
OrgNode.GetLevel() AS EmpLevel, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetLevel() = 0;  
```  
  
### <a name="d-clr-example"></a>D. CLR-Beispiel  
Im folgenden Codeausschnitt wird die GetLevel()-Methode aufgerufen:
  
```sql
this.GetLevel()  
```  
  
## <a name="see-also"></a>Siehe auch
[hierarchyid-Datentyp-Methodenverweis](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Hierarchische Daten &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
