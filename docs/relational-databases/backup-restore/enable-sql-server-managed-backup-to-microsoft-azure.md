---
title: Verwenden von Managed Backup für Azure
ms.custom: seo-lt-2019
ms.date: 12/17/2019
ms.description: Enable SQL Server managed backup to Azure
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 68ebb53e-d5ad-4622-af68-1e150b94516e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 07bb9cf8f0fc697e1d31a80e22a72cd5a0ea484a
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "75257954"
---
# <a name="enable-sql-server-managed-backup-to-azure"></a>Aktivieren von SQL Server Managed Backup für Azure

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] sowohl auf Datenbank- als auch auf Instanzebene mit Standardeinstellungen aktiviert wird. Außerdem wird erläutert, wie E-Mail-Benachrichtigungen aktiviert und Sicherungsaktivitäten überwacht werden.  
  
 In diesem Tutorial wird Azure PowerShell verwendet. Bevor Sie das Tutorial starten, müssen Sie [Azure PowerShell herunterladen und installieren](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).  
  
> [!IMPORTANT]  
>  Wenn Sie auch erweiterte Optionen aktivieren oder einen benutzerdefinierten Zeitplan verwenden möchten, konfigurieren Sie diese Einstellungen zuerst, bevor Sie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]aktivieren. Weitere Informationen finden Sie unter [Konfigurieren der erweiterten Optionen für die verwaltete Sicherung von SQL Server zu Microsoft Azure](../../relational-databases/backup-restore/configure-advanced-options-for-sql-server-managed-backup-to-microsoft-azure.md).  
  
## <a name="create-the-azure-blob-container"></a>Erstellen des Azure-Blobcontainers

Für den Prozess ist ein Azure-Konto erforderlich. Überspringen Sie diesen Schritt, wenn Sie bereits über ein Konto verfügen. Andernfalls können Sie zum Einstieg eine [kostenlose Testversion](https://azure.microsoft.com/pricing/free-trial/) verwenden oder sich die [Kaufoptionen](https://azure.microsoft.com/pricing/purchase-options/)ansehen.

Weitere Informationen zu Speicherkonten finden Sie unter [Informationen zu Azure-Speicherkonten](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/). 

#### <a name="azure-clitabazure-cli"></a>[Azure-Befehlszeilenschnittstelle](#tab/azure-cli)

1. Melden Sie sich bei Ihrem Azure-Konto an.

    ```azurecli-interactive
    az login
    ```
  
1. Erstellen Sie ein Azure-Speicherkonto. Überspringen Sie diesen Schritt, wenn Sie bereits über ein Speicherkonto verfügen. Der folgende Befehl erstellt ein Speicherkonto namens `<backupStorage>` in der Region USA, Osten.  
  
    ```azurecli-interactive
    az storage account create -n <backupStorage> -l "eastus" --resource-group <resourceGroup>
    ```  
    
1. Erstellen Sie einen Blobcontainer namens `<backupContainer>` für die Sicherungsdateien.
  
    ```azurecli-interactive
    $keys = az storage account keys list --account-name <backupStorage> --resource-group <resourceGroup> | ConvertFrom-Json
    az storage container create --name <backupContainer> --account-name <backupStorage> --account-key $keys[0].value 
    ```  
  
1. Erstellen Sie eine Shared Access Signature (SAS) für den Zugriff auf den Container. Der folgende Befehl erstellt ein SAS-Token für den Blobcontainer `<backupContainer>`, das in einem Jahr abläuft.  
  
    ```azurecli-interactive 
    az storage container generate-sas --name <backupContainer> --account-name <backupStorage> --account-key $keys[0].value
    ```

#### <a name="powershelltabazure-powershell"></a>[PowerShell](#tab/azure-powershell)

1. Mit dem folgenden Befehl erfolgt die Anmeldung beim Azure-Konto.

    ```azurepowershell-interactive
    Connect-AzAccount
    Set-AzContext -SubscriptionId "<subscriptionId>"
    ```
  
1. Erstellen Sie ein Azure-Speicherkonto. Überspringen Sie diesen Schritt, wenn Sie bereits über ein Speicherkonto verfügen. Der folgende Befehl erstellt ein Speicherkonto namens `<backupStorage>` in der Region USA, Osten.  
  
    ```azurepowershell-interactive
    New-AzStorageAccount -StorageAccountName <backupStorage> -Location "EAST US" -ResourceGroupName <resourceGroup> -SkuName Standard_GRS
    ```   
  
1. Erstellen Sie einen Blobcontainer namens `<backupContainer>` für die Sicherungsdateien.  
  
    ```azurepowershell-interactive
    $context = New-AzStorageContext -StorageAccountName <backupStorage> -StorageAccountKey (Get-AzStorageAccountKey -Name <backupStorage> -ResourceGroupName <resourceGroup>).Value[0]  
    New-AzStorageContainer -Name <backupContainer> -Context $context  
    ```  
  
1. Erstellen Sie eine Shared Access Signature (SAS) für den Zugriff auf den Container. Der folgende Befehl erstellt ein SAS-Token für den Blobcontainer `<backupContainer>`, das in einem Jahr abläuft.
  
    ```azurepowershell-interactive 
    New-AzStorageContainerSASToken -Name <backupContainer> -Permission rwdl -ExpiryTime (Get-Date).AddYears(1) -FullUri -Context $context 
    ```

* * *

> [!NOTE]
> Diese Schritte können auch im [Azure-Portal](https://portal.azure.com/) durchgeführt werden.

Die Ausgabe enthält entweder die URL zum Container und/oder das SAS-Token. Es folgt ein Beispiel:  
  
  `https://managedbackupstorage.blob.core.windows.net/backupcontainer?sv=2014-02-14&sr=c&sig=xM2LXVo1Erqp7LxQ%9BxqK9QC6%5Qabcd%9LKjHGnnmQWEsDf%5Q%se=2015-05-14T14%3B93%4V20X&sp=rwdl`
  
Wenn die URL enthalten ist, trennen Sie sie an der Stelle des Fragezeichens vom SAS-Token (ohne das Fragezeichen einzubeziehen). Beispielsweise würde die vorherige Ausgabe zu den folgenden beiden Werten führen.  
  
|||  
|-|-|  
|**Container-URL**|https://managedbackupstorage.blob.core.windows.net/backupcontainer|  
|**SAS-Token**|sv=2014-02-14&sr=c&sig=xM2LXVo1Erqp7LxQ%9BxqK9QC6%5Qabcd%9LKjHGnnmQWEsDf%5Q%se=2015-05-14T14%3B93%4V20X&sp=rwdl|  
|||
  
Speichern Sie die Container-URL und die SAS, um sie beim Erstellen von SQL-Anmeldeinformationen zu verwenden. Weitere Informationen zu SAS finden Sie unter [Shared Access Signatures, Teil 1: Grundlegendes zum SAS-Modell](https://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-1/).  
  
## <a name="enable-managed-backup-to-azure"></a>Aktivieren von Managed Backup für Azure
  
1.  **Erstellen von SQL-Anmeldeinformationen für die SAS-URL:** Verwenden Sie das SAS-Token, um SQL-Anmeldeinformationen für die Blobcontainer-URL zu erstellen. Verwenden Sie in SQL Server Management Studio die folgende Transact-SQL-Abfrage, um die Anmeldeinformationen für die Blobcontainer-URL auf Grundlage des folgenden Beispiels zu erstellen:  
  
    ```sql  
    CREATE CREDENTIAL [https://managedbackupstorage.blob.core.windows.net/backupcontainer]   
    WITH IDENTITY = 'Shared Access Signature',  
    SECRET = 'sv=2014-02-14&sr=c&sig=xM2LXVo1Erqp7LxQ%9BxqK9QC6%5Qabcd%9LKjHGnnmQWEsDf%5Q%se=2015-05-14T14%3B93%4V20X&sp=rwdl'  
    ```  
  
2.  **Sicherstellen, dass der SQL Server-Agent-Dienst ausgeführt wird:** Starten Sie den SQL Server-Agent, wenn er nicht ausgeführt wird.  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] benötigt einen laufenden SQL Server-Agent auf der Instanz, um Sicherungsvorgänge durchführen zu können.  Sie können den Starttyp des SQL Server-Agents auf "Automatisch" festlegen, um zu gewährleisten, dass regelmäßige Sicherungsvorgänge durchgeführt werden können.  
  
3.  **Bestimmen des Aufbewahrungszeitraums:** Bestimmen Sie die Beibehaltungsdauer für die Sicherungsdateien. Die Beibehaltungsdauer wird in Tagen angegeben und kann zwischen 1 und 30 Tagen liegen.  
  
4.  **Aktivieren und Konfigurieren von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]:** Starten Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit der SQL Server-Zielinstanz her. Führen Sie im Abfragefenster folgende Anweisung aus, nachdem Sie die Werte für Datenbankname, Container-URL und Beibehaltungsdauer Ihren Anforderungen entsprechend angepasst haben:  
  
    > [!IMPORTANT]  
    >  Geben Sie zum Aktivieren des Managed Backup auf Instanzebene `NULL` für den `database_name` -Parameter an.  
  
    ```sql  
    USE msdb;  
    GO  
    EXEC msdb.managed_backup.sp_backup_config_basic   
     @enable_backup = 1,   
     @database_name = 'yourdatabasename',  
     @container_url = 'https://managedbackupstorage.blob.core.windows.net/backupcontainer',   
     @retention_days = 30  
    GO  
    ```  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ist damit für die angegebene Datenbank aktiviert. Es kann bis zu 15 Minuten dauern, bis die Sicherungsvorgänge für die Datenbank gestartet werden.  
  
5.  **Überprüfen der Standardkonfiguration für erweiterte Ereignisse:** Überprüfen Sie die Einstellungen für erweiterte Ereignisse, indem Sie die folgende Transact-SQL-Anweisung ausführen.  
  
    ```sql
    SELECT * FROM msdb.managed_backup.fn_get_current_xevent_settings()  
    ```  
  
     Stellen Sie sicher, dass Ereignisse der Kanäle Admin, Operational und Analytical standardmäßig aktiviert sind und nicht deaktiviert werden können. Dies sollte ausreichen, um alle Ereignisse zu überwachen, die ein manuelles Eingreifen erfordern.  Sie können die Debugereignisse ebenfalls aktivieren. Diese Kanäle enthalten jedoch auch Informations- und Debugereignisse, die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] intern zur Erkennung und Behebung von Fehlern verwendet.  
  
6.  **Aktivieren und Konfigurieren der Benachrichtigung für den Integritätsstatus:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] verfügt über eine gespeicherte Prozedur, die einen Agent-Auftrag erstellt, um E-Mail-Benachrichtigungen mit Fehlern oder Warnungen zu senden, die möglicherweise ein Eingreifen erfordern. In den folgenden Schritten wird der Prozess zum Aktivieren und Konfigurieren der E-Mail-Benachrichtigungen beschrieben:  
  
    1.  Richten Sie Datenbank-E-Mail ein, falls diese Funktion auf der Instanz noch nicht aktiviert wurde. Weitere Informationen finden Sie unter [Configure Database Mail](../../relational-databases/database-mail/configure-database-mail.md).  
  
    2.  Konfigurieren Sie SQL Server-Agent-Benachrichtigungen für die Verwendung von Datenbank-E-Mail. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server-Agent-Mail zum Verwenden von Datenbank-E-Mails](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Aktivieren der E-mail-Benachrichtigungen für den Empfang von Sicherungsfehlern und Warnungen:** Führen Sie im Abfragefenster die folgenden Transact-SQL-Anweisungen aus:  
  
        ```sql
        EXEC msdb.managed_backup.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email1;email2>'  
        ```  
  
7.  **Anzeigen von Sicherungsdateien im Azure-Speicherkonto:** Stellen Sie eine Verbindung mit dem Speicherkonto von SQL Server Management Studio oder dem Azure-Portal her. Alle Sicherungsdateien im angegebenen Container werden angezeigt. Beachten Sie, dass innerhalb der ersten 5 Minuten nach dem Aktivieren von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für die Datenbank möglicherweise eine Datenbank und eine Protokollsicherung angezeigt werden.  
  
8.  **Überwachen des Integritätsstatus:**  Sie können die zuvor konfigurierten E-Mail-Benachrichtigungen verwenden oder die protokollierten Ereignisse manuell überwachen. Die folgenden Beispiele zeigen einige Transact-SQL-Anweisungen, mit denen die Ereignisse angezeigt werden können:  
  
    ```sql  
    --  view all admin events  
    USE msdb;  
    GO  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC managed_backup.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
    ```  
  
    ```sql  
    -- to enable debug events  
    USE msdb;  
    GO  
    EXEC managed_backup.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
    ```  
  
    ```sql  
    --  View all events in the current week  
    USE msdb;  
    GO  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC managed_backup.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
    ```
  
Die in diesem Abschnitt beschriebenen Schritte sind speziell für die erste Konfiguration von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für die Datenbank vorgesehen. Mithilfe derselben gespeicherten Systemprozeduren können Sie vorhandene Konfigurationen bearbeiten und neue Werte festlegen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Managed Backup für Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
