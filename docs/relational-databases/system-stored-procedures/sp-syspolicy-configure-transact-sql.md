---
title: sp_syspolicy_configure (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_configure
- sp_syspolicy_configure_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_configure
ms.assetid: 70c10922-9345-4190-ba69-808a43f760da
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: bd11fa935dadc2ed7332275f3f6c66613cc831af
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892755"
---
# <a name="sp_syspolicy_configure-transact-sql"></a>sp_syspolicy_configure (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Konfiguriert Einstellungen für richtlinienbasierte Verwaltung, z. B. ob die richtlinienbasierte Verwaltung aktiviert ist.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syspolicy_configure [ @name = ] 'name'  
    , [ @value = ] value  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] 'name'`Der Name der Einstellung, die Sie konfigurieren möchten. *Name ist vom Datentyp* **vom Datentyp sysname**, ist erforderlich und darf nicht NULL oder eine leere Zeichenfolge sein.  
  
 der *Name* kann einen der folgenden Werte aufweisen:  
  
-   'Enabled' – Gibt an, ob die richtlinienbasierte Verwaltung aktiviert ist.  
  
-   'HistoryRetentionInDays' – Gibt die Anzahl der Tage an, wie lange der Richtlinienauswertungsverlauf beibehalten werden soll. Bei der Einstellung 0 wird der Verlauf nicht automatisch entfernt.  
  
-   'LogOnSuccess' – Gibt an, ob die richtlinienbasierte Verwaltung erfolgreiche Richtlinienauswertungen protokolliert.  
  
`[ @value = ] value`Der Wert, der dem angegebenen Wert für *Name*zugeordnet ist. der *Wert* ist **sql_variant**, und ist erforderlich.  
  
-   Wenn Sie "aktiviert" für *Name*angeben, können Sie einen der folgenden Werte verwenden:  
  
    -   0 = Deaktiviert die richtlinienbasierte Verwaltung.  
  
    -   1 = Aktiviert die richtlinienbasierte Verwaltung.  
  
-   Wenn Sie für *Name*"historyrententionindays" angeben, geben Sie die Anzahl der Tage als ganzzahligen Wert an.  
  
-   Wenn Sie für *Name den Namen*"LogOnSuccess" angeben, können Sie einen der folgenden Werte verwenden:  
  
    -   0 = Protokolliert nur fehlerhafte Richtlinienauswertungen.  
  
    -   1 = Protokolliert sowohl erfolgreiche als auch fehlerhafte Richtlinienauswertungen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen sp_syspolicy_configure im Kontext der Systemdatenbank msdb ausführen.  
  
 Um aktuelle Werte für diese Einstellungen anzuzeigen, fragen Sie die Systemsicht msdb.dbo.syspolicy_configuration ab.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Mögliche Erweiterung der Anmeldeinformationen: Benutzer mit der Rolle PolicyAdministratorRole können Servertrigger erstellen und die Ausführung von Richtlinien planen. Dies kann sich auf die Arbeitsweise der [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz auswirken. Ein Benutzer mit der Rolle PolicyAdministratorRole kann beispielsweise eine Richtlinie erstellen, durch die das Erstellen der meisten Objekte in [!INCLUDE[ssDE](../../includes/ssde-md.md)] verhindert wird. Aufgrund dieser möglichen Erweiterung der Anmelde Informationen sollte die PolicyAdministratorRole-Rolle nur Benutzern gewährt werden, die mit dem Steuern der Konfiguration von vertraut sind [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die richtlinienbasierte Verwaltung aktiviert.  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'Enabled'  
, @value = 1;  
  
GO  
```  
  
 Im folgenden Beispiel wird die Richtlinienverlaufsbeibehaltung auf 14 Tage festgelegt.  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'HistoryRetentionInDays'  
, @value = 14;  
  
GO  
```  
  
 Im folgenden Beispiel wird die richtlinienbasierte Verwaltung so konfiguriert, dass sowohl erfolgreiche als auch fehlerhafte Richtlinienauswertungen protokolliert werden.  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'LogOnSuccess'  
, @value = 1;  
  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren der Richtlinien basierten Verwaltung &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_set_config_enabled &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-enabled-transact-sql.md)   
 [sp_syspolicy_set_config_history_retention &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)   
 [sp_syspolicy_set_log_on_success &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-log-on-success-transact-sql.md)  
  
  
