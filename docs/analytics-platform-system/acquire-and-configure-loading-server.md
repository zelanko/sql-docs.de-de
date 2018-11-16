---
title: Abrufen und Konfigurieren eines ladenden Servers – Parallel Data Warehouse | Microsoft-Dokumentation
description: Dieser Artikel beschreibt die zum Abrufen und Konfigurieren eines ladenden Servers als Windows-System nicht zur Appliance gehört zum Senden von Daten lädt, Parallel Data Warehouse (PDW).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: da404aa881f3ff7af26a681751aae12a45f2628f
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51703778"
---
# <a name="acquire-and-configure-a-loading-server-for-parallel-data-warehouse"></a>Abrufen und Konfigurieren eines ladenden Servers für Parallel Data Warehouse
Dieser Artikel beschreibt die zum Abrufen und Konfigurieren eines ladenden Servers als Windows-System nicht zur Appliance gehört zum Senden von Daten lädt, Parallel Data Warehouse (PDW).  
  
## <a name="Basics"></a>Grundlagen  
Der Server laden:  
  
-   Muss keine werden von einem einzelnen Server. Sie können gleichzeitig mehrere beim Laden von Servern mit laden.  
  
-   Bereitgestellt und von Ihren eigenen IT-Team verwaltet wird. Möglicherweise verfügen Sie bereits einen Server oder Server, die zum Laden von Daten in PDW verwendet werden können.  
  
-   Befindet sich in Ihren eigenen Rack nicht zur Appliance gehört, und kann nicht in der Analytics Platform System Appliance platziert werden.  
  
-   An das Gerät über das Gerät InfiniBand-Netzwerk oder über Ethernet ist verbunden werden. Es wird empfohlen, für die Leistung zu erzielen InfiniBand verwenden.  
  
-   Befindet sich in der Domäne Ihren eigenen Kunden, nicht der Domäne der Anwendung. Es ist keine Vertrauensstellung zwischen Ihrem Kunden und der Appliance-Domäne.  
  
## <a name="Step1"></a>Schritt 1: Bestimmen der kapazitätsanforderungen  
Das System laden kann als eine oder mehrere beim Laden von Servern entworfen werden, die paralleler Ladevorgänge ausführen. Jeder Server laden muss nicht nur für das Laden von verwendet werden, solange sie die Leistung und Speicher die Anforderungen Ihrer Workload behandeln soll.  
  
Die Systemanforderungen für einen Server laden hängt der eigenen arbeitsauslastung, fast vollständig. Verwenden der [Laden von Server-Kapazität Planungsarbeitsblatt](loading-server-capacity-planning-worksheet.md) um zu ermitteln, welche kapazitätsanforderungen.  
  
## <a name="Step2"></a>Schritt 2: Abrufen der Server  
Nun, da Sie Ihre kapazitätsanforderungen besser verstehen, können Sie planen, die Server und Netzwerkkomponenten, die Sie erwerben oder bereitstellen müssen. Integrieren Sie die folgende Liste von Anforderungen in den purchasing-Plan, und klicken Sie dann den Server zu erwerben oder Bereitstellen eines vorhandenen Servers.  
  
### <a name="R"></a>Softwareanforderungen  
Unterstützte Betriebssysteme:  
  
-   WindowsServer 2012 oder Windows Server 2012 R2. Diese Betriebssysteme müssen den FDR-Netzwerkadapter.  
  
-   Windows Server 2008 R2. Dieses Betriebssystem wird der DDR-Netzwerkadapter benötigt.  
  
Der Server muss das Gebietsschema EN-US verwenden, um das Laden der Command-Line Dwloader-Tool zu verwenden. Dwloader unterstützt keine anderen Gebietsschemas.  
  
### <a name="networking-requirements-for-windows-server-2012-and-windows-server-2012-r2"></a>Netzwerkanforderungen für WindowsServer 2012 und Windows Server 2012 R2  
Auch für das Laden nicht erforderlich ist, ist InfiniBand empfohlene Verbindungstyp, zum Laden von Servern. Verwenden Sie für eine optimale Leistung Windows Server 2012 oder Windows Server 2012 R2 und der ein FDR InfiniBand-Netzwerkadapter, um den Server Laden mit dem Gerät InfiniBand-Netzwerk zu verbinden.  
  
So bereiten Sie für eine Windows Server 2012 oder Windows Server 2012 R2 InfiniBand-Verbindung Folgendes vor:  
  
1.  Planen den Server im rack nah an das Gerät, damit Sie es an das Gerät eine Verbindung herstellen können InfiniBand wechselt. Weitere Informationen von Mellanox-Technologien zu InfiniBand, finden Sie im Whitepaper, [Einführung in die InfiniBand](https://www.mellanox.com/pdf/whitepapers/IB_Intro_WP_190.pdf).  
  
2.  Erwerben Sie einen Netzwerkadapter von Mellanox ConnectX-3 ein FDR InfiniBand Single- oder dual-Port. Es wird empfohlen, erwerben die Netzwerkkarte mit zwei Ports für die Fehlertoleranz während der Datenübertragung. Ein zwei Port-Netzwerkadapter ist für hohe Verfügbarkeit erforderlich.  
  
3.  Erwerben Sie 2 ein FDR InfiniBand-Kabel für eine Karte mit zwei Ports bzw. 1 ein FDR InfiniBand-Kabel für einen einzelnen Port-Karte. Die Kabel ein FDR InfiniBand werden den Laden von Server mit Appliance InfiniBand-Netzwerk verbunden. Die Länge der Kabel hängt von den Abstand zwischen dem Server geladen und die Einheiten InfiniBand-Switches, gemäß Ihrer Umgebung ab.  
  
## <a name="Step3"></a>Schritt 3: Verbinden Sie den Server mit den InfiniBand-Netzwerken  
Verwenden Sie diese Schritte, um den Server Laden mit dem InfiniBand-Netzwerk zu verbinden. Wenn der Server nicht das InfiniBand-Netzwerk verwendet wird, überspringen Sie diesen Schritt.  
  
1.  Rack Server nah an das Gerät, damit Sie das Gerät InfiniBand-Netzwerk hergestellt werden können.  
  
2.  Installieren Sie den InfiniBand Mellanox ConnectX-3 ein FDR InfiniBand-Netzwerkadapter in den Server laden.  
  
3.  Verwenden Sie die FDR-Kabel, um dem InfiniBand-Netzwerkadapter mit einer der beiden InfiniBand Schalter in das erste Gerät Rack herstellen.  
  
4.  Installieren Sie und konfigurieren Sie den entsprechenden Windows-Treiber für das InfiniBand-Netzwerkadapter.  
  
    -   InfiniBand-Treibern für Windows werden durch die OpenFabrics Alliance, ein Branchenkonsortium von InfiniBand-Anbietern entwickelt.  Der richtige Treiber möglicherweise mit dem InfiniBand-Netzwerkadapter verteilt wurden. Wenn dies nicht der Fall ist, kann der Treiber www.openfabrics.org heruntergeladen werden.  
  
5.  Konfigurieren Sie InfiniBand und DNS-Einstellungen für die Netzwerkadapter. Konfigurationsanweisungen, finden Sie unter [konfigurieren InfiniBand-Netzwerkadapter](configure-infiniband-network-adapters.md).  
  
## <a name="Step4"></a>Schritt 4: Installieren der Tools laden  
Die Clienttools stehen zum Download aus dem Microsoft Download Center zur Verfügung. 

Um Dwloader zu installieren, führen Sie die Installation Dwloader aus den Clienttools aus.
  
Wenn Sie die Verwendung von Integration Services für das laden möchten, müssen Sie zum Installieren von Integration Services und die Integration Services-Zieladapter. Die Adapter sind in den Clienttools verfügbar.

<!-- To install the des[Install Integration Services Destination Adapters](install-integration-services-destination-adapters.md). 
--> 
  
## <a name="Step5"></a>Schritt 5: Starten Sie laden  
Sie können nun damit beginnen, Laden von Daten. Weitere Informationen finden Sie in den folgenden Themen:  
  
1.  [Dwloader laden-Befehlszeilentool](dwloader.md)  
  
2.  [– Übersicht](load-overview.md)  
  
## <a name="performance"></a>Leistung  
Aktivieren Sie für optimale Leistung auf Windows Server 2012 und höher laden Instant File Initialization, damit bei Daten überschrieben werden, das Betriebssystem keine vorhandene Daten mit Nullen überschrieben werden. Ist dies ein Sicherheitsrisiko dar, da frühere Daten auf den Datenträgern noch vorhanden ist, werden Sie sicher, dass die sofortige Dateiinitialisierung zu deaktivieren.  
  
## <a name="Security"></a>Security-Hinweise  
Da die zu ladenden Daten nicht auf dem Gerät gespeichert sind, ist Ihr IT-Team zuständig für die Verwaltung aller Aspekte der Sicherheit für Ihre Daten zu laden. Beispielsweise schließt dies die Verwaltung der Sicherheit der Daten zu laden, die Sicherheit des Servers verwendet, um Lasten zu speichern und die Sicherheit der Netzwerkinfrastruktur, die den Server Laden mit der SQL Server-PDW-Appliance verbindet.  
  
> [!IMPORTANT]  
> Es ist besonders wichtig, um jedem Laden von Server zu sichern, die Command-Line laden Dwloader-Tool verwendet. Wenn Dwloader Daten geladen wird, authentifiziert es zuerst mit den Steuerelementknoten aus, und klicken Sie dann nach der erfolgreichen Authentifizierung es verschiebt Daten vom Server laden direkt auf den Computeknoten über Datenkanäle. Überprüfung des Zertifikats erfolgt nicht während der Hand-Schütteln zwischen jedem Laden von Server und jeder Compute-Knoten. Dadurch wird die Compute-Knoten verfügbar gemacht, potenziellen Man-in-the-Middle-Angriffe auf jeden Datenkanal beim Laden. Diese Angriffe können manipulierte Daten und/oder Offenlegung von Informationen führen.  
  
Um Sicherheitsrisiken mit Ihren Daten zu reduzieren, empfehlen wir Folgendes:  
  
-   Bestimmen Sie ein Windows-Konto, das ausschließlich zum Laden von Daten in PDW verwendet wird. Weisen Sie diesem Konto Berechtigungen für den Load-Speicherort und an keiner anderen Stelle verfügen.  
  
-   Legen Sie einen PDW-Benutzer, die über Berechtigungen zum Laden von Daten verfügt. Abhängig von Ihren sicherheitsanforderungen können Sie einem bestimmten Benutzer pro Datenbank verfügen.  
  
-   Vorgänge auf dem Server laden können kein UNC-Pfad aus dem Daten von außerhalb des internen vertrauenswürdigen Netzwerks akzeptieren. Und ein Angreifer im Netzwerk oder mit der Möglichkeit zum beeinflussen der namensauflösung abfangen oder in der SQL Server PDW gesendete Daten geändert werden kann. Dies stellt ein Risiko der Offenlegung von Manipulationen und Informationen. Manipulationen soll verringert werden, indem Sie ohne Signaturen für die Verbindung. Um dieses Risiko zu verringern, legen Sie die folgende Gruppenrichtlinie-Option in **Sicherheitseinstellungen\Lokale Richtlinien\sicherheitsoptionen** auf dem Server geladen: **Microsoft-Netzwerkclient: Kommunikation digital signieren (immer): Aktiviert**  
  
-   Deaktivieren Sie sofortige Dateiinitialisierung auf Windows Server 2012 und höher. Dies ist ein Kompromiss zwischen Leistung und Sicherheit, wie im Abschnitt Leistung. Sie müssen entscheiden, was am besten gemäß Ihren sicherheitsanforderungen ist.  
  
## <a name="see-also"></a>Siehe auch  
[Sichern und Wiederherstellen – Übersicht](backup-and-restore-overview.md)  
  
