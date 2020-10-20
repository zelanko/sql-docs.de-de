---
description: GetAncestor (Datenbank-Engine)
title: GetAncestor (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GetAncestor_TSQL
- GetAncestor
dev_langs:
- TSQL
helpviewer_keywords:
- GetAncestor [Database Engine]
ms.assetid: b96a986f-d5e4-4034-8013-de7974594ee9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0256deca482147f98ed93f788b8c77ea26a93b02
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92037173"
---
# <a name="getancestor-database-engine"></a>GetAncestor (Datenbank-Engine)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt eine **hierarchyid** zurück, die den *n*-ten Vorgänger von *this* darstellt.
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
-- Transact-SQL syntax  
child.GetAncestor ( n )   
```  
  
```syntaxsql
-- CLR syntax  
SqlHierarchyId GetAncestor ( int n )  
```

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
*n*  
Ein **int**-Wert, der die Anzahl der Hierarchieebenen nach oben darstellt.
  
## <a name="return-types"></a>Rückgabetypen
**SQL Server-Rückgabetyp: hierarchyid**
  
**CLR-Rückgabetyp: SqlHierarchyId**
  
## <a name="remarks"></a>Hinweise  
Hiermit wird getestet, ob jeder Knoten in der Ausgabe den aktuellen Knoten als Vorgänger auf der angegebenen Ebene aufweist.
  
Wenn eine Zahl größer als [GetLevel ()](../../t-sql/data-types/getlevel-database-engine.md) übergeben wird, wird NULL zurückgegeben.
  
Wenn eine negative Zahl übergeben wird, wird eine Ausnahme ausgelöst.
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-finding-the-child-nodes-of-a-parent"></a>A. Suchen der untergeordneten Knoten eines übergeordneten Elements  
`GetAncestor(1)` gibt die Mitarbeiter zurück, die `david0` als unmittelbaren Vorgänger (übergeordnetes Element) haben. Im folgenden Beispiel wird `GetAncestor(1)` verwendet.
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\david0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(1) = @CurrentEmployee ;  
```  
  
### <a name="b-returning-the-grandchildren-of-a-parent"></a>B. Zurückgeben der untergeordneten Elemente zweiter Ordnung eines übergeordneten Elements  
`GetAncestor(2)` gibt die Mitarbeiter zurück, die sich in der aktuellen Hierarchie zwei Ebenen unter dem aktuellen Knoten befinden. Diese Mitarbeiter sind die untergeordneten Knoten zweiter Ordnung des aktuellen Knotens. Im folgenden Beispiel wird `GetAncestor(2)` verwendet.
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\ken0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(2) = @CurrentEmployee ;  
```  
  
### <a name="c-returning-the-current-row"></a>C. Zurückgeben der aktuellen Zeile  
Um den aktuellen Knoten mit `GetAncestor(0)` zurückzugeben, führen Sie den folgenden Code aus.
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\david0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(0) = @CurrentEmployee ;  
```  
  
### <a name="d-returning-a-hierarchy-level-if-a-table-isnt-present"></a>D. Zurückgeben einer Hierarchieebene, wenn keine Tabelle vorhanden ist  
`GetAncestor` gibt die ausgewählte Ebene in der Hierarchie zurück, auch wenn keine Tabelle vorhanden ist. Beispiel: Mit dem folgenden Code wird ein aktueller Mitarbeiter festgelegt, und das `hierarchyid`-Element des Vorgängers des aktuellen Mitarbeiters wird ohne Verweis auf eine Tabelle zurückgegeben.
  
```sql
DECLARE @CurrentEmployee hierarchyid ;  
DECLARE @TargetEmployee hierarchyid ;  
SELECT @CurrentEmployee = '/2/3/1.2/5/3/' ;  
SELECT @TargetEmployee = @CurrentEmployee.GetAncestor(2) ;  
SELECT @TargetEmployee.ToString(), @TargetEmployee ;  
```  
  
### <a name="e-calling-a-common-language-runtime-method"></a>E. Aufrufen einer Common Language Runtime-Methode  
Im folgenden Codeausschnitt wird die `GetAncestor()`-Methode aufgerufen.
  
```sql
this.GetAncestor(1)  
```  
  
## <a name="see-also"></a>Weitere Informationen
[IsDescendantOf &#40;Database Engine&#41; (IsDescendantOf (Datenbank-Engine))](../../t-sql/data-types/isdescendantof-database-engine.md)  
[hierarchyid-Datentyp-Methodenverweis](./hierarchyid-data-type-method-reference.md)  
[Hierarchische Daten &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
