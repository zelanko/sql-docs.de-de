---
title: 'Abrufen #a0 Konfigurieren des Lade Servers'
description: In diesem Artikel wird beschrieben, wie Sie einen Lade Server als nicht-Appliance-Windows-System zum Übermitteln von Daten Ladevorgängen an parallele Data Warehouse (PDW) erwerben und konfigurieren.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ef49bb86c8e16600f2ff1bf2d1c7a92ecc5af964
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401484"
---
# <a name="acquire-and-configure-a-loading-server-for-parallel-data-warehouse"></a>Einen Lade Server für parallele Data Warehouse erwerben und konfigurieren
In diesem Artikel wird beschrieben, wie Sie einen Lade Server als nicht-Appliance-Windows-System zum Übermitteln von Daten Ladevorgängen an parallele Data Warehouse (PDW) erwerben und konfigurieren.  
  
## <a name="Basics"></a>Grundlagen  
Der Lade Server:  
  
-   Es muss sich nicht um einen einzelnen Server handeln. Sie können gleichzeitig mit mehreren Lade Servern laden.  
  
-   Wird von Ihrem eigenen IT-Team bereitgestellt und verwaltet. Möglicherweise verfügen Sie bereits über einen Server oder Server, der zum Laden von Daten in PDW verwendet werden kann.  
  
-   Befindet sich in einem eigenen nicht-Appliance-Rack und kann nicht innerhalb der Analytics Platform System Appliance platziert werden.  
  
-   Ist über das InfiniBand-Netzwerk der Anwendung oder über Ethernet mit dem Gerät verbunden. Aus Leistungsgründen wird die Verwendung von InfiniBand empfohlen.  
  
-   Befindet sich in ihrer eigenen Kunden Domäne und nicht in der Appliance-Domäne. Zwischen Ihrer Kunden Domäne und der Appliance-Domäne besteht keine Vertrauensstellung.  
  
## <a name="Step1"></a>Schritt 1: Ermitteln der Kapazitätsanforderungen  
Das Ladesystem kann als ein oder mehrere Lade Server entworfen werden, von denen gleichzeitige Lasten durchgeführt werden. Jeder Lade Server muss ausschließlich zum Laden dediziert werden, solange er die Leistungs-und Speicheranforderungen Ihrer Arbeitsauslastung übernimmt.  
  
Die Systemanforderungen für einen Lade Server hängen fast vollständig von ihrer eigenen Arbeitsauslastung ab. Verwenden Sie das [Arbeitsblatt Laden der Server Kapazitätsplanung](loading-server-capacity-planning-worksheet.md) , um Ihre Kapazitätsanforderungen zu ermitteln.  
  
## <a name="Step2"></a>Schritt 2: Abrufen des sservers  
Nachdem Sie nun ihre Kapazitätsanforderungen besser verstanden haben, können Sie die Server und Netzwerkkomponenten planen, die Sie erwerben oder bereitstellen müssen. Fügen Sie die folgende Liste von Anforderungen in Ihren Kauf Plan ein, und erwerben Sie dann Ihren Server, oder stellen Sie einen vorhandenen Server bereit.  
  
### <a name="R"></a>Software Anforderungen  
Unterstützte Betriebssysteme:  
  
-   Windows Server 2012 oder Windows Server 2012 R2. Diese Betriebssysteme erfordern den-Netzwerkadapter für die Netzwerkkarte.  
  
-   Windows Server 2008 R2. Dieses Betriebssystem erfordert den DDR-Netzwerkadapter.  
  
Der Server muss das Gebiets Schema "en-US" verwenden, um das Befehlszeilen-Lade Tool "" dwloader "zu verwenden. "" dwloader "unterstützt keine anderen Gebiets Schemas.  
  
### <a name="networking-requirements-for-windows-server-2012-and-windows-server-2012-r2"></a>Netzwerk Anforderungen für Windows Server 2012 und Windows Server 2012 R2  
Obwohl das Laden nicht erforderlich ist, ist InfiniBand der empfohlene Verbindungstyp zum Laden von Servern. Verwenden Sie zum erzielen der optimalen Leistung Windows Server 2012 oder Windows Server 2012 R2 und den FDR InfiniBand-Netzwerkadapter, um den Lade Server mit dem Gerät InfiniBand-Netzwerk zu verbinden.  
  
So bereiten Sie eine Windows Server 2012-oder Windows Server 2012 R2 InfiniBand-Verbindung vor:  
  
1.  Planen Sie, den Server so nah wie möglich zu verbinden, damit Sie ihn mit den InfiniBand-Switches der Anwendung verbinden können. Weitere Informationen von Mellanox-Technologien zu InfiniBand finden Sie im Whitepaper [Introduction to InfiniBand (Einführung in InfiniBand](https://www.mellanox.com/pdf/whitepapers/IB_Intro_WP_190.pdf)).  
  
2.  Erwerben Sie den Netzwerkadapter "Mellanox ConnectX-3 FDR InfiniBand Single" oder "Dual Port". Es wird empfohlen, den Netzwerkadapter mit zwei Ports für die Fehlertoleranz während der Datenübertragung zu erwerben. Für hohe Verfügbarkeit ist ein Netzwerkadapter mit zwei Ports erforderlich.  
  
3.  Erwerben Sie 2 FDR InfiniBand-Kabel für eine Dual-Port-Karte oder 1 FDR InfiniBand-Kabel für eine einzelne Port Karte. Die FDR InfiniBand-Kabel verbinden den Lade Server mit dem Gerät InfiniBand-Netzwerk. Die Länge des Kabels hängt von der Entfernung zwischen dem Lade Server und den InfiniBand-Switches der Anwendung gemäß ihrer Umgebung ab.  
  
## <a name="Step3"></a>Schritt 3: Verbinden des Servers mit den InfiniBand-Netzwerken  
Verwenden Sie diese Schritte, um den Lade Server mit dem InfiniBand-Netzwerk zu verbinden. Wenn der Server das InfiniBand-Netzwerk nicht verwendet, überspringen Sie diesen Schritt.  
  
1.  Verbinden Sie den Server in der Nähe des Geräts, sodass Sie es mit dem InfiniBand-Netzwerkgerät verbinden können.  
  
2.  Installieren Sie den InfiniBand-Netzwerkadapter "Mellanox ConnectX-3" in den Lade Server.  
  
3.  Verwenden Sie die FDR-Kabel, um den InfiniBand-Netzwerkadapter mit einem der beiden InfiniBand-Switches im ersten Geräte Gestell zu verbinden.  
  
4.  Installieren und konfigurieren Sie den entsprechenden Windows-Treiber für den InfiniBand-Netzwerkadapter.  
  
    -   InfiniBand-Treiber für Windows werden von der openfabrics Alliance entwickelt, einem Branchen Konsortium von InfiniBand-Anbietern.  Der richtige Treiber wurde möglicherweise mit dem InfiniBand-Netzwerkadapter verteilt. Andernfalls kann der Treiber von www.openfabrics.org heruntergeladen werden.  
  
5.  Konfigurieren Sie die InfiniBand-und DNS-Einstellungen für die Netzwerkadapter. Konfigurations Anweisungen finden Sie unter [Konfigurieren von InfiniBand-Netzwerkadaptern](configure-infiniband-network-adapters.md).  
  
## <a name="Step4"></a>Schritt 4: Installieren der Lade Tools  
Die Client Tools stehen im Microsoft Download Center zum Download zur Verfügung. 

Führen Sie zum Installieren von "dwloader die" dwloader-Installation über die Client Tools aus.
  
Wenn Sie beabsichtigen, Integration Services zum Laden zu verwenden, müssen Sie Integration Services und die Integration Services Ziel Adapter installieren. Die Adapter sind in den Client Tools verfügbar.

<!-- To install the des[Install Integration Services Destination Adapters](install-integration-services-destination-adapters.md). 
--> 
  
## <a name="Step5"></a>Schritt 5: Starten des Ladens  
Sie sind nun bereit, mit dem Laden von Daten zu beginnen. Weitere Informationen finden Sie unter:  
  
1.  ["dwloader-Befehlszeilen Lade Tool](dwloader.md)  
  
2.  [Übersicht laden](load-overview.md)  
  
## <a name="performance"></a>Leistung  
Aktivieren Sie die sofortige Datei Initialisierung, damit Daten überschrieben werden, wenn Daten überschrieben werden, damit die Leistung am besten in Windows Server 2012 und höher ist. Wenn dies ein Sicherheitsrisiko ist, weil vorherige Daten auf den Datenträgern weiterhin vorhanden sind, sollten Sie die sofortige Datei Initialisierung deaktivieren.  
  
## <a name="Security"></a>Sicherheitshinweise  
Da die zu ladenden Daten nicht auf dem Gerät gespeichert sind, ist das IT-Team für die Verwaltung aller Aspekte der Sicherheit Ihrer Daten verantwortlich. Dies umfasst z. b. die Verwaltung der Sicherheit der zu ladenden Daten, die Sicherheit des Servers, der zum Speichern von Lasten verwendet wird, und die Sicherheit der Netzwerkinfrastruktur, die den Lade Server mit der SQL Server PDW Appliance verbindet.  
  
> [!IMPORTANT]  
> Es ist besonders wichtig, jeden Lade Server zu sichern, der das Befehlszeilen-Lade Tool von "dwloader verwendet. Wenn "dwloader Daten lädt, wird es zuerst mit dem Steuer Knoten authentifiziert, und nach erfolgreicher Authentifizierung werden Daten vom Lade Server direkt auf die Computeknoten über Datenkanäle verschoben. Die Zertifikat Überprüfung erfolgt nicht während des Handshakes zwischen jedem Lade Server und jedem Computeknoten. Dadurch bleiben die Computeknoten für potenzielle man-in-the-Middle-Angriffe auf den einzelnen Datenkanälen beim Laden verfügbar. Diese Angriffe können dazu führen, dass Daten und/oder Informationen offengelegt werden.  
  
Um die Sicherheitsrisiken für Ihre Daten zu verringern, wird Folgendes empfohlen:  
  
-   Legen Sie ein Windows-Konto fest, das ausschließlich zum Laden von Daten in PDW verwendet wird. Erlauben Sie diesem Konto, Berechtigungen für den Lade Speicherort und nirgendwo sonst zu haben.  
  
-   Legen Sie einen PDW-Benutzer fest, der über Berechtigungen zum Laden von Daten verfügt. Abhängig von Ihren Sicherheitsanforderungen können Sie über einen bestimmten Benutzer pro Datenbank verfügen.  
  
-   Vorgänge auf dem Lade Server können einen UNC-Pfad akzeptieren, von dem Daten aus außerhalb des vertrauenswürdigen internen Netzwerks abgerufen werden. Und ein Angreifer im Netzwerk oder die Möglichkeit, die Namensauflösung zu beeinflussen, kann die an die SQL Server PDW gesendeten Daten abfangen oder ändern. Dies stellt ein Risiko zur Offenlegung von Manipulationen und Informationen dar. Manipulationen sollten durch das Signieren der Verbindung verhindert werden. Um dieses Risiko zu mindern, legen Sie die folgende Gruppenrichtlinien Option unter **Sicherheitseinstellungen\Lokale Richtlinien\Sicherheitsoptionen** auf dem Lade Server fest: **Microsoft-Netzwerkclient: Kommunikation digital signieren (immer): aktiviert**  
  
-   Deaktivieren Sie die sofortige Datei Initialisierung auf Windows Server 2012 und höher. Dies ist ein Kompromiss zwischen Leistung und Sicherheit, wie im Abschnitt zur Leistung erläutert. Sie müssen entscheiden, was für Ihre Sicherheitsanforderungen am besten geeignet ist.  
  
## <a name="see-also"></a>Weitere Informationen  
[Übersicht über die Sicherung und Wiederherstellung](backup-and-restore-overview.md)  
  
