---
title: sp_syspolicy_delete_policy_execution_history (Transact-SQL) | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67997333"
---
# <a name="sp_syspolicy_delete_policy_execution_history-transact-sql"></a>sp_syspolicy_delete_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht den Ausführungsverlauf für Richtlinien in der richtlinienbasierten Verwaltung. Sie können diese gespeicherte Prozedur verwenden, um den Ausführungsverlauf für eine bestimmte Richtlinie oder alle Richtlinien zu löschen und um den Ausführungsverlauf vor einem bestimmten Datum zu löschen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syspolicy_delete_policy_execution_history [ @policy_id = ] policy_id ]  
    [ , [ @oldest_date = ] 'oldest_date' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @policy_id = ] policy_id`Der Bezeichner der Richtlinie, für die Sie den Ausführungs Verlauf löschen möchten. *policy_id* ist vom Datentyp **int**und ist erforderlich. Kann den Wert NULL haben.  
  
`[ @oldest_date = ] 'oldest_date'`Ist das älteste Datum, für das Sie den Richtlinien Ausführungs Verlauf beibehalten möchten. Alle Ausführungsverläufe, die vor diesem Datum liegen, werden gelöscht. *oldest_date* ist vom **Datentyp DateTime**und ist erforderlich. Kann den Wert NULL haben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 Sie müssen sp_syspolicy_delete_policy_execution_history im Kontext der Systemdatenbank msdb ausführen.  
  
 Sie können die folgende Abfrage verwenden, um Werte für *policy_id*abzurufen und Datumsangaben zum Ausführungs Verlauf anzuzeigen:  
  
```  
SELECT a.name AS N'policy_name', b.policy_id, b.start_date, b.end_date  
FROM msdb.dbo.syspolicy_policies AS a   
INNER JOIN msdb.dbo.syspolicy_policy_execution_history AS b  
ON a.policy_id = b.policy_id  
```  
  
 Das folgende Verhalten wird angewendet, wenn Sie für einen oder beide Werte NULL angeben:  
  
-   Um den gesamten Richtlinien Ausführungs Verlauf zu löschen, geben Sie für *policy_id* und für *oldest_date*NULL an.  
  
-   Um den gesamten Richtlinien Ausführungs Verlauf für eine bestimmte Richtlinie zu löschen, geben Sie einen Richtlinien Bezeichner für *policy_id*an, und geben Sie NULL als *oldest_date*an.  
  
-   Um den Richtlinien Ausführungs Verlauf für alle Richtlinien vor einem bestimmten Datum zu löschen, geben Sie für *policy_id*NULL an, und geben Sie ein Datum für *oldest_date*an.  
  
 Um den Richtlinienausführungsverlauf zu archivieren, können Sie im Objekt-Explorer das Protokoll zum Richtlinienverlauf öffnen und den Ausführungsverlauf in eine Datei exportieren. Erweitern Sie zum Zugreifen auf das Richtlinien Verlaufs Protokoll **Verwaltung**, klicken Sie mit der rechten Maustaste auf **Richtlinien Verwaltung**, und klicken Sie dann auf **Verlauf anzeigen**.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Mögliche Erweiterung der Anmeldeinformationen: Benutzer mit der Rolle PolicyAdministratorRole können Servertrigger erstellen und die Ausführung von Richtlinien planen. Dies kann sich auf die Arbeitsweise der [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz auswirken. Ein Benutzer mit der Rolle PolicyAdministratorRole kann beispielsweise eine Richtlinie erstellen, durch die das Erstellen der meisten Objekte in [!INCLUDE[ssDE](../../includes/ssde-md.md)] verhindert wird. Aufgrund dieser möglichen Erweiterung der Anmelde Informationen sollte die PolicyAdministratorRole-Rolle nur Benutzern gewährt werden, die mit dem Steuern der Konfiguration von vertraut sind [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Richtlinienausführungsverlauf vor einem bestimmten Datum für eine Richtlinie mit der ID 7 gelöscht.  
  
```  
EXEC msdb.dbo.sp_syspolicy_delete_policy_execution_history @policy_id = 7  
, @oldest_date = '2009-02-16 16:00:00.000';  
  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren der Richtlinien basierten Verwaltung &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_set_config_history_retention &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)   
 [sp_syspolicy_purge_history &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-purge-history-transact-sql.md)  
  
  
