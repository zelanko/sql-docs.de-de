---
title: Webdienst-URL (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.reportservervirtualdirectory.F1
helpviewer_keywords:
- Reporting Services, Web service
ms.assetid: 9d210b5d-2a08-4e56-a4f5-c16715b00d79
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 01e5393ae638ddcecd04211a0a7e01e8116346a9
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952364"
---
# <a name="web-service-url-ssrs-native-mode"></a>Webdienst-URL (einheitlicher SSRS-Modus)
  Auf der Seite der Webdienst-URL können Sie die URL, mit der auf den Berichtsserver zugegriffen wird, konfigurieren bzw. ändern. Eine *URL-Reservierung* wird auf Grundlage des URL erstellt, den Sie angeben. Die URL-Reservierung definiert die Syntax und die Regeln für alle URLs, mit denen danach auf den Report Server-Webdienst zugegriffen werden kann. Die URL-Reservierung umfasst Präfix, Host, Port und das virtuelle Verzeichnis für den Report Server-Webdienst. Je nachdem, wie Sie den Host angeben, können mehrere URLs für eine einzelne Reservierung möglich sein. Der Standardwert für den Host ist ein Platzhalter. Mit einem Platzhalter können Sie in einer URL jeden beliebigen Hostnamen angeben, der in den Computer aufgelöst wird, auf dem der Berichtsserver gehostet wird. Weitere Informationen zur URL-Konfiguration und zu Reservierungen finden Sie unter [konfigurieren &#40;einer URL SSRS Configuration Manager&#41; ](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) und Konfigurieren von [Berichts Server-URLs &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
 Um diese Seite zu öffnen, starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager, und klicken Sie im Navigationsbereich auf **Webdienst-URL** . Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 Diese Seite enthält Werte, die häufig in Berichtsserver-URLs verwendet werden. Wenn Sie weitere URLs erstellen, Hostheader verwenden oder die IP-Adresse in einem bestimmten Format angeben möchten, klicken Sie auf **Erweitert**.  
  
 Ein Link zum Webdienst wird auf dieser Seite angezeigt, nachdem Sie auf **Übernehmen**geklickt haben. Wenn Sie vor der Erstellung der Berichtsserver-Datenbank auf diesen Link klicken, wird höchstwahrscheinlich die Fehlermeldung "Seite nicht gefunden" angezeigt. Dieser Fehler tritt nicht mehr auf, wenn die Datenbank konfiguriert wurde. Weitere Informationen finden Sie unter [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus (SSRS-Konfigurations-Manager)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
 Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] neu installiert haben und Fehlermeldungen bei der Verwendung des Standard-IP-Adressenwerts "Alle zugewiesenen" und Port 80 erhalten, können Sie den Fehler normalerweise beheben, indem Sie die URL nach dem Neustarten des Diensts neu erstellen.  
  
## <a name="options"></a>Optionen  
 **Virtuelles Verzeichnis**  
 Gibt den Namen des virtuellen Verzeichnisses für den Berichtsserver-Webdienst an. Sie können auf einem Computer nur einen Namen eines virtuellen Verzeichnisses für jede Instanz des Report Server-Webdiensts haben.  
  
 **IP-Adresse**  
 Gibt den Berichtsserver-Computer im TCP/IP-Netzwerk an. Gültige Werte sind:  
  
-   Der Wert**Alle zugewiesenen** gibt an, dass alle IP-Adressen, die dem Computer zugewiesen sind, in einer URL verwendet werden können, die auf eine Berichtsserveranwendung verweist. Dieser Wert umfasst auch Host-Anzeigenamen (z. B. Computernamen), die durch einen Domänennamenserver in eine IP-Adresse aufgelöst werden können, die dem Computer zugewiesen ist. Dies ist der Standardwert für eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -URL.  
  
-   Mit dem Wert**Alle nicht zugewiesenen** wird angegeben, dass der Berichtsserver alle Anforderungen annimmt, die keine exakte Entsprechung in der IP-Adresse oder im Hostnamen haben. Verwenden Sie diesen Wert nicht, wenn er bereits von einer anderen Webanwendung verwendet wird. Wenn Sie es trotzdem tun, damit, unterbrechen Sie den Dienst der anderen Anwendung.  
  
-   Mit**127.0.0.1** wird auf localhost zugegriffen. Dieser Wert unterstützt die lokale Verwaltung auf dem Berichtsservercomputer. Wenn Sie nur diesen Wert auswählen, können nur Benutzer, die lokal auf dem Berichtsservercomputer angemeldet sind, auf die Anwendung zugreifen.  
  
-   *Nnn.nnn.nnn.nnn* ist die IPv4-Adresse einer Netzwerkkarte auf Ihrem Computer. Wenn Ihr Netzwerk IPv6-Adressierung verwendet, ist die IP-Adresse ein 128-Bit-Wert von 8 4-Byte-Feldern ähnlich dem folgenden Format: \<header >:*nnnn: nnnn: nnnn: nnnn*  
  
     Wenn Sie mehrere Karten haben, wird für jede Karte eine IP-Adresse angezeigt. Wenn Sie nur diesen Wert auswählen, wird der Anwendungszugriff auf genau diese IP-Adresse (und jeden Hostname, den ein Domänennamenserver dieser Adresse zuordnet) beschränkt. Sie können mit localhost nicht auf einen Berichtsserver zugreifen, und Sie können nicht die IP-Adressen der anderen Netzwerkkarten verwenden, die auf dem Berichtsservercomputer installiert sind.  
  
 **TCP-Port**  
 Gibt den Port an, den der Berichtsserver auf http-Anforderungen für die URLs untersucht, die den Namen des virtuellen Verzeichnisses für den Berichtsserver enthalten.  
  
 **SSL-Zertifikat**  
 Verknüpft ein Zertifikat mit der IP-Adresse, die Sie angegeben haben. Das Zertifikat muss auf dem Computer installiert und konfiguriert werden. Reporting Services enthält keine Funktionen zum Verwalten von Zertifikaten. Das Zertifikat muss für den Namen des Computers oder Hosts ausgegeben werden, der in die IP-Adresse aufgelöst wird. Wenn Sie z. b. ein Zertifikat verwenden möchten, das für http://salesreports ausgestellt wurde, muss die angegebene IP-Adresse auf einen Server mit dem Namen "SalesReports" aufgelöst werden.  
  
 Wenn Sie ein Zertifikat verwenden, müssen Sie die `UrlRoot`-Konfigurationseinstellung in der Datei RSReportServer.config so ändern, dass der vollqualifizierte Name des Computers angegeben wird, für den das Zertifikat registriert ist. Weitere Informationen finden Sie unter [Konfigurieren von SSL-Verbindungen auf einem Berichtsserver im einheitlichen Modus](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
 **SSL-Port**  
 Gibt den Port für SSL-Verbindungen an.  
  
 **Del**  
 Zeigt die für die aktuelle Berichtsserver-Instanz definierten URLs an.  
  
 **Erweitert**  
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
 [Konfigurations-Manager für Reporting Services F1-Hilfe &#40;Themen SSRS im&#41;einheitlichen Modus](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
