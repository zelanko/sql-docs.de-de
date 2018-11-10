---
title: Konfigurieren Sie WSUS - Analytics Platform System | Microsoft-Dokumentation
description: Diese Anweisungen führen Sie durch die Schritte zur Verwendung der Windows Server Update Services (WSUS)-Konfigurations-Assistent zum Konfigurieren von WSUS für Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 4868aa775ac2958cc0e034196a0e911b58e78a34
ms.sourcegitcommit: 87f29b23d5ab174248dab5d558830eeca2a6a0a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51018525"
---
# <a name="configure-windows-server-update-services-wsus-in-analytics-platform-system"></a>Konfigurieren von Windows Server Update Services (WSUS) in Analytics Platform System
Diese Anweisungen führen Sie durch die Schritte zur Verwendung der Windows Server Update Services (WSUS)-Konfigurations-Assistent zum Konfigurieren von WSUS für Analytics Platform System. Sie müssen zum Konfigurieren von WSUS, bevor Sie Softwareupdates auf das Gerät anwenden können. WSUS ist bereits auf dem VMM-virtuellen Computer des Geräts installiert.  
  
Weitere Informationen zum Konfigurieren von WSUS finden Sie unter den [WSUS-Installation Anleitung](http://go.microsoft.com/fwlink/?LinkId=202417) auf die WSUS-Website. Nach dem Konfigurieren von WSUS, finden Sie unter [herunterladen und Anwenden von Microsoft-Updates &#40;Analytics Platform System&#41; ](download-and-apply-microsoft-updates.md) um ein Update zu initiieren.  
  
> [!WARNING]  
> Wenn Sie bei dieser Konfiguration Fehler auftreten, beenden Sie, und wenden Sie sich an den Support, um Unterstützung zu erhalten. Fehler ignorieren, und nicht im Prozess fortgesetzt wird, wenn der Fehler empfangen werden.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
Um WSUS konfigurieren zu können, müssen Sie:  
  
-   Haben Sie die Anmeldeinformationen für Analytics Platform System Appliance Domain Administrator-Konto an.  
  
-   Analytics Platform System Anmeldename mit Berechtigungen zum Zugriff auf die **Verwaltungskonsole** und Ansichtszustandsinformationen für das Gerät.  
  
-   Wissen Sie die IP-Adresse des WSUS-Upstreamserver, wenn Sie Updates von WSUS-Upstreamserver statt Synchronisieren von Updates direkt von Microsoft Update synchronisieren möchten. Stellen Sie sicher Ihre WSUS-Upstreamserver auf anonyme Verbindungen zulassen festgelegt ist und SSL unterstützt.  
  
-   Kennen Sie die IP-Adresse des Proxyservers an, wenn Ihr Gerät einen Proxyserver verwenden auf dem Upstreamserver oder Microsoft Update.  
  
-   In den meisten Fällen muss WSUS-Server außerhalb der Anwendung zugreifen. Um dieses Verwendungsszenario zu unterstützen, die DNS Analytics Platform System so eine Weiterleitung von externen Namen unterstützen, die die Analytics Platform System-Hosts und virtuellen Computern (VMs), externe DNS-Servern zum Auflösen von Namen verwendet werden kann konfiguriert werden, kann außerhalb von, der Appliance. Weitere Informationen finden Sie unter [verwenden Sie eine DNS-Weiterleitung zum Auflösen nicht zu Appliances DNS-Namen &#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
## <a name="to-configure-windows-server-update-services-wsus"></a>So konfigurieren Sie Windows Server Update Services (WSUS)  
  
1.  Melden Sie sich bei der **Verwaltungskonsole**. Auf der **Anwendungszustand** Registerkarte, überprüfen Sie, ob die **Cluster** und **Netzwerk** Spalten zeigen die grünen (oder **NA**) für alle Knoten. Überprüfen Sie die Statusindikatoren für alle Knoten auf den **Anwendungszustand**.  
  
    -   Es ist sicher ist, Grün oder NA Indikatoren fortzusetzen.  
  
    -   Nicht kritische (gelb) Fehler der Warnung ausgewertet werden. In einigen Fällen werden Warnmeldungen nicht blockieren von Aktualisierungen. Ist ein nicht-kritische Volume Datenträgerfehler, der nicht auf dem Laufwerk C:\ ist, können Sie vor dem Beheben des Fehlers der Datenträger-Volume mit dem nächsten Schritt fortfahren.  
  
    -   Die meisten rote Indikatoren müssen vor dem Fortfahren aufgelöst werden. Wenn Datenträgerfehler sind, verwenden Sie die **Admin-Konsole Warnungen** Seite, um sicherzustellen, ist es nicht mehr als einen Datenträgerfehler in jedem Server oder die SAN-Array. Ist nicht mehr als einen Datenträgerfehler in jedem Server oder die SAN-Array, können Sie mit dem nächsten Schritt fortfahren, bevor Sie die Datenträgerfehler zu beheben. Achten Sie darauf, dass Sie den Microsoft-Support, um die Datenträgerfehler so bald wie möglich zu beheben.  
  
2.  Melden Sie sich an den virtuellen Computer von VMM als ein Domänenadministrator Appliance an.  
  
3.  Starten Sie den Konfigurations-Assistenten.  
  
    #### <a name="to-launch-the-configuration-wizard"></a>Um den Konfigurations-Assistenten zu starten.  
  
    1.  In der **Server-Managers**auf die **Tools** Menü klicken Sie auf **Windows Server Update Services**.  
  
    2.  Im linken Bereich die **Update Services** klicken, um die Virtual Machine Management-Knoten-Server zu erweitern (***Appliance_domain *-VMM**), und klicken Sie dann auf **Optionen**.  
  
    3.  In der **Optionen** Bereich, klicken Sie auf **WSUS-Server-Konfigurations-Assistenten** um den Konfigurations-Assistenten zu starten.  
  
        ![Server-Manager-Dashboard-Menü](./media/configure-windows-server-update-services-wsus/WSUS_Wiz0.png "WSUS_Wiz0")  
  
    4.  Wenn das erste Mal haben Sie den WSUS-Konfigurationsassistenten ausführen, werden Sie möglicherweise aufgefordert, ein Verzeichnis zum Speichern der Updates konfigurieren. `C:\wsus` ist Sie ein geeigneten Speicherort. Sie können jedoch einen anderen Pfad bereitstellen.  
  
        ![WSUS-Pfad](./media/configure-windows-server-update-services-wsus/WSUS_Wiz1.png "WSUS_Wiz1")  
  
    5.  Überprüfen Sie die **Vorbemerkungen** Liste von Elementen, die abgeschlossen werden, bevor Sie den Assistenten abzuschließen.  
  
        ![WSUS vor dem Beginn](./media/configure-windows-server-update-services-wsus/WSUS_Wiz2.png "WSUS_Wiz2")  
  
    6.  Auf der **am Programm zur Verbesserung der Microsoft Update** Seite **Ja, ich möchte die Microsoft Update Improvement-Programm beizutreten**, und klicken Sie dann auf **Weiter**.  
  
        ![WSUS – Verbesserungsprogramm](./media/configure-windows-server-update-services-wsus/WSUS_Wiz3.png "WSUS_Wiz3")  
  
    Jetzt sollte die **Upstreamserver auswählen** Seite. Im folgende Screenshot ist der Ausgangspunkt des Konfigurations-Assistenten.  
  
    ![WSUS – Upstreamserversynchronisierung](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4a.png "WSUS_Wiz4a")  
  
4.  Auswählen des Upstreamservers an.  
  
    Auf der **Upstreamserver auswählen** Seite des WSUS-Konfigurations-Assistenten, wählen Sie wie WSUS auf dem Knoten für die Verwaltung virtueller Computer mit einem Upstreamserver zum Abrufen von Softwareupdates eine Verbindung herstellt. Die zwei Optionen lauten, mit dem Upstreamserver synchronisiert [Microsoft Update](http://go.microsoft.com/fwlink/?LinkId=133349) oder für die Synchronisierung von Updates mit einem anderen Windows Server Update Services-Server.  
  
    #### <a name="to-update-by-using-microsoft-update"></a>Mit Microsoft Update aktualisieren  
  
    1.  Wenn Sie mit Microsoft Update synchronisieren möchten, müssen Sie keine Änderungen an der **Upstreamserver auswählen** Seite. Klicken Sie auf **Weiter**.  
  
        ![WSUS – Upstreamserversynchronisierung](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4a.png "WSUS_Wiz4a")  
  
    #### <a name="to-update-from-another-wsus-server"></a>Aktualisieren von einem anderen WSUS-server  
  
    1.  Wenn Sie mit einer anderen Quelle als Microsoft Update (einen Upstreamserver) synchronisieren möchten, geben Sie den Server (Geben Sie die IP-Adresse) und den Port auf dem dieser Server mit dem Upstreamserver kommuniziert.  
  
        ![WSUS – Upstreamserversynchronisierung von WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4b.png "WSUS_Wiz4b")  
  
    2.  Um Secure Sockets Layer (SSL) verwenden möchten, wählen die **SSL beim Synchronisieren der Updateinformationen** Kontrollkästchen. In diesem Fall werden die Server Port 443 für die Synchronisierung verwenden.  
  
        ![WSUS – Upstreamserversynchronisierung von WSUS SSL](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4c.png "WSUS_Wiz4c")  
  
    3.  Wenn es sich um einen Replikatserver handelt, wählen Sie die **Dies ist ein Replikat des Upstreamservers** Kontrollkästchen. Es ist möglich, beide auswählen **SSL beim Synchronisieren der Updateinformationen** und **Dies ist ein Replikat des Upstreamservers**.  
  
        ![WSUS – Upstreamserverreplikat](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4d.png "WSUS_Wiz4d")  
  
    4.  An diesem Punkt sind Sie fertig ist, mit der upstream-Server-Konfiguration. Klicken Sie auf **Weiter**, oder wählen Sie **Proxyserver angeben** im linken Navigationsbereich.  
  
5.  Geben Sie den Proxyserver an.  
  
    Wenn dieser Server einen Proxyserver für Zugriff auf Microsoft Update oder einen anderen upstream-Server erforderlich ist, können Sie die proxyservereinstellungen hier konfigurieren. Klicken Sie anderenfalls auf **Weiter**.  
  
    ![WSUS Proxy](./media/configure-windows-server-update-services-wsus/WSUS_Wiz5a.png "WSUS_Wiz5a")  
  
    #### <a name="to-configure-proxy-server-settings"></a>Zum Konfigurieren von proxyservereinstellungen  
  
    1.  Auf der **Proxyserver angeben** auf der Seite im Konfigurations-Assistenten auf der **Proxyserver beim Synchronisieren von** , und geben Sie die Proxy-Server IP-Adresse (nicht "Name") und die Portnummer (Port 80 als (Standard) in die entsprechenden Felder.  
  
    2.  Sollten Sie mit dem Proxyserver herstellen von Verbindungen mithilfe von spezifischen Anmeldeinformationen, wählen Sie die **Benutzeranmeldeinformationen für die Verbindung mit dem Proxyserver verwenden** , und geben Sie dann in der entsprechenden der Benutzername, Domäne und das Kennwort des Benutzers zu deaktivieren. Wenn Sie die Standardauthentifizierung für den Benutzer, Herstellen einer Verbindung mit dem Proxyserver aktivieren möchten die **Standardauthentifizierung zulassen (Kennwort wird in Klartext gesendet)** Kontrollkästchen.  
  
        ![WSUS – Proxyanmeldeinformationen](./media/configure-windows-server-update-services-wsus/WSUS_Wiz5b.png "WSUS_Wiz5b")  
  
    3.  An diesem Punkt können Sie mit der Konfiguration des Proxyservers abgeschlossen. Klicken Sie auf **Weiter** auf der nächsten Seite wechseln, können Sie beginnen, um den Synchronisierungsprozess einzurichten.  
  
6.  Starten Sie eine Verbindung herstellen.  
  
    ![WSUS – Start der Proxyverbindung](./media/configure-windows-server-update-services-wsus/WSUS_Wiz6.png "WSUS_Wiz6")  
  
    Klicken Sie auf **starten, verbinden**.  
  
    Nachdem die Verbindung erfolgreich hergestellt wurde, klicken Sie auf **Weiter** auf der nächsten Seite wechseln, in denen Sie Sprachen können.  
  
7.  Wählen Sie die Sprachen.  
  
    Wählen Sie **Updates nur in folgenden Sprachen herunterladen**.  
  
    Wählen Sie **Englisch**, und klicken Sie dann auf **Weiter**.  
  
    ![Wählen Sie die Sprachen](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChooseLanguages.png "SQL_Server_PDW_WSUSChooseLanguages")  
  
8.  Wählen Sie die Produkte.  
  
    > [!NOTE]  
    > Wenn Sie einen Upstream-Server verwenden, können Sie nicht Produkte auswählen können. Wenn diese Option nicht verfügbar ist, überspringen Sie diesen Schritt.  
  
    Deaktivieren Sie alle ausgewählten Updates.  
  
    Wählen Sie **Windows Server 2012 R2**, und **System Center 2012 R2 – Virtual Machine Manager-**, und klicken Sie dann auf **Weiter**.  
  
9. Auswählen von Klassifizierungen.  
  
    > [!NOTE]  
    > Wenn Sie einen Upstream-Server verwenden, können Sie nicht Klassifizierungen auswählen können.  Wenn diese Option nicht verfügbar ist, überspringen Sie diesen Schritt.  
  
    Deaktivieren Sie alle zuvor ausgewählten Updates.  
  
    Wählen Sie **kritische Updates** und **Sicherheitsupdates** für die Updates, die für die Analytics Platform System Appliance synchronisiert werden, und klicken Sie dann auf **Weiter**.  
  
    ![Auswählen von Klassifizierungen](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChooseClassifications.png "SQL_Server_PDW_WSUSChooseClassifications")  
  
10. Konfigurieren Sie den Synchronisierungszeitplan an.  
  
    Wählen Sie **manuell synchronisieren**, und klicken Sie dann auf **Weiter**.  
  
    ![Festlegen des Synchronisierungszeitplans](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSyncSchedule.png "SQL_Server_PDW_WSUSSyncSchedule")  
  
11. Beginnen Sie die anfängliche Synchronisierung.  
  
    Wählen Sie **Erstsynchronisierung**, klicken Sie dann auf **Weiter**.  
  
12. Fertig stellen.  
  
    Klicken Sie auf **Fertig stellen**.  
  
## <a name="bkmk_WSUSGroup"></a>Gruppe der Appliance-Servern in WSUS  
Im nächste Schritt werden nach dem Konfigurieren von WSUS für Analytics Platform System, das Gerät Servergruppe. Alle Gerät-Server eine Gruppe hinzufügen, wird WSUS Anwenden von Softwareupdates auf allen Servern in der Appliance können.  
  
> [!NOTE]  
> Das WSUS-System wurde entworfen, um asynchron auszuführen. Initiieren die Aktivität führt nicht immer zu einem sofort zu aktualisieren. Aus diesem Grund müssen Sie eine Weile zu warten, bis der Computer in den Dialogfeldern WSUS sichtbar sind. Ausführen der `setup.exe /action=ReportMicrosoftUpdateClientStatus /DomainAdminPassword="<password>"` am Ende des Themas beschriebenen Befehl [herunterladen und Anwenden von Microsoft-Updates &#40;Analytics Platform System&#41; ](download-and-apply-microsoft-updates.md) können die Dialogfelder zu aktualisieren.  
  
#### <a name="to-group-the-appliance-servers"></a>Auf der Appliance-Servergruppe  
  
1.  Öffnen Sie die WSUS-Konsole, mit der rechten Maustaste **alle Computer** , und klicken Sie dann auf **Computergruppe hinzufügen**.  
  
    ![Fügen Sie eine Computergruppe hinzu. ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSAddComputerGroup.png "SQL_Server_PDW_WSUSAddComputerGroup")  
  
2.  Geben Sie den Namen "APS" für die Computergruppe aus, und klicken Sie dann auf **hinzufügen**.  
  
    ![Geben Sie Namen für die neue Computergruppe ein. ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSpecifyGroupName.png "SQL_Server_PDW_WSUSSpecifyGroupName")  
  
3.  Klicken Sie auf **alle Computer** in diesem Fall ändern Sie den Status in der **Status** Dropdown-Menü **alle**, und klicken Sie dann auf **aktualisieren**. Sie müssen möglicherweise erweitern **alle Computer** durch Klicken auf das Steuerelement der Strukturansicht auf der linken Seite um die neue Gruppe sehen Sie gerade hinzugefügt haben.  
  
    ![Ändern Sie des Status einer, und klicken Sie auf aktualisieren. ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeStatusToAny.png "SQL_Server_PDW_WSUSChangeStatusToAny")  
  
4.  Wählen Sie alle Computer, die Teil der Appliance, mit der rechten Maustaste, und klicken Sie dann auf **Mitgliedschaft ändern**.  
  
    ![Ändern Sie die Mitgliedschaft aller PDW-Computer. ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeMembership.png "SQL_Server_PDW_WSUSChangeMembership")  
  
5.  Wählen Sie die neue Computergruppe, die Sie erstellt haben, indem Sie auf das Kontrollkästchen, und klicken Sie dann auf **OK**.  
  
    ![Set-Computergruppenmitgliedschaft](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSetComputerGroupMembership.png "SQL_Server_PDW_WSUSSetComputerGroupMembership")  
  
6.  Wählen Sie die neue Computergruppe aus, ändern Sie seine **Status** zu **alle**, und klicken Sie dann auf **aktualisieren**. Alle Computer sollte jetzt zu dieser Gruppe zugewiesen werden und im rechten Bereich aufgeführt. Es ist im Allgemeinen sicher ist, um den Vorgang fortzusetzen, wenn Knoten angezeigt werden Warnungen wie z. B. **dieses Knotens weist keinen gemeldeten Status noch**.  
  
    ![Ändern Sie des Status einer, und klicken Sie auf aktualisieren. ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeStatusAnyRefresh.png "SQL_Server_PDW_WSUSChangeStatusAnyRefresh")  
  
