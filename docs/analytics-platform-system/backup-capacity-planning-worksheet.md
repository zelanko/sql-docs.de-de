---
title: Kapazitätsplanung für Sicherungsserver - Parallel Data Warehouse | Microsoft-Dokumentation
description: Dieses Arbeitsblatt für die Planung der Kapazität können Sie bestimmen die Anforderungen für einen backup-Server für das Parallel Data Warehouse-Datenbank-Backup und restore-Vorgängen. Hiermit können Sie um Ihren Plan für den Erwerb neuer oder Bereitstellung vorhandenen backup-Server zu erstellen.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 500bebab375a0d0b94032a1855af3844bc2e6fa7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63295059"
---
# <a name="backup-server-capacity-planning-worksheet---parallel-data-warehouse"></a>Der Sicherungsserver Worksheet zur kapazitätsplanung – Parallel Data Warehouse
Dieses Arbeitsblatt für die Planung der Kapazität können Sie bestimmen die Anforderungen für Sicherungsserver für das Ausführen von SQL Server-PDW-datenbanksicherung und Wiederherstellungsvorgänge. Hiermit können Sie um Ihren Plan für den Erwerb neuer oder Bereitstellung vorhandenen backup-Server zu erstellen.  
  
Dieses Arbeitsblatt ist eine Ergänzung zu den Anweisungen in [abrufen und Konfigurieren eines Servers für die Sicherung](acquire-and-configure-backup-server.md).  
  
## <a name="capacity-planning-worksheet-for-backup-servers"></a>Arbeitsblatt für Kapazität Planung für Sicherungsserver  

### <a name="notes"></a>Hinweise  
  
1.  Dieses Arbeitsblatt für die gilt für Server, die Vorgänge zur Sicherung und Wiederherstellung für PDW-Datenbanken ausführen.  
  
2.  Die einzige Möglichkeit zum Sichern und Wiederherstellen von PDW-Datenbanken werden die Datenbank sichern und Wiederherstellen der Datenbank-SQL-Befehle verwenden. Sobald die Sicherungsdaten werden auf dem backup Server ist, existiert jedoch als einen Satz von Windows-Dateien. Sie können die Sicherungsdateien vom Server an einem anderen Speicherort mit herkömmlichen Windows-basierten Datei Sicherungsmethoden archivieren.  
  
### <a name="clipboard-iconmediaclipboard-iconpng-clipboard-icon-capacity-planning-worksheet"></a>![Zwischenablagesymbol](media/clipboard-icon.png "zwischenablagesymbol") Kapazität Planungsarbeitsblatt 
  
Drucken Sie dieses Arbeitsblatt, und Fülle ihn mit Ihren eigenen Anforderungen entsprechend.  
  
|Komponente|Anforderung|Geben Sie in diesem Artikel mit Ihren eigenen Anforderungen|Empfehlungen|  
|-------------|---------------|--------------------------------------------------|-------------------|  
|Speicherung|Maximale Anzahl Bytes, die Sie auf dem backup Server auf einen bestimmten Zeitraum speichern möchten.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Um die speicheranforderungen zu ermitteln, ermitteln Sie, wie viele Daten, die Sie auf dem backup Server auf einen bestimmten Zeitraum speichern möchten.<br /><br />Die Sicherungsdaten werden auf dem Sicherungsserver in einem komprimierten Format gespeichert. Datenkomprimierungsraten, abhängig von den Eigenschaften der Daten ab.<br /><br />Zum Beispiel: Es wird empfohlen, als eine grobe Schätzung schätzen relativ zur Größe der unkomprimierten Daten ein Komprimierungsverhältnis von 7:1. Dies setzt voraus, dass mindestens 80 % der Daten in gruppierten columnstore-Indizes gespeichert ist. Beispielsweise könnte Wenn 700 GB nicht komprimierter Daten in einer Datenbank haben, und es sich in gruppierten columnstore-Indizes befindet, klicken Sie dann Sie schätzen, dass die datenbanksicherung ungefähr 100 GB benötigen.<br /><br />Wenn Sie mehrere Kopien von datenbanksicherungen auf dem backup Server verfügen möchten, müssen Sie diese zu berücksichtigen.<br /><br />Zum Beispiel: Wenn Sie beabsichtigen, 10 Datenbanken sichern, die jeweils 5 TB unkomprimierte Daten enthalten, verfügen über die Datenbanken auf eine Gesamtgröße von 50 TB aus. Wenn Sie planen, 5 Tage lang in einer Zeile diesen 10 Datenbanken täglich zu sichern, ist die gesamte unkomprimierte Größe 250 TB. Umgestaltung in ein Komprimierungsverhältnis von 7:1, benötigen Sie 250 / 7 = 35,7 TB Speicher auf dem backup Server. Empfohlen wird konservativ und fängt über 30 % die zusätzliche Kapazität abweichungen berücksichtigt, und erweitern.  In diesem Beispiel wäre eine bessere 46,6 TB.|  
|Netzwerk|Typ der Netzwerkverbindung.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Bestimmen der besten Netzwerkverbindungstyp, der Ihre lastanforderungen-Rate erfüllen können.<br /><br />Zum Beispiel: InfiniBand oder 10 Gbit-Ethernet-die optimale bieten Preise werden geladen. 1Gbit Ethernet wird Load Gebühren bis 360 GB pro Stunde oder weniger beschränken.|  
|E/A|Bytes pro Stunde für Schreibvorgänge.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Zum Schreiben von Sicherungen auf dem Datenträger, die 4 TB pro Stunde schreibgeschwindigkeit optimal sind.<br /><br />Zum Beispiel: Für die Laufwerke, die 50 MB pro Sekunde geschrieben werden können, sollten Sie mindestens 24 Laufwerke sowie für die Spiegelung oder Parität.<br /><br />E/a-Kapazität indexvereinigungen berücksichtigt alle e/a erkennt, die in den Server laden. Verfügt der Server Laden anderer e/a-Datenverkehr zusätzlich zu Daten lädt, wie z. B. das Empfangen von Datendateien von einem ETL-Server erhöht die e/a-Anforderungen.|  
|CPU|Anzahl von Sockets.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Empfangen und Speichern von Sicherungsdateien ist keine CPU-Intensive Anwendung.  Es wird empfohlen, als Mindestanforderungen genannt mit einem 2-Socket-Server vor kurzem hergestellt.|  
|RAM|GB Speicher, der ermöglicht Windows zum Zwischenspeichern von Dateien während der lädt.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Empfangen und Speichern von Sicherungsdateien erfordert nur wenig Arbeitsspeicher auf dem Server geladen.<br /><br />Um die RAM-Anforderungen zu ermitteln, finden Sie in Ihrer Windows Server-Installation "und" 3rd Party anwendungsanforderungen. Mindestens 32 GB wird empfohlen, wenn Sie nicht den Anforderungen aus anderen Quellen verfügen.|  
  
Wenn Sie Ihre kapazitätsanforderungen bestimmt haben, zurück zu den [abrufen und Konfigurieren eines Servers geladen](acquire-and-configure-loading-server.md) Thema, um Ihren Einkauf zu planen.  
  
## <a name="see-also"></a>Siehe auch  
[Sicherung und Laden von hardware](backup-and-loading-hardware.md)  
  
