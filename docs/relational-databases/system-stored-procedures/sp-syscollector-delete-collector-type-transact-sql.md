---
title: sp_syscollector_delete_collector_type (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_delete_collector_type
- sp_syscollector_delete_collector_type_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_delete_collector_type
ms.assetid: 3f32905e-0005-42cb-aef1-7bd04c51fbac
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2c24011a274b362a6b8267b7559d2641a4f1c6aa
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892925"
---
# <a name="sp_syscollector_delete_collector_type-transact-sql"></a>sp_syscollector_delete_collector_type (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Löscht die Definition eines Sammlertyps.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_delete_collector_type [[ @collector_type_uid = ] 'collector_type_uid' ]  
          , [[ @name = ] 'name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @collector_type_uid = ] 'collector_type_uid'`Die GUID für den Sammlertyp. *collector_type_uid* ist vom *Datentyp* **uniqueidentifier** und muss über einen Wert verfügen, wenn Name NULL ist.  
  
`[ @name = ] 'name'`Der Name des Sammler Typs. *Name ist vom Datentyp* **vom Datentyp sysname** und muss über einen Wert verfügen, wenn *collector_type_uid* NULL ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Entweder *collector_type_uid* oder *Name* muss einen Wert aufweisen, beide dürfen nicht NULL sein.  
  
 Diese Prozedur löst einen Fehler aus, wenn Sammelelemente dieses Auflistungstyps vorhanden sind.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen dieses Vorgangs ist die Mitgliedschaft in der Daten Bank Rolle **dc_admin** (mit EXECUTE-Berechtigung) erforderlich.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird der generische T-SQL-Abfrage-Sammlertyp gelöscht.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_delete_collector_type @collector_type_uid = '302E93D1-3424-4be7-AA8E-84813ECF2419';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  
