---
title: Konfigurieren von WSUS
description: In diesen Anweisungen werden die Schritte zum Verwenden des Konfigurations-Assistenten für Windows Server Update Services (WSUS) zum Konfigurieren von WSUS für Analytics Platform System erläutert.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 089b76d7167b8561c93b01837dc2189c833362fd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "76761904"
---
# <a name="configure-windows-server-update-services-wsus-in-analytics-platform-system"></a>Konfigurieren von Windows Server Update Services (WSUS) in Analytics Platform System
In diesen Anweisungen werden die Schritte zum Verwenden des Konfigurations-Assistenten für Windows Server Update Services (WSUS) zum Konfigurieren von WSUS für Analytics Platform System erläutert. Sie müssen WSUS konfigurieren, bevor Sie Software Updates auf das Gerät anwenden können. WSUS ist bereits auf dem virtuellen VMM-Computer des Geräts installiert.  
  
Weitere Informationen zum Konfigurieren von WSUS finden Sie auf der WSUS-Website unterschritt Weise Anleitung für die [WSUS-Installation](https://go.microsoft.com/fwlink/?LinkId=202417) . Nach dem Konfigurieren von WSUS finden [Sie weitere Informationen unter herunterladen und Anwenden von Microsoft Updates &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md) zum Initiieren eines Updates.  
  
> [!WARNING]  
> Wenn während dieses Konfigurations Vorgangs Fehler auftreten, wenden Sie sich an den Support, und wenden Sie sich an den Support. Ignorieren Sie keine Fehler, oder fahren Sie fort, wenn Fehler auftreten.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
Zum Konfigurieren von WSUS müssen Sie folgende Schritte ausführen:  
  
-   Stellen Sie die Anmelde Informationen für das Domänen Administrator Konto der Analytics Platform System Appliance dar.  
  
-   Sie verfügen über eine Analytics Platform System-Anmeldung mit Berechtigungen für den Zugriff auf die **Verwaltungskonsole** und Anzeigen von Informationen zum Gerätezustand.  
  
-   Informieren Sie sich über die IP-Adresse des WSUS-Upstream-Servers, wenn Sie beabsichtigen, Updates von einem WSUS-Upstream-Server zu synchronisieren, anstatt Updates direkt von Microsoft Update zu synchronisieren. Stellen Sie sicher, dass der WSUS-Upstream-Server für anonyme Verbindungen und SSL-Unterstützung festgelegt ist.  
  
-   Informieren Sie sich über die IP-Adresse des Proxy Servers, wenn Ihr Gerät einen Proxy Server für den Zugriff auf den Upstreamserver oder Microsoft Update verwendet.  
  
-   In den meisten Fällen muss WSUS auf Server außerhalb des Geräts zugreifen können. Zur Unterstützung dieses Verwendungs Szenarios kann das Analytics Platform System DNS so konfiguriert werden, dass eine externe namens Weiterleitung unterstützt wird, die es den Analytics-Plattformsystem Hosts und-Virtual Machines (VMS) ermöglicht, externe DNS-Server zum Auflösen von Namen außerhalb des Geräts zu verwenden. Weitere Informationen finden Sie unter [Verwenden einer DNS-Weiterleitung zum Auflösen von DNS-Namen, die keine Appliance sind &#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
## <a name="to-configure-windows-server-update-services-wsus"></a>So konfigurieren Sie Windows Server Update Services (WSUS)  
  
1.  Melden Sie sich bei der **Verwaltungskonsole**an. Überprüfen Sie auf der Registerkarte **Appliance State** , ob die Spalten **Cluster** und **Netzwerk** für alle Knoten grün (oder **na**) angezeigt werden. Überprüfen Sie die Status Indikatoren für alle Knoten im **Gerätezustand**.  
  
    -   Es ist sicher, mit grünen oder na-Indikatoren fortzufahren.  
  
    -   Auswerten nicht kritischer (gelber) Warnungs Fehler. In einigen Fällen blockieren Warnmeldungen keine Updates. Wenn ein nicht kritischer datenträgervolumefehler vorliegt, der nicht auf C:\ fest liegt Laufwerk, Sie können mit dem nächsten Schritt fortfahren, bevor Sie den Datenträger Volume-Fehler beheben.  
  
    -   Die meisten roten Indikatoren müssen aufgelöst werden, bevor Sie fortfahren. Wenn Datenträger Fehler auftreten, überprüfen Sie mithilfe der Seite **Warnungen der Verwaltungskonsole** , ob innerhalb der einzelnen Server-oder SAN-Arrays nicht mehr als ein Datenträger Fehler aufgetreten ist. Wenn innerhalb der einzelnen Server oder SAN-Arrays nicht mehr als ein Datenträger Fehler auftritt, können Sie mit dem nächsten Schritt fortfahren, bevor Sie die Datenträger Fehler beheben. Stellen Sie sicher, dass Sie sich an den Microsoft Support wenden, um die Datenträger Fehler schnellstmöglich zu beheben.  
  
2.  Melden Sie sich als Anwendungs Domänen Administrator bei der virtuellen VMM-Maschine an.  
  
3.  Starten Sie den Konfigurations-Assistenten.  
  
    #### <a name="to-launch-the-configuration-wizard"></a>So starten Sie den Konfigurations-Assistenten  
  
    1.  Klicken Sie im **Server-Manager-Dashboard**im **Menü Extras** auf **Windows Server Update Services**.  
  
    2.  Erweitern Sie im linken Bereich des Fensters " **Update Dienste** " den Knoten Server für die Verwaltung virtueller Computer (**_appliance_domain_-VMM**), und klicken Sie dann auf **Optionen**.  
  
    3.  Klicken Sie im Bereich **Optionen** auf **Konfigurations-Assistent für WSUS-Server** , um den Konfigurations-Assistenten zu starten.  
  
        ![Server-Manager-Dashboard (Menü)](./media/configure-windows-server-update-services-wsus/WSUS_Wiz0.png "WSUS_Wiz0")  
  
    4.  Wenn Sie den WSUS-Assistenten zum ersten Mal ausführen, werden Sie möglicherweise aufgefordert, ein Verzeichnis zum Speichern der Updates zu konfigurieren. `C:\wsus`ist ein geeigneter Speicherort. Sie können jedoch einen anderen Pfad angeben.  
  
        ![WSUS-Pfad](./media/configure-windows-server-update-services-wsus/WSUS_Wiz1.png "WSUS_Wiz1")  
  
    5.  Überprüfen Sie **, bevor Sie mit der Liste der** Elemente fertig sind, bevor Sie den Assistenten Fertigstellen.  
  
        ![WSUS – Vorbereitungen](./media/configure-windows-server-update-services-wsus/WSUS_Wiz2.png "WSUS_Wiz2")  
  
    6.  Wählen Sie auf der Seite **Microsoft Update Verbesserungsprogramm beitreten** die Option **Ja, ich möchte am Microsoft Update Verbesserungsprogramm teilnehmen**aus, und klicken Sie dann auf **weiter**.  
  
        ![WSUS – Verbesserungsprogramm](./media/configure-windows-server-update-services-wsus/WSUS_Wiz3.png "WSUS_Wiz3")  
  
    Nun sollte die Seite **Upstreamserver auswählen** angezeigt werden. Der folgende Screenshot ist der Ausgangspunkt des Konfigurations-Assistenten.  
  
    ![WSUS – Upstreamserversynchronisierung](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4a.png "WSUS_Wiz4a")  
  
4.  Wählen Sie den Upstreamserver aus.  
  
    Auf der Seite **Upstreamserver auswählen** des WSUS-Konfigurations-Assistenten wählen Sie aus, wie WSUS auf dem Knoten der virtuellen Computer Verwaltung zum Abrufen von Software Updates eine Verbindung mit einem Upstreamserver herstellt. Sie haben zwei Möglichkeiten, den Upstream-Server mit [Microsoft Update](https://go.microsoft.com/fwlink/?LinkId=133349) zu synchronisieren oder Updates mit einem anderen Windows Server Update Services Server zu synchronisieren.  
  
    #### <a name="to-update-by-using-microsoft-update"></a>So aktualisieren Sie mithilfe von Microsoft Update  
  
    1.  Wenn Sie sich für die Synchronisierung mit Microsoft Update entscheiden, müssen Sie auf der Seite **Upstreamserver auswählen** keine Änderungen vornehmen. Klicken Sie auf **Weiter**.  
  
        ![WSUS – Upstreamserversynchronisierung](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4a.png "WSUS_Wiz4a")  
  
    #### <a name="to-update-from-another-wsus-server"></a>So aktualisieren Sie von einem anderen WSUS-Server  
  
    1.  Wenn Sie sich für die Synchronisierung mit einer anderen Quelle als Microsoft Update (einem Upstreamserver) entscheiden, geben Sie den Server (die IP-Adresse ein) und den Port an, auf dem dieser Server mit dem Upstreamserver kommunizieren soll.  
  
        ![WSUS – Upstreamserversynchronisierung von WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4b.png "WSUS_Wiz4b")  
  
    2.  Wenn Sie Secure Sockets Layer (SSL) verwenden möchten, aktivieren Sie das Kontrollkästchen **SSL beim Synchronisieren der Update Informationen verwenden** . In diesem Fall wird Port 443 für die Synchronisierung verwendet.  
  
        ![WSUS – Upstreamserversynchronisierung von WSUS SSL](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4c.png "WSUS_Wiz4c")  
  
    3.  Falls es sich um einen Replikatserver handelt, aktivieren Sie das Kontrollkästchen **Dies ist ein Replikat des Upstreamservers**. **Wenn Sie Update Informationen synchronisieren** , können Sie sowohl SSL verwenden als auch **ein Replikat des Upstreamservers**auswählen.  
  
        ![WSUS – Upstreamserverreplikat](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4d.png "WSUS_Wiz4d")  
  
    4.  An diesem Punkt sind Sie mit der Upstream-Serverkonfiguration fertig. Klicken Sie auf **weiter**, oder wählen Sie im linken Navigationsbereich **Proxy Server angeben** aus.  
  
5.  Geben Sie den Proxy Server an.  
  
    Wenn dieser Server einen Proxy Server für den Zugriff auf Microsoft Update oder einen anderen Upstreamserver benötigt, können Sie die Proxy Servereinstellungen hier konfigurieren. Klicken Sie andernfalls auf **weiter**.  
  
    ![WSUS – Proxy](./media/configure-windows-server-update-services-wsus/WSUS_Wiz5a.png "WSUS_Wiz5a")  
  
    #### <a name="to-configure-proxy-server-settings"></a>So konfigurieren Sie die Proxyservereinstellungen  
  
    1.  Aktivieren Sie im Konfigurations-Assistenten auf der Seite **Proxy Server angeben** das Kontrollkästchen **Proxy Server beim Synchronisieren verwenden** , und geben Sie dann die IP-Adresse des Proxy Servers (nicht Name) und die Portnummer (standardmäßig Port 80) in die entsprechenden Felder ein.  
  
    2.  Wenn für die Verbindung mit dem Proxyserver bestimmte Benutzeranmeldeinformationen verwendet werden sollen, aktivieren Sie das Kontrollkästchen **Benutzeranmeldeinformationen verwenden, um Verbindung mit dem Proxyserver herzustellen**, und geben Sie dann den Benutzernamen, die Domäne und das Kennwort des Benutzers in die entsprechenden Felder ein. Wenn Sie für den Benutzer, der eine Verbindung mit dem Proxy Server herstellt, die Standard Authentifizierung aktivieren möchten, aktivieren Sie das Kontrollkästchen Standard **Authentifizierung zulassen (Kennwort wird in Klartext gesendet)** .  
  
        ![WSUS – Proxyanmeldeinformationen](./media/configure-windows-server-update-services-wsus/WSUS_Wiz5b.png "WSUS_Wiz5b")  
  
    3.  An diesem Punkt ist die Proxy Serverkonfiguration abgeschlossen. Klicken Sie auf **Weiter**, um mit der nächsten Seite fortzufahren, auf der Sie mit der Einrichtung des Synchronisierungsprozesses beginnen können.  
  
6.  Startet die Verbindung.  
  
    ![WSUS – Start der Proxyverbindung](./media/configure-windows-server-update-services-wsus/WSUS_Wiz6.png "WSUS_Wiz6")  
  
    Klicken Sie auf **Verbindung starten**.  
  
    Nachdem die Verbindung erfolgreich hergestellt wurde, **Klicken Sie auf Weiter,** um zur nächsten Seite zu wechseln, auf der Sie Sprachen auswählen können.  
  
7.  Wählen Sie Sprachen aus.  
  
    Wählen Sie **Updates nur in diesen Sprachen herunterladen aus**.  
  
    Wählen Sie **Englisch**aus, und klicken Sie dann auf **weiter**.  
  
    ![Auswählen von Sprachen](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChooseLanguages.png "SQL_Server_PDW_WSUSChooseLanguages")  
  
8.  Wählen Sie Produkte aus.  
  
    > [!NOTE]  
    > Wenn Sie einen Upstreamserver verwenden, können Sie möglicherweise keine Produkte auswählen. Wenn diese Option nicht verfügbar ist, überspringen Sie diesen Schritt.

    > [!WARNING]  
    > Schließen Sie alle SQL Server 2016-Updates aus.
  
    Deaktivieren Sie alle ausgewählten Updates.  
  
    Wählen Sie **SQL Server 2012**, **SQL Server 2014**, **Windows Server 2012 R2**und **System Center 2012 R2-Virtual Machine Manager**aus, und klicken Sie dann auf **weiter**.  
  
9. Wählen Sie Klassifizierungen aus.  
  
    > [!NOTE]  
    > Wenn Sie einen Upstreamserver verwenden, können Sie möglicherweise keine Klassifizierungen auswählen.  Wenn diese Option nicht verfügbar ist, überspringen Sie diesen Schritt.  
  
    Deaktivieren Sie alle zuvor ausgewählten Updates.  
  
    Wählen Sie **wichtige Updates** und **Sicherheitsupdates** für die Updates aus, die für die Analytics Platform System-Appliance synchronisiert werden sollen, und klicken Sie dann auf **weiter**.  
  
    ![Auswählen von Klassifizierungen](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChooseClassifications.png "SQL_Server_PDW_WSUSChooseClassifications")  
  
10. Konfigurieren Sie den Synchronisierungs Zeitplan.  
  
    Wählen Sie **manuell synchronisieren**aus, und klicken Sie dann auf **weiter**.  
  
    ![Festlegen des Synchronisierungszeitplans](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSyncSchedule.png "SQL_Server_PDW_WSUSSyncSchedule")  
  
11. Anfängliche Synchronisierung starten.  
  
    Wählen Sie **anfängliche Synchronisierung starten**aus, und klicken Sie auf **weiter**.  
  
12. Fertig  
  
    Klicken Sie auf **Fertig stellen**.  
  
## <a name="group-the-appliance-servers-in-wsus"></a><a name="bkmk_WSUSGroup"></a>Gruppieren der Geräteserver in WSUS  
Nach dem Konfigurieren von WSUS für Analytics Platform System besteht der nächste Schritt im Gruppieren der Geräteserver. Wenn alle Geräteserver einer Gruppe hinzugefügt werden, kann WSUS Software Updates auf alle Server in der Appliance anwenden.  
  
> [!NOTE]  
> Das WSUS-System ist so konzipiert, dass es asynchron ausgeführt wird. Das Initiieren einer Aktivität führt nicht immer zu einem sofortigen Update. Daher müssen Sie möglicherweise eine Weile warten, bis die Computer in den WSUS-Dialogfeldern angezeigt werden. Wenn Sie `setup.exe /action=ReportMicrosoftUpdateClientStatus /DomainAdminPassword="<password>"` den am Ende des Themas beschriebenen Befehl zum [herunterladen und Anwenden von Microsoft Updates &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md) ausführen, können Sie die Dialogfelder aktualisieren.  
  
#### <a name="to-group-the-appliance-servers"></a>So gruppieren Sie die Geräteserver  
  
1.  Öffnen Sie die WSUS-Konsole, klicken Sie mit der rechten Maustaste auf **alle Computer** und dann auf **Computer Gruppe hinzufügen**.  
  
    ![Fügen Sie eine Computergruppe hinzu.](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSAddComputerGroup.png "SQL_Server_PDW_WSUSAddComputerGroup")  
  
2.  Geben Sie den Namen "APS" für die Computergruppe ein, und klicken Sie dann auf **Hinzufügen**.  
  
    ![Geben Sie den Namen für die neue Computergruppe ein.](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSpecifyGroupName.png "SQL_Server_PDW_WSUSSpecifyGroupName")  
  
3.  Klicken Sie erneut auf **alle Computer** , ändern Sie den Status im Dropdown Menü **Status** in **any**, und klicken Sie dann auf **Aktualisieren**. Sie müssen möglicherweise **alle Computer** erweitern, indem Sie auf der linken Seite auf die Schaltfläche klicken, um die neue Gruppe anzuzeigen, die Sie soeben hinzugefügt haben.  
  
    ![Ändern Sie den Status in 'Beliebig', und klicken Sie auf 'Aktualisieren'.](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeStatusToAny.png "SQL_Server_PDW_WSUSChangeStatusToAny")  
  
4.  Wählen Sie alle Computer aus, die Teil des Geräts sind, klicken Sie mit der rechten Maustaste, und klicken Sie dann auf **Mitgliedschaft ändern**.  
  
    ![Ändern Sie die Mitgliedschaft aller PDW-Computer.](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeMembership.png "SQL_Server_PDW_WSUSChangeMembership")  
  
5.  Wählen Sie die neue Computergruppe aus, die Sie erstellt haben, indem Sie auf das Kontrollkästchen und dann auf **OK**klicken.  
  
    ![Festlegen der Mitgliedschaft in Computergruppe](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSetComputerGroupMembership.png "SQL_Server_PDW_WSUSSetComputerGroupMembership")  
  
6.  Wählen Sie die neue Computergruppe aus, ändern Sie Ihren **Status** in **any**, und klicken Sie dann auf **Aktualisieren**. Alle Computer sollten nun dieser Gruppe zugewiesen und im rechten Bereich aufgelistet werden. Im Allgemeinen ist es sicher, den Vorgang fortzusetzen, wenn Knoten Warnungen anzeigen, z. b. **dieser Knoten hat noch keinen Status gemeldet**.  
  
    ![Ändern Sie den Status in beliebig, und klicken Sie auf Aktualisieren](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeStatusAnyRefresh.png "SQL_Server_PDW_WSUSChangeStatusAnyRefresh")  
  
