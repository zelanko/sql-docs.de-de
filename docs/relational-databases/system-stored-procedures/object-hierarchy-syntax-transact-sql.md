---
description: Objekthierarchiesyntax (Transact-SQL)
title: Objekt Hierarchie Syntax (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], hierarchy syntax
ms.assetid: 7ed8df86-9fd2-4e09-96bc-5381fec85f65
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: be02e82ef4ba1718f15bd083e3ffc3b86058a24b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88498106"
---
# <a name="object-hierarchy-syntax-transact-sql"></a>Objekthierarchiesyntax (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Der *propertyName* -Parameter von sp_OAGetProperty und sp_OASetProperty und der *MethodName* -Parameter von sp_OAMethod unterstützen eine Objekt Hierarchie Syntax, die mit der von vergleichbar ist [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . Bei Verwendung dieser speziellen Syntax haben diese Parameter das folgende allgemeine Format.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
'TraversedObject.PropertyOrMethod'  
```  
  
## <a name="arguments"></a>Argumente  
 *Travermendobject*  
 Ein OLE-Objekt in der Hierarchie unter dem *objecttoken* , das in der gespeicherten Prozedur angegeben ist. Mithilfe der [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]-Syntax geben Sie eine Folge von Auflistungen, Objekteigenschaften und Methoden an, die Objekte zurückgeben. Alle Objektbezeichner in dieser Folge müssen durch Punkte (.) getrennt werden.  
  
 Ein Element der Folge kann der Name einer Auflistung sein. Mit der folgenden Syntax geben Sie eine Auflistung an:  
  
 Collection ("*Item*")  
  
 Die doppelten Anführungszeichen (") sind erforderlich. Das [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]-Ausrufezeichen (!) der Syntax für Auflistungen wird nicht unterstützt.  
  
 *PropertyOrMethod*  
 Der Name einer Eigenschaft oder Methode von *travermendobject*.  
  
 Um alle Index- oder Methodenparameter mit den Parametern sp_OAGetProperty, sp_OASetProperty oder sp_OAMethod (einschließlich der Unterstützung für Ausgabeparameter von sp_OAMethod) anzugeben, verwenden Sie die folgende Syntax:  
  
 *PropertyOrMethod*  
  
 Um alle Index- oder Methodenparameter innerhalb der Klammern anzugeben (dadurch werden alle Index- oder Methodenparameter von sp_OAGetProperty, sp_OASetProperty und sp_OAMethod ignoriert), verwenden Sie die folgende Syntax:  
  
 *PropertyOrMethod*([Parameter *Name*: =] "*Parameter*" [,...])  
  
 Die doppelten Anführungszeichen (") sind erforderlich. Alle benannten Parameter müssen nach den Positionsparametern angegeben werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn *travermendobject* nicht angegeben wird, ist *PropertyOrMethod* erforderlich.  
  
 Wenn *PropertyOrMethod* nicht angegeben wird, wird das *TraversedObject* -Objekt als Objekt Token-Ausgabeparameter von der gespeicherten OLE-Automatisierungs Prozedur zurückgegeben. Wenn *PropertyOrMethod* angegeben wird, wird die-Eigenschaft oder die-Methode des *traversierten* -Objekts aufgerufen, und der-Eigenschafts Wert oder der Methodenrückgabewert wird als Output-Parameter aus der gespeicherten OLE-Automatisierungs Prozedur zurückgegeben.  
  
 Wenn ein Element in der *TraversedObject* -Liste kein OLE-Objekt zurückgibt, wird ein Fehler ausgelöst.  
  
 Weitere Informationen zur [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]-OLE-Objektsyntax finden Sie in der [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]-Dokumentation.  
  
 Weitere Informationen zu HRESULT-Rückgabe Codes finden Sie unter [sp_OACreate &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-oacreate-transact-sql.md).  
  
## <a name="examples"></a>Beispiele  
 Es folgen Beispiele für die Objekthierarchiesyntax mithilfe eines SQLServer-Objekts von SQL-DMO.  
  
```  
-- Get the AdventureWorks2012 Person.Address Table object.  
EXEC @hr = sp_OAGetProperty @object,  
   'Databases("AdventureWorks2012").Tables("Person.Address")',  
   @table OUT  
  
-- Get the Rows property of the AdventureWorks2012 Person.Address table.  
EXEC @hr = sp_OAGetProperty @object,  
   'Databases("AdventureWorks2012").Tables("Person.Address").Rows',  
   @rows OUT  
  
-- Call the CheckTable method to validate the   
-- AdventureWorks2012 Person.Address table.  
EXEC @hr = sp_OAMethod @object,  
   'Databases("AdventureWorks2012").Tables("Person.Address").CheckTable',  
   @checkoutput OUT  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE-Automatisierungs Beispielskript](../../relational-databases/stored-procedures/ole-automation-sample-script.md)   
 [Gespeicherte OLE-Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)  
  
  
