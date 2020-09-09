---
description: sp_OASetProperty (Transact-SQL)
title: sp_OASetProperty (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OASetProperty
- sp_OASetProperty_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OASetProperty
ms.assetid: 0fe7d554-6b67-4d55-9d3e-4096802c47f8
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e2865189ad38f31382257a51117c62cd5d52454c
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538704"
---
# <a name="sp_oasetproperty-transact-sql"></a>sp_OASetProperty (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Legt für eine Eigenschaft eines OLE-Objekts einen neuen Wert fest.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_OASetProperty objecttoken , propertyname , newvalue [ , index... ]  
```  
  
## <a name="arguments"></a>Argumente  
 *objecttoken*  
 Ist das Objekt Token eines OLE-Objekts, das zuvor von **sp_OACreate**erstellt wurde.  
  
 *propertyname*  
 Der Eigenschaftsname des OLE-Objekts, dessen Wert neu festgelegt wird  
  
 *NewValue*  
 Der neue Wert der Eigenschaft, der den entsprechenden Datentyp aufweisen muss  
  
 *Index*  
 Ein Indexparameter. Wenn angegeben, muss der *Index* ein Wert des entsprechenden Datentyps sein.  
  
 Einige Eigenschaften besitzen Parameter. Diese Eigenschaften werden als Indiziert-Eigenschaften und die Parameter als Indexparameter bezeichnet. Eine Eigenschaft kann mehrere Indexparameter aufweisen.  
  
> [!NOTE]  
>  Die Parameter für diese gespeicherte Prozedur werden durch die Position, nicht durch den Namen angegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Zahl ungleich Null (Fehler), die dem ganzzahligen Wert von HRESULT entspricht, der vom OLE-Automatisierungsobjekt zurückgegeben wird.  
  
 Weitere Informationen zu HRESULT-Rückgabecodes finden Sie unter [Rückgabecodes und Fehlerinformationen der OLE-Automatisierung](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Server Rolle **sysadmin** oder die EXECUTE-Berechtigung direkt für diese gespeicherte Prozedur. `Ole Automation Procedures` die Konfiguration muss **aktiviert** sein, um alle System Prozeduren für OLE-Automatisierung verwenden zu können.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die- `HostName` Eigenschaft (des zuvor erstellten **SQLServer** -Objekts) auf einen neuen Wert festgelegt.  
  
```  
EXEC @hr = sp_OASetProperty @object, 'HostName', 'Gizmo';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END'  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte OLE-Automatisierungs Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [OLE-Automatisierungsbeispielskript](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
