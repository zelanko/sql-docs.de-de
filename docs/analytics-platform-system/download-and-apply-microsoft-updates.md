---
title: Herunterladen von Microsoft Updates – Analytics Platform System | Microsoft-Dokumentation
description: In diesem Thema wird erläutert, wie Updates von Microsoft Update-Katalogs auf Windows Server Update Services (WSUS) herunterladen und Anwenden von Updates mit den Servern des Analytics Platform System Appliance. Microsoft Update installiert alle anwendbaren Updates für Windows und SQL Server. WSUS ist auf die VMM-VM, des Geräts installiert.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d71a6ddc965b422f0f96f40788352213501b4db2
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52521478"
---
# <a name="download-and-apply-microsoft-updates-for-analytics-platform-system"></a>Herunterladen und Anwenden von Microsoft-Updates für Analytics Platform System
In diesem Thema wird erläutert, wie Updates von Microsoft Update-Katalogs auf Windows Server Update Services (WSUS) herunterladen und Anwenden von Updates mit den Servern des Analytics Platform System Appliance. Microsoft Update installiert alle anwendbaren Updates für Windows und SQL Server. WSUS ist auf die VMM-VM, des Geräts installiert.  
  
## <a name="TOP"></a>Vorbereitungen  
  
> [!WARNING]  
> Versuchen Sie nicht, um Updates anzuwenden, ist dem Gerät oder eine appliancekomponente heruntergefahren oder in einem fehlerhaften Zustand. In diesem Fall erhalten Sie Support um Unterstützung zu erhalten.  
>   
> Microsoft-Updates werden nicht angewendet werden, während das Gerät verwendet wird. Anwenden von Updates kann dazu führen, dass applianceknoten neu starten. Die Updates sollten während eines Wartungsfensters angewendet werden, wenn das Gerät nicht verwendet wird.  
  
### <a name="prerequisites"></a>Erforderliche Komponenten  
Bevor Sie diese Schritte ausführen, müssen Sie:  
  
-   Konfigurieren von WSUS auf Ihrem Gerät mithilfe der Anweisungen in [Konfigurieren von Windows Server Update Services &#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md).  
  
-   Kenntnisse in Bezug auf die Anmeldeinformationen für ein Fabric-Domänenadministrator-Konten.  
  
-   Haben Sie einen Anmeldenamen mit Berechtigungen zum Zugriff auf die Verwaltungskonsole für Analytics Platform System und die Ansichtszustandsinformationen für das Gerät.  
  
-   In den meisten Fällen muss WSUS-Server außerhalb der Anwendung zugreifen. Um dieses Verwendungsszenario zu unterstützen, die DNS Analytics Platform System so eine Weiterleitung von externen Namen unterstützen, die die Analytics Platform System-Hosts und virtuellen Computern (VMs), externe DNS-Servern zum Auflösen von Namen verwendet werden kann konfiguriert werden, kann außerhalb von, der Appliance. Weitere Informationen finden Sie unter [verwenden Sie eine DNS-Weiterleitung zum Auflösen nicht zu Appliances DNS-Namen &#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
## <a name="bkmk_ImportUpdates"></a>Das Herunterladen und Anwenden von Microsoft-updates  
  
#### <a name="verify-the-appliance-state-indicators"></a>Überprüfen Sie die Appliance Statusindikatoren  
  
1.  Öffnen Sie die Admin-Konsole, und navigieren Sie zu der Seite "Status der Appliance". Weitere Informationen finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
2.  Vergewissern Sie sich die Statusindikatoren für alle Knoten auf den Anwendungszustand.  
  
    -   Es ist sicher ist, Grün oder NA Indikatoren fortzusetzen.  
  
    -   Nicht kritische (gelb) Fehler der Warnung ausgewertet werden. In einigen Fällen werden Warnmeldungen nicht blockieren von Aktualisierungen. Ist ein nicht-kritische Volume Datenträgerfehler, der nicht auf dem Laufwerk C:\ ist, können Sie vor dem Beheben des Fehlers der Datenträger-Volume mit dem nächsten Schritt fortfahren.  
  
    -   Die meisten rote Indikatoren müssen vor dem Fortfahren aufgelöst werden. Wenn Datenträgerfehler sind, verwenden Sie der Seite "Admin-Konsole Warnungen", um sicherstellen, dass derzeit nicht mehr als ein Fehler auf dem Datenträger in jedem Server oder die SAN-Array. Ist nicht mehr als einen Datenträgerfehler in jedem Server oder die SAN-Array, können Sie mit dem nächsten Schritt fortfahren, bevor Sie die Datenträgerfehler zu beheben. Achten Sie darauf, dass Sie den Microsoft-Support, um die Datenträgerfehler so bald wie möglich zu beheben.  
  
#### <a name="synchronize-the-wsus-server"></a>Den WSUS-Server synchronisieren  
  
1.  Melden Sie sich an den virtuellen Computer von VMM als Domänenadministrator an.  
  
2.  In der **Server-Managers**auf die **Tools** Menü klicken Sie auf **Windows Server Update Services** (**wsus.msc**).  
  
3.  Klicken Sie in der WSUS-Verwaltungskonsole auf **Synchronisierungen**.  
  
4.  Wenn die Synchronisierung nicht ausgeführt wird, klicken Sie auf **jetzt synchronisieren** im rechten Bereich. Im unteren Bereich werden der Status einer Synchronisierung. Warten Sie, bis die Synchronisierung abgeschlossen ist.  
  
#### <a name="approve-microsoft-updates-in-wsus"></a>Microsoft-Updates in WSUS genehmigt  
  
1.  Klicken Sie im linken Bereich der WSUS-Konsole auf **alle Updates**.  
  
2.  In der **alle Updates** Bereich, klicken Sie auf die **Genehmigung** Dropdown-Menü, Set **Genehmigung** zu **alle bis auf abgelehnte**. Klicken Sie auf die **Status** Dropdown-Menü, Satz **Status** zu **alle**. Klicken Sie auf **Aktualisieren**.  
  
    Mit der rechten Maustaste die **Titel** Spalte, und wählen **Dateistatus** den Dateistatus zu überprüfen, nachdem der Download abgeschlossen ist.  
  
    Sie können auch auswählen, **kritische Updates** oder **Sicherheitsupdates** im linken Bereich und die Ansicht verfügbaren Updates für diese Kategorien.  
  
    ![Wählen Sie alle Updates aus, und Ändern von Status an. ](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectAllUpdates.png "SQL_Server_PDW_WSUSSelectAllUpdates")  
  
3.  Wählen Sie alle Updates, und klicken Sie dann auf die **genehmigen** Link im rechten Bereich.  
  
    Sie können auch Maustaste auf die ausgewählten Updates auswirken könnte, und klicken Sie dann auf **genehmigen**. Sie werden möglicherweise aufgefordert, die "Microsoft Software License Terms" zu akzeptieren. Wenn dies der Fall ist, klicken Sie auf **akzeptieren** im Fenster, um den Vorgang fortzusetzen.  
  
    ![Wählen Sie alle Updates, die gelten, und klicken Sie auf genehmigen. ](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectApprove.png "SQL_Server_PDW_WSUSSelectApprove")  
  
4.  Wählen Sie die Appliance Server aus, die Sie erstellt, im haben [Konfigurieren von Windows Server Update Services &#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md).  
  
5.  Klicken Sie auf **für die Installation genehmigt**, und klicken Sie dann auf **OK**.  
  
    ![Genehmigen Sie Updates für die Computergruppe. ](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectApprovalType.png "SQL_Server_PDW_WSUSSelectApprovalType")  
  
6.  In der **Status der Genehmigung** Dialogfeld nach Abschluss des Genehmigungsprozesses, klicken Sie auf **schließen**.  
  
    ![Fenster schließen, wenn Updates genehmigt wurden. ](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSCloseApprovalProgressWindow.png "SQL_Server_PDW_WSUSCloseApprovalProgressWindow")  
  
#### <a name="verify-that-the-updates-are-in-wsus"></a>Stellen Sie sicher, dass die Updates in WSUS  
  
-  Überprüfen Sie den Dateistatus aller Updates aus. Jede Datei muss einen grüner Pfeil auf der linken Seite des Titels. Dies gibt an, dass die Datei zur Installation bereit ist.  
  
    ![Dateistatus ist erfolgreich](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUS_File_Status.png "SQL_Server_PDW_WSUS_File_Status")  
  
    Stellen Sie vor der Installation der Updates sicher, dass sie alle heruntergeladen und in der WSUS-Konsole verfügbar sind.  
  
#### <a name="to-verify-that-all-updates-are-downloaded"></a>Um sicherzustellen, dass alle Updates heruntergeladen wurden  
  
-  Überprüfen Sie die **Downloadstatus** von Updates in der WSUS-Verwaltungskonsole, wie im folgenden Screenshot gezeigt. Überprüfen Sie, ob **Updates, die Dateien erfordern** ist 0, um sicherzustellen, dass alle Updates heruntergeladen wurden. Wenn diese Zahl größer als NULL ist, müssen Sie zurückgehen und weitere Updates genehmigen.  
  
    ![Stellen Sie sicher, dass alle Updates heruntergeladen werden. ](./media/download-and-apply-microsoft-updates/SQL_Server_PDS_WSUS_VerifyDownloadUpdateJPG.png "SQL_Server_PDS_WSUS_VerifyDownloadUpdateJPG")  
  
#### <a name="apply-microsoft-updates"></a>Anwenden von Microsoft-updates  
  
1.  Bevor Sie beginnen, öffnen Sie die [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md), klicken Sie auf der **Anwendungszustand** Registerkarte, und überprüfen Sie, ob die  **Cluster** und **Netzwerk** Spalten anzeigen Grün (oder NV) für alle Knoten. Wenn keine Warnungen in diesen Spalten vorhanden sind, das Gerät nicht ordnungsgemäß installiert. Updates möglicherweise. Beheben Sie alle vorhandene Warnungen in der **Cluster** und **Netzwerk** Spalten, bevor Sie fortfahren.  
  
2.  Melden Sie sich an den _< Domänenname >_**-HST01** als Domänenadministrator Fabric-Knoten.  
  
3.  Um alle Updates für WSUS genehmigt anzuwenden, führen Sie das Update-Programm. Finden Sie unter [führen Sie das Update-Programm](#RunUpdateWizard) folgenden Anweisungen.  
  
#### <a name="verify-the-updates-on-all-nodes"></a>Überprüfen Sie die Updates auf allen Knoten  
  
1.  Starten Sie die WSUS-Verwaltungskonsole, aus dem VMM-Knoten. Diese Anwendung finden Sie unter **starten**, **Verwaltung**, **Windows Server Update Services**.  
  
2.  Erweitern Sie **Computer**.  
  
3.  Erweitern Sie **alle Computer**.  
  
4.  Wählen Sie die Appliance Server aus, die Sie erstellt, im haben [Konfigurieren von Windows Server Update Services &#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md).  
  
5.  In der **Status** wählen Sie im Dropdownmenü **alle** , und klicken Sie auf **aktualisieren**.  
  
6.  Erweitern Sie **Dienste aktualisieren**, *<appliance name>*- VMM **Updates**, **alle Updates**, wobei *<appliance name>* ist der Name des Geräts.  
  
7.  In der **alle Updates** legen **Genehmigung** zu **alle bis auf abgelehnte**.  
  
8.  In der **alle Updates** legen **Status** zu **Fehler oder benötigt**.  
  
9. Klicken Sie auf **Aktualisieren**.  
  
10. Wenn **erforderlichen Updates** ist größer als 0 (null), wenden Sie sich an Support um Unterstützung zu erhalten.  
  
#### <a name="ensure-there-are-no-critical-alerts-in-the-sql-server-pdw-admin-console"></a>Stellen Sie sicher, dass keine kritischen Warnungen vorliegen, in der SQL Server PDW-Verwaltungskonsole  
  
1.  Öffnen Sie die Verwaltungskonsole, klicken Sie auf der Registerkarte "Status der Appliance". Finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics-Plattformsystem&#41;](monitor-the-appliance-by-using-the-admin-console.md).  
  
2.  Überprüfen Sie, ob die **Cluster** und **Netzwerk** Spalten anzeigen Grün (oder NV) für alle Knoten. Wenn keine Warnungen in diesen Spalten vorhanden sind, das Gerät nicht ordnungsgemäß installiert. Updates möglicherweise. An den wenden Sie Support, wenn kritische Warnungen vorliegen.  
  
## <a name="RunUpdateWizard"></a>Führen Sie das Update-Programm  
Um das Analytics Platform System Update-Programm auszuführen, gehen Sie wie folgt vor.  
  
> [!NOTE]  
> Der WSUS-System dient zur Ausführung asynchron kann einige Zeit dauern, das vollständig alle Updates anzuwenden. Initiiert ein Update ein Update geplant ist jedoch kein Garant sofortiges Update-Aktivität.  
  
1.  Stellen Sie sicher, dass Sie bei der HST01-Knoten als der Fabric-Domänenadministrator angemeldet sind.  
  
2.  Öffnen Sie ein Eingabeaufforderungsfenster, und geben Sie die folgenden Befehle aus. Ersetzen Sie dies *<parameter>* mit den angegebenen Informationen.  
  
**So führen Sie die Microsoft Update aus:**  
  
```  
C:\pdwinst\media\setup.exe /action="MicrosoftUpdate" /DomainAdminPassword="<password>"  
```  
  
**Um den Microsoft Update-Status zu melden:**  
  
```  
C:\pdwinst\media\setup.exe /action="ReportMicrosoftUpdateClientStatus" /DomainAdminPassword="<password>"  
```  
  
## <a name="see-also"></a>Siehe auch  
[Deinstallieren von Microsoft-Updates &#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
[Anwenden von Hotfixes für Analytics Platform System &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
[Deinstallieren von Hotfixes für Analytics Platform System &#40;Analytics Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
[Softwarewartung &#40;Analytics Platform System&#41;](software-servicing.md)  
  
