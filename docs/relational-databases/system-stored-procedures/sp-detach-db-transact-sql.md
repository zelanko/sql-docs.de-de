---
title: sp_detach_db (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/30/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_detach_db
- sp_detach_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_detach_db
- detaching databases [SQL Server]
ms.assetid: abcb1407-ff78-4c76-b02e-509c86574462
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d9eaae9a00a125a2ffe2f290e2bd772eb40d84c6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717358"
---
# <a name="sp_detach_db-transact-sql"></a>sp_detach_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Trennt eine zurzeit nicht verwendete Datenbank von einer Serverinstanz und führt optional vor dem Trennvorgang für alle Tabellen UPDATE STATISTICS aus.  
  
> [!IMPORTANT]  
>  Eine replizierte Datenbank kann nur getrennt werden, wenn sie nicht veröffentlicht ist. Weitere Informationen finden Sie im Abschnitt "Hinweise" weiter unten in diesem Thema.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_detach_db [ @dbname= ] 'database_name'   
    [ , [ @skipchecks= ] 'skipchecks' ]   
    [ , [ @keepfulltextindexfile = ] 'KeepFulltextIndexFile' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @dbname = ] 'database_name'`Der Name der Datenbank, die getrennt werden soll. *database_name* ist ein Wert vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL.  
  
`[ @skipchecks = ] 'skipchecks'`Gibt an, ob die Update Statistik übersprungen oder ausgeführt werden soll. *wobei skipchecks "* ist ein **nvarchar (10)** -Wert mit dem Standardwert NULL. Um die Update Statistik zu überspringen, geben Sie **true**an Um Update Statistics explizit auszuführen, geben Sie **false**an.  
  
 UPDATE STATISTICS wird standardmäßig ausgeführt, um Informationen zu den Daten in den Tabellen und Indizes zu aktualisieren. Das Ausführen von UPDATE STATISTICS ist nützlich für Datenbanken, die auf Nur-Lese-Medien verschoben werden sollen.  
  
`[ @keepfulltextindexfile = ] 'KeepFulltextIndexFile'`Gibt an, dass die Volltextindex Datei, die der zu trennende Datenbank zugeordnet ist, während des Trenn Vorgangs der Datenbank nicht gelöscht wird. *Keepfulltextindexfile* ist ein **nvarchar (10)** -Wert mit dem Standardwert **true**. Wenn *keepfulltextindexfile* den Wert **false**aufweist, werden alle der Datenbank zugeordneten Volltextindex Dateien und die Metadaten des voll Text Indexes gelöscht, es sei denn, die Datenbank ist schreibgeschützt. Wenn NULL oder **true**, werden voll Text bezogene Metadaten beibehalten.  
  
> [!IMPORTANT]
>  Der ** \@ keepfulltextindexfile** -Parameter wird in einer zukünftigen Version von entfernt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Verwenden Sie diesen Parameter beim Entwickeln neuer Anwendungen nicht, und planen Sie so bald wie möglich das Ändern von Anwendungen, in denen er zurzeit verwendet wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine Datenbank getrennt wird, werden alle Metadaten darin gelöscht. Wenn die Datenbank die Standarddatenbank aller Anmeldekonten war, wird **Master** zur Standarddatenbank.  
  
> [!NOTE]  
>  Informationen dazu, wie Sie die Standarddatenbank aller Anmeldekonten anzeigen, finden Sie unter [sp_helplogins &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md). Wenn Sie über die erforderlichen Berechtigungen verfügen, können Sie die [Alter Login](../../t-sql/statements/alter-login-transact-sql.md) -Anweisung verwenden, um einer Anmeldung eine neue Standarddatenbank zuzuweisen.  
  
## <a name="restrictions"></a>Einschränkungen  
 Eine Datenbank kann nicht getrennt werden, wenn Folgendes zutrifft:  
  
-   Die Datenbank ist zurzeit in Verwendung. Weitere Informationen finden Sie im Abschnitt "Erhalten exklusiven Zugriffs" weiter unten in diesem Thema.  
  
-   Wenn die Datenbank repliziert ist, wird sie veröffentlicht.  
  
     Bevor Sie die Datenbank trennen können, müssen Sie die Veröffentlichung durch Ausführen von [sp_replicationdboption](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)deaktivieren.  
  
    > [!NOTE]  
    >  Wenn Sie **sp_replicationdboption**nicht verwenden können, können Sie die Replikation durch Ausführen von [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)entfernen.  
  
-   Eine Datenbankmomentaufnahme ist in der Datenbank vorhanden.  
  
     Bevor Sie die Datenbank trennen können, müssen Sie alle Momentaufnahmen löschen. Weitere Informationen finden Sie unter [Löschen einer Datenbank-Momentaufnahme &#40;Transact-SQL&#41;](../../relational-databases/databases/drop-a-database-snapshot-transact-sql.md)angefügt werden.  
  
    > [!NOTE]  
    >  Eine Datenbankmomentaufnahme kann nicht getrennt oder angefügt werden.  
  
-   Die Datenbank ist gespiegelt.  
  
     Die Datenbank kann nur getrennt werden, wenn die Datenbank-Spiegelungssitzung beendet wird. Weitere Informationen finden Sie unter [Entfernen der Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md).  
  
-   Die Datenbank ist fehlerverdächtig.  
  
     Sie müssen für eine fehlerverdächtige Datenbank den Notfallmodus aktivieren, bevor Sie die Datenbank trennen können. Weitere Informationen zum Aktivieren des Notfallmodus für eine Datenbank finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
-   Die Datenbank ist eine Systemdatenbank.  
  
## <a name="obtaining-exclusive-access"></a>Erhalten exklusiven Zugriffs  
 Das Trennen einer Datenbank erfordert den exklusiven Zugriff auf die Datenbank. Wenn die zu trennende Datenbank gerade verwendet wird, müssen Sie vor dem Trennen für die Datenbank den SINGLE_USER-Modus festlegen, um exklusiven Zugriff zu erhalten.

 Bevor Sie die Datenbank auf SINGLE_USER festlegen, müssen Sie überprüfen, ob die AUTO_UPDATE_STATISTICS_ASYNC-Option auf OFF festgelegt ist. Wenn diese Option auf ON festgelegt ist, stellt der Hintergrundthread, der zum Aktualisieren von Statistiken verwendet wird, eine Verbindung mit der Datenbank her, und Sie können im Einzelbenutzermodus nicht auf die Datenbank zugreifen. Weitere Informationen finden Sie unter [Festlegen des Einzelbenutzermodus für eine Datenbank](../databases/set-a-database-to-single-user-mode.md).

 Beispielsweise erhält die folgende `ALTER DATABASE` Anweisung exklusiven Zugriff auf die [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] Datenbank, nachdem alle aktuellen Benutzer die Verbindung mit der Datenbank getrennt haben.  
  
```  
USE master;  
ALTER DATABASE AdventureWorks2012  
SET SINGLE_USER;  
GO  
```  
  
> [!NOTE]  
>  Verwenden Sie die Option Rollback, um die aktuellen Benutzer sofort oder innerhalb einer angegebenen Anzahl von Sekunden aus der Datenbank zu erzwingen. verwenden Sie die Option Rollback: ALTER DATABASE *database_name* SET SINGLE_USER with Rollback *rollback_option*. Weitere Informationen zu dieser Einstellung finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="reattaching-a-database"></a>Erneutes Anfügen einer Datenbank  
 Die getrennten Dateien bleiben erhalten und können mithilfe von Create Database (mit der Option for Attach oder for ATTACH_REBUILD_LOG) erneut angefügt werden. Die Dateien können auf einen anderen Server verschoben und dort angefügt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Server Rolle **sysadmin** oder die Mitgliedschaft in der **db_owner** Rolle der Datenbank.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die- [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] Datenbank getrennt, wobei *wobei skipchecks "* auf true festgelegt ist.  
  
```  
EXEC sp_detach_db 'AdventureWorks2012', 'true';  
```  
  
 Im folgenden Beispiel wird die [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank getrennt, wobei die Dateien für den Volltextindex und die Metadaten des Volltextindexes beibehalten werden. Durch diesen Befehl wird UPDATE STATISTICS ausgeführt. Dies entspricht dem Standardverhalten.  
  
```  
exec sp_detach_db @dbname='AdventureWorks2012'  
    , @keepfulltextindexfile='true';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Anfügen und Trennen von Datenbanken &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Trennen einer Datenbank](../../relational-databases/databases/detach-a-database.md)  
  
  
