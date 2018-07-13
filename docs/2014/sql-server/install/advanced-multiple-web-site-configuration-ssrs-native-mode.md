---
title: Erweiterte Konfiguration für mehrere Websites (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.advancedmultiplewebsiteconfig.F1
ms.assetid: af4ede43-2225-45b5-ae7e-9202411551ba
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: eafcc3b69916ba253b430a61fb5b510eb3480d91
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220730"
---
# <a name="advanced-multiple-web-site-configuration-ssrs-native-mode"></a>Erweiterte Konfiguration mehrerer Websites (einheitlicher SSRS-Modus)
  In diesem Dialogfeld können Sie die URLs erstellen und verwalten, mit denen Sie einen Berichtsserver oder den Berichts-Manager aufrufen. Im Dialogfeld **Erweiterte Konfiguration mehrerer Websites** können Sie weitere URLs erstellen, benutzerdefinierte URLs, die einen Hostheadernamen enthalten oder in denen eine IP-Adresse im Format IPv4 oder IPv6 angegeben ist.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
 Die Erstellung mehrerer URLs ist nützlich, wenn Sie verschiedene Möglichkeiten konfigurieren möchten, um auf einen Berichtsserver zugreifen zu können. Beispielsweise erfordert der Zugriff auf einen Berichtsserver über eine Intranet- und Extranet-Verbindung normalerweise für jede Art der Verbindung andere URLs.  
  
 Öffnen der **erweiterte Konfiguration für mehrere Websites** im Dialogfeld klicken Sie auf **erweitert** auf die **Webdienst-URL** oder die **Report Manager URL**auf der Seite die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager. Wenn das Dialogfeld **Erweiterte Konfiguration mehrerer Websites** offen ist, können Sie auf **Hinzufügen** oder **Bearbeiten** klicken, um neue URLs zu definieren oder vorhandene URLs zu ändern.  
  
 Klicken Sie auf **OK** , um die Änderungen zu speichern. Wenn Sie URLs hinzufügen oder entfernen, jedoch dann das Dialogfeld ohne Klicken auf **OK**schließen, werden die Änderungen nicht gespeichert.  
  
## <a name="options"></a>Tastatur  
 **IP-Adresse**  
 Gibt den Berichtsserver-Computer im TCP/IP-Netzwerk an. Gültige Werte sind:  
  
-   Der Wert**Alle zugewiesenen** gibt an, dass alle IP-Adressen, die dem Computer zugewiesen sind, in einer URL verwendet werden können, die auf eine Berichtsserveranwendung verweist. Dieser Wert umfasst auch Host-Anzeigenamen (z. B. Computernamen), die durch einen Domänennamenserver in eine IP-Adresse aufgelöst werden können, die dem Computer zugewiesen ist. Dies ist der Standardwert für eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -URL.  
  
-   Mit dem Wert**Alle nicht zugewiesenen** wird angegeben, dass der Berichtsserver alle Anforderungen annimmt, die keine exakte Entsprechung in der IP-Adresse oder im Hostnamen haben. Verwenden Sie diesen Wert nicht, wenn er bereits von einer anderen Webanwendung verwendet wird. Wenn Sie es trotzdem tun, damit, unterbrechen Sie den Dienst der anderen Anwendung.  
  
-   Mit**127.0.0.1** wird auf localhost zugegriffen. Dieser Wert unterstützt die lokale Verwaltung auf dem Berichtsservercomputer. Wenn Sie nur diesen Wert auswählen, können nur Benutzer, die lokal auf dem Berichtsservercomputer angemeldet sind, auf die Anwendung zugreifen.  
  
-   *Nnn.nnn.nnn.nnn* ist die IPv4-Adresse einer Netzwerkkarte auf Ihrem Computer. Wenn Ihr Netzwerk IPv6-Adressen verwendet, werden die IP-Adresse einem 128-Bit-Wert, der 8 4-Byte-Feldern, die ähnlich wie das folgende Format: \<Header >:*Nnnn:nnnn:nnnn:nnnn*.  
  
     Wenn Sie mehrere Karten haben, wird für jede Karte eine IP-Adresse angezeigt. Wenn Sie nur diesen Wert auswählen, wird der Anwendungszugriff auf genau diese IP-Adresse (und jeden Hostname, den ein Domänennamenserver dieser Adresse zuordnet) beschränkt. Sie können mit localhost nicht auf einen Berichtsserver zugreifen, und Sie können nicht die IP-Adressen der anderen Netzwerkkarten verwenden, die auf dem Berichtsservercomputer installiert sind.  
  
 **Port**  
 Gibt den Port an, den dieser Berichtsserver auf Anforderungen prüft. Port 80 ist der Standardport. Wenn Sie Port 80 verwenden, ist es ist nicht notwendig, diesen in die URL zu übernehmen. Wenn Sie eine andere Portnummer verwenden, Sie müssen immer enthalten sie in der URL (z. B. http://localhost:8181/reports).  
  
 **Hostheader**  
 Wenn Sie bereits einen Hostheader in einem Domänennamenserver definiert haben, der auf Ihrem Computer aufgelöst wird, können Sie diesen Hostheader in einer URL angeben, die Sie für den Zugriff auf den Berichtsserver konfigurieren.  
  
 Ein Hostheader ist ein eindeutiger Name, der es mehreren Websites erlaubt, dieselbe IP-Adresse und denselben Port zu verwenden. Hostheadernamen sind leichter zu behalten und einzugeben als IP-Adressen und Portnummern. Ein Beispiel für einen Hostheadernamen könnte www.adventure-works.com sein.  
  
 **SSL-Port**  
 Gibt den Port für SSL-Verbindungen an. Der Standardport für SSL ist 443.  
  
 **SSL-Zertifikat**  
 Gibt den Zertifikatsnamen eines SSL-Zertifikats an, das Sie auf diesem Computer installiert haben. Wenn das Zertifikat einem Platzhalter zugeordnet wird, können Sie es für eine Berichtsserververbindung verwenden.  
  
 Gibt den vollqualifizierten Namen des Computers an, für den das Zertifikat registriert ist. Der von Ihnen angegebene Namen muss mit dem Namen identisch sein, für den das Zertifikat registriert ist.  
  
 Um diese Option verwenden zu können, müssen Sie ein Zertifikat installiert haben. Sie müssen auch die UrlRoot-Konfigurationseinstellung in der Datei RSReportServer.config so ändern, dass der vollqualifizierte Name des Computers angegeben wird, für den das Zertifikat registriert ist. Weitere Informationen finden Sie unter [Konfigurieren von SSL-Verbindungen auf einem Berichtsserver im einheitlichen Modus](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
 **Ausgestellt für**  
 Zeigt den Namen des Computers an, für den das Zertifikat erstellt wurde.  
  
 **Hinzufügen**  
 Definieren Sie eine zusätzliche URL.  
  
 **Bearbeiten**  
 Ändern Sie beliebige Teile der URL-Syntax.  
  
 **Entfernen**  
 Entfernen Sie eine URL aus der Liste.  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurations-Manager &#40;im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Konfigurieren einer URL &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
 [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
