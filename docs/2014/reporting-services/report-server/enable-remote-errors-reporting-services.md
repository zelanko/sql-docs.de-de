---
title: Aktivieren von Remotefehlern (Reporting Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- remote data source [Reporting Services]
- EnableRemoteError server property
ms.assetid: 5f05022b-d557-43e0-b50a-f5e2a1846b83
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e2d239dfc3d094f72d40ce6d020610fe1c0eabbc
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66103808"
---
# <a name="enable-remote-errors-reporting-services"></a>Aktivieren von Remotefehlern (Reporting Services)
  Sie können Servereigenschaften auf einem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] festlegen, um zusätzliche Informationen zu auf Remoteservern aufgetretenen Fehlerbedingungen zurückzugeben. Wenn in einer Fehlermeldung der Text "Um weitere Informationen zu diesem Fehler zu erhalten, navigieren Sie zum Berichtsserver auf dem lokalen Servercomputer, oder aktivieren Sie Remotefehler." angezeigt wird, können Sie die `EnableRemoteErrors`-Eigenschaft festlegen, um zusätzliche Informationen zum Behandeln des Problems zu erhalten. Weitere Informationen finden Sie unter [Berichtsserver-Systemeigenschaften](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
 **In diesem Thema:**  
  
-   [Aktivieren von Remotefehlern für den SharePoint-Modus](#bkmk_sharepoint)  
  
-   [Aktivieren von Remotefehlern durch SQL Server Management Studio (Einheitlicher Modus)](#bkmk_mgtStudio)  
  
-   [Aktivieren von Remotefehlern per Skript (Einheitlicher Modus)](#bkmk_script)  
  
-   [Ändern der ConfigurationInfo-Tabelle (Einheitlicher Modus)](#bkmk_ConfigurationInfo)  
  
##  <a name="bkmk_sharepoint"></a> Aktivieren von Remotefehlern für den SharePoint-Modus  
 Es gibt zwei verschiedene Prozeduren zum Aktivieren von Remotefehlern für den SharePoint-Modus von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Die Prozedur ist für die beiden verschiedenen Berichtsserverarchitekturen unterschiedlich. Die neuere, auf dem SharePoint-Dienst basierende Architektur, die in der [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] -Version eingeführt wurde, verwendet eine Einstellung, die für jede [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung konfiguriert werden kann. Die ältere Architektur verwendet eine einzelne Einstellung auf Websiteebene.  
  
#### <a name="enable-remote-errors-for-a-reporting-services-service-application"></a>Aktivieren von Remotefehlern für eine Reporting Services-Dienstanwendung  
  
1.  Aktivieren Sie für einen Berichtsserver im SharePoint-Modus, der mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] oder einer neueren Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]installiert wurde, die Dienstanwendungseinstellung **Remotefehler aktivieren**. Die Einstellung kann für jede [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung konfiguriert werden.  
  
2.  Klicken Sie in der SharePoint-Zentraladministration in der Gruppe **Anwendungsverwaltung** auf **Dienstanwendungen verwalten** .  
  
3.  Suchen Sie Ihre [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung, und klicken Sie auf den Namen der Dienstanwendung.  
  
4.  Klicken Sie auf **Systemeinstellungen**.  
  
5.  Klicken Sie im Abschnitt **Sicherheit** auf **Remotefehler aktivieren** .  
  
6.  Klicken Sie auf **OK**.  
  
#### <a name="enable-remote-errors-for-a-sharepoint-site"></a>Aktivieren von Remotefehlern für eine SharePoint-Website  
  
1.  Aktivieren Sie für einen Berichtsserver im SharePoint-Modus, der mit einer Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vor [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]installiert ist, die Websiteeinstellung **Remotefehler im lokalen Modus aktivieren**.  
  
2.  Klicken Sie unter **Websiteaktionen** auf **Siteeinstellungen** für die zu ändernde Website.  
  
3.  Klicken Sie in der Gruppe **Reporting Services** auf **Einstellungen für Reporting Services-Websites** .  
  
4.  Klicken Sie auf **Remotefehler im lokalen Modus aktivieren**.  
  
5.  Klicken Sie auf **OK**.  
  
##  <a name="bkmk_mgtStudio"></a> Aktivieren von Remotefehlern durch SQL Server Management Studio (Einheitlicher Modus)  
  
1.  Starten Sie Management Studio, und stellen Sie eine Verbindung mit einer Berichtsserverinstanz her. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](../tools/connect-to-a-report-server-in-management-studio.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Berichtsserverknoten, und wählen Sie **Eigenschaften**aus.  
  
3.  Klicken Sie auf **Erweitert** , um die Eigenschaftenseite zu öffnen. Weitere Informationen finden Sie unter [Servereigenschaften (Seite „Erweitert“) – Reporting Services](../tools/server-properties-advanced-page-reporting-services.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
4.  In `EnableRemoteErrors`Option `True`.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="bkmk_script"></a> Aktivieren von Remotefehlern per Skript (Einheitlicher Modus)  
  
1.  Erstellen Sie eine Textdatei, und kopieren Sie das folgende Skript in die Datei.  
  
    ```  
    Public Sub Main()  
      Dim P As New [Property]()  
      P.Name = "EnableRemoteErrors"  
      P.Value = True  
      Dim Properties(0) As [Property]  
      Properties(0) = P  
      Try  
        rs.SetSystemProperties(Properties)  
        Console.WriteLine("Remote errors enabled.")  
      Catch SE As SoapException  
        Console.WriteLine(SE.Detail.OuterXml)  
      End Try  
    End Sub  
    ```  
  
2.  Speichern Sie die Datei unter dem Namen EnableRemoteErrors.rss.  
  
3.  Klicken Sie auf **Start**, zeigen Sie auf **Ausführen**, geben Sie **cmd**ein, und klicken Sie auf **OK** , um eine Eingabeaufforderung zu öffnen.  
  
4.  Wechseln Sie in das Verzeichnis, das die zuvor von Ihnen erstellte RSS-Datei enthält.  
  
5.  Geben Sie die folgenden Befehlszeile ein. Ersetzen Sie dabei *servername* durch den Namen Ihres aktuellen Servers:  
  
    ```  
    rs -i EnableRemoteErrors.rss -s http://servername/ReportServer  
    ```  
  
6.  Weitere Informationen finden Sie unter [Hilfsprogramm RS.exe &#40;SSRS&#41;](../tools/rs-exe-utility-ssrs.md).  
  
##  <a name="bkmk_ConfigurationInfo"></a> Ändern der ConfigurationInfo-Tabelle (Einheitlicher Modus)  
  
1.  > [!NOTE]  
    >  Können Sie bearbeiten die **ConfigurationInfo** -Tabelle in der Berichtsserver-Datenbank festlegen `EnableRemoteErrors` zu `True`, aber wenn der Berichtsserver aktiv verwendet wird, verwenden Sie SQL Server Management Studio oder ein Skript zum Ändern der Einstellungen. Wenn Sie die Einstellung in der Datenbank ändern, müssen Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienst neu starten, bevor die Änderungen wirksam werden.  
  
  
