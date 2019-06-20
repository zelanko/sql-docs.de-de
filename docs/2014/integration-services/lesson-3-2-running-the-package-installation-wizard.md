---
title: 'Schritt 2: Ausführen des Paketinstallations-Assistenten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f91fbb89-4626-4c47-b96d-56052dc45861
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0fe0862438943fec36728a3c4e6c796061c86593
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62891578"
---
# <a name="step-2-running-the-package-installation-wizard"></a>Schritt 2: Ausführen des Paketinstallations-Assistenten
  In diesem Schritt führen Sie den Paketinstallations-Assistenten aus, um die Pakete aus dem Deployment Tutorial-Projekt auf einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]bereitzustellen. In der sysssispackages-Tabelle der msdb-Datenbank von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] können nur Pakete installiert werden. Die unterstützenden Dateien, die das Bereitstellungspaket enthält, werden im Dateisystem bereitgestellt.  
  
 Vom Paketinstallations-Assistenten werden Sie durch die Schritte der Paketinstallation und -konfiguration geführt. Sie installieren die Pakete auf einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf dem Zielcomputer (der Computer, auf den Sie das Bereitstellungspaket kopiert haben). Weiterhin erstellen Sie den Ordner C:\DeploymentTutorialInstall, in dem der Assistent die Nichtpaketdateien installieren wird.  
  
 In einer früheren Lektion haben Sie die Pakete des Lernprogramms so geändert, dass sie Konfigurationen verwenden. Sie bearbeiten diese Konfigurationen mithilfe des Paketinstallations-Assistenten, sodass Pakete erfolgreich in der Installationszielumgebung ausgeführt werden können.  
  
### <a name="to-install-the-packages"></a>So installieren Sie die Pakete  
  
1.  Suchen Sie das Bereitstellungspaket auf dem Zielcomputer.  
  
     Wenn Sie den Standardwert, bin\Deployment, als Speicherort für das Bereitstellungshilfsprogramm verwendet haben, befindet sich das Bereitstellungspaket im Ordner „Deployment“ des Deployment Tutorial-Projekts.  
  
2.  Doppelklicken Sie im Ordner Deployment auf die Manifestdatei Deployment Tutorial.SSISDeploymentManifest.  
  
3.  Klicken Sie auf der Seite Willkommen des Paketinstallations-Assistenten auf **Weiter**.  
  
4.  Wählen Sie auf der Seite SSIS-Pakete bereitstellen die Option **Bereitstellung in SQL Server** aus, aktivieren Sie das Kontrollkästchen **Pakete nach der Installation überprüfen** , und klicken Sie dann auf **Weiter**.  
  
5.  Geben Sie auf der Seite Zielserver mit SQL Server angeben **(local)** im Feld **Servername** an.  
  
6.  Wenn die SQL Server-Instanz die Windows-Authentifizierung unterstützt, wählen Sie **Windows-Authentifizierung verwenden**aus. Andernfalls wählen Sie **SQL Server-Authentifizierung verwenden** aus und geben einen Benutzernamen und ein Kennwort an.  
  
7.  Überprüfen Sie, ob das Kontrollkästchen **Serverspeicher für die Verschlüsselung verwenden** deaktiviert ist.  
  
8.  Klicken Sie auf **Weiter**.  
  
9. Klicken Sie auf der Seite Installationsordner auswählen auf **Durchsuchen**.  
  
10. Erweitern Sie im Dialogfeld **Nach Ordner suchen** die Option **Arbeitsplatz** , und klicken Sie anschließend auf **Lokaler Datenträger (C:)** .  
  
11. Klicken Sie auf **Neuen Ordner erstellen** , und ersetzen Sie den Standardnamen des neuen Ordners, **Neuer Ordner**, durch **DeploymentTutorialInstall**.  
  
    > [!IMPORTANT]  
    >  Auf diesen Namen wird im Wert der Umgebungsvariablen verwiesen, die in Konfigurationen verwendet werden. Der Name des Ordners und der Verweis müssen übereinstimmen. Andernfalls kann das Paket nicht ausgeführt werden.  
  
12. Klicken Sie auf **OK**.  
  
13. Überprüfen Sie auf der Seite Installationsordner auswählen, ob das Feld Ordner den Eintrag **C:\DeploymentTutorialInstall** enthält, und klicken Sie anschließend auf **Weiter**.  
  
14. Klicken Sie auf der Seite Installation bestätigen auf **Weiter**.  
  
     Die Pakete werden vom Assistenten installiert. Nachdem die Installation abgeschlossen ist, wird die Seite Pakete konfigurieren geöffnet.  
  
15. Überprüfen Sie auf der Seite Pakete konfigurieren, ob im Feld **Konfigurationsdatei** die Dateien datatransferconfig.dtsconfig und loadxmldataconfig.dtsconfig aufgelistet sind.  
  
16. Klicken Sie in der Liste **Konfigurationsdatei** auf **datatransferconfig.dtsconfig**, erweitern Sie Eigenschaft in der **Pfad** -Spalte des Felds **Konfigurationen** , und aktualisieren Sie die **Wert** -Spalte mit den folgenden Werten:  
  
    |Eigenschaft|Wert|Aktualisierter Wert|  
    |--------------|-----------|-------------------|  
    |\Package.Connections[Deployment Tutorial Log].Properties[ConnectionString]|C:\Programme\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages\Deployment Tutorial Log|C:\DeploymentTutorialInstall\Deployment Tutorial Log|  
    |\Package.Connections[NewCustomers].Properties[ConnectionString]|C:\Programme\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\NewCustomers.txt|C:\DeploymentTutorialInstall\NewCustomers.txt|  
  
17. Klicken Sie in der Liste **Konfigurationsdatei** auf loadxmldataconfig.dtsconfig, erweitern Sie Eigenschaft in der **Pfad** -Spalte des Felds **Konfigurationen** , und aktualisieren Sie die **Wert** -Spalte mit den folgenden Werten:  
  
    |Eigenschaft|Wert|Aktualisierter Wert|  
    |--------------|-----------|-------------------|  
    |\Package.LoadXMLData.Properties[[XML Source].[XMLData]]|C:\Programme\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xml|C:\DeploymentTutorialInstall\orders.xml|  
    |\Package.LoadXMLData.Properties[[XML Source].[XMLSchemaDefinition]]|C:\Programme\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xsd|C:\DeploymentTutorialInstall\orders.xsd|  
  
18. Auf der Seite zur Paketüberprüfung werden die Überprüfungsergebnisse jedes installierten Pakets angezeigt. Klicken Sie auf **Weiter**.  
  
     Da die Werte der Umgebungsvariablen auf dem Zielcomputer von den Werten der Umgebungsvariablen auf dem Entwicklungscomputer abweichen, werden auf der Seite zur Paketüberprüfung mehrere Warnungen angezeigt. Vier Warnungen sollten angezeigt werden:  
  
    -   Die Konfigurationsdatei: „C:\DeploymentTutorial\DataTransferConfig.dtsConfig“ ist ungültig. Überprüfen Sie den Konfigurationsdateinamen.  
  
    -   Fehler beim Laden von mindestens einem Konfigurationseintrag für das Paket. Überprüfen Sie die Konfigurationseinträge und vorherige Warnungen, um festzustellen, bei welcher Konfiguration der Fehler aufgetreten ist.  
  
    -   Die Konfigurationsdatei: „C:\DeploymentTutorial\LoadXMLDataConfig.dtsConfig“ ist ungültig. Überprüfen Sie den Konfigurationsdateinamen.  
  
    -   Fehler beim Laden von mindestens einem Konfigurationseintrag für das Paket. Überprüfen Sie die Konfigurationseinträge und vorherige Warnungen, um festzustellen, bei welcher Konfiguration der Fehler aufgetreten ist.  
  
     Diese Warnungen haben keinen Einfluss auf die Paketinstallation.  
  
     Wenn Sie die Option **Pakete nach der Installation überprüfen** auf der Seite SSIS-Pakete bereitstellen nicht ausgewählt haben, werden die Seiten für die Paketüberprüfung nicht geöffnet, und im Assistenten werden nach der Installation keine Informationen zur Überprüfung angezeigt.  
  
19. Lesen Sie die Installationszusammenfassung auf der Seite Fertigstellen des Assistenten, und klicken Sie dann auf **Fertig stellen**.  
  
    > [!NOTE]  
    >  Es wird eine temporäre Protokolldatei erstellt, die für die Paketüberprüfung verwendet wird. Diese Datei wird bei der Ausführung des Pakets nicht verwendet.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Schritt 3: Testen der bereitgestellten Pakete](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
![Integration Services (kleines Symbol)](media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Dienst &#40;SSIS-Dienst&#41;](service/integration-services-service-ssis-service.md)   
 [Verwalten des Integration Services-Diensts](../../2014/integration-services/manage-the-integration-services-service.md)  
  
  
