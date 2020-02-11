---
title: Installieren oder Deinstallieren des Reporting Services-Add-Ins für SharePoint (SharePoint 2010 und SharePoint 2013) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2804a9a-08ea-4f4a-805d-a2c19c68733d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7ad18eef777b9bf56f1170d4342621adc1f87e0d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "72796427"
---
# <a name="install-or-uninstall-the-reporting-services-add-in-for-sharepoint-sharepoint-2010-and-sharepoint-2013"></a>Installieren oder Deinstallieren des Reporting Services-Add-Ins für SharePoint (SharePoint 2010 und SharePoint 2013)
  Führen Sie das Installations [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Paket-Add-in für SharePoint-Produkte (rsSharePoint. msi) auf SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Servern aus, um Funktionen innerhalb einer SharePoint-Bereitstellung zu aktivieren. Zu den Funktionen gehören Power View, ein Berichts-Viewer-Webpart, ein URL-Proxyendpunkt, Inhaltstypen sowie Anwendungsseiten, mit deren Hilfe Berichte, Berichtsmodelle, Datenquellen und andere Berichtsserverinhalte auf einer SharePoint-Website erstellt, angezeigt und verwaltet werden können. Das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte ist eine erforderliche Komponente für Berichtsserver, die im SharePoint-Modus ausgeführt werden. Zum Installieren des Add-Ins führen Sie entweder den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Setup-Assistenten aus oder laden rsSharePoint.msi aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack herunter. Eine Liste der Versionen der Add-In- und Downloadseiten finden Sie unter [Verfügbarkeit des Reporting Services-Add-Ins für SharePoint-Produkte](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
 **In diesem Thema:**  
  
-   [Voraussetzungen](#bkmk_prereq)  
  
-   [Was wird durch das Add-in installiert?](#bkmk_whatinstalled)  
  
-   [Übersicht über die Installationsmethoden](#bkmk_3ways_to_install)  
  
-   [Installieren des Add-Ins mithilfe der Installationsdatei "rsSharePoint. msi"](#bkmk_install_rssharepoint)  
  
    -   [Reine Datei Installation](#bkmk_files_only_installation)  
  
-   [Entfernen des Reporting Services-Add-ins](#bkmk_remove_addin)  
  
-   [Reparieren von "rsSharePoint. msi" über die Befehlszeile](#bkmk_repair)  
  
-   [Setup Protokolldateien](#bkmk_logfiles)  
  
-   [Aktualisieren](#bkmk_upgrade)  
  
-   [RsCustomAction. exe](#bkmk_rscustomaction)  
  
##  <a name="bkmk_prereq"></a> Voraussetzungen  
 Die Installation des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-Ins ist einer der zahlreichen Schritte, die notwendig sind, um einen Berichtsserver in eine Instanz eines SharePoint-Produkts zu integrieren. Weitere Informationen zu den gesamten Anforderungen, die zur Verwendung des SharePoint-Modus erforderlich sind, finden Sie unter [Hardware and Software Requirements for Reporting Services in SharePoint Mode](../../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md). Weitere Informationen zum Installieren und Konfigurieren von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]finden Sie unter [Install Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).  
  
-   Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in eine SharePoint-Farm mit mehreren Web-Front-End-Anwendungen integrieren, installieren Sie das Add-In auf jedem Computer in der Farm, der über ein Webserver-Front-End verfügt. Führen Sie diesen Schritt nur für Web-Front-Ends durch, mit denen auf Berichtsserverinhalte zugegriffen wird.  
  
-   Sie müssen über Administratorrechte auf dem Computer verfügen, um das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In installieren zu können. Wenn Sie beispielsweise **rsSharePoint.msi** an der Eingabeaufforderung ausführen möchten, sollten Sie die Eingabeaufforderung mit Administratorprivilegien öffnen, indem Sie die Option Als Administrator ausführen verwenden.  
  
-   Zum Installieren des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-Ins müssen Sie ein Mitglied der SharePoint-Gruppe "Farmadministratoren" sein.  
  
-   Sie müssen Site Collection-Administrator sein, um die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Integrationsfunktion zu aktivieren.  
  
-   Diagramme zu Beispiel Bereitstellungen mit dem Add-in finden Sie unter [Deployment Topologien for SQL Server BI Features in SharePoint](../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).  
  
##  <a name="bkmk_whatinstalled"></a>Was wird durch das Add-in installiert?  
 Der Add-In-Installationsvorgang besteht aus zwei Phasen, beide werden automatisch abgeschlossen, wenn Sie eine Standardinstallation abschließen:  
  
-   In der ersten Phase werden die Dateien in den entsprechenden Ordnern installiert. Bei den Ordnern handelt es sich um die Standardordner für SharePoint-Bereitstellungen. Eine der installierten Dateien ist rsCustomAction.exe.  
  
-   Im zweiten Teil der Installation wird eine Reihe benutzerdefinierter Aktionen zum Registrieren der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dateien bei SharePoint ausgeführt. Die benutzerdefinierten Aktionen werden von rsCustomAction.exe ausgeführt. Die EXE-Datei wird entfernt, sobald beide Installationsphasen vollständig abgeschlossen sind. Sie können eine **Nur-Datei** -Installation ausführen, wobei rsCustomAction.exe am Ende der Installation nicht ausgeführt wird und auf dem Laufwerk verbleibt.  
  
## <a name="the-reporting-services-installation-order"></a>Die Reporting Services-Installationsreihenfolge  
 Das Add-In kann vor oder nach der Installation von SharePoint installiert werden. Das Add-In entspricht den SharePoint-Standards vor der Bereitstellung und installiert Dateien in von der SharePoint-Installation verwendeten Speicherorten.  
  
> [!NOTE]  
>  Wenn das Add-In vor der Installation des SharePoint-Produkts installiert wird, hat dies den Vorteil, dass das Reporting Services-Add-In durch die SharePoint-Farm konfiguriert und aktiviert wird, wenn der Farm neue Server hinzugefügt werden.  
  
 **SharePoint 2010**  
  
-   Durch das Vorbereitungstool für SharePoint 2010-Produkte wird die [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] -Version des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-Ins installiert. 
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] umfasst eine neue Version des Add-Ins, das für Funktionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erforderlich ist.  
  
     Wenn Sie das Vorbereitungstool für SharePoint-Produkte ausführen, müssen Sie weiterhin die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-Ins installieren.  
  
-   Wenn Sie zuerst die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-Ins installieren, wird bei der Ausführung des Vorbereitungstools für SharePoint-Produkte folgendes Dialogfeld eingeblendet, in dem Sie darauf hingewiesen werden, dass die ältere Add-In-Version vom Vorbereitungstool nicht installiert wurde, weil die neuere Version erkannt wurde. Dieses Verhalten wird erwartet.  
  
     ![SSRS-Add-In ist bereits installiert.](../../../2014/sql-server/install/media/rs-sharepointprereq-complete.gif "SSRS-Add-In ist bereits installiert.")  
  
 **SharePoint 2013**  
  
 Das Vorbereitungstool für SharePoint 2013-Produkte führt **keine** Installation des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-Ins für SharePoint-Produkte aus.  
  
##  <a name="bkmk_3ways_to_install"></a>Übersicht über die Installationsmethoden  
 Das [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-in für SharePoint-Produkte kann mithilfe einer der folgenden beiden Methoden installiert werden:  
  
-   **Der Installations-Assistent:** ![beachten Sie](../../../2014/reporting-services/media/rs-fyinote.png "note"), dass das Add-in mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installations-Assistenten installiert werden kann. Wählen Sie im Assistenten auf der Seite **Funktionsauswahl** die Option **Reporting Services-Add-In für SharePoint-Produkte** .  
  
-   **rsSharePoint. msi:** Das Add-in kann direkt von den Installationsmedien installiert oder heruntergeladen und installiert werden. rsSharepoint.msi unterstützt sowohl die Installation über die grafische Benutzeroberfläche als auch über die Befehlszeile. Sie müssen die MSI-Datei mit Administratorrechten ausführen, indem Sie zuerst eine Eingabeaufforderung mit erhöhten Rechten öffnen und dann die Datei rsSharepoint.msi über die Befehlszeile ausführen. Weitere Informationen zum Herunterladen des Add-Ins finden Sie unter [Verfügbarkeit des Reporting Services-Add-Ins für SharePoint-Produkte](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
    > [!NOTE]  
    >  Wenn Sie den Schalter **/q** für eine Befehlszeileninstallation im unbeaufsichtigten Modus verwenden, wird der Endbenutzer-Lizenzvertrag nicht angezeigt. Unabhängig von der Installationsmethode unterliegt die Verwendung dieser Software einem Lizenzvertrag, dessen Einhaltung in Ihrer Verantwortung liegt.  
  
##  <a name="bkmk_install_rssharepoint"></a>Installieren des Add-Ins mithilfe der Installationsdatei "rsSharePoint. msi"  
 In diesem Abschnitt wird die direkte Installation der Datei rssharepoint.msi beschrieben, indem entweder der Installations-Assistent für MSI-Dateien oder eine Befehlszeileninstallation ausgeführt wird. Wenn Sie das Add-In mithilfe des SQL Server-Installations-Assistenten installiert haben, müssen folgende Schritte nicht ausgeführt werden.  
  
 Führen Sie folgenden Befehl aus, um eine vollständige Liste der Befehlszeilenschalter anzuzeigen:  
  
```  
Rssharepoint.msi /?  
```  
  
1.  Laden Sie das-Setup`rsSharepoint.msi`Programm () [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] für das-Add-in herunter. Weitere Informationen zum Herunterladen des Add-Ins finden Sie unter [Verfügbarkeit des Reporting Services-Add-Ins für SharePoint-Produkte](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
2.  Führen Sie `rsSharepoint.msi` als Administrator aus, um den Installations-Assistenten auszuführen. Der Assistent zeigt eine Willkommensseite, die Softwarelizenzbedingungen und eine Seite mit Registrierungsinformationen an. Setup erstellt Ordner unter folgendem Pfad und kopiert Dateien in die Ordner:  
  
     `%program files%\common files\Microsoft Shared\Web Server Extensions\14\`  
  
     oder  
  
     `%program files%\common files\Microsoft Shared\Web Server Extensions\15\`  
  
3.  Konfigurieren Sie die Berichtsservereinstellungen und die Funktionsaktivierung in der SharePoint-Zentraladministration. . Weitere Informationen zum Installieren und Konfigurieren des SharePoint-Modus von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] finden Sie unter [Installieren des SharePoint-Modus von Reporting Services für SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
###  <a name="bkmk_files_only_installation"></a>Reine Datei Installation  
 Wenn Sie die Dateien installieren möchten, die Installationsphase mit benutzerdefinierten Aktionen jedoch übersprungen werden soll, führen Sie die Datei rssharepoint.msi über die Befehlszeile mit der SKIPCA-Option aus:  
  
1.  Öffnen Sie eine Eingabeaufforderung **mit Administrator Berechtigungen**.  
  
2.  Führen Sie den folgenden Befehl aus:  
  
    ```cmd
    Msiexec.exe /i rsSharePoint.msi SKIPCA=1  
    ```  
  
 Die Benutzeroberfläche für die Installation wird geöffnet und wie gewohnt ausgeführt. Außerdem wird die Datei `rsCustomAction.exe` installiert. Die ausführbare Datei wird am Ende der Installation jedoch nicht ausgeführt, und `rsCustomAction.exe` verbleibt nach Abschluss der Installation auf dem Datenträger.  
  
### <a name="use-a-two-step-installation-to-troubleshoot-installation-issues-or-install-the-content-types"></a>Installation in zwei Schritten zur Behandlung von Installationsproblemen oder zur Installation der Inhaltstypen  
 Wenn während der Installation Fehler auftreten oder die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Inhaltstypen nicht in den Dokumentbibliothekseinstellungen angezeigt werden, können Sie Setup über die Befehlszeile in zwei Schritten ausführen:  
  
1.  Öffnen Sie eine Eingabeaufforderung **mit Administratorberechtigungen** , und führen eine Nur-Datei-Installation aus, wie im vorherigen Abschnitt beschrieben.  
  
2.  Führen Sie die ausführbare Datei für benutzerdefinierte Aktionen aus:  
  
    1.  Wechseln Sie zu dem Ordner, in dem die Datei `rsCustomAction.exe` enthalten ist. Diese Datei wird bei der ausschließlichen Installation von Dateien des Add-Ins auf den Computer kopiert. `rsCustomAction.exe`befindet sich im Verzeichnis **% Temp%** . Geben Sie an der Eingabeaufforderung Folgendes ein, um zur Datei zu navigieren:  
  
         **CD% Temp%**.  
  
         Die Datei sollte sich hier befinden: **\Benutzer\\<Ihr Name\>\AppData\Local\Temp**.  
  
    2.  Geben Sie folgenden Befehl ein. Dieser Konfigurationsschritt dauert mehrere Minuten. Der W3SVC-Dienst wird während des Prozesses neu gestartet. Während das Programm Dateien kopiert, Komponenten registriert und den Konfigurations-Assistenten für SharePoint-Produkte ausführt, werden mehrere Statusmeldungen angezeigt.  
  
        ```cmd
        rsCustomAction.exe /i  
        ```  
  
    3.  Die Zeit bis zum Wirksamwerden der Änderungen kann je nach Serverumgebung variieren. Sie können auch **iisreset** ausführen, um ein schnelleres Update zu erzwingen.  
  
### <a name="quiet-installation-for-scripting"></a>Stille Installation unter Verwendung eines Skripts  
 Mithilfe der Schalter **/q** oder **/quiet** können Sie eine unbeaufsichtigte Installation ausführen, bei der keine Dialogfelder oder Warnungen angezeigt werden. Die stille Installation ist nützlich, wenn Sie für die Installation des Add-Ins ein Skript schreiben möchten.  
  
> [!NOTE]  
>  Wenn Sie den Schalter **/q** für eine Befehlszeileninstallation im unbeaufsichtigten Modus verwenden, wird der Endbenutzer-Lizenzvertrag nicht angezeigt. Unabhängig von der Installationsmethode unterliegt die Verwendung dieser Software einem Lizenzvertrag, dessen Einhaltung in Ihrer Verantwortung liegt.  
  
 So führen Sie eine stille Installation aus:  
  
1.  Öffnen Sie eine Eingabeaufforderung **mit Administrator Berechtigungen**.  
  
2.  Führen Sie den folgenden Befehl aus:  
  
    ```cmd
    Msiexec.exe /i rsSharePoint.msi /q  
    ```  
  
##  <a name="bkmk_remove_addin"></a>Entfernen des Reporting Services-Add-ins  
 Sie können das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte über die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Systemsteuerung oder über die Befehlszeile deinstallieren.  
  
1.  Indem Sie die Systemsteuerung dafür verwenden, werden die Daten auf dem aktuellen Computer vollständig deinstalliert **UND** die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Objekte und -Funktionen aus der SharePoint-Farm entfernt. Wenn das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Objekt und die -Funktionen entfernt werden, können Sie Berichte nicht mehr überprüfen und aktualisieren.  
  
2.  Indem Sie über die Befehlszeilenmethode das Add-In deinstallieren, können Sie den LocalOnly-Parameter dafür verwenden, nur die Add-In-Dateien vom lokalen Computer zu entfernen, und das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] - und die -Funktionen in der Farm werden nicht geändert.  
  
 Beim Deinstallieren des Add-Ins werden Serverintegrationsfunktionen entfernt, die zur Verarbeitung von Berichten auf einem Berichtsserver verwendet werden. Zusätzlich werden die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Seiten aus der SharePoint-Zentraladministration und weitere benutzerdefinierte [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Seiten entfernt. Sie können auf alle Berichte und anderen Berichtsserverelemente auf den betroffenen SharePoint-Websites entfernen, die Sie nicht mehr verwenden. Sie werden nach dem Entfernen des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-Ins nicht mehr ausgeführt.  
  
 Um das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In zu deinstallieren, muss eine [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] -Installation oder eine [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] -Installation ausgeführt werden. Wenn Sie zuerst das SharePoint 2010-Produkt deinstallieren, ist eine Neuinstallation erforderlich, bevor Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In deinstallieren können.  
  
 Die Schritte zum Deinstallieren des Add-Ins sind für eigenständige Server und Serverfarmen gleich. Das Setup entfernt Programmdateien und Konfigurationseinstellungen, die bei der Installation hinzugefügt wurden.  
  
 Durch das Deinstallieren des Add-Ins wird Folgendes nicht entfernt:  
  
-   Anmeldungen für das Berichtsserver-Dienstkonto für den Zugriff auf die SharePoint-Konfiguration und die SharePoint-Inhaltsdatenbanken. Sie müssen alle Anmeldungen für das Berichts Server-Dienst Konto aus der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz löschen, die zum Hosten der SharePoint-Datenbanken verwendet wird.  
  
-   Berechtigungen oder Gruppen, die Sie für Benutzer von Berichten erstellt haben. Wenn Sie benutzerdefinierte Berechtigungsebenen oder SharePoint-Gruppen erstellt haben, um Zugriff auf Berichtsserverfunktionen zu gewähren, sollten Sie nicht mehr benötigte Berechtigungen aufheben.  
  
-   Datendateien, die Sie in eine SharePoint-Bibliothek hochgeladen haben, wie Berichtsdefinitionen (RDL-Dateien), freigegebene Datenquellen (RSDS-Dateien) und veröffentlichte Berichtselemente (RSC-Dateien). Diese werden nicht gelöscht, sind jedoch nicht mehr ausführbar. Sie müssen die Dateien manuell löschen.  
  
-   Durch das Setup wird weder die Berichtsserver-Datenbank gelöscht noch die Berichtsserverinstanz geändert, die für integrierte Vorgänge verwendet wurde.  
  
### <a name="to-uninstall-from-windows-control-panel"></a>So deinstallieren Sie von der Windows-Systemsteuerung aus  
 So starten Sie den Assistenten von der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Systemsteuerung und entfernen das Add-In  
  
1.  Klicken Sie in der Systemsteuerung unter **Programme**auf **Programm deinstallieren**.  
  
2.  Wählen Sie **Microsoft SQL Server RS Add-In für SharePoint**aus. Sie können den Deinstallations-Assistenten auch starten, indem Sie **rssharepoint.msi** über die Befehlszeile ohne Schalter ausführen.  
  
3.  Klicken Sie auf **Entfernen**.  
  
### <a name="uninstall-from-the-command-line"></a>Deinstallieren über die Befehlszeile  
 So deinstallieren Sie das Add-In über die Befehlszeile  
  
1.  Öffnen Sie eine Eingabeaufforderung **mit Administrator Berechtigungen**.  
  
2.  Führen Sie den folgenden Befehl aus:  
  
    ```cmd
    msiexec.exe /uninstall rsSharePoint.msi  
    ```  
  
3.  Ein Meldungsfeld zur Bestätigung wird angezeigt. Klicken Sie auf **Ja**.  
  
### <a name="uninstall-the-add-in-from-the-local-server-only"></a>Deinstallieren des Add-Ins nur vom lokalen Server  
 Durch die vorherigen Methoden zum Deinstallieren des Add-Ins werden die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Funktionen und das -Objekt der Farm entfernt. Führen Sie die folgenden Schritte aus, wenn Sie über eine Multiserverfarm verfügen und das Add-In nur von einem lokalen Computer deinstallieren und die SharePoint-Farm in einem funktionsfähigen Status belassen möchten:  
  
1.  Öffnen Sie eine Eingabeaufforderung **mit Administrator Berechtigungen**.  
  
2.  Führen Sie den folgenden Befehl aus:  
  
    ```cmd
    Msiexec.exe /uninstall rsSharePoint.msi LocalOnly=1  
    ```  
  
 Dadurch wird die Registrierung der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Komponenten in SharePoint aufgehoben, und die Dateien werden entfernt. Dies gilt jedoch nur für den lokalen Computer.  
  
 Führen Sie die folgenden Schritte aus, wenn Sie die Registrierung der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Funktionen in SharePoint aufheben, die Dateien zur späteren Verwendung jedoch auf dem Datenträger belassen möchten.  
  
1.  Öffnen Sie eine Eingabeaufforderung **mit Administrator Berechtigungen**.  
  
2.  Führen Sie den folgenden Befehl aus:  
  
    ```cmd
    rsCustomAction.exe /p  
    ```  
  
 In den obigen Schritten wird davon ausgegangen, dass Sie die Installation der MSI-Datei mit SkipCA=1 abgeschlossen haben und dass die Datei "rscusstomaction.exe" verfügbar ist. Weitere Informationen finden Sie im Abschnitt, in dem die "Nur-Datei"-Installation beschrieben wird.  
  
##  <a name="bkmk_repair"></a>Reparieren von "rsSharePoint. msi" über die Befehlszeile  
 Führen Sie zum Reparieren oder Deinstallieren des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-Ins mit der Befehlszeile die folgenden Schritte aus:  
  
1.  Öffnen Sie eine Eingabeaufforderung **mit Administrator Berechtigungen**.  
  
2.  Führen Sie den folgenden Befehl aus:  
  
    ```cmd
    msiexec.exe /f rssharepoint.msi  
    ```  
  
##  <a name="bkmk_logfiles"></a>Setup Protokolldateien  
 Beim Ausführen von Setup werden Informationen zum Benutzer, der das **-Add-In installiert hat, in einer Protokolldatei im Ordner** %temp% [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] protokolliert. Beispiel: **C:\Benutzer\\<Benutzername\>\AppData\Local\Temp**. Der Dateiname lautet **RS_SP_\<Nummer>.log**, also beispielsweise **RS_SP_0.log**. Alle Fehler im Protokoll beginnen mit der Zeichenfolge SSRSCustomActionError.  
  
> [!NOTE]  
>  AppData ist ein ausgeblendeter Ordner im Betriebssystem Windows. Sie müssen möglicherweise die Windows-Explorer-Ordnereinstellungen ändern, damit ausgeblendete Dateien und Ordner angezeigt werden.  
  
#### <a name="view-a-log-file-with-windows-notepad"></a>Anzeigen einer Protokolldatei mit Windows Editor  
  
1.  Mit den folgenden Befehlen werden der Eingabeaufforderungspfad geändert, die RS-Protokolldateien aufgelistet und eine der Dateien mit Windows Editor geöffnet:  
  
    ```cmd
    cd %temp%  
    ```  
  
    ```cmd
    dir rs_sp*.log  
    ```  
  
    ```cmd
    notepad rs_sp_3.log  
    ```  
  
#### <a name="view-a-log-file-with-powershell"></a>Anzeigen einer Protokolldatei mit PowerShell  
  
1.  Geben Sie den folgenden Befehl in der SharePoint-Verwaltungsshell ein, um eine gefilterte Liste der Zeilen, die „ssrscustomactionerror“ enthalten, aus der Datei abzurufen:  
  
    ```powershell
    Get-Content -Path C:\Users\<UserName\AppData\Local\Temp\rs_sp_0.log | Select-String "ssrscustomactionerror"  
    ```  
  
2.  Die Ausgabe sieht etwa wie folgt aus:  
  
     `2011-05-23 12:40:12: SSRSCustomActionError: SharePoint is installed, but not configured`.  
  
##  <a name="bkmk_upgrade"></a>Zuführen  
 Wenn Sie bereits über eine Installation des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-Ins verfügen, können Sie diese auf die aktuelle Version aktualisieren. Das Setupprogramm für das Add-In erkennt die vorhandene Version und fordert Sie auf, das Update zu bestätigen. Die Meldung lautet wie folgt oder ähnlich:  
  
 **Eine niedrigere Version dieses Produkts wurde auf Ihrem System erkannt. Möchten Sie die vorhandene Installation aktualisieren?**  
  
 Wenn Sie bestätigen, wird die frühere Version des Add-Ins entfernt und die neue Version installiert.  
  
 Beachten Sie, dass das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In nicht instanzabhängig ist. Es kann nur eine Instanz des Add-Ins auf einem Computer vorhanden sein. Sie können keine unterschiedlichen Versionen parallel zur aktuellen Version ausführen.  
  
##  <a name="bkmk_rscustomaction"></a>RsCustomAction. exe  
 In der folgenden Tabelle sind die Schalter für rscustomaction.exe zusammengefasst:  
  
|Schalter|BESCHREIBUNG|  
|------------|-----------------|  
|i|Installiert die benutzerdefinierten Aktionen. Dadurch werden die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Komponenten in SharePoint registriert. Startet den W3SVC-Dienst neu.|  
|r|Reparieren|  
|u|Deinstallation Dadurch wird die Registrierung der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Komponenten in der gesamten SharePoint-Farm aufgehoben, die Dateien werden jedoch auf dem Datenträger belassen. Startet den W3SVC-Dienst neu.|  
|p|Lokale Deinstallation Dadurch wird die Registrierung der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Komponenten nur auf dem lokalen Computer aufgehoben. Die Dateien verbleiben auf dem Datenträger. Startet den W3SVC-Dienst neu.|  
|t|Nur SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005. Der Schalter testet, ob der Berichtsserver ordnungsgemäß mit der Berichtsserver-Datenbank verbunden ist.|  
  
## <a name="configuring-reporting-services"></a>Konfigurieren von Reporting Services  
 Nachdem das Add-In auf allen erforderlichen Computern installiert wurde, muss der Berichtsserver über die SharePoint-Zentraladministration konfiguriert werden. Die erforderlichen Schritte richten sich nach der Reihenfolge, in der die verschiedenen Technologien installiert wurden. Weitere Informationen finden Sie unter [install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) and [Reporting Services Report Server &#40;SharePoint Mode&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren Reporting Services SharePoint-Modus für SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)   
 [Reporting Services Berichts Server &#40;SharePoint-Modus&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)  
