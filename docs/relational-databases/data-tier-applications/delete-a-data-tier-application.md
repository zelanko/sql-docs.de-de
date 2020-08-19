---
description: Löschen einer Datenebenenanwendung
title: Löschen einer Datenebenenanwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.deletedacwizard.deletedac.f1
- sql13.swb.deletedacwizard.summary.f1
- sql13.swb.deletedacwizard.introduction.f1
- sql13.swb.deletedacwizard.choosemethod.f1
helpviewer_keywords:
- How to [DAC], delete
- data-tier application [SQL Server], delete
- wizard [DAC], delete
- delete DAC
ms.assetid: 16fe1c18-4486-424d-81d6-d276ed97482f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2bde888ff6091ae8d05445acce1afb1469843c18
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386636"
---
# <a name="delete-a-data-tier-application"></a>Löschen einer Datenebenenanwendung
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Sie können eine Datenebenenanwendung entweder mit dem Assistenten zum Löschen von Datenebenenanwendungen oder mit einem Windows PowerShell-Skript löschen. Sie können angeben, ob die zugeordnete Datenbank beibehalten, getrennt oder gelöscht wird.  
  
-   **Vorbereitungen:**  [Begrenzungen und Einschränkungen](#LimitationsRestrictions), [Berechtigungen](#Permissions)  
  
-   **So aktualisieren Sie eine DAC:**  [dem Assistenten zum Registrieren von Datenschichtanwendungen](#UsingDeleteDACWizard), [PowerShell](#DeleteDACPowerShell)  
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Wenn Sie eine Instanz einer Datenebenenanwendung (Data-Tier Application, DAC) löschen, legen Sie mit einer von drei Optionen fest, wie mit der der Datenebenenanwendung zugeordneten Datenbank verfahren werden soll. Durch alle drei Optionen werden die Metadaten der DAC-Definition gelöscht. Die Optionen unterscheiden sich in der Art, wie mit der Datenbank, die der Datenebenenanwendung zugeordnet ist, verfahren wird. Der Assistent löscht keine der Objekte auf Instanzebene, wie Anmeldenamen, die der DAC oder Datenbank zugeordnet sind.  
  
|Option|Datenbankaktionen|  
|------------|----------------------|  
|Registrierung löschen|Die zugeordnete Datenbank bleibt intakt.|  
|Datenbank trennen|Die zugeordnete Datenbank wird getrennt. Die Instanz der Datenbank-Engine kann nicht auf die Datenbank verweisen, die Daten und Protokolldateien bleiben jedoch intakt.|  
|Datenbank löschen|Die zugeordnete Datenbank wird gelöscht. Die Daten und Protokolldateien werden gelöscht.|  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Einschränkungen  
 Nach dem Löschen einer DAC gibt es keinen automatischen Mechanismus zum Wiederherstellen der Metadaten der DAC-Definition oder -Datenbank. Es hängt von der Löschoption ab, wie Sie die DAC-Instanz manuell neu erstellen können.  
  
|Option|Wiederherstellen der DAC-Instanz|  
|------------|-------------------------------------|  
|Registrierung löschen|Registrieren Sie eine DAC von der Datenbank, die nicht gelöscht wurde.|  
|Datenbank trennen|Fügen Sie die Datenbank erneut mit **sp_attachdb** oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]an, und registrieren Sie anschließend eine neue DAC-Instanz von der Datenbank.|  
|Datenbank löschen|Stellen Sie die Datenbank von einer vollständigen Sicherung, die vor dem Löschen der DAC erstellt wurde, wieder her, und registrieren Sie dann eine neue DAC-Instanz von der Datenbank.|  
  
> [!WARNING]  
>  Wenn Sie eine DAC-Instanz wiederherstellen, indem Sie eine DAC von einer wiederhergestellten oder erneut angefügten Datenbank registrieren, werden einige Teile der ursprünglichen DAC, z. B. die Richtlinie zur Serverauswahl, nicht neu erstellt.  
  
###  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Eine DAC kann nur von Mitgliedern der festen Serverrollen **sysadmin** bzw. **serveradmin** oder vom Datenbankbesitzer gelöscht werden. Außerdem kann das integrierte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Systemadministratorkonto mit der Bezeichnung **sa** zum Starten des Assistenten verwendet werden.  
  
##  <a name="using-the-delete-data-tier-application-wizard"></a><a name="UsingDeleteDACWizard"></a> Verwenden des Assistenten zum Löschen von Datenebenenanwendungen  
 **So löschen Sie eine DAC mithilfe eines Assistenten**  
  
1.  Erweitern Sie im **Objekt-Explorer**den Knoten für die Instanz, die die zu löschende DAC enthält.  
  
2.  Erweitern Sie den Knoten **Verwaltung** .  
  
3.  Erweitern Sie den Knoten **Datenebenenanwendungen** .  
  
4.  Klicken Sie mit der rechten Maustaste auf die zu löschende DAC, und wählen Sie anschließend **Datenebenenanwendung löschen...** aus.  
  
5.  Bearbeiten Sie die Dialogfenster des Assistenten:  
  
    1.  [Introduction (Einführung)](#Introduction)  
  
    2.  [Methode auswählen](#Choose_method)  
  
    3.  [Zusammenfassung](#Summary)  
  
    4.  [Datenebenenanwendung löschen](#Delete_datatier_application)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> Seite "Einführung"  
 Auf dieser Seite werden die Schritte zum Löschen einer Datenebenenanwendung beschrieben.  
  
 **Diese Seite nicht mehr anzeigen.** – Aktivieren Sie dieses Kontrollkästchen, damit die Seite in Zukunft nicht mehr angezeigt wird.  
  
 **Weiter >** – Geht zur Seite **Methode auswählen** über.  
  
 **Abbrechen** – Beendet den Assistenten, ohne eine Datenebenenanwendung oder Datenbank zu löschen.  
  
 [Verwenden des Assistenten zum Löschen von Datenebenenanwendungen](#UsingDeleteDACWizard)  
  
##  <a name="choose-method-page"></a><a name="Choose_method"></a> Seite "Methode auswählen"  
 Auf dieser Seite können Sie die Option zum Behandeln der der zu löschenden DAC zugeordneten Datenbank angeben.  
  
 **Registrierung löschen** – Entfernt die Metadaten, die die Datenebenenanwendung definieren, während die zugeordnete Datenbank intakt bleibt.  
  
 **Datenbank trennen** – Entfernt die Metadaten, die die Datenebenenanwendung definieren, und trennt die zugeordnete Datenbank.  
  
 Von dieser [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz kann nicht mehr auf die Datenbank verwiesen werden, während die Daten und Protokolldateien jedoch intakt bleiben.  
  
 **Datenbank löschen** – Entfernt die Metadaten, die die DAC definieren, und löscht die zugeordnete Datenbank.  
  
 Die Daten und Protokolldateien für die Datenbank werden dauerhaft gelöscht.  
  
 **< Zurück**: Kehrt zur Seite **Einführung** zurück.  
  
 **Weiter >**: Geht zur Seite **Zusammenfassung** über.  
  
 **Abbrechen** – Beendet den Assistenten, ohne die DAC oder Datenbank zu löschen.  
  
 [Verwenden des Assistenten zum Löschen von Datenebenenanwendungen](#UsingDeleteDACWizard)  
  
##  <a name="summary-page"></a><a name="Summary"></a> Seite "Zusammenfassung"  
 Verwenden Sie diese Seite, um die Aktionen zu überprüfen, die der Assistent beim Löschen der DAC-Instanz ausführt.  
  
 **Überprüfen Sie Ihre Auswahl** – Überprüfen Sie die DAC, Datenbank und Löschmethode, die im Feld angezeigt werden. Wenn die Informationen richtig sind, wählen Sie entweder **Weiter** oder **Fertig stellen** aus, um die DAC zu löschen. Falls die DAC und die Datenbankinformationen nicht richtig sind, klicken Sie auf **Abbrechen** und wählen dann die richtige DAC aus. Wenn die Löschmethode nicht richtig ist, wählen Sie **Zurück** aus, um zur Seite **Methode auswählen** zurückzukehren, und wählen eine andere Methode aus.  
  
 **< Zurück** – Kehrt zur Seite **Methode auswählen** zurück, um eine andere Löschmethode auszuwählen.  
  
 **Weiter >** – Löscht die DAC-Instanz unter Verwendung der auf der vorherigen Seite ausgewählten Methode und geht zur Seite **Datenebenenanwendung löschen** über.  
  
 **Abbrechen** – Beendet den Assistenten, ohne die DAC-Instanz zu löschen.  
  
 [Verwenden des Assistenten zum Löschen von Datenebenenanwendungen](#UsingDeleteDACWizard)  
  
##  <a name="delete-data-tier-application-page"></a><a name="Delete_datatier_application"></a> Seite "Datenebenenanwendung löschen"  
 Auf dieser Seite wird angegeben, ob der Löschvorgang erfolgreich war oder fehlgeschlagen ist.  
  
 **Die DAC wird gelöscht** – Gibt an, ob die Aktionen zum Löschen der DAC-Instanz erfolgreich waren oder fehlgeschlagen sind. Überprüfen Sie die Informationen, um zu bestimmen, ob die einzelnen Aktionen erfolgreich waren oder fehlgeschlagen sind. Für alle Aktionen, die fehlerhaft waren, ist in der Spalte **Ergebnis** ein Link enthalten. Klicken Sie auf den Link, um einen Bericht des für diese Aktion aufgetretenen Fehlers anzuzeigen.  
  
 **Bericht speichern** – Klicken Sie auf diese Schaltfläche, um den Löschbericht in einer HTML-Datei zu speichern. In der Datei ist der Status der einzelnen Aktionen aufgeführt, einschließlich aller durch die Aktionen generierten Fehler. Der Standardordner entspricht dem Ordner "SQL Server Management Studio\DAC Packages" im Ordner "Dokumente" unter Ihrem Windows-Konto.  
  
 **Fertig stellen** – Beendet den Assistenten.  
  
 [Verwenden des Assistenten zum Löschen von Datenebenenanwendungen](#UsingDeleteDACWizard)  
  
##  <a name="using-powershell"></a><a name="DeleteDACPowerShell"></a> PowerShell  

1. Erstellen Sie ein SMO-Serverobjekt, und legen Sie es auf die Instanz fest, die die zu löschende DAC enthält.  
  
1. Öffnen Sie ein **ServerConnection** -Objekt, und stellen Sie eine Verbindung mit derselben Instanz her.  
  
1. Verwenden Sie `add_DacActionStarted` und `add_DacActionFinished`, um die DAC-Aktualisierungsereignisse zu abonnieren.  
  
1. Geben Sie die zu löschende DAC an.  
  
1. Verwenden Sie je nach geeigneter Löschoption eines dieser drei Beispiele:  
  
   - Verwenden Sie die `Unmanage`-Methode, um die DAC-Registrierung zu löschen, während die Datenbank intakt bleibt.  
   - Verwenden Sie die `Uninstall`-Methode, und geben Sie `DetachDatabase` an, um die DAC-Registrierung zu löschen und die Datenbank zu trennen.  
   - Verwenden Sie die `Uninstall`-Methode, und geben Sie `DropDatabase` an, um die DAC-Registrierung zu löschen und die Datenbank zu trennen.
  
### <a name="delete-the-dac-and-leave-the-database"></a>Löschen der DAC und Belassen der Datenbank

Im folgenden Beispiel wird die DAC `<myApplication>` mithilfe der `Unmanage`-Methode gelöscht. Dabei wird die DAC gelöscht, die Datenbank bleibt jedoch intakt.  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$server = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverConnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($server.ConnectionContext.SqlConnectionObject)  
$serverConnection.Connect()  
$dacStore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverConnection)  
  
## Subscribe to the DAC delete events.  
$dacStore.add_DacActionStarted({Write-Host `n`nStarting at $(Get-Date) :: $_.Description})  
$dacStore.add_DacActionFinished({Write-Host Completed at $(Get-Date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "<myApplication>"  
  
## Only delete the DAC definition from msdb, the associated database remains active.  
$dacStore.Unmanage($dacName)  
```
  
### <a name="delete-the-dac-and-detach-the-database"></a>Löschen der DAC und Trennen der Datenbank

Im folgenden Beispiel wird die DAC `<myApplication>` mithilfe der `Uninstall`-Methode gelöscht und die Datenbank getrennt.  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$server = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverConnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($server.ConnectionContext.SqlConnectionObject)  
$serverConnection.Connect()  
$dacStore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverConnection)  
  
## Subscribe to the DAC delete events.  
$dacStore.add_DacActionStarted({Write-Host `n`nStarting at $(Get-Date) :: $_.Description})  
$dacStore.add_DacActionFinished({Write-Host Completed at $(Get-Date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "<myApplication>"  
  
## Delete the DAC definition from msdb and detach the associated database.  
$dacStore.Uninstall($dacName, [Microsoft.SqlServer.Management.Dac.DacUninstallMode]::DetachDatabase)  
```
  
### <a name="delete-the-dac-and-drop-the-database"></a>Löschen der DAC und der Datenbank

Im folgenden Beispiel wird die DAC `<myApplication>` mithilfe der `Uninstall`-Methode gelöscht. Die Datenbank wird ebenfalls gelöscht.  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$server = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverConnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($server.ConnectionContext.SqlConnectionObject)  
$serverConnection.Connect()  
$dacStore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverConnection)  
  
## Subscribe to the DAC delete events.  
$dacStore.add_DacActionStarted({Write-Host `n`nStarting at $(Get-Date) :: $_.Description})  
$dacStore.add_DacActionFinished({Write-Host Completed at $(Get-Date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "<myApplication>"  
  
## Delete the DAC definition from msdb and drop the associated database.  
$dacStore.Uninstall($dacName, [Microsoft.SqlServer.Management.Dac.DacUninstallMode]::DropDatabase)  
```
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenebenenanwendungen](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [Datenebenenanwendungen](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [Bereitstellen einer Datenebenenanwendung](../../relational-databases/data-tier-applications/deploy-a-data-tier-application.md)   
 [Registrieren einer Datenbank als eine DAC](../../relational-databases/data-tier-applications/register-a-database-as-a-dac.md)   
 [Sichern und Wiederherstellen von SQL Server-Datenbanken](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Anfügen und Trennen von Datenbanken &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  
