---
title: GetReparentedValue (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Reparent_TSQL
- Reparent
dev_langs:
- TSQL
helpviewer_keywords:
- Reparent [Database Engine]
ms.assetid: f47f8e25-08ef-498b-84f4-a317aca1f358
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3d8b691febc1f52074451a777c7e163be8e10f80
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68077964"
---
# <a name="getreparentedvalue-database-engine"></a>GetReparentedValue (Datenbank-Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt einen Knoten zurück, dessen Pfad vom Stamm der Pfad zu _newRoot_ gefolgt vom Pfad von _oldRoot_ ist.
  
## <a name="syntax"></a>Syntax  
  
```sql
-- Transact-SQL syntax  
node. GetReparentedValue ( oldRoot, newRoot )  
```  
  
```sql
-- CLR syntax  
SqlHierarchyId GetReparentedValue ( SqlHierarchyId oldRoot , SqlHierarchyId newRoot )  
```  
  
## <a name="arguments"></a>Argumente  
_oldRoot_  
Ein **hierarchyid**-Wert, der den Knoten der zu ändernden Hierarchieebene angibt.
  
_newRoot_  
Ein **hierarchyid**-Wert, der den Knoten darstellt. Ersetzen Sie den _OldRoot_ Abschnitt des aktuellen Knotens, um den Knoten zu verschieben.
  
## <a name="return-types"></a>Rückgabetypen  
**SQL Server-Rückgabetyp: hierarchyid**
  
**CLR-Rückgabetyp: SqlHierarchyId**
  
## <a name="remarks"></a>Remarks  
Wird verwendet, um die Struktur durch Verschieben von Knoten von _oldRoot_ nach _newRoot_ zu ändern. „GetReparentedValue“ wird zum Verschieben eines Hierarchieknotens an eine neue Position in der Hierarchie verwendet. Der **hierarchyid**-Datentyp stellt die hierarchische Struktur dar, setzt sie jedoch nicht durch. Benutzer müssen sicherstellen, dass der hierarchyid-Wert für die neue Position angemessen strukturiert ist. Mit einem eindeutigen Index für den **hierarchyid**-Datentyp können Sie doppelte Einträge vermeiden. Ein Beispiel für die Verschiebung einer vollständigen Teilstruktur finden Sie unter [Hierarchische Daten &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md).
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-comparing-two-node-locations"></a>A. Vergleichen von zwei Knotenpositionen  
Im folgenden Beispiel wird der aktuelle hierarchyid-Wert eines Knotens gezeigt. Des Weiteren wird der **hierarchyid**-Wert gezeigt, den der Knoten aufweist, wenn Sie ihn an die Position des Nachfolgers des **@NewParent** -Knotens verschieben. Zur Darstellung der hierarchischen Beziehungen wird die `ToString()`-Methode verwendet.
  
```sql
DECLARE @SubjectEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
SELECT @SubjectEmployee = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\gail0' ;  
SELECT @OldParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\roberto0' ; -- who is /1/1/  
SELECT @NewParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\wanida0' ; -- who is /2/3/  
  
SELECT OrgNode.ToString() AS Current_OrgNode_AS_Text,   
(@SubjectEmployee. GetReparentedValue(@OldParent, @NewParent) ).ToString() AS Proposed_OrgNode_AS_Text,  
OrgNode AS Current_OrgNode,  
@SubjectEmployee. GetReparentedValue(@OldParent, @NewParent) AS Proposed_OrgNode,  
*  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode = @SubjectEmployee ;  
GO  
```  
  
### <a name="b-updating-a-node-to-a-new-location"></a>B. Aktualisieren eines Knotens mit einer neuen Position  
Im folgenden Beispiel wird `GetReparentedValue()` in einer UPDATE-Anweisung verwendet, um einen Knoten in einer Hierarchie von einer alten an eine neue Position zu verschieben:
  
```sql
DECLARE @SubjectEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
SELECT @SubjectEmployee = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\gail0' ; -- Node /1/1/2/  
SELECT @OldParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\roberto0' ; -- Node /1/1/  
SELECT @NewParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\wanida0' ; -- Node /2/3/  
  
UPDATE HumanResources.EmployeeDemo  
SET OrgNode = @SubjectEmployee. GetReparentedValue(@OldParent, @NewParent)   
WHERE OrgNode = @SubjectEmployee ;  
  
SELECT OrgNode.ToString() AS Current_OrgNode_AS_Text,   
*  
FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\gail0' ; -- Now node /2/3/2/  
```  
  
### <a name="c-clr-example"></a>C. CLR-Beispiel  
Im folgenden Codeausschnitt wird die GetReparentedValue ()-Methode aufgerufen:
  
```sql
this. GetReparentedValue(oldParent, newParent)  
```  
  
## <a name="see-also"></a>Siehe auch
[hierarchyid-Datentyp-Methodenverweis](https://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Hierarchische Daten &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
