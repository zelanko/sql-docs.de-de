---
title: sp_add_targetsvrgrp_member (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_targetsvrgrp_member
- sp_add_targetsvrgrp_member_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_targetsvrgrp_member
ms.assetid: 5021ed5b-acca-4f8b-b9db-18733059c359
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fb35ca1a700390b51776333e5a62280d5de842ff
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826284"
---
# <a name="sp_add_targetsvrgrp_member-transact-sql"></a>sp_add_targetsvrgrp_member (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt der angegebenen Zielservergruppe den angegebenen Zielserver hinzu.  
   
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_targetsvrgrp_member [ @group_name = ] 'group_name' , [ @server_name = ] 'server_name'   
```  
  
## <a name="arguments"></a>Argumente  
`[ @group_name = ] 'group_name'`Der Name der Gruppe. *group_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @server_name = ] 'server_name'`Der Name des Servers, der der angegebenen Gruppe hinzugefügt werden soll. *server_name* ist vom Datentyp **nvarchar (30)** und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Zielserver kann Mitglied mehrerer Zielservergruppen sein.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Gruppe `Servers Maintaining Customer Information` hinzugefügt und dann der Server `LONDON1` dieser Gruppe hinzugefügt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_targetsvrgrp_member  
   @group_name = N'Servers Maintaining Customer Information',  
   @server_name = N'LONDON1' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_delete_targetsvrgrp_member &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetsvrgrp-member-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
