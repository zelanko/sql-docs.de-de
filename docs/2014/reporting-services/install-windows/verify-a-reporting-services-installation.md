---
title: Überprüfen einer Installation von Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- checking report server installations
- verifying report server installations
- Report Designer [Reporting Services], verifying installations
- installing Reporting Services, verifying installations
- Report Manager [Reporting Services], verifying installations
- report servers [Reporting Services], verifying installations
- Setup [Reporting Services], verifying installations
ms.assetid: 82a51a99-66f0-4b0c-b05b-07d22387adb0
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e1ea6363f2acb76d7c95fb6d2e8f7c0e9dbdbc6a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48108930"
---
# <a name="verify-a-reporting-services-installation"></a>Überprüfen einer Installation von Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsserver können in zwei Modi installiert werden: einheitlich oder SharePoint. Die Schritte, die Sie zum Überprüfen der Installation ausführen sollten, hängen vom Berichtsservermodus ab.  
  
 Dieses Thema enthält folgende Informationen:  
  
-   [Überprüfen der Installation von SharePoint-Modus](#bkmk_sharepointmode)  
  
-   [Überprüfen einer Installation im einheitlichen Modus](#bkmk_nativemode)  
  
##  <a name="bkmk_sharepointmode"></a> Überprüfen der SharePoint-Modus-Installation  
  
#### <a name="to-verify-the-reporting-services-service"></a>So überprüfen Sie Reporting Services  
  
1.  Klicken Sie in der SharePoint-Zentraladministration in der Gruppe **Systemeinstellungen** auf **Dienste auf dem Server verwalten** .  
  
2.  Überprüfen Sie, ob der **SQL Server Reporting Services-Dienst** installiert ist und den Status **Wird ausgeführt** aufweist.  
  
     Wird der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienst nicht in der Liste aufgeführt, überprüfen Sie, ob der Dienst installiert ist. Weitere Informationen finden Sie im Abschnitt "Installieren und Starten der Reporting Services SharePoint Service" des [installieren Sie Reporting Services SharePoint Mode for SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
#### <a name="to-verify-the-service-application"></a>So überprüfen Sie die Dienstanwendung  
  
1.  Um in der Zentraladministration zu überprüfen, ob mindestens eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung vorhanden ist, klicken Sie in der Gruppe **Anwendungsverwaltung** auf **Dienstanwendungen verwalten** .  
  
2.  Stellen Sie sicher, dass eine Dienstanwendung des Typs **SQL Server Reporting Services-Dienstanwendung** und ein entsprechender Anwendungsproxy vorhanden ist.  
  
3.  Klicken Sie auf eine Stelle **in der Nähe** des Namens der Dienstanwendung, und klicken Sie dann auf der SharePoint-Symbolleiste auf **Eigenschaften** .  Wenn Sie direkt auf den Namen der Dienstanwendung klicken, werden die Verwaltungsseiten der Dienstanwendung und nicht die Eigenschaftenseite geöffnet.  
  
4.  Überprüfen Sie, ob die **Zuordnung der Webanwendung** so konfiguriert ist, dass sie auf die gewünschte Webanwendung verweist.  
  
#### <a name="to-verify-the-site-collection-feature"></a>So überprüfen Sie die Websitesammlungsfunktion  
  
1.  Klicken Sie in den Websiteeinstellungen auf **Websitesammlungsfunktionen** in der Gruppe **Websitesammlungsverwaltung** .  
  
2.  Überprüfen Sie, dass die **Berichtsserver-Integrationsfunktion** aktiviert ist.  
  
#### <a name="to-verify-reporting-server-content-types"></a>So überprüfen Sie Berichtsserverinhaltstypen  
  
1.  Zur Überprüfung oder Hinzufügung [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Berichtsserver-Inhaltstypen, finden Sie unter [Hinzufügen von Report Server-Inhaltstypen zu einer Bibliothek &#40;Reporting Services im integrierten SharePoint-Modus&#41;](../add-reporting-services-content-types-to-a-sharepoint-library.md).  
  
#### <a name="to-verify-you-can-launch-report-builder"></a>So überprüfen Sie, dass Sie der Berichts-Generator gestartet werden kann  
  
1.  Klicken Sie von einer Dokumentbibliothek auf **Dokumente** im SharePoint-Menüband.  
  
2.  Klicken Sie auf **Neues Dokument** und anschließend auf **Berichts-Generator-Bericht**. Wenn Sie diese Option nicht sehen, überprüfen Sie die vorherige Prozedur über das Hinzufügen der Berichtsserverinhaltstypen zu einer Bibliothek.  
  
#### <a name="create-a-basic-report"></a>Erstellen eines einfachen Berichts  
  
1.  Erstellen Sie in einer SharePoint-Dokumentbibliothek einen grundlegenden [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Bericht, der nur ein Textfeld enthält, z. B. einen Titel. Der Bericht enthält keine Datenquellen oder Datasets. Ziel ist es, zu überprüfen, ob Sie den Berichts-Generator öffnen und einen grundlegenden Bericht in der Vorschau anzeigen können.  
  
2.  Speichern Sie den Bericht in der Dokumentbibliothek, und führen Sie den Bericht dann aus der Bibliothek heraus aus. Weitere Informationen zum Erstellen von Berichten mit dem Berichts-Generator finden Sie unter [Starten des Berichts-Generators (Berichts-Generator)](http://technet.microsoft.com/library/ms159221.aspx).  
  
#### <a name="reporting-services-samples"></a>Reporting Services-Beispiele  
  
1.  Führen Sie eines der Lernprogramme zu Reporting Services durch. Weitere Informationen finden Sie unter [Reporting Services-Tutorials (SSRS)](../reporting-services-tutorials-ssrs.md).  
  
2.  Laden Sie die Adventure Works-Beispieldatenbank und die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Beispielberichte von CodePlex herunter. Weitere Informationen finden Sie unter [AdventureWorks-Beispielberichte](https://msftrsprodsamples.codeplex.com/wikipage?title=SS2012!AdventureWorks2012%20Report%20Samples&referringTitle=Home).  
  
##  <a name="bkmk_nativemode"></a> Überprüfen einer Installation im einheitlichen Modus  
 Wenn Sie einen Berichtsserver im einheitlichen Modus anhand der Standardkonfiguration installieren, wird der Server durch das Setup installiert und bereitgestellt. Um festzustellen, ob der Berichtsserver durch das Setup bereitgestellt wurde, führen Sie einige wenige einfache Tests aus. Um diese Schritte ausführen zu können, müssen Sie ein lokaler Administrator sein. Um weitere Benutzer für das Ausführen der Tests zu aktivieren, konfigurieren Sie für diese Benutzer den Berichtsserverzugriff.  
  
#### <a name="to-verify-that-the-report-server-is-installed-and-running"></a>So überprüfen Sie, ob der Berichtsserver installiert ist und ausgeführt wird  
  
1.  Führen Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool aus, und stellen Sie eine Verbindung mit der soeben installierten Berichtsserverinstanz her. Auf der Seite Webdienst-URL finden Sie einen Link zum Report Server-Webdienst. Klicken Sie auf den Link, um zu überprüfen, ob Sie auf den Server zugreifen können. Wenn die Berichtsserver-Datenbank noch nicht konfiguriert ist, holen Sie dies nach, bevor Sie auf den Link klicken.  
  
2.  Öffnen Sie Konsolenanwendungen für die Dienste, und überprüfen Sie, ob der Berichtsserver-Dienst ausgeführt wird. Um den Status des Berichtsserver-Diensts anzuzeigen, klicken Sie auf **Start**, zeigen Sie auf **Systemsteuerung**, doppelklicken Sie auf **Verwaltung**, und doppelklicken Sie anschließend auf **Dienste**. Führen Sie in der Liste mit den Diensten einen Bildlauf zu **Berichtsserver (MSSQLSERVER)** durch. Der Status sollte **Gestartet**lauten.  
  
3.  Öffnen Sie einen Browser, und geben Sie die Berichtsserver-URL in der Adressleiste ein. Die Adresse besteht aus dem Servernamen und dem Namen des virtuellen Verzeichnisses, das Sie bei beim Setup für den Berichtsserver angegeben haben. Standardmäßig lautet das virtuelle Verzeichnis des Berichtsservers **ReportServer**. Mit der folgenden URL können Sie die Berichtsserverinstallation überprüfen: http://*\<Computername>*/ReportServer*\<_Instanzname>*. Wenn der Berichtsserver als eine benannte Instanz installiert wurde, lautet die URL anders. Weitere Informationen zum URL-Format finden Sie unter [Konfigurieren von Berichtsserver-URLs (SSRS-Konfigurations-Manager)](configure-report-server-urls-ssrs-configuration-manager.md). Informationen für lokale Administratoren unter Windows Vista oder Windows Server 2008 finden Sie unter [Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung (SSRS)](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
4.  Führen Sie Berichte aus, um die Berichtsservervorgänge zu testen. Für diesen Schritt können Sie einen Beispielbericht aus einem Lernprogramm erstellen. Weitere Informationen finden Sie unter [Erstellen eines einfachen Tabellenberichts (SSRS-Tutorial)](../create-a-basic-table-report-ssrs-tutorial.md).  
  
#### <a name="to-verify-that-report-manager-is-installed-and-running"></a>So überprüfen Sie, ob der Berichts-Manager installiert ist und ausgeführt wird  
  
1.  Öffnen Sie einen Browser, und geben Sie die URL des Berichts-Managers in der Adressleiste ein. Die Adresse besteht aus dem Servernamen und dem Namen des virtuellen Verzeichnisses, das Sie beim Setup für den Berichts-Manager oder im Konfigurations-Manager für Reporting Services auf der Seite Berichts-Manager-URL angegeben haben. Standardmäßig lautet das virtuelle Verzeichnis des Berichts-Managers **Reports**. Mit der folgenden URL können Sie die Berichts-Manager-Installation überprüfen:  
  
     http://*\<Computername>*/Reports*\<_Instanzname>*.  
  
2.  Verwenden Sie den Berichts-Manager, um einen neuen Ordner zu erstellen, oder laden Sie eine Datei hoch, um zu testen, ob Definitionen an die Berichtsserver-Datenbank zurückgegeben werden. Falls diese Vorgänge erfolgreich sind, ist die Verbindung einsatzbereit.  
  
     Weitere Informationen finden Sie unter [Berichts-Manager (einheitlicher SSRS-Modus)](../report-manager-ssrs-native-mode.md).  
  
#### <a name="to-verify-that-report-designer-is-installed-and-running"></a>So überprüfen Sie, ob der Berichts-Designer installiert ist und ausgeführt wird  
  
1.  Öffnen Sie [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], und erstellen Sie auf Grundlage eines Berichtsserverprojekttyps ein neues Projekt. Weitere Informationen zum Verwenden des Berichtsserverprojekt-Assistenten finden Sie in der SQL Server-Onlinedokumentation unter [Reporting Services in SQL Server-Datentools (SSDT)](../tools/reporting-services-in-sql-server-data-tools-ssdt.md).  
  
2.  Wenn Sie Berichtsbeispiele installiert haben, öffnen Sie die Beispielberichts-Projektdateien, und veröffentlichen Sie die Berichte auf einem Berichtsserver.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei einer Installation von Reporting Services](troubleshoot-a-reporting-services-installation.md)   
 [Cause and Resolution of Reporting Services Errors (Ursachen und Lösungen für Reporting Services-Fehler)](../troubleshooting/cause-and-resolution-of-reporting-services-errors.md)  
  
  
