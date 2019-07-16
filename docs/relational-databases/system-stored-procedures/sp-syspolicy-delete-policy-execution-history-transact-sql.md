---
title: Sp_syspolicy_delete_policy_execution_history (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_delete_policy_execution_history
- sp_syspolicy_delete_policy_execution_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_delete_policy_execution_history
ms.assetid: fe651af9-267e-45ec-b4e7-4b0698fb1be3
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: f0cb7f631b75be4e8b2f4063b03aca1895ba6900
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997333"
---
# <a name="spsyspolicydeletepolicyexecutionhistory-transact-sql"></a>sp_syspolicy_delete_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht den Ausführungsverlauf für Richtlinien in der richtlinienbasierten Verwaltung. Sie können diese gespeicherte Prozedur verwenden, um den Ausführungsverlauf für eine bestimmte Richtlinie oder alle Richtlinien zu löschen und um den Ausführungsverlauf vor einem bestimmten Datum zu löschen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syspolicy_delete_policy_execution_history [ @policy_id = ] policy_id ]  
    [ , [ @oldest_date = ] 'oldest_date' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @policy_id = ] policy_id` Ist der Bezeichner der Richtlinie für die Sie den Ausführungsverlauf löschen möchten. *Policy_id* ist **Int**, und es ist erforderlich. Kann den Wert NULL haben.  
  
`[ @oldest_date = ] 'oldest_date'` Ist der am weitesten zurückliegende Datum, die für den richtlinienausführungsverlauf beibehalten werden sollen. Alle Ausführungsverläufe, die vor diesem Datum liegen, werden gelöscht. *Oldest_date* ist **"DateTime"** , und es ist erforderlich. Kann den Wert NULL haben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen sp_syspolicy_delete_policy_execution_history im Kontext der Systemdatenbank msdb ausführen.  
  
 Zum Abrufen von Werten für *Policy_id*, um Datumsangaben des Ausführungsverlaufs anzuzeigen, können Sie die folgende Abfrage verwenden:  
  
```  
SELECT a.name AS N'policy_name', b.policy_id, b.start_date, b.end_date  
FROM msdb.dbo.syspolicy_policies AS a   
INNER JOIN msdb.dbo.syspolicy_policy_execution_history AS b  
ON a.policy_id = b.policy_id  
```  
  
 Das folgende Verhalten wird angewendet, wenn Sie für einen oder beide Werte NULL angeben:  
  
-   Um den gesamten richtlinienausführungsverlauf zu löschen, geben Sie NULL für beide *Policy_id* und *Oldest_date*.  
  
-   Um den gesamten richtlinienausführungsverlauf für eine bestimmte Richtlinie zu löschen, geben Sie einen richtlinienbezeichner für *Policy_id*, und geben Sie NULL als *Oldest_date*.  
  
-   Um den richtlinienausführungsverlauf für alle Richtlinien vor einem bestimmten Datum zu löschen, geben Sie NULL für *Policy_id*, und geben Sie ein Datum für *Oldest_date*.  
  
 Um den Richtlinienausführungsverlauf zu archivieren, können Sie im Objekt-Explorer das Protokoll zum Richtlinienverlauf öffnen und den Ausführungsverlauf in eine Datei exportieren. Um auf das richtlinienverlaufsprotokoll zuzugreifen, erweitern Sie **Management**, mit der rechten Maustaste **richtlinienverwaltung**, und klicken Sie dann auf **Versionsgeschichte**.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Mögliche Erweiterung der Anmeldeinformationen: Benutzer der Rolle PolicyAdministratorRole können Servertrigger erstellen und Ausführung von Richtlinien planen, die den Betrieb der Instanz von beeinflussen, können die [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Ein Benutzer mit der Rolle PolicyAdministratorRole kann beispielsweise eine Richtlinie erstellen, durch die das Erstellen der meisten Objekte in [!INCLUDE[ssDE](../../includes/ssde-md.md)] verhindert wird. Aufgrund dieser möglichen Erweiterung der Anmeldeinformationen, sollte die PolicyAdministratorRole-Rolle gewährt werden nur für Benutzer, die mit der Kontrolle der Konfiguration von vertrauenswürdigen sind die [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Richtlinienausführungsverlauf vor einem bestimmten Datum für eine Richtlinie mit der ID 7 gelöscht.  
  
```  
EXEC msdb.dbo.sp_syspolicy_delete_policy_execution_history @policy_id = 7  
, @oldest_date = '2009-02-16 16:00:00.000';  
  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren für Richtlinie der richtlinienbasierten Verwaltung &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_set_config_history_retention &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)   
 [sp_syspolicy_purge_history &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-purge-history-transact-sql.md)  
  
  
