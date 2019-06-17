---
title: Konfigurieren einer URL (SSRS-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], syntax
ms.assetid: 851e163a-ad2a-491e-bc1e-4df92327092f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 617a4e01b3fd4f8dcbc6d929c2a26d483f2fa1ec
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66108860"
---
# <a name="configure-a-url--ssrs-configuration-manager"></a>Konfigurieren einer URL (SSRS-Konfigurations-Manager)
  Bevor Sie den Berichts-Manager oder den Report Server-Webdienst verwenden können, müssen Sie mindestens eine URL für jede Anwendung konfigurieren. Die Konfiguration der URLs ist obligatorisch, wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im Modus zur ausschließlichen Installation von Dateien installiert haben (also durch Auswahl der Option **Server installieren, jedoch nicht konfigurieren** auf der Seite mit den Berichtsserver-Installationsoptionen im Installations-Assistenten). Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in der Standardkonfiguration installiert haben, sind die URLs bereits für jede Anwendung konfiguriert. Falls Sie mit einem Berichtsserver arbeiten, der für den integrierten SharePoint-Modus konfiguriert ist, und Sie die URL des Berichtsserver-Webdienstes mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool aktualisieren, müssen Sie auch die URL in der SharePoint-Zentraladministration aktualisieren.  
  
 Verwenden Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool zur Konfiguration der URLs: Alle Teile der URL werden in diesem Tool definiert. Im Gegensatz zu früheren Versionen bieten die Websites des Internetinformationsdienste-Managers (IIS) keinen Zugriff mehr auf [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Anwendungen in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höheren Versionen.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bietet Standardwerte, die in den meisten Bereitstellungszenarien gut funktionieren, einschließlich parallelen Bereitstellungen mit anderen Webdiensten und -anwendungen. Standard-URLs beinhalten Instanznamen, wodurch das Risiko von URL-Konflikten bei Ausführung mehrerer Berichtsserverinstanzen auf demselben Computer minimiert wird.  
  
 Dieses Thema enthält Anweisungen für die folgenden Aufgaben:  
  
-   Erstellen Sie eine URL für den Report Server-Webdienst.  
  
-   Erstellen Sie eine URL für den Berichts-Manager.  
  
-   Legen Sie erweiterte URL-Eigenschaften fest, um zusätzliche URLs zu definieren.  
  
 Weitere Informationen über die URLs gespeichert und verwaltet werden zu Interoperabilitätsproblemen finden Sie unter [über URL-Reservierungen und Registrierung &#40;SSRS-Konfigurations-Manager&#41; ](about-url-reservations-and-registration-ssrs-configuration-manager.md) und [Reporting installieren Dienste und Internetinformationen Services-Seite-an-Seite &#40;einheitlicher SSRS-Modus&#41;](install-reporting-and-internet-information-services-side-by-side.md)in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation. Beispiele für URLs, die häufig in Reporting Services-Installationen verwendet werden, finden Sie unter [Beispiele für URLs](#URLExamples) in diesem Thema.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Bevor Sie eine URL erstellen oder ändern, beachten Sie folgende Punkte:  
  
-   Sie müssen ein Mitglied der lokalen Administratorengruppe auf dem Berichtsservercomputer sein.  
  
-   Wenn IIS 6.0 oder 7.0 auf demselben Computer installiert ist, müssen Sie die Namen der virtuellen Verzeichnisse auf jeder Website überprüfen, die Port&nbsp;80 verwendet. Wenn virtuelle Verzeichnisse angezeigt werden, die die Reporting Service-Standardnamen für virtuelle Verzeichnisse verwenden (also Reports und ReportServer), wählen Sie andere Namen für virtuelle Verzeichnisse für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -URLs aus, die Sie konfigurieren.  
  
-   Zum Konfigurieren der URL müssen Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool neu starten. Verwenden Sie kein Systemhilfsprogramm. Ändern Sie niemals die URL-Reservierungen im Abschnitt `URLReservations` der Datei RSReportServer.config direkt. Die Verwendung des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstools ist zur Aktualisierung der zugrunde liegenden URL-Reservierung, die intern gespeichert wird, sowie zur Synchronisation der URL-Einstellungen, die in der Datei RSReportServer.config gespeichert werden.  
  
-   Wählen Sie eine Zeit mit niedriger Berichtsaktivität aus. Bei jeder Änderung der URL-Reservierung können Sie davon ausgehen, dass die Anwendungsdomänen für den Report Server-Webdienst und den Berichts-Manager möglicherweise wiederverwendet werden.  
  
-   Eine Übersicht über die Erstellung und Verwendung von URLs in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]finden Sie unter [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md).  
  
### <a name="to-configure-a-url-for-the-report-server-web-service"></a>So konfigurieren Sie eine URL für den Report Server-Webdienst  
  
1.  Starten Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool, und stellen Sie eine Verbindung mit einer lokalen Berichtsserverinstanz her.  
  
2.  Klicken Sie auf **Webdienst-URL**.  
  
3.  Geben Sie das virtuelle Verzeichnis an. Der Name des virtuellen Verzeichnisses gibt an, welche Anwendung die Anforderung empfängt. Da eine IP-Adresse und ein Port von mehreren Anwendungen gemeinsam verwendet werden können, gibt der Name des virtuellen Verzeichnisses an, welche Anwendung die Anforderung erhält.  
  
     Dieser Wert muss eindeutig sein, um sicherzustellen, dass die Anforderung das beabsichtigte Ziel erreicht. Dieser Wert ist erforderlich. Dabei wird die Groß- und Kleinschreibung nicht berücksichtigt. Es gibt eine 1:1-Entsprechung zwischen dem Namen eines virtuellen Verzeichnisses und einer Instanz einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Anwendung. Wenn Sie mehrere URLs zur selben Anwendungsinstanz erstellen, müssen Sie in allen URLs, die Sie für diese Anwendungsinstanz erstellen, denselben Namen für das virtuelle Verzeichnis verwenden.  
  
     Beim Report Server-Webdienst lautet der Standardname für das virtuelle Verzeichnis **reportserver**.  
  
4.  Geben Sie die IP-Adresse an, die den Berichtsservercomputer im Netzwerk eindeutig identifiziert. Wenn Sie einen Hostheader angeben oder weitere URLs für dieselbe Anwendungsinstanz definieren möchten, müssen Sie auf **Erweitert**klicken. Anweisungen zur Einrichtung erweiterter Eigenschaften für die URL finden Sie weiter unten in diesem Thema. Verwenden Sie andernfalls die Seite **Webdienst-URL** , um eine Auswahl aus folgenden Werten zu treffen:  
  
    -   Der Wert**Alle zugewiesenen** gibt an, dass alle IP-Adressen, die dem Computer zugewiesen sind, in einer URL verwendet werden können, die auf eine Berichtsserveranwendung verweist. Dieser Wert umfasst auch Host-Anzeigenamen (z. B. Computernamen), die durch einen Domänennamenserver in eine IP-Adresse aufgelöst werden können, die dem Computer zugewiesen ist. Dies ist der Standardwert für eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -URL.  
  
    -   Mit**Alle nicht zugewiesenen** wird angegeben, dass der Berichtsserver alle Anforderungen erhält, die nicht von einer anderen Anwendung bearbeitet werden. Sie sollten diese Option vermeiden. Wenn Sie diese Option auswählen, kann eine andere Anwendung, die eine stärkere URL-Reservierung aufweist, Anforderungen abfangen, die für den Berichtsserver gedacht waren.  
  
    -   **127.0.0.1** ist die für den Zugriff auf localhost verwendete IPv4-Adresse. Sie unterstützt die lokale Verwaltung auf dem Berichtsservercomputer. Wenn Sie nur diesen Wert auswählen, haben nur Benutzer, die lokal auf dem Berichtsservercomputer angemeldet sind, Zugriff auf die Anwendung.  
  
    -   **::1** ist die Loopback-Adresse im IPv6-Format.  
  
    -   Bestimmte IP-Adressen werden ebenfalls in dieser Liste angezeigt. IP-Adressen können in den Formaten IPv4 und IPv6 vorliegen *Nnn.nnn.nnn.nnn* ist die 32-Bit-IPv4-Adresse einer Netzwerkadapterkarte auf dem Computer. IPv6-Adressen sind 128-Bit-Adressen mit acht 4-Byte-Feldern, die durch Doppelpunkte getrennt sind: \<Präfix>:*nnnn:nnnn:nnnn:nnnn:nnnn:nnnn*  
  
         Wenn Sie über mehrere Karten verfügen oder wenn Ihr Netzwerk sowohl IPv4- als auch IPv6-Adressen unterstützt, werden Ihnen mehrere IP-Adressen angezeigt. Wenn Sie nur eine einzige IP-Adresse auswählen, wird der Anwendungszugriff auf genau diese IP-Adresse (und jeden Hostnamen, den ein Domänennamenserver dieser Adresse zuordnet) beschränkt. Sie können mit localhost nicht auf einen Berichtsserver zugreifen, und Sie können nicht die IP-Adressen der anderen Netzwerkkarten verwenden, die auf dem Berichtsservercomputer installiert sind. Normalerweise wählen Sie diesen Wert aus, weil Sie mehrere URL-Reservierungen konfigurieren, die auch explizite IP-Adressen oder Hostnamen angeben (z. B. einen für eine Netzwerkadapterkarte für Intranetverbindungen und einen zweiten für Extranetverbindungen).  
  
5.  Geben Sie den Port an. Port 80 ist der Standard für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] unter [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] und Windows Server 2008, da er gemeinsam mit anderen Anwendungen genutzt werden kann. Wenn Sie eine benutzerdefinierte Portnummer verwenden möchten, müssen Sie sie immer in der URL angeben, die für den Zugriff auf den Berichtsserver verwendet wird. Mit folgenden Verfahren können Sie nach einem verfügbaren Port suchen:  
  
    -   Geben Sie an einer Eingabeaufforderung den folgenden Befehl ein, um eine Liste der verwendeten TCP-Anschlüsse auszugeben:  
  
         `netstat -a -n -p tcp`  
  
    -   Im Microsoft-Support-Artikel [Informationen zur Zuweisung von TCP/IP-Ports](https://support.microsoft.com/kb/174904)finden Sie Informationen zur Zuweisung von TCP-Ports und zu den Unterschieden zwischen bekannten Ports (0 bis 1023), registrierten Ports (1024 bis 49151) und dynamischen bzw. privaten Ports (49152 bis 65535).  
  
    -   Bei Verwendung der Windows-Firewall müssen Sie den Port öffnen. Anweisungen finden Sie unter [Configure a Firewall for Report Server Access](../report-server/configure-a-firewall-for-report-server-access.md).  
  
6.  Wenn nicht bereits geschehen, überprüfen Sie, dass IIS (sofern installiert) kein virtuelles Verzeichnis besitzt, das den Namen trägt, den Sie verwenden möchten.  
  
7.  Wenn Sie ein SSL-Zertifikat installiert haben, können Sie es nun auswählen, um die URL an das SSL-Zertifikat zu binden, das auf Ihrem Computer installiert ist.  
  
8.  Optional können Sie bei Auswahl eines SSL-Zertifikats einen benutzerdefinierten Port angeben. Standardmäßig wird Port Nummer&nbsp;443 verwendet, aber Sie können jeden Port verwenden, der verfügbar ist.  
  
9. Klicken Sie auf **Anwenden** , um die URL zu erstellen.  
  
10. Testen Sie die URL, indem Sie auf den Link im Abschnitt **URLs** der Seite klicken. Beachten Sie, dass die Berichtsserver-Datenbank erstellt und konfiguriert werden muss, bevor Sie die URL testen können. Anweisungen finden Sie unter [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus (SSRS-Konfigurations-Manager)](ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
11. Wenn Ihr Berichtsserver für die Ausführung im integrierten SharePoint-Modus konfiguriert ist, konfigurieren Sie außerdem die URL für den Berichtsserver-Webdienst in der SharePoint-Zentraladministration. Weitere Informationen über das Aktualisieren der URL des Berichtsserver-Webdienst im SharePoint-Zentraladministration finden Sie unter [Konfiguration und Verwaltung eines Berichtsservers &#40;Reporting Services SharePoint Mode&#41; ](../configure-administer-report-server-reporting-services-sharepoint-mode.md) und [Reporting Services-Berichtsserver &#40;SharePoint-Modus&#41;](../reporting-services-report-server-sharepoint-mode.md).  
  
### <a name="to-create-a-url-reservation-for-report-manager"></a>So erstellen Sie eine URL-Reservierung für den Berichts-Manager  
  
1.  Starten Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool, und stellen Sie eine Verbindung mit der Berichtsserverinstanz her.  
  
2.  Klicken Sie auf **Berichts-Manager-URL**.  
  
3.  Geben Sie das virtuelle Verzeichnis an. Der Berichts-Manager lauscht auf derselben IP-Adresse und demselben Port wie der Report Server-Webdienst. Wenn Sie den Berichts-Manager so konfiguriert haben, dass er auf einen anderen Berichtsserver-Webdienst verweist, müssen Sie die URL-Einstellungen des Berichts-Managers in der Datei RSReportServer.config überprüfen. Anweisungen hierzu finden Sie unter [Berichts-Manager konfigurieren &#40;im einheitlichen Modus&#41; ](../report-server/configure-web-portal.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
4.  Wenn Sie ein SSL-Zertifikat installiert haben, können Sie es auswählen, um festzulegen, dass alle Anforderungen an den Berichts-Manager über HTTPS geleitet werden.  
  
     Optional können Sie bei Auswahl eines SSL-Zertifikats einen benutzerdefinierten Port angeben. Standardmäßig wird Port Nummer&nbsp;443 verwendet, aber Sie können jeden Port verwenden, der verfügbar ist.  
  
5.  Klicken Sie auf **Anwenden** , um die URL zu erstellen.  
  
6.  Testen Sie die URL, indem Sie auf den Link im Abschnitt **URLs** der Seite klicken.  
  
## <a name="setting-advanced-properties-to-specify-additional-urls"></a>Festlegen der erweiterten Eigenschaften zur Angabe zusätzlicher URLs  
 Sie können mehrere URLs für den Report Server-Webdienst oder den Berichts-Manager reservieren, indem Sie verschiedene Ports bzw. Hostnamen angeben (entweder eine IP-Adresse oder ein Hostheader-Name, den ein Domänennamenserver in eine IP-Adresse auflösen kann, die dem Computer zugewiesen ist). Indem Sie mehrere URLs erstellen, können Sie verschiedene Zugriffspfade zur gleichen Berichtsserverinstanz einrichten. Um beispielsweise Intranet- und Extranet-Zugriff auf einen Berichtsserver zu aktivieren, könnten Sie die Standard-URL für den Zugriff im gesamten Intranet und einen weiteren vollqualifizierten Hostnamen für Extranetzugriff verwenden:  
  
-   http://myserver01/reportserver  
  
-   http://www.adventure-works.com/reportserver  
  
 Sie können nicht mehrere Namen für virtuelle Verzeichnisse für dieselbe Anwendungsinstanz festlegen. Jede [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Anwendungsinstanz wird genau einem Namen für virtuelle Verzeichnisse zugeordnet. Wenn mehrere Instanzen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf demselben Computer vorliegen, sollte der Name für das virtuelle Verzeichnis für eine Anwendung den Instanznamen beinhalten, um sicherzustellen, dass jede Anforderung ihr vorgesehenes Ziel erreicht.  
  
#### <a name="to-set-advanced-properties-on-a-url"></a>So legen Sie erweiterte Eigenschaften für eine URL fest  
  
1.  Klicken Sie auf der Seite **Webdienst-URL** oder **Berichts-Manager-URL** auf **Erweitert**.  
  
2.  Klicken Sie auf **Hinzufügen**.  
  
3.  Klicken Sie auf IP-Adresse oder Hostheadernamen. Achten Sie bei der Angabe eines Hostheaders darauf, einen Namen anzugeben, den der DNS-Service auflösen kann. Wenn Sie einen öffentlich verfügbaren Domänennamen angeben, schließen Sie die ganze URL ein, einschließlich http://www.  
  
4.  Geben Sie den Port an. Wenn Sie einen benutzerdefinierten Port angeben, muss die URL für die Anwendung immer die Portnummer einschließen.  
  
5.  Klicken Sie auf **OK**.  
  
6.  Testen Sie die URL durch das Öffnen eines Browserfensters und Eingeben der URL.  
  
## <a name="urls-for-multiple-report-server-instances-on-the-same-computer"></a>URLs für mehrere Berichtsserverinstanzen auf demselben Computer.  
 Wenn Sie URLs für mehrere Instanzen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]reservieren, sollten Sie Benennungskonventionen einhalten, um Namenskonflikte zu vermeiden. Weitere Informationen finden Sie unter [URL-Reservierungen für Berichtsserver-Bereitstellungen mit mehreren Instanzen &#40;SSRS-Konfigurations-Manager&#41;](url-reservations-for-multi-instance-report-server-deployments.md).  
  
##  <a name="URLExamples"></a> Beispiele für URL-Konfigurationen  
 In der folgenden Liste sind einige Beispiele für Berichtsserver-URLs aufgeführt:  
  
-   http://localhost/reportserver  
  
-   http://localhost/reportserver_SQLEXPRESS  
  
-   http://sales01/reportserver  
  
-   http://sales01:8080/reportserver  
  
-   https://sales.adventure-works.com/reportserver  
  
-   https://www.adventure-works.com:8080/reportserver01  
  
 Für den Zugriff auf den Berichts-Manager verwendete URLs weisen ein ähnliches Format auf und werden i. d. R. unter derselben Website erstellt, die den Berichtsserver hostet. Der einzige Unterschied ist der Name des virtuellen Verzeichnisses (in diesem Fall lautet er **reports** , Sie können jedoch einen beliebigen Namen konfigurieren):  
  
-   http://localhost/reports  
  
-   http://localhost/reports_SQLEXPRESS  
  
-   http://sales01/reports  
  
-   http://sales01:8080/reports  
  
-   https://sales.adventure-works.com/reports  
  
-   https://www.adventure-works.com:8080/reports  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
