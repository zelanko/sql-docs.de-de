---
title: Informationen zu URL-Reservierungen und -Registrierungen (SSRS-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- URL reservations
- URL registration
- Report Server service, URL reservations
ms.assetid: c2c460c3-e749-4efd-aa02-0f8a98ddbc76
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 31ff1f88e55905e8d67dd96c91cd80c8b6677fe2
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "48905980"
---
# <a name="about-url-reservations-and-registration--ssrs-configuration-manager"></a>Informationen zu URL-Reservierungen und Registrierungen (SSRS-Konfigurations-Manager)
  Anwendungen für URLs für Reporting Services werden als URL-Reservierungen in HTTP.SYS definiert. Eine URL-Reservierung definiert die Syntax eines URL-Endpunkts für eine Webanwendung. URL-Reservierungen werden sowohl für den Berichtsserver-Webdienst als auch für den Berichts-Manager beim Konfigurieren der Anwendungen auf dem Berichtsserver definiert. Beim Konfigurieren von URLs mit Setup oder mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool werden URL-Reservierungen automatisch für Sie erstellt:  
  
-   Setup erstellt URL-Reservierungen mit Standardwerten. Im Rahmen der Standardkonfiguration werden zwei URLs von Setup reserviert, eine für den Berichtsserver-Webdienst und eine für den Berichts-Manager. Mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool können Sie weitere URLs hinzufügen oder die von Setup erstellten Standard-URLs ändern.  
  
-   Das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool erstellt eine URL-Reservierung anhand der URL, die Sie auf der Seite **Webdienst-URL** oder auf der Seite **Berichts-Manager-URL** im Tool angegeben haben.  
  
 Setup und das Tool weisen dem Berichtsserver-Dienst außerdem Berichtigungen für die URL zu, suchen nach doppelten Instanzen und fügen HTTP.SYS die URL-Reservierung hinzu. Erstellen oder ändern Sie URL-Reservierungen für Reporting Services niemals direkt mit HttpCfg.exe oder einem anderen Tool. Wenn Sie einen Schritt überspringen oder einen ungültigen Wert festlegen, kann es zu Problemen kommen, die schwer zu diagnostizieren oder zu beheben sind.  
  
> [!NOTE]  
>  HTTP.SYS ist eine Komponente des Betriebssystems, die nach Netzwerkanforderungen lauscht und diese an eine Warteschlange für Anforderungen weiterleitet. In dieser Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]erstellt HTTP.SYS die Warteschlange für Anforderungen für den Berichtsserver-Webdienst und für den Berichts-Manager und verwaltet diese. Internetinformationsdienste (IIS) wird nicht mehr zum Hosten von oder Zugreifen auf [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Anwendungen verwendet. Weitere Informationen über HTTP.SYS-Funktionen finden Sie unter [HTTP-Server-API](http://go.microsoft.com/fwlink/?LinkId=92652) auf MSDN.  
  
##  <a name="ReportingServicesURLs"></a> URLs in Reporting Services  
 In einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation können Sie über URLs auf die folgenden Tools, Anwendungen und Elemente zugreifen:  
  
-   Report Server-Webdienst  
  
-   Berichts-Manager  
  
-   Berichts-Generator  
  
-   Berichte, die auf einem Berichtsserver veröffentlicht wurden  
  
 Andere veröffentlichte Elemente wie Modelle und freigegebene Datenquellen, die via URL adressierbar sind, sollten nicht über URLs in Form von eigenständigen Elementen zugreifbar sein. Diese Elemente werden vom Berichtsserver bei der Anzeige in einem Browserfenster nicht in einem aussagekräftigen Format dargestellt.  
  
> [!NOTE]  
>  In diesem Thema wird nicht der URL-Zugriff auf den Berichts-Generator oder auf bestimmte Berichte beschrieben, die auf dem Berichtsserver gespeichert sind. Weitere Informationen zum URL-Zugriff auf diese Elemente finden Sie in der [-Onlinedokumentation unter](../access-report-server-items-using-url-access.md) Zugreifen auf Berichtsserverelemente über den URL-Zugriff [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
##  <a name="URLreservation"></a> Registrierung und Reservierung für URLs  
 Eine URL-Reservierung definiert die URLs, über die auf eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Anwendung zugegriffen werden kann. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] reserviert mindestens eine URL für den Berichtsserver-Webdienst und für den Berichts-Manager in HTTP.SYS und registriert diese, wenn der Dienst gestartet wird. Die URLs für den Berichts-Generator und die Berichte basieren auf der URL-Reservierung für den Berichtsserver-Webdienst. Sie können Berichts-Generator oder Berichte über den Webdienst öffnen, indem Sie Parameter an die URL anfügen. Reservierungen und Registrierungen werden von HTTP.SYS bereitgestellt. Weitere Informationen finden Sie unter [Namespacereservierungen, Registrierung und Routing](http://go.microsoft.com/fwlink/?LinkId=92653) auf MSDN.  
  
 Bei der*URL-Reservierung* wird ein URL-Endpunkt für eine Webanwendung erstellt und in HTTP.SYS gespeichert. HTTP.SYS ist das allgemeine Repository für alle URL-Reservierungen, die auf einem Computer definiert wurden, und definiert eine Reihe allgemeiner Regeln für eindeutige URL-Reservierungen.  
  
 Die*URL-Registrierung* wird bei Dienststart vorgenommen. Die Anforderungswarteschlange wird erstellt, und HTTP.SYS beginnt mit dem Weiterleiten von Anforderungen an diese Warteschlange. URL-Endpunkte müssen registriert werden, bevor Anforderungen an diese Endpunkte der Warteschlange hinzugefügt werden. Beim Start des Berichtsserver-Diensts werden alle URLs registriert, die für die entsprechenden Anwendungen reserviert wurden. Dies bedeutet, dass der Webdienst für eine Registrierung aktiviert sein muss. Wenn Sie die **WebServiceAndHTTPAccessEnabled** -Eigenschaft im Facet Oberflächen-Konfiguration für Reporting Services der richtlinienbasierten Verwaltung auf **False** festgelegt haben, wird die URL für den Webdienst bei Dienststart nicht registriert.  
  
 Wenn Sie den Dienst anhalten oder die Anwendungsdomäne des Webdiensts oder des Berichts-Managers wiederverwenden, wird die Registrierung der URLs aufgehoben. Wenn Sie eine URL-Reservierung ändern, während der Dienst ausgeführt wird, wird die Anwendungsdomäne  vom Berichtsserver unmittelbar wiederverwendet, um die Registrierung der alten URL aufzuheben und die Verwendung einer neuen URL zu ermöglichen.  
  
 Mit einigen einfachen Beispielen werden das Konzept der URL-Reservierung und der Zusammenhang mit URL-Adressen für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Anwendungen veranschaulicht. Ein wichtiger Punkt zu beachten ist, dass die URL-Reservierung andere Syntax als die URL, die Sie verwenden verfügt, um die Anwendung zugreifen:  
  
|URL-Reservierung in HTTP.SYS|URL|Erklärung|  
|---------------------------------|---------|-----------------|  
|http://+:80/reportserver|http://\<Computername > / Reportserver<br /><br /> http://\<IP-Adresse > / Reportserver<br /><br /> http://localhost/reportserver|Die URL-Reservierung gibt ein Platzhalterzeichen (+) für Port 80 an. Dadurch werden alle eingehenden Anforderungen, die einen Host für die Auflösung zum Berichtsservercomputer auf Port 80 angeben, in der Berichtsserverwarteschlange abgelegt. Mit dieser URL-Reservierung kann eine beliebige Anzahl von URLs für den Zugriff auf den Berichtsserver verwendet werden.<br /><br /> Dies ist die Standard-URL-Reservierung für einen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsserver für die meisten Betriebssysteme.|  
|http://123.45.67.0:80/reportserver|http://123.45.67.0/reportserver|Diese URL-Reservierung gibt eine IP-Adresse an und ist viel restriktiver als die Platzhalter-URL-Reservierung. Nur mit URLs, die eine IP-Adresse enthalten, kann eine Verbindung mit dem Berichtsserver hergestellt werden. Dieser URL-Reservierung angegeben haben, wird eine Anforderung an einen Berichtsserver unter http:// angegebenen\<Computername > / Reportserver oder http://localhost/reportserver fehlschlug.|  
  
##  <a name="DefaultURLs"></a> Standard-URLs  
 Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in der Standardkonfiguration installieren, reserviert Setup URLs für den Berichtsserver-Webdienst und den Berichts-Manager. Sie können diese Standardwerte auch für URL-Reservierungen im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool verwenden. Wenn Sie [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installieren oder wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] als benannte Instanz installieren, enthalten Standard-URLs einen Instanznamen.  
  
> [!IMPORTANT]  
>  Das Instanzzeichen ist ein Unterstrich (`_`).  
  
 URL-Reservierungen enthalten eine Portnummer. In den folgenden Betriebssystemen kann ein Port von mehreren Webanwendungen verwendet werden:  
  
1.  [!INCLUDE[win8srv](../../includes/win8srv-md.md)]  
  
2.  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]  
  
3.  [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]  
  
4.  [!INCLUDE[win7](../../includes/win7-md.md)]  
  
5.  [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)]  
  
|Instanztyp|Application|Standard-URL|Tatsächliche URL-Reservierung in HTTP.SYS|  
|-------------------|-----------------|-----------------|----------------------------------------|  
|Standardinstanz|Report Server-Webdienst|http://\<Servername > / Reportserver|http://\<Servername >: 80/Reportserver|  
|Standardinstanz|Berichts-Manager|http://\<Servername > / Reportserver|http://\<Servername >: 80/Reportserver|  
|Benannte Instanz|Report Server-Webdienst|http://\<Servername > / Reportserver_\<Instanzname >|http://\<Servername >: 80/Reportserver_\<Instanzname >|  
|Benannte Instanz|Berichts-Manager|http://\<Servername > / Reports_\<Instanzname >|http://\<Servername >: 80/Reports_\<Instanzname >|  
|SQL Server Express|Report Server-Webdienst|http://\<Servername > / Reportserver_SQLExpress|http://\<Servername >: 80/Reportserver_SQLExpress|  
|SQL Server Express|Berichts-Manager|http://\<Servername > / Reports_SQLExpress|http://\<Servername >: 80/Reports_SQLExpress|  
  
##  <a name="URLPermissionsAccounts"></a> Authentifizierung und Dienstidentität für Reporting Services-URLs  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL-Reservierungen geben das Dienstkonto für den Berichtsserver-Dienst an. Das Konto, unter dem der Dienst ausgeführt wird, wird für alle URLs verwendet, die für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Anwendungen erstellt werden, die in der gleichen Instanz ausgeführt werden. Die Dienstidentität der Berichtsserverinstanz wird in der Datei RSReportServer.config gespeichert.  
  
 Das Dienstkonto hat keinen Standardwert. Während der Ausführung von Setup ist jedoch die Angabe eines Dienstkontos unter `URLReservation` in RSReportServer.config erforderlich. Dies gilt auch, wenn der Server im Dateimodus installiert wird. Gültige Werte für das Dienstkonto enthalten ein Domänenbenutzerkonto, ein `LocalSystem` oder einen `NetworkService`.  
  
 Der anonyme Zugriff ist aufgrund der Standardsicherheitseinstellung `RSWindowsNegotiate` deaktiviert. Berichtsserver-URLs verwenden Netzwerkcomputernamen für den Intranetzugriff. Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] für Internetverbindungen konfigurieren möchten, müssen Sie andere Einstellungen verwenden. Weitere Informationen finden Sie in der [-Onlinedokumentation unter](../security/authentication-with-the-report-server.md) Authentifizierung beim Berichtsserver [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
##  <a name="URLlocalAdmin"></a> URLs für die lokale Verwaltung  
 Sie können http://localhost/reportserver oder http://localhost/reports verwenden, wenn Sie einen starken oder einen schwachen Platzhalter für die URL-Reservierung angegeben haben.  
  
 Die URL http://localhost wird wie http://127.0.0.1 interpretiert. Wenn Sie die URL-Reservierung mit einem Computernamen oder einer einzelnen IP-Adresse verbunden haben, können Sie localhost nicht verwenden, es sei denn, Sie erstellen eine zusätzliche Reservierung für 127.0.0.1 auf dem lokalen Computer. Analog dazu gilt, dass Sie die URL nicht verwenden können, wenn Sie localhost oder 127.0.0.1 auf Ihrem Computer deaktiviert haben.  
  
 [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] und [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] enthalten neue Sicherheitsfunktionen, um das Risiko einer versehentlichen Ausführung von Programmen mit erweiterten Berechtigungen zu verhindern. Zur Aktivierung der lokalen Verwaltung für diese Betriebssysteme müssen zusätzliche Schritte ausgeführt werden. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
##  <a name="URLSharePoint"></a> URLs für Berichtsserver im integrierten SharePoint-Modus  
 Falls ein eigenständiger Berichtsserver zur Ausführung in einer umfangreichen Bereitstellung eines SharePoint-Produkts oder einer -Technologie konfiguriert ist, wird die Erstellung von URLs und virtuellen Verzeichnissen wie folgt beeinflusst:  
  
-   URLs für Berichte und andere Elemente werden über die URL der SharePoint-Webanwendung adressiert. Verwenden Sie für den Zugriff auf bestimmte Berichte stets eine vollqualifizierte URL einschließlich Pfad für die Website, Dokumentenbibliothek, Elementname und Dateinamenerweiterung (z.&nbsp;B. .rdl für einen Bericht). Beim Verweisen auf freigegebene Datenquellen und Modelle in Berichten müssen Sie vollständig qualifizierte URLs angeben, ebenso beim Angeben eines Zielservers und von Ordnern für Veröffentlichungsvorgänge auf einem Berichtsserver.  
  
-   Die Dateinamenerweiterung dient der Unterscheidung zwischen verschiedenen Typen von Berichtsserverelementen. Gültige Erweiterungen sind: .rdl für Berichtsdefinitionen, .smd. für Berichtsmodelle und .rsds für freigegebene Datenquellen, die für eine SharePoint-Website erstellt werden.  
  
-   SharePoint-Produkte und -Technologien weisen entsprechende URL-Reservierungen auf. Diese können jedoch bei der Veröffentlichung auf dem Server ignoriert werden. Im Hinblick auf SharePoint-Webanwendungen handelt es sich bei URL-Reservierungen um interne Vorgänge.  
  
-   Für Bereitstellungen mit einem Server, auf dem ein integrierter Berichtsserver und SharePoint-technologieinstanz auf demselben Computer installiert sind, können keine http://localhost/reportserver. Wenn http://localhost wird verwendet, um die SharePoint-Webanwendung zuzugreifen, verwenden Sie eine nicht standardmäßige-Website oder eine eindeutige portzuweisung auf einen Berichtsserver zugreifen. Außerdem kann der localhost-Zugriff auf einen Berichtsserver nicht für Knoten in der Bereitstellung auf Remotecomputern aufgelöst werden, wenn der Berichtsserver in eine SharePoint-Farm integriert ist.  
  
-   Die URL-Reservierung und der URL-Endpunkt für den Berichts-Manager können nicht konfiguriert werden, wenn der Berichtsserver im integrierten SharePoint-Modus ausgeführt wird. Falls Sie ihn konfigurieren, ist er bei der Bereitstellung eines Berichtsservers im integrierten SharePoint-Modus nicht mehr funktionsfähig. Der Berichts-Manager wird in diesem Modus nicht unterstützt.  
  
 Wenn Sie eine Berichtsserverbereitstellung für horizontales Skalieren zur Ausführung in einer umfangreichen Bereitstellung eines SharePoint-Produkts oder einer SharePoint-Technologie konfiguriert haben, müssen Sie für einen Lastenausgleich zwischen den Berichtsserverknoten sorgen und eine einzelne virtuelle Server-URL für die Bereitstellung für horizontales Skalieren definieren. Mithilfe der Integrationseinstellungen für den Berichtsserver können Sie nur eine einzelne Berichtsserver-URL angeben. Bei der Bereitstellung für horizontales Skalieren muss die URL als Zugriffspunkt für die Serverknoten in der Bereitstellung für horizontales Skalieren dienen.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren einer URL &#40;SSRS-Konfigurations-Manager&#41;](configure-a-url-ssrs-configuration-manager.md)   
 [URL-Reservierungssyntax &#40;SSRS-Konfigurations-Manager&#41;](url-reservation-syntax-ssrs-configuration-manager.md)  
  
  
