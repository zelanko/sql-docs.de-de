---
title: URLs in Konfigurationsdateien (SSRS-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- URL configuration [Reporting Services]
ms.assetid: 4f5e7fe0-b5b1-4665-93d4-80dce12d6b14
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 48deeb3ba6badb1d01b895467f2a8418bdf37ba9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2020
ms.locfileid: "80380711"
---
# <a name="urls-in-configuration-files--ssrs-configuration-manager"></a>URLs in Konfigurationsdateien (SSRS-Konfigurations-Manager)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] speichert Anwendungseinstellungen in einer RSReportServer.config-Datei. In dieser Datei befinden sich Konfigurationseinstellungen sowohl für URLs als auch für URL-Reservierungen. Diese Konfigurationseinstellungen haben ganz verschiedene Zwecke und Regeln für Änderungen. Wenn Sie es gewohnt sind, Konfigurationsdateien zu ändern, um eine Bereitstellung zu optimieren, finden Sie in diesem Thema hilfreiche Informationen dazu, wie jede URL-Einstellung verwendet wird.  
  
## <a name="url-settings-in-rsreportserverconfig-file"></a>URL-Einstellungen in der RSReportServer.config-Datei  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] speichert URLs für den Anwendungs- und Berichtszugriff und zur Verbindung von Web-Front-End-Komponenten mit einem Back-End-Berichtsserver.  
  
#### <a name="urls-for-application-access"></a>URLs für Anwendungszugriff  
 URLs werden für den Zugriff auf den Report Server-Webdienst und den Berichts-Manager verwendet. Verwenden Sie zum Konfigurieren der URLs das Reporting Services-Konfigurationstool. Das Tool erstellt die URL-Reservierungen für jede Anwendung in HTTP.SYS und fügt Einträge für die URLs im Abschnitt `URLReservations` der Datei RSReportServer.config hinzu.  
  
-   Informationen zum Anzeigen der Beschreibungen der einzelnen Elemente im `URLReservations` Abschnitt finden Sie unter [RSReportServer-Konfigurationsdatei](../report-server/rsreportserver-config-configuration-file.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
-   Weitere Informationen zur Syntax nur `UrlString` des Elements finden Sie unter [URL-Reservierungssyntax &#40;SSRS Configuration Manager&#41;](url-reservation-syntax-ssrs-configuration-manager.md).  
  
-   Anweisungen zum Konfigurieren von URLs für den Anwendungszugriff finden Sie unter [Konfigurieren einer URL &#40;SSRS-Konfigurations-Manager&#41;](configure-a-url-ssrs-configuration-manager.md)verwendet.  
  
#### <a name="urls-for-report-access"></a>URLs für Berichtszugriff  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] umfasst eine Berichtsserver-E-Mail-Übermittlungserweiterung, mit der Sie Berichtslinks oder Anlagen senden können. Ein Berichtshyperlink wird erstellt, wenn der Bericht übermittelt wird. Die Berichtsserver-E-Mail-Übermittlungserweiterung erstellt den Link mithilfe der `UrlRoot`-Einstellung in der Konfigurationsdatei. Die `UrlRoot`-Einstellung wird außerdem dazu verwendet, Links in einem gerenderten Bericht, der über die unbeaufsichtigte Berichtsverarbeitung generiert wird, aufzulösen.  
  
 `UrlRoot` wird automatisch in der RSReportServer.config-Datei angegeben, wenn Sie URLs für den Anwendungszugriff konfigurieren. Wenn Sie diesen Wert in der Konfigurationsdatei ändern, müssen Sie eine gültige URL-Adresse für einen Report Server-Webdienst angeben, der mit einer Berichtsserver-Datenbank mit Berichten, die Sie übermitteln möchten, verbunden ist. Sie können nur einen `UrlRoot`-Wert für eine einzelne Berichtsserverinstanz angeben. In der RSReportServer.config-Datei kann nur ein `UrlRoot`-Eintrag für eine bestimmte Berichtsserverinstanz vorhanden sein. Wenn mehrere URLs für den Report Server-Webdienst reserviert sind, müssen Sie einen der verfügbaren Werte für `UrlRoot` auswählen.  
  
 In den meisten Fällen ist es nicht notwendig, `UrlRoot` zu ändern. Wenn jedoch über eine vollqualifizierte URL auf den Berichtsserver zugegriffen wird und Sie keine URL konfiguriert haben, die einen Hostheader für den vollqualifizierten Websitenamen verwendet, müssen Sie die RSReportServer.config manuell bearbeiten, um die `UrlRoot` auf die vollqualifizierte Berichtsserver-URL festzulegen, die zum Rendern des Berichts verwendet wird (z. `https://www.adventure-works.com/mywebapp/reportserver`B. ).  
  
#### <a name="urls-connecting-report-manager-and-web-parts-to-the-report-server-web-service"></a>URLs zur Verbindung des Berichts-Managers und Webparts zum Report Server-Webdienst  
 Der Berichts-Manager und SharePoint 2.0 Webparts für Reporting Services sind Web-Front-End-Komponenten, die eine Verbindung zu einem Berichtsserver herstellen. URLs, die verwendet werden, um eine Verbindung mit einem Back-End-Berichtsserver herzustellen, umfassen Folgendes:  
  
-   `ReportServerUrl` (wird vom Berichts-Manager verwendet)  
  
-   `ReportServerExternalUrl` (wird von Webparts verwendet)  
  
> [!NOTE]  
>  Frühere Versionen von Reporting Services beinhalteten das `ReportServerVirtualDirectory`-Element. Dieser Wert ist in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und in höheren Versionen veraltet. Wenn Sie eine vorhandene Installation aktualisiert haben und eine Konfigurationsdatei mit dieser Einstellung verwenden, wird dieser Wert vom Berichtsserver nicht mehr gelesen.  
  
 Die folgende Tabelle bietet einen Überblick über alle URLs, die in einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationsdatei angegeben werden können.  
  
|Einstellung|Verwendung|Beschreibung|  
|-------------|-----------|-----------------|  
|`ReportServerUrl`|Optional. Dieses Element ist nicht in der RSReportServer.config-Datei enthalten, es sei denn, Sie fügen es selbst hinzu. Legen Sie dieses Element nur fest, wenn Sie eines der folgenden Szenarios konfigurieren:<br /><br /> Der Berichts-Manager bietet Web-Front-End-Zugriff auf einen Report Server-Webdienst, der auf einem anderen Computer oder einer anderen Instanz desselben Computers ausgeführt wird.<br /><br /> Wenn Sie mehrere URLs zu einem Berichtsserver haben und der Berichts-Manager einen bestimmten URL verwenden soll.<br /><br /> Sie haben einen bestimmten Berichtsserver-URL, der für alle Berichts-Manager-Verbindungen verwendet werden soll.<br /><br /> Sie aktivieren beispielsweise den Berichts-Manager-Zugriff für alle Computer im Netzwerk, möchten jedoch, dass sich der Berichts-Manager über eine lokale Verbindung mit dem Berichtsserver verbindet. In diesem Fall können `ReportServerUrl` Siehttp://localhost/reportserver"" konfigurieren.<br /><br /> <br /><br /> Anweisungen zum Implementieren dieser Szenarien finden Sie unter Konfigurieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des [Berichts-Managers &#40;systemeigenen Modus&#41;](../report-server/configure-web-portal.md) in Books Online.|Dieser Wert gibt eine URL zum Berichtsserver-Webdienst an. Dieser Wert wird von der Berichts-Manager-Anwendung beim Start gelesen. Wenn dieser Wert festgelegt ist, stellt der Berichts-Manager eine Verbindung zu dem im URL angegebenen Berichtsserver her.<br /><br /> Der Berichts-Manager bietet standardmäßig Web-Front-End-Zugriff auf den Report Server-Webdienst, der innerhalb derselben Berichtsserver-Instanz ausgeführt wird wie der Berichts-Manager. Wenn Sie den Berichts-Manager jedoch mit einem Report Server-Webdienst verwenden möchten, der zu einer anderen Instanz gehört oder in einer Instanz auf einem anderen Computer ausgeführt wird, können Sie diesen URL zur Weiterleitung des Berichts-Managers festlegen, sodass dieser eine Verbindung mit dem externen Report Server-Webdienst herstellt.<br /><br /> Wenn ein SSL-Zertifikat (Secure Sockets Layer) auf dem Berichtsserver installiert ist, mit dem Sie eine Verbindung herstellen, muss der Wert `ReportServerUrl` dem Namen des Servers entsprechen, der für das Zertifikat registriert ist. Wenn Sie die Fehlermeldung "Die zugrunde liegende Verbindung wurde geschlossen: Für den geschützten SSL/TLS-Kanal konnte keine Vertrauensstellung hergestellt werden" erhalten, legen Sie `ReportServerUrl` auf den vollqualifizierten Domänennamen des Servers fest, für den das Zertifikat ausgestellt wurde. Wenn das Zertifikat beispielsweise bei **https:\//adventure-works.com.onlinesales**registriert ist, lautet die URL des Berichtsservers **https:\//adventure-works.com.onlinesales/reportserver**.|  
|`ReportServerExternalUrl`|Optional. Dieses Element ist nicht in der RSReportServer.config-Datei enthalten, es sei denn, Sie fügen es selbst hinzu.<br /><br /> Legen Sie dieses Element nur fest, wenn Sie SharePoint 2.0 Webparts verwenden und möchten, dass Benutzer einen Bericht abrufen und in einem neuen Browserfenster öffnen können.<br /><br /> Fügen `ReportServerExternalUrl` Sie <`ReportServerUrl`> unter dem <>-Element hinzu, und legen Sie ihn dann auf einen vollqualifizierten Berichtsservernamen fest, der in eine Berichtsserverinstanz aufgelöst wird, wenn in einem separaten Browserfenster darauf zugegriffen wird. Löschen Sie `ReportServerUrl` <> nicht.<br /><br /> Das folgende Beispiel veranschaulicht die Syntax:<br /><br /> `<ReportServerExternalUrl>http://myserver/reportserver</ReportServerExternalUrl>`|Dieser Wert wird von SharePoint 2.0 Webparts verwendet.<br /><br /> In früheren Versionen wurde empfohlen, diesen Wert festzulegen, um den Berichts-Generator auf einem mit dem Internet verbundenen Berichtsserver bereitzustellen. Dies ist ein ungeprüftes Bereitstellungsszenario. Wenn Sie diese Einstellung in der Vergangenheit verwendet haben, um den Zugriff auf den Berichts-Generator aus dem Internet zu unterstützen, sollten Sie sich eine Alternative überlegen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Berichtsserver-URLs &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md)   
 [Konfigurieren einer URL &#40;SSRS-Konfigurations-Manager&#41;](configure-a-url-ssrs-configuration-manager.md)  
  
  
