---
title: Laden die Serverkapazität Planung - Analytics Platform System | Microsoft-Dokumentation
description: Dieses Arbeitsblatt für die Planung der Kapazität können Sie bestimmen die Anforderungen für einen Server laden, für das Laden von Daten in Analytics Platform System Parallel Data Warehouse."
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2f0efd7e0688496d5af7887431ca00ae683c874f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63213393"
---
# <a name="loading-server-capacity-planning-worksheet-for-analytics-platform-system"></a>Laden Server Worksheet zur kapazitätsplanung eines für Analytics Platform System
Dieses Arbeitsblatt für die Planung der Kapazität können Sie die Anforderungen für einen Server laden, für das Laden von Daten in SQL Server PDW zu bestimmen. Hiermit können Sie um Ihren Plan erwerben oder vorhandene Laden von Server-Bereitstellung zu erstellen.  
  
## <a name="worksheet-notes"></a>Anmerkungen zu dieser Version Arbeitsblatt
  
1.  Dieses Arbeitsblatt für die gilt für Server, die Daten mit geladen werden, werden die **Dwloader** laden-Befehlszeilentool.  
  
2.  Zum Laden von Daten mit Integration Services oder eine dritte Partei-ladetool, können die Anforderungen abhängig von der Unterschiede in den Ladevorgang zu variieren.  
  
3.  Die meisten Anforderungen gelten für Laden von beiden Dateien komprimierte oder unkomprimierte Daten; Alle Unterschiede in Anforderungen werden fett aufgeführt.  
  
## <a name="clipboardmediaclipboard-iconpng-clipboard-capacity-planning-worksheet"></a>![Zwischenablage](media/clipboard-icon.png "Zwischenablage") Arbeitsblatt – Kapazitätsplanung  
  
Drucken Sie dieses Arbeitsblatt, und Fülle ihn mit Ihren eigenen Anforderungen entsprechend.  
  
|Komponente|Anforderung|Geben Sie in diesem Artikel mit Ihren eigenen Anforderungen|Empfehlungen|  
|-------------|---------------|--------------------------------------------------|-------------------|  
|Speicherung|Maximale Anzahl Bytes, die Sie auf dem Server laden alle angegebenen Zeitraum speichern möchten.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Um die speicheranforderungen zu ermitteln, ermitteln Sie, wie viele Daten, die Sie auf dem Server Laden an alle angegebenen Zeitraum speichern möchten.  Die kapazitätsanforderungen sind für Laden von Dateien werden. das Betriebssystem und das Laden von Dateien muss sich auf andere Datenträgerarrays.<br /><br />Zum Beispiel: Wenn Sie planen, 100 GB an Daten vom Datenträger zu 3 Mal Laden benötigen jeden Tag, aber nicht löschen, die die Daten bis zum Ende der Woche, dann können Sie Dateien Sie eine minimale 2.1 TB nicht auf die Datendateien zu speichern. Empfohlen wird konservativ und fängt über 30 % mehr Speicher für abweichungen und das Wachstum berücksichtigt.  In diesem Beispiel wäre eine bessere 2,73 TB Speicherplatz.|  
|Auslastungsrate|Maximale Anzahl von Bytes pro Stunde Daten zum Laden in PDW.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Hierbei handelt es sich um eine Schätzung. Wenn Sie diese Anforderung zu berechnen, wird davon ausgegangen Sie, dass die Dateien bereits auf dem Server geladen sind und andere Bedingungen laden so gut wie möglich sind.<br /><br />Zum Beispiel: Nicht erforderlich, Sie Komprimierbarkeit der Daten zu berücksichtigen, da Dwloader immer sendet unkomprimierte Daten für die PDW. Nicht erforderlich, datentypkonvertierungen und die Größe der Zieltabelle zu berücksichtigen.|  
|Netzwerk|Typ der Netzwerkverbindung.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Bestimmen der besten Netzwerkverbindungstyp für Ihre lastanforderungen für die Rate an.<br /><br />Zum Beispiel: InfiniBand oder 10 stellt Gbit-Ethernet-die optimale laden Gebühren bereit. 1 Gbit-Ethernet wird Load Gebühren bis 360 GB pro Stunde oder weniger beschränken.|  
|E/A|Bytes pro Stunde für Lese- und Schreibvorgänge.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Zum Laden von Daten muss Dwloader aller Daten vom Datenträger lesen vor dem Senden in PDW.<br /><br />Jeder Server Laden von kann nicht Daten geladen schneller als das Gerät Daten aus allen laden Quellen empfangen kann. Planen Sie die e/a, lesen die Kapazität für das Laden, damit der Auslastungskapazität des Geräts nicht überschritten wird, um Geld zu sparen.<br /><br />Zum Beispiel:<br />PDW empfängt und lädt Daten in ein Rack 1 Gerät mit einer maximalen Rate von 1,8 TB pro Stunde. Für ein Gerät mit mindestens 2 Racks ist die maximale Last-Rate 3,6 TB pro Stunde an.<br /><br />Wenn Sie planen, die aus mehreren beim Laden von Servern gleichzeitig zu laden, werden die e/a-Anforderungen für jeden Server laden kleiner, wenn ein Server alle laden ausführt.<br /><br />Zum Beispiel: Eine laden-Server kann maximal 1,8 TB pro Stunde für ein 1-Rack-Gerät geladen werden. Zwei beim Laden der Server konnte jeder gleichzeitig 900 GB pro Stunde in ein Rack 1 Gerät geladen werden. Höheres Maß an Parallelität können Effizienz und maximalen Durchsatz reduzieren.<br /><br />E/a-Kapazität indexvereinigungen berücksichtigt alle e/a erkennt, die in den Server laden. Verfügt der Server Laden anderer e/a-Datenverkehr zusätzlich zu Daten lädt, wie z. B. das Empfangen von Datendateien von einem ETL-Server erhöht die e/a-Anforderungen.<br /><br />Für komprimierte Daten hängen die Komprimierungsrate Daten die e/a-Anforderungen. Dwloader die komprimierten Daten liest und dekomprimiert ihn dann vor dem Senden in PDW. Je höher die Komprimierungsrate, desto weniger Daten der Server laden müssen vom Datenträger gelesen.<br /><br />Zum Beispiel: Wenn die erforderliche Rate 1,8 TB pro Stunde beträgt und die Daten auf dem Server "laden" mit 2:1-Komprimierung gespeichert ist, muss der Server Laden nur zum Lesen von 900 GB pro Stunde vom Datenträger anstelle 1,8 TB. Ein Komprimierungsverhältnis von 3:1 bedeutet, dass der Server beim Laden mindestens 600 GB pro Stunde vom Datenträger lesen muss.|  
|CPU|Anzahl von Sockets.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Zum Laden von nicht komprimierten Daten, ist Dwloader keine CPU-Intensive Anwendung.  Es wird empfohlen, als Mindestanforderungen genannt mit einem 2-Socket-Server vor kurzem hergestellt.<br /><br />Komprimierte Daten laden, benötigen Sie ausreichend CPU-Leistung, dekomprimieren die Daten vor dem Senden in PDW. Dwloader kann 10 aktiven Threads gleichzeitig ausführen. Wenn Sie planen das gleichzeitige Laden von 10 komprimierte Dateien, empfehlen wir, dass der Server über mindestens eine 10-Kern-CPU oder zwei CPUs mit 6 Kernen verfügt.|  
|RAM|GB Speicher, der ermöglicht Windows zum Zwischenspeichern von Dateien während der lädt.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Dwloader verwendet nur sehr wenig RAM auf dem Server geladen. Für die Leistung zu erzielen verwendet Windows Arbeitsspeicher zum Laden von Dateien zwischenspeichern, nach der sie vom Datenträger gelesen werden.<br /><br />Um die RAM-Anforderungen zu ermitteln, finden Sie in Ihrer Windows Server-Installation "und" 3rd Party anwendungsanforderungen. Mindestens 32 GB wird empfohlen, wenn Sie nicht den Anforderungen aus anderen Quellen verfügen.<br /><br />Für komprimierte Daten ist ein schneller RAM nützlich, da es die dekomprimierung beschleunigen wird.|  
  
## <a name="see-also"></a>Siehe auch  
[Erwerben und Konfigurieren eines ladenden Servers](acquire-and-configure-loading-server.md)  
[Dwloader Command-Line-Ladeprogramm](dwloader.md)  
  
