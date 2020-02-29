---
title: Konfigurieren eines Berichts Servers im einheitlichen Modus für die Bereitstellung für horizontales Skalieren (SSRS-Configuration Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], deployments
- deploying [Reporting Services], scale-out deployment model
- scale-out deployments [Reporting Services]
ms.assetid: b30d0308-4d9b-4f85-9f83-dece4dcb2775
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2f9fea6ae71046de3cf1a6b4dc765b1a2a19e149
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78173580"
---
# <a name="configure-a-native-mode-report-server-scale-out-deployment-ssrs-configuration-manager"></a>Konfigurieren eines Berichtsservers im einheitlichen Modus für Bereitstellungen für horizontales Skalieren (SSRS-Konfigurations-Manager)

  Der einheitliche Modus von Reporting Services unterstützt ein Bereitstellungsmodell für horizontales Skalieren, das die Ausführung mehrerer Berichtsserverinstanzen ermöglicht, die eine einzelne Berichtsserver-Datenbank gemeinsam nutzen. Die Bereitstellung für horizontales Skalieren wird verwendet, um die Skalierbarkeit von Berichtsservern zu erhöhen, sodass diese mehr gleichzeitige Benutzer und größere Berichtsausführungslasten unterstützen. Darüber hinaus können damit bestimmte Server für die Verarbeitung von interaktiven oder geplanten Berichten reserviert werden.

 Berichts Server im SharePoint-Modus verwenden die SharePoint-Produkt Infrastruktur für horizontales Skalieren. Das horizontale hochskalieren im SharePoint-Modus wird durch Hinzufügen von weiteren Berichts Servern im SharePoint-Modus zur SharePoint-Farm ausgeführt. Informationen zur horizontalen Skalierung im SharePoint-Modus finden Sie unter [Add an Additional Report Server to a Farm (SSRS Scale-out) (Hinzufügen eines zusätzlichen Berichtsservers zu einer Farm (Horizontales Skalieren für SSRS))](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md).

 **Bereit Stellungen für horizontales Skalieren bestehen aus folgenden Elementen:**

-   Zwei oder mehr Berichtsserverinstanzen, die eine Berichtsserver-Datenbank gemeinsam nutzen

-   Optional: Ein NLB-Cluster (Network Load Balancing, Netzwerklastenausgleich), um interaktive Benutzerlasten auf die Berichtsserverinstanzen zu verteilen

 Wenn Sie Reporting Services auf einem NLB-Cluster bereitstellen, müssen Sie bei der Konfiguration von Berichtsserver-URLs den Namen des virtuellen NLB-Servers verwenden, und die Server müssen für die Verwendung desselben Anzeigestatus konfiguriert sein.

 Reporting Services ist nicht Teil von MSCS-Clustern (Microsoft Clusterdienste). Sie können die Berichtsserver-Datenbank jedoch auf einer Datenbank-Engine-Instanz erstellen, die Teil eines Failover-Clusters ist.

 **Gehen Sie folgendermaßen vor, um eine Bereitstellung für horizontales Skalieren zu planen, zu installieren und zu konfigurieren:**

-   Anweisungen zum Installieren von Berichts Server Instanzen finden Sie unter [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der-Online Dokumentation.

-   Wenn Sie vorhaben, die Bereitstellung für horizontales Skalieren auf einem NLB-Cluster (Network Load Balancing, Netzwerklastenausgleich) zu hosten, müssen Sie den NLB-Cluster zuerst konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers auf einem Netzwerklastenausgleich-Cluster](../report-server/configure-a-report-server-on-a-network-load-balancing-cluster.md).

-   Machen Sie sich mit den Verfahren in diesem Thema vertraut. Hier finden Sie Anweisungen zum Freigeben einer Berichtsserver-Datenbank und zum Verknüpfen von Berichtsservern für das horizontale Skalieren.

     In den Verfahren wird erläutert, wie eine Bereitstellung für horizontales Skalieren mit Zwei-Knoten-Berichtsserver konfiguriert wird. Wiederholen Sie die Schritte in diesem Thema, um zusätzliche Berichtsserverknoten zur Skalierung hinzuzufügen.

    -   Über das Setup können Sie jede Berichtsserverinstanz installieren, die mit der horizontalen Skalierung verbunden werden soll.

         Damit Datenbank-Kompatibilitätsfehler vermieden werden, wenn Sie die Serverinstanzen mit der freigegebenen Datenbank verbinden, müssen Sie sicherstellen, dass alle Instanzen dieselbe Version aufweisen. Wenn Sie beispielsweise die Berichtsserverdatenbank mithilfe einer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Berichtsserverinstanz erstellen, müssen alle anderen Instanzen in dieser Anwendung auch [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]sein.

    -   Mit dem Konfigurations-Manager für Reporting Services stellen Sie eine Verbindung von den einzelnen Berichtsservern zu der gemeinsamen Datenbank her. Sie können nur jeweils eine Verbindung zu einem Berichtsserver herstellen und diesen Berichtsserver konfigurieren.

    -   Mit dem Konfigurationstool für Reporting Services können Sie die horizontale Skalierung durchführen, indem Sie eine Verbindung von den neuen Berichtsserverinstanzen zur ersten Berichtsserverinstanz herstellen, die bereits an die Berichtsserverdatenbank angeschlossen ist.

### <a name="to-install-a-sql-server-instance-to-host-the-report-server-databases"></a>So installieren Sie eine SQL Server-Instanz zum Hosten der Berichtsserver-Datenbanken

1.  Installieren Sie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz auf einem Computer, der als Host für die Berichtsserver-Datenbanken fungiert. Sie müssen mindestens [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]installieren.

2.  Falls notwendig, aktivieren Sie Remoteverbindungen auf dem Berichtsserver. In einigen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind Remoteverbindungen für TCP/IP und Named Pipes standardmäßig nicht aktiviert. Verwenden Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager, und zeigen Sie die Einstellungen für die Netzwerkkonfiguration der Zielinstanz an, um festzustellen, ob Remoteverbindungen zugelassen werden. Wenn die Remoteinstanz zudem eine benannte Instanz ist, müssen Sie sicherstellen, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst auf dem Zielserver aktiviert ist und ausgeführt wird. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser stellt die Portnummer bereit, mit der die Verbindung zur benannten Instanz hergestellt wird.

### <a name="to-install-the-first-report-server-instance"></a>So installieren Sie die erste Berichtsserverinstanz

1.  Installieren Sie die erste Berichtsserverinstanz, die Teil der Bereitstellung ist. Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]installieren, wählen Sie auf der Seite Berichtsserver-Installationsoptionen die Option **Server installieren, jedoch nicht konfigurieren** .

2.  Starten Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool.

3.  Konfigurieren Sie die URLs für den Berichtsserver-Webdienst und den Berichts-Manager sowie die Berichtsserver-Datenbank. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers &#40;einheitlicher Reporting Services-Modus&#41;](../report-server/configure-a-report-server-reporting-services-native-mode.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.

4.  Überprüfen Sie, ob der Berichtsserver betriebsbereit ist. Weitere Informationen finden Sie unter [Überprüfen einer Installation von Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.

### <a name="to-install-and-configure-the-second-report-server-instance"></a>So installieren und konfigurieren Sie die zweite Berichtsserverinstanz

1.  Führen Sie das Setup aus, um eine zweite Instanz von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf einem anderen Computer oder als benannte Instanz auf demselben Computer zu installieren. Wenn Sie Reporting Services installieren, wählen Sie auf der Seite Berichtsserver-Installationsoptionen die Option **Server installieren, jedoch nicht konfigurieren** .

2.  Starten Sie das Konfigurationstool für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , und stellen Sie eine Verbindung mit der soeben installierten neuen Instanz her.

3.  Stellen Sie eine Verbindung zwischen dem Berichtsserver und der Datenbank her, die Sie für die erste Berichtsserverinstanz verwendet haben:

    1.  Klicken Sie auf **Datenbank** , um die Datenbankseite zu öffnen.

    2.  Klicken Sie auf **Datenbank ändern**.

    3.  Sie können auch auf **Wählen Sie eine vorhandene Berichtsserver-Datenbank aus**klicken.

    4.  Geben Sie den Servernamen für die Instanz der SQL Server-Datenbank-Engine an, auf der die gewünschte Berichtsserver-Datenbank gehostet wird. Dies muss derselbe Server sein, zu dem Sie in den vorherigen Schritten eine Verbindung hergestellt haben.

    5.  Klicken Sie auf **Verbindung testen**, und klicken Sie dann auf **Weiter**.

    6.  Wählen Sie unter **Berichtsserver-Datenbank**die Datenbank aus, die Sie für den ersten Berichtsserver erstellt haben. Klicken Sie anschließend auf **Weiter**. Der Standardname lautet "ReportServer". Wählen Sie nicht die Option ReportServerTempDB. Dieser Eintrag wird nur zum Speichern temporärer Daten während der Berichtsverarbeitung verwendet. Wiederholen Sie die letzten vier Schritte, um eine Verbindung zum Server herzustellen, wenn die Datenbank leer ist.

    7.  Wählen Sie auf der Seite Anmeldeinformationen den Typ des Kontos und der Anmeldeinformationen aus, die der Berichtsserver für die Verbindung zur Berichtsserver-Datenbank verwendet. Sie können dieselben Anmeldeinformationen verwenden, die von der ersten Berichtsserverinstanz verwendet werden, oder andere. Klicken Sie auf **Weiter**.

    8.  Klicken Sie auf **Zusammenfassung** und dann auf **Fertig stellen**.

4.  Konfigurieren Sie die URL für den Report Server-Webdienst. Testen Sie die URL noch nicht. Diese wird erst aufgelöst, wenn der Berichtsserver mit der horizontalen Skalierung verbunden wird.

5.  Konfigurieren Sie die Berichts-Manager-URL. Testen Sie die URL noch nicht, und versuchen Sie noch nicht, die Anwendung zu überprüfen. Der Berichtsserver steht erst zur Verfügung, wenn er mit der horizontalen Skalierung verbunden ist.

### <a name="to-join-the-second-report-server-instance-to-the-scale-out-deployment"></a>So verbinden Sie die zweite Berichtsserverinstanz mit der horizontalen Skalierung

1.  Öffnen Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool, und stellen Sie wieder eine Verbindung mit der ersten Berichtsserverinstanz her. Der erste Berichtsserver ist bereits für umkehrbare Verschlüsselungsvorgänge initialisiert. Daher kann er verwendet werden, um weitere Berichtsserverinstanzen mit der Bereitstellung für horizontales Skalieren zu verbinden.

2.  Klicken Sie auf **Bereitstellung für horizontales Skalieren** , um die Seite „Bereitstellung für horizontales Skalieren“ zu öffnen. Hier sollten zwei Einträge angezeigt werden, einer für jede Berichtsserverinstanz, die mit der Berichtsserver-Datenbank verbunden ist. Für die erste Berichtsserverinstanz sollte bereits eine Verbindung bestehen. Der zweite Berichtsserver sollte auf den Join warten. Wenn Sie keine ähnlichen Einträge für die Skalieranwendung sehen, sollten Sie sich vergewissern, dass Sie mit dem ersten Berichtsserver verbunden sind, der bereits für die Verwendung der Berichtsserver-Datenbank konfiguriert und initialisiert wurde.

     ![Bildschirmteilfoto der Seite „Bereitstellung für dezentrales Skalieren“](../../../2014/sql-server/install/media/scaloutscreen.gif "Bildschirmteilfoto der Seite „Bereitstellung für dezentrales Skalieren“")

3.  Wählen Sie auf der Seite Bereitstellung für horizontales Skalieren die Berichts Serverinstanz aus, die auf den Beitritt zur Bereitstellung wartet, und klicken Sie auf **Server hinzufügen**.

    > [!NOTE]
    >  **Problem:** Wenn Sie versuchen, eine Reporting Services-Berichts Serverinstanz mit der Bereitstellung für horizontales Skalieren zu verknüpfen, treten möglicherweise Fehlermeldungen wie "Zugriff verweigert" auf.
    > 
    >  Problem **Umgehung:** Sichern Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Verschlüsselungsschlüssel von der ersten [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz, und stellen Sie den Schlüssel [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf dem zweiten Berichts Server wieder her. Versuchen Sie dann, den zweiten Server mit der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Bereitstellung für horizontales Skalieren zu verknüpfen.

4.  Sie sollten jetzt feststellen können, dass beide Berichtsserverinstanzen funktionstüchtig sind. Zur Überprüfung der zweiten Instanz können Sie über das Konfigurationstool für Reporting Services eine Verbindung zum Berichtsserver herstellen und auf die URL des Report Server-Webdienstes oder des Berichts-Managers klicken.

 Wenn Sie die Berichtsserver in einem Servercluster mit Lastenausgleich ausführen möchten, sind zusätzliche Konfigurationsschritte erforderlich. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers auf einem Netzwerklastenausgleich-Cluster](../report-server/configure-a-report-server-on-a-network-load-balancing-cluster.md).

## <a name="see-also"></a>Weitere Informationen
 [Konfigurieren eines Dienst Kontos &#40;SSRS-Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) [Konfigurieren einer URL &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) [Erstellen einer Berichts Server-Datenbank im einheitlichen Modus &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) [Konfigurieren von Berichts Server-URLs &#40;SSRS Configuration Manager](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)&#41;[Konfigurieren einer Berichts Server-Datenbankverbindung &#40;SSRS Configuration Manager](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)&#41;[Hinzufügen und Entfernen von Verschlüsselungsschlüsseln für die Bereitstellung für horizontales Skalieren &#40;SSRS](../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md) [Configuration Manager&#41;Dienste-Berichts Server](../report-server/manage-a-reporting-services-native-mode-report-server.md) im einheitlichen Modus


