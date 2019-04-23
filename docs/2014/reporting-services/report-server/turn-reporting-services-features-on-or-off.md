---
title: Aktivieren und Deaktivieren von Features von Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, configuration
- security [Reporting Services], strategies
ms.assetid: b69db02a-43a7-4fdc-ad9b-438d817a7f83
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f5e927e8b25097e09d3ecba67bfd3e75d9e8c9be
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59954786"
---
# <a name="turn-reporting-services-features-on-or-off"></a>Aktivieren und Deaktivieren der Reporting Services-Funktionen
  Sie können Berichtsserver-Funktionen, die Sie nicht als Teil einer Sicherheitsstrategie verwenden, deaktivieren, um die Angriffsfläche eines Produktionsberichtsservers zu verkleinern. In den meisten Fällen sollten Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Features gleichzeitig ausführen, damit Sie alle Funktionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]verwenden können. Sie können jedoch je nach Bereitstellungsmodell die Funktionen deaktivieren, die Sie nicht benötigen. Beispielweise können Sie nur die Hintergrundverarbeitung aktivieren, wenn die gesamte Berichtsverarbeitung in Form von geplanten Vorgängen konfiguriert ist. Entsprechend können Sie nur den Report Server-Webdienst ausführen, wenn Sie ausschließlich interaktive, bedarfsgesteuerte Berichte wünschen.  
  
 Die Prozeduren in diesem Thema erläutern, wie Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Funktionen des einheitlichen Modus deaktivieren. Sie können die Funktionen auf verschiedene Arten konfigurieren, z.B. indem Sie die Datei `RsReportServer.config` direkt bearbeiten oder indem Sie das Facet **Oberflächenkonfiguration für Reporting Services** der richtlinienbasierten Verwaltung in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]bearbeiten. Verwenden Sie die Links, um auf die Prozeduren zuzugreifen, in denen das Aktivieren und Deaktivieren einer Funktion erläutert wird:  
  
-   [Report Server-Webdienst](#RSWebSvc)  
  
-   [Geplante Ereignisse und Verarbeitung](#Sched)  
  
-   [Berichts-Manager](#ReportManager)  
  
-   [Report Builder (Berichts-Generator)](#ReportBuilder)  
  
-   [Integrierte Sicherheit von Windows für Berichtsdatenquellen](#WinIntSec)  
  
##  <a name="RSWebSvc"></a> Report Server Web Service  
  
#### <a name="to-turn-on-or-off-the-report-server-web-service-by-editing-configuration"></a>So aktivieren bzw. deaktivieren Sie den Berichtsserver-Webdienst, indem Sie die Konfiguration bearbeiten  
  
1.  Öffnen Sie die Datei `RsReportServer.config` in einem Texteditor. Weitere Informationen finden Sie unter [Ändern einer Reporting Services-Konfigurationsdatei (RSreportserver.config)](modify-a-reporting-services-configuration-file-rsreportserver-config.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
2.  Um den Berichtsserver-Webdienst zu aktivieren, setzen Sie `IsWebServiceEnabled` auf `true`:  
  
    ```  
    <IsWebServiceEnabled>true</IsWebServiceEnabled>  
    ```  
  
3.  Um den Berichtsserver-Webdienst zu deaktivieren, setzen Sie `IsWebServiceEnabled` auf `false`:  
  
    ```  
    <IsWebServiceEnabled>false</IsWebServiceEnabled>  
    ```  
  
4.  Speichern Sie die Änderungen, und schließen Sie dann die Datei.  
  
#### <a name="to-turn-on-or-off-the-report-server-web-service-by-using-sql-server-management-studio"></a>So aktivieren bzw. deaktivieren Sie den Berichtsserver-Webdienst mithilfe von SQL Server Management Studio  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , und stellen Sie eine Verbindung zu der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz her, die Sie konfigurieren möchten.  
  
2.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Knoten, zeigen Sie auf **Richtlinien**, und klicken Sie auf **Facets**.  
  
3.  Wählen Sie in der Liste **Facet** den Eintrag **Oberflächenkonfiguration für Reporting Services**aus.  
  
4.  Führen Sie unter **Facet-Eigenschaften**Folgendes durch:  
  
    -   Um auf die Berichtsserver-Webdienst zu aktivieren, setzen **WebServiceAndHTTPAccessEnabled** zu `True`.  
  
    -   Um die Berichtsserver-Webdienst zu deaktivieren, setzen **WebServiceAndHTTPAccessEnabled** zu `False`.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="Sched"></a> Geplante Ereignisse und Übermittlung  
  
#### <a name="to-turn-on-or-off-scheduled-events-and-delivery-by-editing-configuration"></a>So aktivieren bzw. deaktivieren Sie geplante Ereignisse und die Übermittlung, indem Sie die Konfiguration bearbeiten  
  
1.  Öffnen Sie die Datei RSReportServer.config in einem Text-Editor. Weitere Informationen finden Sie unter [Ändern einer Reporting Services-Konfigurationsdatei (RSreportserver.config)](modify-a-reporting-services-configuration-file-rsreportserver-config.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
2.  Um die geplante Berichtsverarbeitung und -übermittlung zu aktivieren, setzen Sie `IsSchedulingService`, `IsNotificationService` und `IsEventService` auf `true`:  
  
    ```  
    <IsSchedulingService>true</IsSchedulingService>  
    <IsNotificationService>true</IsNotificationService>  
    <IsEventService>true</IsEventService>  
    ```  
  
3.  Um die geplante Berichtsverarbeitung und -übermittlung zu deaktivieren, setzen Sie `IsSchedulingService`, `IsNotificationService` und `IsEventService` auf `false`:  
  
    ```  
    <IsSchedulingService>false</IsSchedulingService>  
    <IsNotificationService>false</IsNotificationService>  
    <IsEventService>false</IsEventService>  
    ```  
  
4.  Speichern Sie die Änderungen, und schließen Sie dann die Datei.  
  
> [!NOTE]  
>  Die Hintergrundverarbeitung kann nicht vollständig deaktiviert werden, da sie Datenbankverwaltungsfunktionen enthält, die für den Serverbetrieb benötigt werden.  
  
#### <a name="to-turn-on-or-off-scheduled-events-and-delivery-by-using-sql-server-management-studio"></a>So aktivieren bzw. deaktivieren Sie geplante Ereignisse und die Übermittlung mithilfe von SQL Server Management Studio  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , und stellen Sie eine Verbindung zu der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz her, die Sie konfigurieren möchten.  
  
2.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Knoten, zeigen Sie auf **Richtlinien**, und klicken Sie auf **Facets**.  
  
3.  Wählen Sie in der Liste **Facet** den Eintrag **Oberflächenkonfiguration für Reporting Services**aus.  
  
4.  Führen Sie unter **Facet-Eigenschaften**Folgendes durch:  
  
    -   Um geplante Ereignisse und Übermittlung aktivieren, setzen **ScheduleEventsAndReportDeliveryEnabled** zu `True`.  
  
    -   Um geplante Ereignisse und Übermittlung zu deaktivieren, setzen **ScheduleEventsAndReportDeliveryEnabled** zu `False`.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  Die Hintergrundverarbeitung kann nicht vollständig deaktiviert werden, da sie Datenbankverwaltungsfunktionen enthält, die für den Serverbetrieb benötigt werden.  
  
##  <a name="ReportManager"></a> Berichts-Manager  
  
#### <a name="to-turn-on-or-off-report-manager-by-editing-configuration"></a>So aktivieren bzw. deaktivieren Sie den Berichts-Manager, indem Sie die Konfiguration bearbeiten  
  
1.  Öffnen Sie die Datei RSReportServer.config in einem Text-Editor. Anweisungen finden Sie unter [Ändern einer Reporting Services-Konfigurationsdatei &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
2.  Um den Berichts-Manager zu aktivieren, setzen Sie `IsReportManagerEnabled` auf `true`:  
  
    ```  
    <IsReportManagerEnabled>true</IsReportManagerEnabled>  
    ```  
  
3.  Um den Berichts-Manager zu deaktivieren, setzen Sie `IsReportManagerEnabled` auf `false`:  
  
    ```  
    <IsReportManagerEnabled>false</IsReportManagerEnabled>  
    ```  
  
4.  Speichern Sie die Änderungen, und schließen Sie dann die Datei.  
  
#### <a name="to-turn-on-or-off-report-manager-by-using-sql-server-management-studio"></a>So aktivieren bzw. deaktivieren Sie den Berichts-Manager mithilfe von SQL Server Management Studio  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , und stellen Sie eine Verbindung zu der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz her, die Sie konfigurieren möchten.  
  
2.  Klicken Sie im **Objekt-Explorer**mit der rechten Maustaste auf den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Knoten, zeigen Sie auf **Richtlinien**, und klicken Sie auf **Facets**.  
  
3.  Wählen Sie in der Liste **Facet** den Eintrag **Oberflächenkonfiguration für Reporting Services**aus.  
  
4.  Führen Sie unter **Facet-Eigenschaften**Folgendes durch:  
  
    -   Um Berichts-Manager zu aktivieren, setzen **ReportManagerEnabled** zu `True`.  
  
    -   Um Berichts-Manager zu aktivieren, setzen **ReportManagerEnabled** zu `False`.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="ReportBuilder"></a> Berichts-Generator  
  
#### <a name="to-turn-on-or-off-report-builder-by-using-sql-server-management-studio"></a>So aktivieren bzw. deaktivieren Sie den Berichts-Generator mithilfe von SQL Server Management Studio  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , und stellen Sie eine Verbindung zu der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz her, die Sie konfigurieren möchten.  
  
2.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Knoten, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Klicken Sie im Dialogfeld **Servereigenschaften** unter **Seite auswählen**auf **Sicherheit**.  
  
    -   Um den Berichts-Generator zu aktivieren, wählen Sie die Option **Ad-hoc-Berichtsausführungen aktivieren** .  
  
    -   Um den Berichts-Generator zu deaktivieren, heben Sie die Auswahl der Option **Ad-hoc-Berichtsausführungen aktivieren** auf.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="WinIntSec"></a> Integrierte Sicherheit von Windows  
  
#### <a name="to-turn-on-or-off-windows-integrated-security-by-using-sql-server-management-studio"></a>So aktivieren bzw. deaktivieren Sie die integrierte Windows-Sicherheit mithilfe von SQL Server Management Studio  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , und stellen Sie eine Verbindung zu der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz her, die Sie konfigurieren möchten.  
  
2.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Knoten, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Klicken Sie im Dialogfeld **Servereigenschaften** unter **Seite auswählen**auf **Sicherheit**.  
  
    -   Um die integrierte Sicherheit von Windows zu aktivieren, wählen Sie die Option **Integrierte Sicherheit von Windows für Berichtsdatenquellen aktivieren** .  
  
    -   Um die integrierte Sicherheit von Windows zu deaktivieren, heben Sie die Auswahl der Option **Integrierte Sicherheit von Windows für Berichtsdatenquellen aktivieren** auf.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
