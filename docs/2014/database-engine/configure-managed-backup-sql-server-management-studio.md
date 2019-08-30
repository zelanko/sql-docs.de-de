---
title: Konfigurieren der verwalteten Sicherung (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.managedbackup.configure.f1
ms.assetid: 79397cf6-0611-450a-b0d8-e784a76e3091
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 021db5a2283eb6ec68ea80302e938f08e7ba1a5c
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154339"
---
# <a name="configure-managed-backup-sql-server-management-studio"></a>Konfigurieren der verwalteten Sicherung (SQL Server Management Studio)
  Im Dialogfeld für die **verwaltete Sicherung** können [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Sie die Standardwerte für die-Instanz konfigurieren. In diesem Thema wird beschrieben, wie Sie mit diesem Dialogfeld die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Standardeinstellungen für die Instanz konfigurieren und welche Optionen Sie dabei berücksichtigen müssen. Wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für die Instanz konfiguriert ist, gelten die Einstellungen gelten für jede danach erstellte Datenbank.  
  
 Wenn Sie für eine bestimmte [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Datenbank konfigurieren möchten, finden Sie weitere Informationen unter [aktivieren und konfigurieren SQL Server verwalteten Sicherung in Azure für eine-Datenbank](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).  
 
> [!NOTE] 
> SQL Server Managed Backup wird nicht von Proxyservern unterstützt. 
  
## <a name="task-list"></a>Aufgabenliste  
  
## <a name="includess_smartbackupincludesss-smartbackup-mdmd-functions-using-managed-backup-interface-in-sql-server-management-studio"></a>[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Funktionen mithilfe der Schnittstelle für verwaltete Sicherung in SQL Server Management Studio  
 In dieser Version können Sie nur die Standardeinstellungen auf Instanzebene mithilfe der **Verwaltungs Sicherungs** Schnittstelle konfigurieren. Sie können [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] nicht für eine Datenbank konfigurieren, keine [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Vorgänge anhalten oder fortsetzen und keine E-Mail-Benachrichtigungen einrichten. Informationen zum Ausführen von Vorgängen, die derzeit nicht über die **verwaltete Sicherungs** Schnittstelle unterstützt werden, finden Sie unter [SQL Server Managed Backup to Azure-Retention and Storage Settings](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).  
  
## <a name="permissions"></a>Berechtigungen  
 **Der Knoten "verwaltete Sicherung anzeigen" ist SQL Server Management Studio:** Um den Knoten **verwaltete Sicherung** in **Objekt-Explorer**anzuzeigen, müssen Sie entweder System Administrator sein oder über die folgenden Berechtigungen verfügen, die speziell für Ihr Benutzerkonto gewährt werden:  
  
-   `db_backupoperator`  
  
-   `VIEW SERVER STATE`  
  
-   `ALTER ANY CREDENTIAL`  
  
-   `VIEW ANY DEFINITION`  
  
-   `EXECUTE`ein `smart_admin.fn_is_master_switch_on`.  
  
-   `SELECT`ein `smart_admin.fn_backup_instance_config`.  
  
 So konfigurieren Sie die **verwaltete Sicherung:** zum Konfigurieren [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] von in SQL Server Management Studio müssen Sie System Administrator sein oder über die folgenden Berechtigungen verfügen:  
  
 Mitglied der `db_backupoperator`-Datenbankrolle mit Berechtigungen `ALTER ANY CREDENTIAL` und `EXECUTE` für gespeicherte Prozedur `sp_delete_backuphistory`.  
  
 `SELECT`Berechtigungen für die `smart_admin.fn_get_current_xevent_settings` Funktion.  
  
 `EXECUTE`Berechtigungen für die `smart_admin.sp_get_backup_diagnostics` gespeicherte Prozedur. Außerdem sind `VIEW SERVER STATE`-Berechtigungen erforderlich, da andere Systemobjekte, die diese Berechtigung erfordern, intern aufgerufen werden.  
  
 `EXECUTE`Berechtigungen für `smart_admin.sp_set_instance_backup` und `smart_admin.sp_backup_master_switch`.  
  
## <a name="configure-includess_smartbackupincludesss-smartbackup-mdmd-using-sql-server-management-studio"></a>Konfigurieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] mit SQL Server Management Studio  
 Erweitern Sie im **Objekt-Explorer**den Knoten **Verwaltung** , und klicken Sie mit der rechten Maustaste auf **Managed Backup**. Wählen Sie **Konfigurieren**aus. Das Dialogfeld **Managed Backup** wird geöffnet.  
  
 Aktivieren Sie die Option **verwaltete Sicherung aktivieren** , und geben Sie die Konfigurationswerte an:  
  
 Die Beibehaltungs Dauer für **Dateien** wird in Tagen angegeben und sollte zwischen 1 und 30 liegen.  
  
 Die **SQL** -Anmelde Informationen, die Sie auswählen, müssen dem Speicherkonto entsprechen. Wenn Sie derzeit nicht über SQL-Anmelde Informationen verfügen, in denen die Authentifizierungsinformationen gespeichert sind, können Sie eine erstellen, indem Sie auf **Erstellen**klicken. Sie können die Anmeldeinformationen auch mit der CREATE CREDENTIAL-Transact-SQL-Anweisung erstellen, und den Speicherkontonamen für die Identität des Speicherkontos und den Zugriffsschlüssel für die geheimen Parameter angeben. Weitere Informationen finden Sie unter [Create a Credential](../relational-databases/backup-restore/sql-server-backup-to-url.md#credential).  
  
 Geben Sie die **Speicher-URL** für das Azure-Speicherkonto, die SQL-Anmelde Informationen, in denen die Authentifizierungsinformationen für das Speicherkonto gespeichert sind, und die Beibehaltungs Dauer für die Sicherungsdateien an.  
  
 Das Format der Speicher-URL lautet\<: https://storageaccount >. BLOB. Core. Windows. net/  
  
 Um die Verschlüsselungseinstellungen auf Instanzebene festzulegen, aktivieren Sie die Option **Sicherung verschlüsseln** , und geben Sie den Algorithmus und ein Zertifikat oder einen asymmetrischen Schlüssel an, der für die Verschlüsselung verwendet werden soll.  Dies wird auf Instanzebene festgelegt und für alle neuen nach der Anwendung dieser Konfiguration erstellten Datenbanken verwendet.  
  
> [!WARNING]  
>  Die Verschlüsselungsoptionen können nicht in diesem Dialogfeld ohne die Konfiguration von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] angegeben werden. Diese Verschlüsselungsoptionen gelten nur für [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Vorgänge. Informationen zum Verwenden der Verschlüsselung für andere Sicherungs Prozeduren finden Sie unter [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).  
  
### <a name="considerations"></a>Weitere Überlegungen  
 Wenn Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf Instanzebene konfigurieren, gelten die Einstellungen nur für alle nach diesem Zeitpunkt neu erstellten Datenbanken.  Diese Einstellungen werden jedoch nicht automatisch von vorhandenen Datenbanken geerbt. Zum Konfigurieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für bereits vorhandene Datenbanken müssen Sie jede Datenbank konfigurieren. Weitere Informationen finden Sie unter [aktivieren und konfigurieren SQL Server verwalteten Sicherung in Azure für eine-Datenbank](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).  
  
 Wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] mithilfe der `smart_admin.sp_backup_master_switch`angehalten wurde, wird eine Warnmeldung angezeigt: "die verwaltete Sicherung ist deaktiviert, und die aktuellen Konfigurationen werden nicht wirksam..." Wenn Sie versuchen, die Konfiguration abzuschließen. Verwenden Sie `smart_admin.sp_backup_master_switch` die gespeicherte und legen @new_stateSie den Wert = 1 fest. Damit werden die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Dienste fortgesetzt und die Konfigurationseinstellungen angewendet. Weitere Informationen zur gespeicherten Prozedur finden Sie unter [smart_admin. sp_ backup_master_switch &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql).  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server verwaltete Sicherung in Azure: Interoperabilität und Koexistenz](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
  
