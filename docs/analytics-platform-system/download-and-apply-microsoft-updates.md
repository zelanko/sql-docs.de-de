---
title: Microsoft-Updates herunterladen
description: In diesem Thema wird erläutert, wie Sie Updates aus dem Microsoft Update Katalog in Windows Server Update Services (WSUS) herunterladen und diese Updates auf die Analytics Platform System Appliance-Server anwenden. In Microsoft Update werden alle anwendbaren Updates für Windows und SQL Server installiert. WSUS ist auf dem virtuellen VMM-Computer des Geräts installiert.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 2b24d55720d6db5997bfa85c2621f0e8d58c5f95
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401191"
---
# <a name="download-and-apply-microsoft-updates-for-analytics-platform-system"></a>Herunterladen und Anwenden von Microsoft-Updates für Analytics Platform System
In diesem Thema wird erläutert, wie Sie Updates aus dem Microsoft Update Katalog in Windows Server Update Services (WSUS) herunterladen und diese Updates auf die Analytics Platform System Appliance-Server anwenden. In Microsoft Update werden alle anwendbaren Updates für Windows und SQL Server installiert. WSUS ist auf dem virtuellen VMM-Computer des Geräts installiert.  
  
## <a name="before-you-begin"></a><a name="TOP"></a>Bevor Sie beginnen  
  
> [!WARNING]  
> Versuchen Sie nicht, Updates anzuwenden, wenn Ihr Gerät oder eine Appliance-Komponente ausgefallen ist oder sich in einem failoverzustand befindet. Wenden Sie sich in diesem Fall an den Support.  
>   
> Wenden Sie Microsoft Updates nicht an, während das Gerät verwendet wird. Durch das Anwenden von Updates können Geräteknoten neu gestartet werden. Die Updates sollten während eines Wartungs Fensters angewendet werden, wenn das Gerät nicht verwendet wird.  
  
### <a name="prerequisites"></a>Voraussetzungen  
Bevor Sie diese Schritte ausführen, müssen Sie folgende Schritte ausführen:  
  
-   Konfigurieren Sie WSUS auf Ihrer Appliance, indem Sie die Anweisungen unter [Konfigurieren von Windows Server Update Services &#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md)befolgen.  
  
-   Kenntnisse über die Anmelde Informationen eines Fabric-Domänen Administrator Kontos.  
  
-   Sie verfügen über einen Anmelde Namen mit Berechtigungen für den Zugriff auf die Verwaltungskonsole des Analytics-plattformsystems und zeigen Informationen zum Gerätezustand  
  
-   In den meisten Fällen muss WSUS auf Server außerhalb des Geräts zugreifen können. Zur Unterstützung dieses Verwendungs Szenarios kann das Analytics Platform System DNS so konfiguriert werden, dass eine externe namens Weiterleitung unterstützt wird, die es den Analytics-Plattformsystem Hosts und-Virtual Machines (VMS) ermöglicht, externe DNS-Server zum Auflösen von Namen außerhalb des Geräts zu verwenden. Weitere Informationen finden Sie unter [Verwenden einer DNS-Weiterleitung zum Auflösen von DNS-Namen, die keine Appliance sind &#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
## <a name="to-download-and-apply-microsoft-updates"></a><a name="bkmk_ImportUpdates"></a>Herunterladen und Anwenden von Microsoft-Updates  
  
#### <a name="verify-the-appliance-state-indicators"></a>Überprüfen der Gerätestatus Indikatoren  
  
1.  Öffnen Sie die Verwaltungskonsole, und navigieren Sie zur Seite Gerätestatus. Weitere Informationen finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
2.  Überprüfen Sie die Status Indikatoren für alle Knoten im Gerätezustand.  
  
    -   Es ist sicher, mit grünen oder na-Indikatoren fortzufahren.  
  
    -   Auswerten nicht kritischer (gelber) Warnungs Fehler. In einigen Fällen blockieren Warnmeldungen keine Updates. Wenn ein nicht kritischer datenträgervolumefehler vorliegt, der nicht auf C:\ fest liegt Laufwerk, Sie können mit dem nächsten Schritt fortfahren, bevor Sie den Datenträger Volume-Fehler beheben.  
  
    -   Die meisten roten Indikatoren müssen aufgelöst werden, bevor Sie fortfahren. Wenn Datenträger Fehler auftreten, überprüfen Sie mithilfe der Seite Warnungen der Verwaltungskonsole, ob innerhalb der einzelnen Server-oder SAN-Arrays nicht mehr als ein Datenträger Fehler aufgetreten ist. Wenn innerhalb der einzelnen Server oder SAN-Arrays nicht mehr als ein Datenträger Fehler auftritt, können Sie mit dem nächsten Schritt fortfahren, bevor Sie die Datenträger Fehler beheben. Stellen Sie sicher, dass Sie sich an den Microsoft Support wenden, um die Datenträger Fehler schnellstmöglich zu beheben.  
  
#### <a name="synchronize-the-wsus-server"></a>Synchronisieren des WSUS-Servers  
  
1.  Melden Sie sich als Domänen Administrator bei der virtuellen VMM-Maschine an.  
  
2.  Klicken Sie **im Server-Manager-Dashboard**im **Menü Extras** auf **Windows Server Update Services** (**WSUS. msc**).  
  
3.  Klicken Sie in der WSUS-Verwaltungskonsole auf **synchronierungen**.  
  
4.  Wenn die Synchronisierung nicht ausgeführt wird, klicken Sie im rechten Bereich auf **Jetzt synchronisieren** . Im unteren Bereich wird der Synchronisierungs Status angezeigt. Warten Sie, bis die Synchronisierung abgeschlossen ist.  
  
#### <a name="approve-microsoft-updates-in-wsus"></a>Genehmigen von Microsoft-Updates in WSUS  
  
1.  Klicken Sie im linken Bereich der WSUS-Konsole auf **alle Updates**.  
  
2.  Klicken Sie im Bereich **alle Updates** auf das Dropdown Menü **Genehmigung** , und legen Sie **Genehmigung** auf **alle außer abgelehnt**fest. Klicken Sie auf das Dropdown Menü **Status** , und legen Sie **Status** auf **beliebig**fest. Klicken Sie auf **Aktualisieren**.  
  
    Klicken Sie mit der rechten Maustaste auf die Spalte **Titel** , und wählen Sie **Dateistatus** aus, um den Dateistatus nach dem Download zu überprüfen  
  
    Sie können im linken Bereich auch **kritische Updates** oder **Sicherheitsupdates** auswählen und verfügbare Updates für diese Kategorien anzeigen.  
  
    ![Wählen Sie alle Updates aus, und ändern Sie den Status in 'Beliebig'.](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectAllUpdates.png "SQL_Server_PDW_WSUSSelectAllUpdates")  
  
3.  Wählen Sie alle Updates aus, und klicken Sie dann im rechten Bereich auf den Link **genehmigen** .  
  
    Sie können auch mit der rechten Maustaste auf die ausgewählten Updates klicken und dann auf **genehmigen**klicken. Möglicherweise werden Sie aufgefordert, die Microsoft-Software-Lizenzbedingungen zu akzeptieren. Wenn dies der Fall ist, klicken Sie im Fenster auf **akzeptieren** , um fortzufahren.  
  
    ![Wählen Sie alle zutreffenden Updates aus, und klicken Sie auf 'Genehmigen'.](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectApprove.png "SQL_Server_PDW_WSUSSelectApprove")  
  
4.  Wählen Sie die Geräteserver Gruppe aus, die Sie unter [Konfigurieren von Windows Server Update Services &#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md)erstellt haben.  
  
5.  Klicken Sie auf **Für die Installation genehmigt**und anschließend auf **OK**.  
  
    ![Genehmigen Sie Updates für die Computergruppe.](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectApprovalType.png "SQL_Server_PDW_WSUSSelectApprovalType")  
  
6.  Klicken Sie im Dialogfeld **Genehmigungs** Status auf **Schließen**, wenn der Genehmigungs Vorgang abgeschlossen ist.  
  
    ![Schließen Sie das Fenster nach dem Genehmigen der Updates.](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSCloseApprovalProgressWindow.png "SQL_Server_PDW_WSUSCloseApprovalProgressWindow")  
  
#### <a name="verify-that-the-updates-are-in-wsus"></a>Überprüfen, ob sich die Updates in WSUS befinden  
  
-  Überprüfen Sie den Dateistatus aller Updates. Jede Datei muss über ein grünes Pfeilsymbol auf der linken Seite des Titels verfügen. Dies gibt an, dass die Datei für die Installation bereit ist.  
  
    ![Dateistatus ist erfolgreich](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUS_File_Status.png "SQL_Server_PDW_WSUS_File_Status")  
  
    Stellen Sie vor der Installation der Updates sicher, dass Sie alle heruntergeladen und in der WSUS-Konsole verfügbar sind.  
  
#### <a name="to-verify-that-all-updates-are-downloaded"></a>So überprüfen Sie, ob alle Updates heruntergeladen wurden  
  
-  Überprüfen Sie den **Download Status** von Updates in der WSUS-Konsole, wie im folgenden Screenshot zu sehen. Vergewissern Sie sich, dass die Dateien, die **Dateien benötigen** , 0 sind, um sicherzustellen, dass alle Updates Wenn diese Zahl größer als 0 (null) ist, müssen Sie möglicherweise zurückkehren und weitere Updates genehmigen.  
  
    ![Stellen Sie sicher, dass alle Updates heruntergeladen wurden.](./media/download-and-apply-microsoft-updates/SQL_Server_PDS_WSUS_VerifyDownloadUpdateJPG.png "SQL_Server_PDS_WSUS_VerifyDownloadUpdateJPG")  
  
#### <a name="apply-microsoft-updates"></a>Anwenden von Microsoft-Updates  
  
1.  Öffnen Sie zunächst das [Gerät überwachen mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md), klicken Sie auf die Registerkarte **Appliance State** , und vergewissern Sie sich, dass die Spalten **Cluster** und **Netzwerk** für alle Knoten grün (oder Na) angezeigt werden. Wenn in einer dieser Spalten Warnungen vorhanden sind, ist das Gerät möglicherweise nicht in der Lage, Updates ordnungsgemäß zu installieren. Beheben Sie alle vorhandenen Warnungen in den **Cluster** -und **Netzwerk** Spalten, bevor Sie fortfahren.  
  
2.  Melden Sie sich beim _<domain_name _ **-Knoten>-HST01** als Fabric-Domänen Administrator an.  
  
3.  Führen Sie das Update Programm aus, um alle für WSUS genehmigten Updates anzuwenden. Anweisungen hierzu finden Sie unter [Ausführen des Aktualisierungs Programms](#RunUpdateWizard) .  
  
#### <a name="verify-the-updates-on-all-nodes"></a>Überprüfen der Updates auf allen Knoten  
  
1.  Starten Sie die WSUS-Verwaltungskonsole über den VMM-Knoten. Diese Anwendung befindet sich unter **Start**, **Verwaltung**, **Windows Server Update Services**.  
  
2.  Erweitern Sie **Computer**.  
  
3.  Erweitern Sie **alle Computer**.  
  
4.  Wählen Sie die Geräteserver Gruppe aus, die Sie unter [Konfigurieren von Windows Server Update Services &#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md)erstellt haben.  
  
5.  Wählen Sie im Dropdown Menü **Status** **einen beliebigen** aus, und klicken Sie auf **Aktualisieren**.  
  
6.  Erweitern **Sie Update Services** *<appliance name>*,-VMM, **Updates**und **alle Updates**, *<appliance name>* wobei der Name der Anwendung ist.  
  
7.  Legen Sie im Fenster **alle Updates** die **Genehmigung** auf **alle außer abgelehnt**fest.  
  
8.  Legen Sie im Fenster **alle Updates** den **Status** auf **failed oder erforderlich**fest.  
  
9. Klicken Sie auf **Aktualisieren**.  
  
10. Wenn die **erforderlichen Updates** größer als 0 (null) sind, wenden Sie sich an den Support.  
  
#### <a name="ensure-there-are-no-critical-alerts-in-the-sql-server-pdw-admin-console"></a>Stellen Sie sicher, dass in der SQL Server PDW Admin Console keine kritischen Warnungen vorhanden sind.  
  
1.  Öffnen Sie die Verwaltungskonsole, und klicken Sie auf die Registerkarte Appliance State. Weitere Informationen finden [Sie unter Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md).  
  
2.  Vergewissern Sie sich, dass die Spalten **Cluster** und **Netzwerk** für alle Knoten grün (oder Na) angezeigt werden. Wenn in einer dieser Spalten Warnungen vorhanden sind, ist das Gerät möglicherweise nicht in der Lage, Updates ordnungsgemäß zu installieren. Wenden Sie sich an den Support, wenn kritische Warnungen vorliegen.  
  
## <a name="run-the-update-program"></a><a name="RunUpdateWizard"></a>Ausführen des Aktualisierungs Programms  
Befolgen Sie diese Anweisungen, um das Programm zum Aktualisieren von Analytics-Platt Form Systemen auszuführen.  
  
> [!NOTE]  
> Die asynchrone Ausführung des WSUS-Systems kann einige Zeit in Anspruch nehmen, um alle Updates vollständig anzuwenden. Beim Initiieren eines Updates wird ein Update geplant, aber es wird keine sofortige Aktualisierungs Aktivität garantiert.  
  
1.  Stellen Sie sicher, dass Sie beim Knoten HST01 als Fabric-Domänen Administrator angemeldet sind.  
  
2.  Öffnen Sie ein Eingabe Aufforderungs Fenster, und geben Sie die folgenden Befehle ein. Ersetzen *<parameter>* Sie dies durch die angegebenen Informationen.  
  
**So führen Sie den Microsoft Update aus:**  
  
```  
C:\pdwinst\media\setup.exe /action="MicrosoftUpdate" /DomainAdminPassword="<password>"  
```  
  
**So melden Sie den Microsoft Update Status:**  
  
```  
C:\pdwinst\media\setup.exe /action="ReportMicrosoftUpdateClientStatus" /DomainAdminPassword="<password>"  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[Deinstallieren von Microsoft Updates &#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
[Anwenden von Analytics-Plattformsystem-Hotfixes &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
[Deinstallieren Sie die Analytics Platform System-Hotfixes &#40;Analytics Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
[Software Wartung &#40;Analytics-Platt Form System&#41;](software-servicing.md)  
  
