---
title: Verwenden von PowerShell zum Sichern mehrerer Datenbanken in Azure BLOB Storage Dienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: f7008339-e69d-4e20-9265-d649da670460
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2b0bddf426a7cedaa8f11620355427143bcaa47b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84959600"
---
# <a name="use-powershell-to-backup-multiple-databases-to-azure-blob-storage-service"></a>Verwenden von PowerShell zum Sichern mehrerer Datenbanken im Azure Blob Storage-Dienst
  Dieses Thema enthält Beispielskripts, die verwendet werden können, um Sicherungen im Azure Blob Storage-Dienst mit PowerShell-Cmdlets zu automatisieren.  
  
## <a name="overview-of-powershell-cmdlets-for-backup-and-restore"></a>Übersicht über PowerShell-Cmdlets für Sicherungen und Wiederherstellungen  
 `Backup-SqlDatabase` und `Restore-SqlDatabase` sind die beiden wichtigsten Cmdlets, die für Sicherungs- und Wiederherstellungsvorgänge verfügbar sind. Darüber hinaus gibt es andere Cmdlets, die möglicherweise erforderlich sind, um Sicherungen im Azure Blob Storage-Dienst zu automatisieren, wie den Satz von **SqlCredential**-Cmdlets. Im Anschluss finden Sie eine Liste der PowerShell-Cmdlets, die in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verfügbar sind und die in den Sicherungs- und Wiederherstellungsvorgängen verwendet werden:  
  
 Backup_SqlDatabase  
 Dieses Cmdlet wird verwendet, um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherung zu erstellen.  
  
 Restore-SqlDatabase  
 Wird zum Wiederherstellen einer Datenbank verwendet.  
  
 New-SqlCredential  
 Dieses Cmdlet wird verwendet, um SQL-Anmeldeinformationen zu erstellen, die für die SQL Server-Sicherung in Azure Storage verwendet werden. Weitere Informationen zu Anmelde Informationen und deren Verwendung in SQL Server Sicherung und Wiederherstellung finden Sie unter [SQL Server sichern und Wiederherstellen mit Azure BLOB Storage Dienst](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
 Get-SqlCredential  
 Dieses Cmdlet wird verwendet, um das Objekt mit den Anmeldeinformationen und den entsprechenden Eigenschaften abzurufen.  
  
 Remove-SqlCredential  
 Löscht ein Objekt mit SQL-Anmeldeinformationen.  
  
 Set-SqlCredential  
 Dieses Cmdlet wird verwendet, um die Eigenschaften des Objekts mit SQL-Anmeldeinformationen festzulegen oder zu ändern.  
  
> [!TIP]  
>  Die Cmdlets für Anmeldeinformationen werden in Szenarien für den Azure Blob Storage bei der Sicherung und Wiederherstellung verwendet.  
  
### <a name="powershell-for-multi-database-multi-instance-backup-operations"></a>PowerShell für mehrere Datenbanken, Sicherungsvorgänge mit mehreren Instanzen  
 Die folgenden Abschnitte enthalten die Skripts für verschiedene Vorgänge wie das Erstellen von SQL-Anmeldeinformationen in mehreren SQL Server-Instanzen, das Sichern aller Benutzerdatenbanken in einer Instanz von SQL Server usw. Sie können diese Skripts verwenden, um Sicherungsvorgänge gemäß den Anforderungen Ihrer Umgebung zu automatisieren oder zu planen. Die Skripts, die hier bereitgestellt werden, sind Beispiele und können für Ihre Umgebung geändert oder erweitert werden.  
  
 Folgende Überlegungen sind bei Beispielskripts zu bedenken:  
  
1.  **Navigieren durch SQL Server PowerShell-Pfade:** Windows PowerShell implementiert Cmdlets, um in der Pfadstruktur zu navigieren, die die Hierarchie der von einem PowerShell-Anbieter unterstützten Objekte darstellt. Wenn Sie zu einem Knoten im Pfad navigiert haben, können Sie andere Cmdlets verwenden, um grundlegende Vorgänge für das aktuelle Objekt auszuführen.  
  
2.  `Get-ChildItem`-Cmdlet: Welche Informationen von `Get-ChildItem` zurückgegeben werden, hängt vom Speicherort in einem SQL Server PowerShell-Pfad ab. Wenn der Speicherort auf der Computerebene liegt, gibt dieses Cmdlets alle SQL Server-Datenbank-Engine-Instanzen zurück, die auf dem Computer installiert sind. Wenn der Speicherort aber auf Objektebene, wie z. B. Datenbanken, liegt, dann gibt dieses Cmdlets eine Liste von Datenbankobjekten zurück.  Standardmäßig gibt das `Get-ChildItem`-Cmdlet keine Systemobjekte zurück.  Wenn Sie den -Force-Parameter verwenden, können Sie die Systemobjekte anzeigen.  
  
     Weitere Informationen finden Sie unter [Navigate SQL Server PowerShell Paths](../../powershell/navigate-sql-server-powershell-paths.md).  
  
3.  Die Codebeispiele können unabhängig voneinander ausprobiert werden, indem die Variablenwerte geändert werden. Die Erstellung des Azure-Speicherkontos und der SQL-Anmeldeinformationen sind aber Voraussetzungen, die für alle Sicherungs- und Wiederherstellungsvorgänge im Azure Blob Storage-Dienst erforderlich sind.  
  
### <a name="create-a-sql-credential-on-all-the-instances-of-sql-server"></a>Erstellen von SQL-Anmeldeinformationen für alle Instanzen von SQL Server  
 Es gibt zwei Beispielskripts, und beide erstellen Anmeldeinformationen mit der Bezeichnung „mybackupToURL“ für alle Instanzen von SQL Server auf einem Computer. Das erste Beispiel ist einfach; die Anmeldeinformationen werden erstellt und keine Ausnahmen aufgefangen.  Wenn beispielsweise bereits vorhandene Anmeldeinformationen mit dem gleichen Namen für eine der Instanzen des Computers vorliegen, schlägt das Skript fehl. Im zweiten Beispiel werden Fehler aufgefangen, und das Skript kann fortgesetzt werden.  
  
```powershell
import-module sqlps  
  
# create variables  
$storageAccount = "mystorageaccount"  
$storageKey = "<storageaccesskeyvalue>"  
$secureString = ConvertTo-SecureString $storageKey  -asplaintext -force  
$credentialName = "mybackuptoURL"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
# get the list of instances  
$instances = Get-ChildItem  
#pipe the instances to new-sqlcredentail cmdlet to create SQL credential  
$instances | New-SqlCredential -Name $credentialName -Identity $storageAccount -Secret $secureString  
```  
  
```powershell
import-module sqlps  
  
# set the parameter values
$storageAccount = "mystorageaccount"  
$storageKey = "<storageaccesskeyvalue>"  
$secureString = ConvertTo-SecureString $storageKey  -asplaintext -force  
$credentialName = "mybackuptoURL"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
# get the list of instances  
$instances = Get-ChildItem  
#loop through instances and create a SQL credential, output any errors  
ForEach ($instance In $instances)  
{  
    Try  
{  
     New-SqlCredential -Name $credentialName -path "SQLServer:\SQL\$($instance.name)" -Identity $storageAccount -Secret $secureString -ea Stop
}  
Catch [Exception]  
    {
            Write-Host "instance - $($instance.name): "$_.Exception.Message
    }
 }
```  
  
### <a name="remove-a-sql-credential-from-all-the-instances-of-sql-server"></a>Entfernen von SQL-Anmeldeinformationen für alle Instanzen von SQL Server  
 Dieses Skript kann verwendet werden, um bestimmte Anmeldeinformationen von allen SQL Server-Instanzen auf dem Computer zu entfernen. Wenn das Credential-Objekt in einer bestimmten Instanz nicht vorhanden ist, wird eine Fehlermeldung angezeigt, und das Skript wird fortgesetzt, bis alle Instanzen überprüft sind.  
  
```powershell
import-module sqlps  
  
cd SQLServer:\SQL\COMPUTERNAME  
$credentialName = "mybackuptoURL"  
  
$instances = Get-ChildItem  
  
ForEach ($instance In $instances)  
   {
    Try  
        {  
            $path = "SQLServer:\SQL\$($instance.name)\credentials\$credentialName"   
            Remove-SqlCredential -Path $path -ea stop   
         }  
         Catch [Exception]  
         {  
            Write-Host $_.Exception.Message
        }
    }  
```  
  
### <a name="full-database-backup-for-all-databases-including-system-databases"></a>Vollständige Sicherung für alle Datenbanken (EINSCHLIESSLICH SYSTEMDATENBANKEN)  
 Mit dem folgenden Skript erstellen Sie Sicherungen aller Datenbanken auf dem Computer. Dies gilt sowohl für Benutzerdatenbanken als auch für die **msdb** -Systemdatenbank. Das Skript filtert **tempdb** - und **model** -Systemdatenbanken heraus.  
  
```powershell
import-module sqlps  
# set the parameter values  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackuptoURL"  
  
# cd to computer level
cd SQLServer:\SQL\COMPUTERNAME  
$instances = Get-ChildItem
# loop through each instances and backup up all the  databases -filter out tempdb and model databases  
  
 ForEach ($instance In $instances)  
 {  
   $path = "sqlserver:\sql\$($instance.name)\databases"  
   $alldatabases = Get-ChildItem -Force -path $path | Where-Object {$_.name -ne "tempdb" -and $_.name -ne "model"}   
   $alldatabases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On -script   
 }
```  
  
### <a name="full-database-backup-for-all-user-databases"></a>Vollständige Sicherung ALLER Benutzerdatenbanken  
 Das folgende Skript kann verwendet werden, um alle Benutzerdatenbanken in allen Instanzen von SQL Server auf dem Computer zu sichern.  
  
```powershell
import-module sqlps
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackuptoURL"  
  
# cd to computer level
cd SQLServer:\SQL\COMPUTERNAME  
$instances = Get-ChildItem
# loop through each instances and backup up all the user databases  
 ForEach ($instance In $instances)  
 {  
    $databases = dir "sqlserver:\sql\$($instance.name)\databases"  
    $databases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On
 }  
```  
  
### <a name="full-database-backup-for-master-and-msdb-system-databases-on-all-the-instances-of-sql-server"></a>Vollständige Sicherung für MASTER und MSDB (SYSTEMDATENBANKEN) in allen Instanzen von SQL Server  
 Das folgende Skript kann verwendet werden, um alle **master** - und **msdb** -Datenbanken in allen Instanzen von SQL Server auf dem Computer zu sichern.  
  
```powershell
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackupToUrl"  
$sysDbs = "master", "msdb"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
$instances = Get-ChildItem
ForEach ($instance In $instances)  
 {  
      ForEach ($s In $sysdbs)  
     {  
        Backup-SqlDatabase -Database $s -path "sqlserver:\sql\$($instance.name)" -BackupContainer  $backupUrlContainer -SqlCredential $credentialName -Compression On   
}
 } 
```  
  
### <a name="full-database-backup-for-all-user-databases-on-an-instance-of-sql-server"></a>Vollständige Sicherung für alle Benutzerdatenbanken in einer Instanz von SQL Server  
 Das folgenden Skript wird verwendet, um nur die Benutzerdatenbanken zu sichern, die in einer benannten Instanz von SQL Server verfügbar sind. Das gleiche Skript kann für die Standardinstanz auf dem Computer verwendet werden, indem der $srvPath-Parameterwert geändert wird.  
  
```powershell
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$srvPath = "SQLServer:\SQL\COMPUTERNAME\INSTANCENAME"  # for default instance, the $srvpath variable is "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
$credentialName = "mybackupToUrl"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
  
#retrieves the database objects for a specific instance  
$databases = dir $srvPath\databases  
  
#backup all the user databases  
$databases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On  
```  
  
### <a name="full-database-backup-for-only-system-databases-master-and-msdb-on-an-instance-of-sql-server"></a>Vollständige Sicherung nur für Systemdatenbanken (MASTER UND MSDB) in einer Instanz von SQL Server  
 Das vollständige Skript kann zum Sichern der **master** - und der **msdb** -Datenbanken in einer benannten Instanz von SQL Server verwendet werden. Das gleiche Skript kann für die Standardinstanz auf dem Computer verwendet werden, indem der $srvPath-Parameterwert geändert wird.  
  
```powershell
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$srvPath = "SQLServer:\SQL\COMPUTERNAME\INSTANCENAME" # for default instance, the $srvpath variable is "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
$credentialName = "mybackupToUrl"  
  
#navigate to instance level  
cd $srvPath  
  
$sysDbs = "master", "msdb"  
ForEach ($s In $sysDbs)
{  
Backup-SqlDatabase -Database $s -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On  
}
```  
  
## <a name="see-also"></a>Weitere Informationen
 [SQL Server sichern und Wiederherstellen mit Azure BLOB Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) [SQL Server bewährte Methoden und Problem](sql-server-backup-to-url-best-practices-and-troubleshooting.md) Behandlung bei URLs  
