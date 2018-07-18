---
title: Webdienst-URL (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.reportservervirtualdirectory.F1
helpviewer_keywords:
- Reporting Services, Web service
ms.assetid: 9d210b5d-2a08-4e56-a4f5-c16715b00d79
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 21a9ede5ef83169d312bb59e84bfd3f33619dafb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37270236"
---
# <a name="web-service-url-ssrs-native-mode"></a>Webdienst-URL (einheitlicher SSRS-Modus)
  Auf der Seite der Webdienst-URL können Sie die URL, mit der auf den Berichtsserver zugegriffen wird, konfigurieren bzw. ändern. Eine *URL-Reservierung* wird auf Grundlage des URL erstellt, den Sie angeben. Die URL-Reservierung definiert die Syntax und die Regeln für alle URLs, mit denen danach auf den Report Server-Webdienst zugegriffen werden kann. Die URL-Reservierung umfasst Präfix, Host, Port und das virtuelle Verzeichnis für den Report Server-Webdienst. Je nachdem, wie Sie den Host angeben, können mehrere URLs für eine einzelne Reservierung möglich sein. Der Standardwert für den Host ist ein Platzhalter. Mit einem Platzhalter können Sie in einer URL jeden beliebigen Hostnamen angeben, der in den Computer aufgelöst wird, auf dem der Berichtsserver gehostet wird. Weitere Informationen zu URL-Konfiguration und-Reservierung finden Sie unter [Konfigurieren einer URL &#40;SSRS-Konfigurations-Manager&#41; ](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) und [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41; ](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
 Um diese Seite zu öffnen, starten die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager, und klicken Sie auf **Webdienst-URL** im Navigationsbereich. Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 Diese Seite enthält Werte, die häufig in Berichtsserver-URLs verwendet werden. Wenn Sie weitere URLs erstellen, Hostheader verwenden oder die IP-Adresse in einem bestimmten Format angeben möchten, klicken Sie auf **Erweitert**.  
  
 Ein Link zum Webdienst wird auf dieser Seite angezeigt, nachdem Sie auf **Übernehmen**geklickt haben. Wenn Sie vor der Erstellung der Berichtsserver-Datenbank auf diesen Link klicken, wird höchstwahrscheinlich die Fehlermeldung "Seite nicht gefunden" angezeigt. Dieser Fehler tritt nicht mehr auf, wenn die Datenbank konfiguriert wurde. Weitere Informationen finden Sie unter [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus (SSRS-Konfigurations-Manager)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
 Wenn Sie erneut installiert [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und feststellen, dass es treten Fehler beim Versuch, den IP-Adresse-Standardwert der alle zugewiesenen "und" Port 80 verwenden, die Sie in der Regel können Sie den Fehler beheben, erstellen Sie die URL nach dem Neustart des Diensts.  
  
## <a name="options"></a>Tastatur  
 **Virtuelles Verzeichnis**  
 Gibt den Namen des virtuellen Verzeichnisses für den Berichtsserver-Webdienst an. Sie können auf einem Computer nur einen Namen eines virtuellen Verzeichnisses für jede Instanz des Report Server-Webdiensts haben.  
  
 **IP-Adresse**  
 Gibt den Berichtsserver-Computer im TCP/IP-Netzwerk an. Gültige Werte sind:  
  
-   Der Wert**Alle zugewiesenen** gibt an, dass alle IP-Adressen, die dem Computer zugewiesen sind, in einer URL verwendet werden können, die auf eine Berichtsserveranwendung verweist. Dieser Wert umfasst auch Host-Anzeigenamen (z. B. Computernamen), die durch einen Domänennamenserver in eine IP-Adresse aufgelöst werden können, die dem Computer zugewiesen ist. Dies ist der Standardwert für eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -URL.  
  
-   Mit dem Wert**Alle nicht zugewiesenen** wird angegeben, dass der Berichtsserver alle Anforderungen annimmt, die keine exakte Entsprechung in der IP-Adresse oder im Hostnamen haben. Verwenden Sie diesen Wert nicht, wenn er bereits von einer anderen Webanwendung verwendet wird. Wenn Sie es trotzdem tun, damit, unterbrechen Sie den Dienst der anderen Anwendung.  
  
-   Mit**127.0.0.1** wird auf localhost zugegriffen. Dieser Wert unterstützt die lokale Verwaltung auf dem Berichtsservercomputer. Wenn Sie nur diesen Wert auswählen, können nur Benutzer, die lokal auf dem Berichtsservercomputer angemeldet sind, auf die Anwendung zugreifen.  
  
-   *Nnn.nnn.nnn.nnn* ist die IPv4-Adresse einer Netzwerkkarte auf Ihrem Computer. Wenn Ihr Netzwerk IPv6-Adressen verwendet, werden die IP-Adresse einem 128-Bit-Wert, der 8 4-Byte-Feldern, die ähnlich wie das folgende Format: \<Header >:*Nnnn:nnnn:nnnn:nnnn*  
  
     Wenn Sie mehrere Karten haben, wird für jede Karte eine IP-Adresse angezeigt. Wenn Sie nur diesen Wert auswählen, wird der Anwendungszugriff auf genau diese IP-Adresse (und jeden Hostname, den ein Domänennamenserver dieser Adresse zuordnet) beschränkt. Sie können mit localhost nicht auf einen Berichtsserver zugreifen, und Sie können nicht die IP-Adressen der anderen Netzwerkkarten verwenden, die auf dem Berichtsservercomputer installiert sind.  
  
 **TCP-Port**  
 Gibt den Port an, den der Berichtsserver auf http-Anforderungen für die URLs untersucht, die den Namen des virtuellen Verzeichnisses für den Berichtsserver enthalten.  
  
 **SSL-Zertifikat**  
 Verknüpft ein Zertifikat mit der IP-Adresse, die Sie angegeben haben. Das Zertifikat muss auf dem Computer installiert und konfiguriert werden. Reporting Services enthält keine Funktionen zum Verwalten von Zertifikaten. Das Zertifikat muss für den Namen des Computers oder Hosts ausgegeben werden, der in die IP-Adresse aufgelöst wird. Um beispielsweise ein Zertifikat verwenden, die ausgegeben wurden http://salesreports, die IP-Adresse, die Sie angegeben haben, muss auf einem Server mit dem Namen "Salesreports" aufgelöst.  
  
 Wenn Sie ein Zertifikat verwenden, müssen Sie ändern die `UrlRoot` -Konfigurationseinstellung in der RSReportServer.config-Datei, damit sie gibt den vollqualifizierten Namen des Computers, für den das Zertifikat registriert ist. Weitere Informationen finden Sie unter [Konfigurieren von SSL-Verbindungen auf einem Berichtsserver im einheitlichen Modus](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
 **SSL-Port**  
 Gibt den Port für SSL-Verbindungen an.  
  
 **URLs**  
 Zeigt die für die aktuelle Berichtsserver-Instanz definierten URLs an.  
  
 **Erweitert:**  
 Klicken Sie, um zusätzliche URLs für die aktuelle Anwendungsinstanz zu erstellen.  
  
> [!NOTE]  
>  Wenn Sie über vorhandene SSL-Bindungen und URL-Reservierungen verfügen und die SSL-Bindung ändern möchten, um z. B. ein anderes Zertifikat bzw. einen anderen Hostheader zu verwenden, wird empfohlen, die folgenden Schritte in der angegebenen Reihenfolge auszuführen:  
>   
>  1.  Entfernen Sie zuerst alle URL-Reservierungen.  
> 2.  Entfernen Sie anschließend alle SSL Bindungen.  
> 3.  Erstellen Sie die URLs und SSL-Bindungen anschließend neu.  
>   
>  Die vorangehenden Schritte können mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager ausgeführt werden.  
>   
>  Microsoft Windows unterstützt eine Bindung für jede Kombination aus IP-Adresse und Port. Wenn Sie einen Berichtsserver für die Verwendung eines bestimmten Hostheaderwerts konfigurieren und das Zertifikat für die Kombination aus Port und IP-Adresse ebenfalls in einen anderen Hostheaderwert ausgegeben wird, wird im Browser eine Warnung angezeigt, dass das Zertifikat nicht mit der verwendeten URL übereinstimmt.  
>   
>  Um den Fehler zu beheben, löschen Sie alle Bindungen und erstellen anschließend neue Bindungen mit eindeutigen Einstellungen oder konfigurieren die Registrierungen der Reporting Services-URLs mit Platzhaltern.  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurations-Manager-F1-Hilfethemen &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
