---
title: sp_msx_defect (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_msx_defect
- sp_msx_defect_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_defect
ms.assetid: 0dfd963a-3bc5-4b58-94f7-aec976da2883
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 102698d7efffa753510f3e3b9af6fe40e35408fc
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715162"
---
# <a name="sp_msx_defect-transact-sql"></a>sp_msx_defect (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Entfernt den aktuellen Server für Multiservervorgänge.  
  
> [!CAUTION]  
>  **sp_msx_defect** bearbeitet die Registrierung. Die Registrierung sollte nicht manuell bearbeitet werden, da durch ungeeignete oder fehlerhafte Änderungen schwerwiegende Konfigurationsprobleme auf dem System verursacht werden können. Nur erfahrene Benutzer sollten deshalb den Registrierungs-Editor zum Bearbeiten der Registrierung verwenden. Weitere Informationen finden Sie in der Dokumentation zu Microsoft Windows.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_msx_defect [@forced_defection =] forced_defection  
```  
  
## <a name="arguments"></a>Argumente  
`[ @forced_defection = ] forced_defection`Gibt an, ob der Abgleich erzwungen werden soll, wenn der Master SQLServerAgent aufgrund einer unumkehrbar beschädigten **msdb** -Datenbank oder einer **msdb** -Datenbanksicherung dauerhaft verloren gegangen ist. *forced_defection*ist vom Typ **Bit**. der Standardwert ist **0**. Dies bedeutet, dass keine erzwungene Ausführung erfolgen soll. Ein Wert von **1** erzwingt das Abgleichen.  
  
 Nachdem Sie durch Ausführen von **sp_msx_defect**eine Ablauf Verfolgung erzwungen haben, muss ein Mitglied der festen Server Rolle **sysadmin** auf dem Master SQLServerAgent den folgenden Befehl ausführen, um den Abgleich abzuschließen:  
  
```  
EXECUTE msdb.dbo.sp_delete_targetserver @server_name = 'tsx-server', @post_defection =  0;  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn **sp_msx_defect** ordnungsgemäß abgeschlossen ist, wird eine Meldung zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen dieser gespeicherten Prozedur muss ein Benutzer Mitglied der festen Serverrolle **sysadmin** sein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_msx_enlist &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
