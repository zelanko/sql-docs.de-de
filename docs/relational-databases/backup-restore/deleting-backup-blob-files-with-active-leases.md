---
title: Löschen von BLOB-Sicherungsdateien mit aktiver Lease | Microsoft-Dokumentation
description: Wenn eine SQL Server-Sicherung oder -Wiederherstellung fehlschlägt, kann dies zu einem verwaisten Blob in Azure Storage führen. Hier erfahren Sie, wie Sie ein verwaistes Blob entfernen.
ms.custom: ''
ms.date: 08/17/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 13a8f879-274f-4934-a722-b4677fc9a782
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 95b7165fb16832b8b76e6a9c7a331433d49ff0a9
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91809636"
---
# <a name="delete-backup-blob-files-with-active-leases"></a>Löschen von Blob-Sicherungsdateien mit aktiven Leases

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Wenn Sicherungs- oder Wiederherstellungsvorgänge in Microsoft Azure Storage ausgeführt werden, reserviert SQL Server eine Lease für eine unbegrenzte Dauer, um den exklusiven Zugriff auf das Blob zu gewährleisten. Nachdem die Sicherung oder Wiederherstellung erfolgreich abgeschlossen wurde, wird die Lease wieder freigegeben. Wenn eine Sicherung oder Wiederherstellung fehlschlägt, wird im Rahmen des Sicherungsvorgangs versucht, ungültige Blobs zu bereinigen. Kann die Sicherung jedoch aufgrund eines längeren bzw. dauerhaften Netzwerkverbindungsfehlers nicht ausgeführt werden, ist der Sicherungsvorgang u. U. nicht in der Lage, auf das BLOB zuzugreifen, sodass das BLOB verwaist ist. Dies bedeutet, dass das Blob erst wieder beschreibbar ist bzw. gelöscht werden kann, nachdem die Lease freigegeben wurde. In diesem Thema wird beschrieben, wie die Lease freigegeben (abgeschaltet) und das Blob gelöscht wird.
  
Weitere Informationen zu Leasetypen finden Sie [in diesem Artikel](/rest/api/storageservices/Lease-Blob).  
  
Ist der Sicherungsvorgang fehlerhaft, kann eine ungültige Sicherungsdatei generiert werden. Außerdem kann für die BLOB-Sicherungsdatei eine aktive Lease bestehen, die verhindert, dass sie gelöscht oder überschrieben wird. Zum Löschen oder Überschreiben derartiger Blobs sollte die Lease zuerst freigegeben (abgeschaltet) werden. Bei Backupfehlern wird empfohlen, dass Sie die Leases bereinigen und Blobs löschen. Im Rahmen Ihrer Speicherverwaltungsaufgaben können Sie auch in regelmäßigen Abständen Leases bereinigen und Blobs löschen.  
  
Da bei einem Wiederherstellungsfehler nachfolgende Wiederherstellungen nicht blockiert werden, stellt eine aktive Lease u. U. kein Problem dar. Die Unterbrechung der Lease ist nur erforderlich, wenn das BLOB überschrieben oder gelöscht werden muss.  
  
## <a name="manage-orphaned-blobs"></a>Verwalten verwaister Blobs

In den folgenden Schritten wird beschrieben, wie nach einem fehlerhaften Sicherungs- oder Wiederherstellungsvorgang ein Cleanup ausgeführt wird. Sämtliche Schritte können mithilfe von PowerShell-Skripts ausgeführt werden. Im folgenden Abschnitt wird ein Beispiel-PowerShell-Skript dargestellt:  
  
1. **Ermitteln von Blobs mit Leases:** Falls Sie über ein Skript oder einen Prozess zum Ausführen der Sicherungsvorgänge verfügen, können Sie den Fehler möglicherweise innerhalb des Skripts oder Prozesses ermitteln und die Blobs entsprechend bereinigen.  Sie können die Blobs mit aktiven Leases auch mithilfe den Eigenschaften „LeaseStats“ und „LeastState“ identifizieren. Nachdem Sie die Blobs identifiziert haben, überprüfen Sie die Liste, stellen Sie sicher, dass die Sicherungsdatei gültig ist, und löschen Sie erst dann das Blob.  
  
1. **Unterbrechen der Lease:** Durch eine autorisierte Anforderung kann die Lease ohne Angabe einer Lease-ID unterbrochen werden. Weitere Informationen finden Sie [hier](/rest/api/storageservices/Lease-Blob) .  
  
    > [!TIP]  
    > SQL Server gibt eine Lease-ID aus, um während des Wiederherstellungsvorgangs einen exklusiven Zugriff zu gewährleisten. Die ID für die Wiederherstellungslease lautet BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2.  
  
1. **Löschen des Blobs:** Um ein BLOB mit einer aktiven Lease zu löschen, müssen Sie zunächst die Lease unterbrechen.  

###  <a name="powershell-script-example"></a><a name="Code_Example"></a> Beispiel für ein PowerShell-Skript  
  
> [!IMPORTANT]
> Bei Verwendung von PowerShell 2.0 können Probleme beim Laden der Assembly Microsoft.WindowsAzure.Storage.dll auftreten. Es wird empfohlen, ein Upgrade von [PowerShell](/powershell/) auszuführen, um das Problem zu beheben. Lassen Sie die .NET 2.0- und .NET 4.0-Assemblys zur Laufzeit laden. Dazu können Sie auch die folgende Problemumgehung verwenden, um die Datei powershell.exe.config zu erstellen bzw. eine bereits vorhandene Datei mit folgendem Code zu ändern:  
>
> ```xml
> <?xml version="1.0"?>
>     <configuration>
>         <startup useLegacyV2RuntimeActivationPolicy="true">
>             <supportedRuntime version="v4.0.30319"/>
>             <supportedRuntime version="v2.0.50727"/>
>         </startup>
>     </configuration>  
> ```  
  
 Das folgende Beispielskript ermittelt Blobs mit aktiven Leases und schaltet sie anschließend ab. Das Beispiel zeigt auch, wie Sie nach freigegebenen Lease-IDs filtern.  
  
#### <a name="tips-on-running-this-script"></a>Tipps zum Ausführen des Skripts
  
> [!WARNING]  
> Wenn zeitgleich mit diesem Skript eine Sicherung im Azure Blob Storage ausgeführt wird, kann die Sicherung fehlschlagen, weil durch das Skript die Lease unterbrochen wird, die der Sicherungsvorgang zu reservieren versucht. Führen Sie das Skript während eines Wartungsfensters oder in Phasen aus, in denen keine Sicherungsaktivitäten ausgeführt werden oder zu erwarten sind.  
  
- Geben Sie vor Ausführen des Skripts Werte für folgende Parameter an: Speicherkonto, Speicherschlüssel und Container sowie Pfad und Name der Azure Storage-Assembly. Der Pfad der Speicherassembly entspricht dem Installationsverzeichnis der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz. Der Dateiname der Speicherassembly lautet "Microsoft.WindowsAzure.Storage.dll".
  
- Wenn Blobs mit gesperrten Leases vorhanden sind, sollten Meldungen ähnlich den folgenden angezeigt werden: `There are no blobs with locked lease status`
  
- Wenn Blobs mit gesperrten Leases vorhanden sind, sollten Meldungen ähnlich den folgenden angezeigt werden: `Breaking Leases`, `The lease on <URL of the Blob> is a restore lease: You will see this message only if you have a blob with a restore lease that is still active.` und `The lease on <URL of the Blob> is not a restore lease Breaking lease on <URL of the Bob>.`
  
```powershell
$storageAccount = "<myStorageAccount>"
$storageKey = "<myStorageKey>"
$blobContainer = "<myBlobContainer>"
$storageAssemblyPathName = "<myStorageAssemblyPathName>"
  
# well known Restore Lease ID  
$restoreLeaseId = "BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2"  
  
# load the storage assembly without locking the file for the duration of the PowerShell session  
$bytes = [System.IO.File]::ReadAllBytes($storageAssemblyPath)  
[System.Reflection.Assembly]::Load($bytes)  
  
$cred = New-Object 'Microsoft.WindowsAzure.Storage.Auth.StorageCredentials' $storageAccount, $storageKey  
$client = New-Object 'Microsoft.WindowsAzure.Storage.Blob.CloudBlobClient' "https://$storageAccount.blob.core.windows.net", $cred  
$container = $client.GetContainerReference($blobContainer)  
  
# list all the blobs  
$blobs = $container.ListBlobs($null,$true)
  
# filter blobs that are have Lease Status as "locked"
$lockedBlobs = @()  
foreach($blob in $blobs)  
{  
    $blobProperties = $blob.Properties
    if($blobProperties.LeaseStatus -eq "Locked")  
    {  
        $lockedBlobs += $blob  
    }  
}  

if($lockedBlobs.Count -gt 0)  
{  
    Write-Host "Breaking leases..."
    foreach($blob in $lockedBlobs )
    {  
        try  
        {  
            $blob.AcquireLease($null, $restoreLeaseId, $null, $null, $null)  
            Write-Host "The lease on $($blob.Uri) is a restore lease."  
        }  
        catch [Microsoft.WindowsAzure.Storage.StorageException]  
        {  
            if($_.Exception.RequestInformation.HttpStatusCode -eq 409)  
            {  
                Write-Host "The lease on $($blob.Uri) is not a restore lease."  
            }  
        }  
  
        Write-Host "Breaking lease on $($blob.Uri)."  
        $blob.BreakLease($(New-TimeSpan), $null, $null, $null) | Out-Null  
    }  
} else { Write-Host " There are no blobs with locked lease status." }
```  
  
## <a name="see-also"></a>Weitere Informationen

[SQL Server-Sicherung über URLs – bewährte Methoden und Problembehandlung](../../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)