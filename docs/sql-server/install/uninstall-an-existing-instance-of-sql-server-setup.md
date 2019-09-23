---
title: Deinstallieren einer vorhandenen SQL Server-Instanz (Setup) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/27/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- removing instances of SQL Server
- uninstalling instances of SQL Server
- removing SQL Server
- instances of SQL Server, uninstalling
- uninstalling SQL Server
ms.assetid: 3c64b29d-61d7-4b86-961c-0de62261c6a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c4f9dc408f5b0cab4d568e8b63dfa3f61acdcd59
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68126051"
---
# <a name="uninstall-an-existing-instance-of-sql-server-setup"></a>Deinstallieren einer vorhandenen SQL Server-Instanz (Setup)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In diesem Artikel wird beschrieben, wie eine eigenständige Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deinstalliert wird. Mit den Schritten in diesem Artikel bereiten Sie das System außerdem für die erneute Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor.  
  
  >[!IMPORTANT]
  > Sie müssen ein lokaler Administrator sein und über die Berechtigung verfügen, sich als Dienst anzumelden, um eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deinstallieren zu können.  
  
 > [!NOTE]
 > Zur Deinstallation eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Failovercluster verwenden Sie die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup bereitgestellte Funktion Knoten entfernen, um jeden Knoten einzeln zu entfernen. Weitere Informationen finden Sie unter [Hinzufügen oder Entfernen von Knoten in einem SQL Server-Failovercluster &#40;Setup&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
 Beachten Sie vor der Deinstallation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die folgenden wichtigen Szenarien:  
  
-   Bevor Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten von einem Computer entfernen, der die Mindestanforderungen für den physischen Arbeitsspeicher erfüllt, müssen Sie sicherstellen, dass die Auslagerungsdatei ausreichend groß ist. Die Auslagerungsdatei muss zwei Mal so groß sein wie der physische Speicher. Unzureichender virtueller Arbeitsspeicher kann dazu führen, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nur unvollständig entfernt wird.  
  
-   Wenn Sie mehrere Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert haben, wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser automatisch deinstalliert, sobald die letzte Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] deinstalliert ist.  
  
     Um alle Komponenten von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]zu deinstallieren, müssen Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Browserkomponente in der **Systemsteuerung** unter **Programme und Funktionen** manuell deinstallieren.  
  
1.  Beim Deinstallieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden tempdb-Datendateien gelöscht, die während des Installationsvorgangs hinzugefügt wurden. Dateien mit dem Namensmuster „tempdb_mssql_*.ndf“ werden gelöscht, wenn sie im Verzeichnis der Systemdatenbank vorhanden sind.  
  
### <a name="before-you-uninstall"></a>Vor der Deinstallation  
  
1.  **Sichern Sie die Daten.** Obwohl dieser Schritt nicht zwingend erforderlich ist, verfügen Sie möglicherweise über Datenbanken, die Sie in ihrem aktuellen Zustand speichern möchten. Möglicherweise möchten Sie auch an den Systemdatenbanken vorgenommene Änderungen speichern. Wenn einer dieser Fälle zutrifft, stellen Sie sicher, dass die Daten vor dem Deinstallieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gesichert werden. Speichern Sie alternativ eine Kopie aller Daten- und Protokolldateien in einem anderen Ordner als dem MSSQL-Ordner. Der MSSQL-Ordner wird während der Deinstallation gelöscht.  
  
     Die Dateien, die Sie speichern müssen, umfassen die im Folgenden aufgeführten Datenbankdateien:  
  
    -   Master.mdf  
  
    -   Mastlog.ldf  
  
    -   Model.mdf  
  
    -   Modellog.ldf  
  
    -   Msdbdata.mdf  
  
    -   Msdblog.ldf  
  
    -   Mssqlsystemresource.mdf  
  
    -   Mssqlsustemresource.ldf  
  
    -   Tempdb.mdf  
  
    -   Templog.ldf  
  
    -   ReportServer[$InstanceName] Dies ist die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Standarddatenbank.  
  
    -   ReportServer[$InstanceName] TempDB Dies ist die temporäre [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Standarddatenbank.  
  
2.  **Löschen Sie die lokalen Sicherheitsgruppen.** Löschen Sie vor dem Deinstallieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die lokalen Sicherheitsgruppen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten.  
  
3.  **Beenden Sie alle**  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Dienste.** Beenden Sie alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste vor dem Deinstallieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten. Aktive Verbindungen können eine erfolgreiche Deinstallation verhindern.  
  
4.  **Verwenden Sie ein Konto mit den entsprechenden Berechtigungen.** Melden Sie sich am Server an, indem Sie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienstkonto oder ein Konto mit entsprechenden Berechtigungen verwenden. Beispielsweise können Sie sich mit einem Konto beim Server anmelden, das Mitglied der lokalen Administratorgruppe ist.  
  
### <a name="to-uninstall-an-instance-of-includessnoversionincludesssnoversion-mdmd"></a>To Uninstall an Instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  Um den Deinstallationsvorgang zu starten, wechseln Sie in der **Systemsteuerung** zu **Programme und Funktionen**.  

2. Klicken Sie mit der rechten Maustaste auf **SQL Server 2016**, und wählen Sie **Deinstallieren** aus. Klicken Sie auf **Entfernen**. Dadurch wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installations-Assistent gestartet.  
  
     Unterstützungsregeln für Setup werden ausgeführt, um die Computerkonfiguration zu überprüfen. Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.  
  
3.  Wählen Sie im Dropdownfeld auf der Seite Instanz auswählen die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus, die Sie entfernen möchten, oder legen Sie fest, dass nur die freigegebenen Funktionen sowie die Verwaltungstools von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entfernt werden sollen. Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.  
  
4.  Geben Sie auf der Seite Funktionen auswählen die Funktionen an, die aus der angegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entfernt werden sollen.  
  
     Entfernungsregeln werden ausgeführt, um zu überprüfen, dass der Vorgang erfolgreich abgeschlossen werden kann.  
  
5.  Überprüfen Sie auf der Seite **Deinstallation kann jetzt ausgeführt werden** die Liste der Komponenten und Funktionen, die deinstalliert werden sollen. Klicken Sie auf **Entfernen**, um mit der Deinstallation zu beginnen.  
  
6.  Unmittelbar nach der Deinstallation der letzten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz sind die anderen Programme, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugeordnet sind, in der Programmliste in **Programme und Funktionen** weiterhin sichtbar. Wenn Sie **Programme und Funktionen** jedoch schließen, wird die Programmliste beim nächsten Öffnen von **Programme und Funktionen** aktualisiert, sodass nur die Programme angezeigt werden, die weiterhin installiert sind.  
  
### <a name="if-the-uninstallation-fails"></a>Falls die Deinstallation einen Fehler verursacht  
  
1.  Wenn der Deinstallationsvorgang nicht erfolgreich abgeschlossen wird, versuchen Sie, das Problem, das den Deinstallationsfehler verursacht hat, zu beheben. Die folgenden Artikel sollen helfen, den Ursachen für die fehlgeschlagene Deinstallation auf den Grund zu gehen:  
  
    -   [Identifizieren von SQL Server 2008-Setupproblemen in den Setupprotokolldateien](https://support.microsoft.com/kb/955396/en-us)  
  
    -   [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
2.  Falls sich die Ursache für den Deinstallationsfehler nicht beheben lässt, können Sie sich an den [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Support wenden. In einigen Fällen, z. B. falls wichtige Dateien versehentlich gelöscht wurden, muss vor der Neuinstallation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] u. U. das Betriebssystem auf dem Computer neu installiert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
