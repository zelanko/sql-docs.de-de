---
title: sysmail_configure_sp (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_configure_sp_TSQL
- sysmail_configure_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_configure_sp
ms.assetid: 73b33c56-2bff-446a-b495-ae198ad74db1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8e3ca89ab5974dbe53b12a2b5b369958ab38755c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85720167"
---
# <a name="sysmail_configure_sp-transact-sql"></a>sysmail_configure_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Ändert Konfigurationseinstellungen für Datenbank-E-Mail. Die mit **sysmail_configure_sp** angegebenen Konfigurationseinstellungen gelten für die gesamte- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_configure_sp [ [ @parameter_name = ] 'parameter_name' ]  
    [ , [ @parameter_value = ] 'parameter_value' ]  
    [ , [ @description = ] 'description' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@parameter_name** =] **'**_parameter_name_**'**  
 Der Name des Parameters, der geändert werden soll  
  
 [ **@parameter_value** =] **'**_parameter_value_**'**  
 Der neue Wert des Parameters  
  
 [ **@description** =] **'**_Beschreibung_**'**  
 Eine Beschreibung des Parameters  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Datenbank-E-Mail verwendet die folgenden Parameter:  
  
||||  
|-|-|-|  
|Parametername|BESCHREIBUNG|Standardwert|  
|*AccountRetryAttempts*|Gibt an, wie oft der externe E-Mail-Prozess versucht, die E-Mail-Nachricht zu senden, wobei jedes Konto im angegebenen Profil verwendet wird.|**1**|  
|*AccountRetryDelay*|Gibt an, wie lange (in Sekunden) der externe E-Mail-Prozess zwischen zwei Versuchen, eine Nachricht zu senden, warten soll.|**5000**|  
|*DatabaseMailExeMinimumLifeTime konfigurierten*|Gibt an, wie lange (in Sekunden) der externe E-Mail-Prozess mindestens aktiv bleibt. Wenn Datenbank-E-Mail viele Nachrichten sendet, sollten Sie diesen Wert erhöhen, damit Datenbank-E-Mail aktiv bleibt und unnötiger Aufwand durch häufiges Starten und Beenden vermieden wird.|**600**|  
|*Defaultattachmentencoding*|Die Standardcodierung für E-Mail-Anlagen|MIME|  
|*MaxFileSize*|Die maximale Größe einer Anlage in Bytes.|**1 Million**|  
|*ProhibitedExtensions*|Eine durch Trennzeichen getrennte Liste mit Erweiterungen, die nicht als Anlagen einer E-Mail-Nachricht gesendet werden können.|**exe,dll,vbs,js**|  
|*LoggingLevel*|Gibt an, welche Nachrichten im Datenbank-E-Mail-Protokoll aufgezeichnet werden. Einer der folgenden numerischen Werte:<br /><br /> 1 - Dies ist der normale Modus. Es werden nur Fehler protokolliert.<br /><br /> 2 - Dies ist der erweiterte Modus. Es werden Fehler-, Warn- und Informationsmeldungen protokolliert.<br /><br /> 3 - Dies ist der ausführliche Modus. Es werden Fehler-, Warn-, Informations-, Erfolgs- sowie zusätzliche interne Meldungen protokolliert. Verwenden Sie diesen Modus zur Problembehandlung.|**2**|  
  
 Die gespeicherte Prozedur **sysmail_configure_sp** wird in der **msdb** -Datenbank gespeichert und befindet sich im Besitz des **dbo** -Schemas. Handelt es sich bei der aktuellen Datenbank nicht um **msdb**, muss die Prozedur mit einem dreiteiligen Namen ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Über die Ausführungsberechtigungen für diese Prozedur verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 **A. Festlegen, dass Datenbank-E-Mail für jedes Konto 10 Wiederholungsversuche unternimmt**  
  
 Im folgenden Beispiel wird gezeigt, wie Datenbank-E-Mail so konfiguriert wird, dass für jedes Konto 10 Wiederholungsversuche unternommen werden, bevor das jeweilige Konto als nicht erreichbar eingestuft wird.  
  
```  
EXECUTE msdb.dbo.sysmail_configure_sp  
    'AccountRetryAttempts', '10' ;  
```  
  
 **B. Festlegen der maximalen Anlagengröße auf 2 MB**  
  
 Im folgenden Beispiel wird gezeigt, wie die maximale Anlagengröße auf 2 MB festgelegt wird.  
  
```  
EXECUTE msdb.dbo.sysmail_configure_sp  
    'MaxFileSize', '2097152' ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [sysmail_help_configure_sp &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sysmail-help-configure-sp-transact-sql.md)   
 [Datenbank-E-Mail gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
