---
title: sp_migrate_user_to_contained (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/11/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_migrate_user_to_contained
- sp_migrate_user_to_contained_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_migrate_user_to_contained
ms.assetid: b3a49ff6-46ad-4ee7-b6fe-7e54213dc33e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d3faf15999e0c157859e3d2eee9c4119ab344844
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727149"
---
# <a name="sp_migrate_user_to_contained-transact-sql"></a>sp_migrate_user_to_contained (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Konvertiert einen Datenbankbenutzer, der mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen verknüpft ist, in den Benutzer einer enthaltenen Datenbank mit Kennwort. In einer eigenständigen Datenbank können Sie mit diesem Verfahren Abhängigkeiten für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entfernen, in der die Datenbank installiert ist. **sp_migrate_user_to_contained** trennt den Benutzer vom ursprünglichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmelde Namen, damit Einstellungen wie Kennwort und Standardsprache für die eigenständige Datenbank separat verwaltet werden können. **sp_migrate_user_to_contained** kann verwendet werden, bevor die enthaltene Datenbank in eine andere Instanz von verschoben wird [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , um Abhängigkeiten von den aktuellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instanzanmeldungen auszuschließen.  
  
> [!NOTE]
> Seien Sie vorsichtig, wenn Sie **sp_migrate_user_to_contained**verwenden, da Sie den Effekt nicht umkehren können. Diese Prozedur wird nur in einer eigenständigen Datenbank verwendet. Weitere Informationen finden Sie unter [eigenständige Datenbanken](../../relational-databases/databases/contained-databases.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_migrate_user_to_contained [ @username = ] N'user' ,   
    [ @rename = ] { N'copy_login_name' | N'keep_name' } ,   
    [ @disablelogin = ] { N'disable_login' | N'do_not_disable_login' }   
```  
  
## <a name="arguments"></a>Argumente  
 [** @username =** ] **N '***Benutzer***'**  
 Der Name eines Benutzers in der aktuellen eigenständigen Datenbank, der mit einem authentifizierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen verknüpft ist. Der Wert ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert **null**.  
  
 [** @rename =** ] **N '***copy_login_name***'**  |  **N '***keep_name***'**  
 Wenn ein Datenbankbenutzer, der auf einem Anmelde Namen basiert, einen anderen Benutzernamen als den Anmelde Namen hat, verwenden Sie *keep_name* , um den Datenbankbenutzer Namen während der Migration beizubehalten. Verwenden Sie *copy_login_name* , um den neuen eigenständigen Datenbankbenutzer mit dem Namen der Anmeldung anstelle des Benutzers zu erstellen. Wenn der Benutzername eines Datenbankbenutzers dem Anmeldenamen entspricht, wird mit beiden Optionen der Benutzer der enthaltenen Datenbank erstellt, ohne den Namen zu ändern.  
  
 [** @disablelogin =** ] **N '***disable_login***'**  |  **N '***do_not_disable_login***'**  
 *disable_login* deaktiviert den Anmelde Namen in der Master-Datenbank. Um eine Verbindung herzustellen, wenn die Anmeldung deaktiviert ist, muss die Verbindung den Namen der eigenständigen Datenbank als **anfangs Katalog** als Teil der Verbindungs Zeichenfolge bereitstellen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_migrate_user_to_contained** erstellt den Benutzer der eigenständigen Datenbank mit Kennwort, unabhängig von den Eigenschaften oder Berechtigungen des Anmelde namens. Beispielsweise kann die Prozedur erfolgreich ausgeführt werden, wenn die Anmeldung deaktiviert ist oder dem Benutzer die **Connect** -Berechtigung für die Datenbank verweigert wird.  
  
 **sp_migrate_user_to_contained** weist die folgenden Einschränkungen auf.  
  
-   Der Benutzername darf nicht bereits in der Datenbank vorhanden sein.  
  
-   Integrierte Benutzer wie dbo und guest, können nicht konvertiert werden.  
  
-   Der Benutzer kann nicht in der **EXECUTE AS** -Klausel einer signierten gespeicherten Prozedur angegeben werden.  
  
-   Der Benutzer kann keine gespeicherte Prozedur besitzen, die die **Execute As Owner** -Klausel einschließt.  
  
-   **sp_migrate_user_to_contained** kann nicht in einer Systemdatenbank verwendet werden.  
  
## <a name="security"></a>Sicherheit  
 Achten Sie beim Migrieren von Benutzern darauf, dass nicht alle Administratoranmeldungen von der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gelöscht werden. Wenn alle Anmeldungen gelöscht werden, finden Sie weitere Informationen unter [Herstellen einer Verbindung mit SQL Server, wenn System Administratoren gesperrt sind](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md).  
  
 Wenn die Anmeldung " **BUILTIN\Administrators** " vorhanden ist, können Administratoren eine Verbindung herstellen, indem Sie Ihre Anwendung mit der Option **als Administrator ausführen** starten.  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die **CONTROL SERVER** -Berechtigung.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-migrating-a-single-user"></a>A. Migrieren eines einzelnen Benutzers  
 Im folgenden Beispiel wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldename `Barry` in den Benutzer einer enthaltenen Datenbankbenutzer mit Kennwort migriert. Im Beispiel wird der Benutzername nicht geändert, und der Anmelde Name wird als aktiviert beibehalten.  
  
```sql  
sp_migrate_user_to_contained   
@username = N'Barry',  
@rename = N'keep_name',  
@disablelogin = N'do_not_disable_login' ;  
  
```  
  
### <a name="b-migrating-all-database-users-with-logins-to-contained-database-users-without-logins"></a>B. Migrieren aller Datenbankbenutzer mit Anmeldenamen zu Benutzern in eigenständigen Datenbanken ohne Anmeldenamen  
 Im folgenden Beispiel werden alle Benutzer, die auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldungen basieren, in Benutzer enthaltener Datenbanken mit Kennwörtern migriert. Nicht berücksichtigt werden Anmeldungen, die nicht aktiviert sind. Das Beispiel muss in der enthaltenen Datenbank ausgeführt werden.  
  
```sql  
DECLARE @username sysname ;  
DECLARE user_cursor CURSOR  
    FOR   
        SELECT dp.name   
        FROM sys.database_principals AS dp  
        JOIN sys.server_principals AS sp   
        ON dp.sid = sp.sid  
        WHERE dp.authentication_type = 1 AND sp.is_disabled = 0;  
OPEN user_cursor  
FETCH NEXT FROM user_cursor INTO @username  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
        EXECUTE sp_migrate_user_to_contained   
        @username = @username,  
        @rename = N'keep_name',  
        @disablelogin = N'disable_login';  
    FETCH NEXT FROM user_cursor INTO @username  
    END  
CLOSE user_cursor ;  
DEALLOCATE user_cursor ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Migrieren zu einer teilweise eigenständigen Datenbank](../../relational-databases/databases/migrate-to-a-partially-contained-database.md)   
 [Eigenständige Datenbanken](../../relational-databases/databases/contained-databases.md)  
  
  
