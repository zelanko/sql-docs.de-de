---
title: Konfigurieren Sie eine im einheitlichen Modus Report Server-Bereitstellung für horizontales Skalieren (SSRS-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], deployments
- deploying [Reporting Services], scale-out deployment model
- scale-out deployments [Reporting Services]
ms.assetid: b30d0308-4d9b-4f85-9f83-dece4dcb2775
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2ccf18bd73c36717385f77e1adbe14bcc1535634
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63261535"
---
# <a name="configure-a-native-mode-report-server-scale-out-deployment-ssrs-configuration-manager"></a>Konfigurieren eines Berichtsservers im einheitlichen Modus für Bereitstellungen für horizontales Skalieren (SSRS-Konfigurations-Manager)

  Der einheitliche Modus von Reporting Services unterstützt ein Bereitstellungsmodell für horizontales Skalieren, das die Ausführung mehrerer Berichtsserverinstanzen ermöglicht, die eine einzelne Berichtsserver-Datenbank gemeinsam nutzen. Die Bereitstellung für horizontales Skalieren wird verwendet, um die Skalierbarkeit von Berichtsservern zu erhöhen, sodass diese mehr gleichzeitige Benutzer und größere Berichtsausführungslasten unterstützen. Darüber hinaus können damit bestimmte Server für die Verarbeitung von interaktiven oder geplanten Berichten reserviert werden.  
  
 Berichtsserver im SharePoint-Modus verwenden die SharePoint-Produktinfrastruktur für horizontales Skalieren. Der SharePoint-Modus für horizontales Skalieren wird durch das Hinzufügen weiterer Berichtsserver im SharePoint-Modus zur SharePoint-Farm ausgeführt. Informationen zur horizontalen Skalierung im SharePoint-Modus finden Sie unter [Add an Additional Report Server to a Farm (SSRS Scale-out) (Hinzufügen eines zusätzlichen Berichtsservers zu einer Farm (Horizontales Skalieren für SSRS))](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md).  
  
 **Bereitstellungen für horizontales Skalieren bestehen aus folgenden Komponenten:**  
  
-   Zwei oder mehr Berichtsserverinstanzen, die eine Berichtsserver-Datenbank gemeinsam nutzen  
  
-   Optional: Ein NLB-Cluster (Network Load Balancing, Netzwerklastenausgleich), um interaktive Benutzerlasten auf die Berichtsserverinstanzen zu verteilen  
  
 Wenn Sie Reporting Services auf einem NLB-Cluster bereitstellen, müssen Sie bei der Konfiguration von Berichtsserver-URLs den Namen des virtuellen NLB-Servers verwenden, und die Server müssen für die Verwendung desselben Anzeigestatus konfiguriert sein.  
  
 Reporting Services ist nicht Teil von MSCS-Clustern (Microsoft Clusterdienste). Sie können die Berichtsserver-Datenbank jedoch auf einer Datenbank-Engine-Instanz erstellen, die Teil eines Failover-Clusters ist.  
  
 **Führen Sie folgende Schritte aus, um eine Bereitstellung für horizontales Skalieren zu planen, zu installieren und zu konfigurieren:**  
  
-   Überprüfen Sie [Installieren von SQL Server 2014 vom Installations-Assistenten &#40;Setup&#41; ](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Onlinedokumentation Anweisungen zum Installieren von Berichtsserverinstanzen.  
  
-   Wenn Sie vorhaben, die Bereitstellung für horizontales Skalieren auf einem NLB-Cluster (Network Load Balancing, Netzwerklastenausgleich) zu hosten, müssen Sie den NLB-Cluster zuerst konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers auf einem Netzwerklastenausgleich-Cluster](../report-server/configure-a-report-server-on-a-network-load-balancing-cluster.md).  
  
-   Machen Sie sich mit den Verfahren in diesem Thema vertraut. Hier finden Sie Anweisungen zum Freigeben einer Berichtsserver-Datenbank und zum Verknüpfen von Berichtsservern für das horizontale Skalieren.  
  
     In den Verfahren wird erläutert, wie eine Bereitstellung für horizontales Skalieren mit Zwei-Knoten-Berichtsserver konfiguriert wird. Wiederholen Sie die Schritte in diesem Thema, um zusätzliche Berichtsserverknoten zur Skalierung hinzuzufügen.  
  
    -   Über das Setup können Sie jede Berichtsserverinstanz installieren, die mit der horizontalen Skalierung verbunden werden soll.  
  
         Damit Datenbank-Kompatibilitätsfehler vermieden werden, wenn Sie die Serverinstanzen mit der freigegebenen Datenbank verbinden, müssen Sie sicherstellen, dass alle Instanzen dieselbe Version aufweisen. Wenn Sie beispielsweise die Berichtsserverdatenbank mithilfe einer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Berichtsserverinstanz erstellen, müssen alle anderen Instanzen in dieser Anwendung auch [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]sein.  
  
    -   Mit dem Konfigurations-Manager für Reporting Services stellen Sie eine Verbindung von den einzelnen Berichtsservern zu der gemeinsamen Datenbank her. Sie können nur jeweils eine Verbindung zu einem Berichtsserver herstellen und diesen Berichtsserver konfigurieren.  
  
    -   Mit dem Konfigurationstool für Reporting Services können Sie die horizontale Skalierung durchführen, indem Sie eine Verbindung von den neuen Berichtsserverinstanzen zur ersten Berichtsserverinstanz herstellen, die bereits an die Berichtsserverdatenbank angeschlossen ist.  
  
### <a name="to-install-a-sql-server-instance-to-host-the-report-server-databases"></a>So installieren Sie eine SQL Server-Instanz zum Hosten der Berichtsserver-Datenbanken  
  
1.  Installieren Sie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz auf einem Computer, der als Host für die Berichtsserver-Datenbanken fungiert. Sie müssen mindestens [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]installieren.  
  
2.  Falls notwendig, aktivieren Sie Remoteverbindungen auf dem Berichtsserver. In einigen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind Remoteverbindungen für TCP/IP und Named Pipes standardmäßig nicht aktiviert. Verwenden Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager, und zeigen Sie die Einstellungen für die Netzwerkkonfiguration der Zielinstanz an, um festzustellen, ob Remoteverbindungen zugelassen werden. Wenn die Remoteinstanz zudem eine benannte Instanz ist, müssen Sie sicherstellen, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst auf dem Zielserver aktiviert ist und ausgeführt wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser stellt die Portnummer bereit, mit der die Verbindung zur benannten Instanz hergestellt wird.  
  
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
  
    3.  Sie können auch auf **Vorhandene Berichtsserver-Datenbank auswählen**klicken.  
  
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
  
     ![Screenshot von einem Ausschnitt der Seite „Bereitstellung für die horizontale Skalierung“](../../../2014/sql-server/install/media/scaloutscreen.gif "Partial screenshot of Scale-out Deployment page")  
  
3.  Wählen Sie auf der Seite Bereitstellung für horizontales Skalieren der Berichtsserverinstanz her, die darauf warten, fügen Sie die Bereitstellung, und klicken Sie auf **-Server hinzufügen**.  
  
    > [!NOTE]  
    >  **Problem:** Wenn Sie versuchen, eine Reporting Services-Berichtsserverinstanz mit der Bereitstellung für horizontales Skalieren zu verknüpfen, können Fehler vom Typ "Zugriff verweigert" auftreten.  
    >   
    >  **Problemumgehung:** Sichern Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Verschlüsselungsschlüssel aus der ersten [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz und den Schlüssel wiederherstellen, mit dem zweiten [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Berichtsserver. Versuchen Sie dann, den zweiten Server mit der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Bereitstellung für horizontales Skalieren zu verknüpfen.  
  
4.  Sie sollten jetzt feststellen können, dass beide Berichtsserverinstanzen funktionstüchtig sind. Zur Überprüfung der zweiten Instanz können Sie über das Konfigurationstool für Reporting Services eine Verbindung zum Berichtsserver herstellen und auf die URL des Report Server-Webdienstes oder des Berichts-Managers klicken.  
  
 Wenn Sie die Berichtsserver in einem Servercluster mit Lastenausgleich ausführen möchten, sind zusätzliche Konfigurationsschritte erforderlich. Weitere Informationen finden Sie unter [Configure a Report Server on a Network Load Balancing Cluster](../report-server/configure-a-report-server-on-a-network-load-balancing-cluster.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren eines Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)   
 [Konfigurieren einer URL &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
 [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Hinzufügen und Entfernen von Verschlüsselungsschlüsseln für die Bereitstellung für horizontales Skalieren &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md)   
 [Manage a Reporting Services Native Mode Report Server (Verwalten eines Berichtsservers von Reporting Services im einheitlichen Modus)](../report-server/manage-a-reporting-services-native-mode-report-server.md)  
  
  
