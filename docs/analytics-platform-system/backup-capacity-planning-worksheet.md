---
title: Kapazitätsplanung für Sicherungs Server
description: Mithilfe dieses Arbeitsblatts zur Kapazitätsplanung können Sie die Anforderungen für einen Sicherungs Server für die Ausführung paralleler Data Warehouse Daten Bank Sicherungs-und Wiederherstellungs Vorgänge ermitteln. Verwenden Sie diese Informationen, um einen Plan für den Erwerb neuer oder vorhandener Sicherungs Server zu erstellen.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 57b036269dd4aeed91cf8af811bd2f24faecbb98
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78171609"
---
# <a name="backup-server-capacity-planning-worksheet---parallel-data-warehouse"></a>Arbeitsblatt zur Kapazitätsplanung für Sicherungs Server-parallele Data Warehouse
Mithilfe dieses Arbeitsblatts zur Kapazitätsplanung können Sie die Anforderungen für einen Sicherungs Server für die Durchführung von SQL Server PDW Daten Bank Sicherungs-und Wiederherstellungs Vorgängen ermitteln. Verwenden Sie diese Informationen, um einen Plan für den Erwerb neuer oder vorhandener Sicherungs Server zu erstellen.

Dieses Arbeitsblatt ist eine Ergänzung zu den Anweisungen unter [erwerben und Konfigurieren eines Sicherungs Servers](acquire-and-configure-backup-server.md).

## <a name="capacity-planning-worksheet-for-backup-servers"></a>Arbeitsblatt zur Kapazitätsplanung für Sicherungs Server

### <a name="notes"></a>Notizen

1.  Dieses Arbeitsblatt gilt für Server, von denen Sicherungs-und Wiederherstellungs Vorgänge für PDW-Datenbanken durchgeführt werden.

2.  Die einzige Möglichkeit zum Sichern und Wiederherstellen von PDW-Datenbanken ist die Verwendung der SQL-Befehle Backup Database und RESTORE DATABASE. Wenn sich die Sicherungsdaten jedoch auf dem Sicherungs Server befinden, sind Sie als ein Satz von Windows-Dateien vorhanden. Sie können die Sicherungsdateien von Ihrem Server mithilfe herkömmlicher Windows-Datei basierter Sicherungsmethoden an einem anderen Speicherort archivieren.

### <a name="clipboard-icon-capacity-planning-worksheet"></a>![Zwischenablage Symbol](media/clipboard-icon.png "Zwischenablage Symbol") Arbeitsblatt zur Kapazitätsplanung 

Drucken Sie dieses Arbeitsblatt, und füllen Sie es mit ihren eigenen Anforderungen aus.

|Komponente|Anforderung|Füllen Sie diese Spalte mit ihren eigenen Anforderungen aus.|Empfehlungen|
|-------------|---------------|--------------------------------------------------|-------------------|
|Storage|Maximale Anzahl von Bytes, die Sie zu einem beliebigen Zeitpunkt auf dem Sicherungs Server speichern möchten.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Um die Speicheranforderungen zu ermitteln, ermitteln Sie, wie viele Daten Sie in einem beliebigen Zeitraum auf dem Sicherungs Server speichern möchten.<br /><br />Die Sicherungsdaten werden auf dem Sicherungs Server in komprimiertem Format gespeichert. Die Daten Komprimierungs Raten hängen von den Eigenschaften der Daten ab.<br /><br />Beispiel: als grobe Schätzung empfiehlt es sich, ein 7:1-Komprimierungs Verhältnis in Relation zur Größe ihrer nicht komprimierten Daten einzuschätzen. Dabei wird davon ausgegangen, dass mindestens 80% der Daten in gruppierten columnstore--Indizes gespeichert werden. Wenn Sie z. b. über 700 GB unkomprimierte Daten in einer Datenbank verfügen und in gruppierten columnstore--Indizes gespeichert sind, können Sie einschätzen, dass die Datenbanksicherung ungefähr 100 GB benötigt.<br /><br />Wenn Sie beabsichtigen, mehrere Kopien von Datenbanksicherungen auf dem Sicherungs Server zu haben, müssen Sie diese berücksichtigen.<br /><br />Beispiel: Wenn Sie planen, 10 Datenbanken zu sichern, die jeweils 5 TB unkomprimierter Daten enthalten, haben die Datenbanken eine kombinierte Größe von 50 TB. Wenn Sie beabsichtigen, diese 10 Datenbanken täglich für fünf Tage in einer Zeile zu sichern, beträgt die Gesamtgröße für die nicht komprimierte Größe 250 TB. Factoring bei einem 7:1-Komprimierungs Verhältnis benötigen Sie 250/7 = 35,7 TB Speicher auf dem Sicherungs Server. Es wird empfohlen, konservativ zu sein und ca. 30% zusätzliche Kapazität zu erhalten, um Abweichungen zu berücksichtigen und zu wachsen.  In diesem Beispiel wäre 46,6 TB besser.|
|Netzwerk|Der Netzwerk Verbindungstyp.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Bestimmen Sie den optimalen Netzwerk Verbindungstyp, der Ihren Anforderungen an die Lasten Raten gerecht werden kann.<br /><br />Beispiel: InfiniBand oder 10Gbit Ethernet bietet die optimalen Lade Raten. 1Gbit Ethernet schränkt die Last Raten auf 360 GB pro Stunde oder weniger ein.|
|E/A|Bytes pro Stunde für Schreibvorgänge.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Zum Schreiben von Sicherungen auf den Datenträger sind die Schreibgeschwindigkeiten von 4 TB pro Stunde optimal.<br /><br />Beispiel: bei Laufwerken, die 50 MB/Sek. schreiben können, benötigen Sie mindestens 24 Laufwerke und mehr für Spiegelung oder Parität.<br /><br />Berücksichtigen Sie für die e/a-Kapazität alle e/a-Vorgänge auf dem Lade Server. Wenn der Lade Server zusätzlich zu den Daten Auslastungen (z. b. beim Empfangen von Datendateien von einem ETL-Server) anderen e/a-Datenverkehr aufweist, werden die e/a-Anforderungen erhöht.|
|CPU|Anzahl der Sockets.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Das empfangen und Speichern von Sicherungsdateien ist keine CPU-intensive Anwendung.  Als Mindestanforderung empfiehlt sich die Verwendung eines vor kurzem hergestellten 2-Socket-Servers.|
|RAM|GB Arbeitsspeicher, der Windows das Zwischenspeichern von Dateien während des Ladevorgängen ermöglicht.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Zum empfangen und Speichern von Sicherungsdateien ist auf dem Lade Server sehr wenig RAM erforderlich.<br /><br />Informationen zum Ermitteln der RAM-Anforderungen finden Sie in der Windows Server-Installation und in den Anwendungsanforderungen von Drittanbietern. Es wird mindestens 32 GB empfohlen, wenn Sie keine Anforderungen aus anderen Quellen haben.|

Wenn Sie die Kapazitätsanforderungen festgelegt haben, kehren Sie zum Thema [erwerben und Konfigurieren eines Lade Servers](acquire-and-configure-loading-server.md) zurück, um Ihren Kauf zu planen.

## <a name="see-also"></a>Weitere Informationen
[Sicherung und Laden von Hardware](backup-and-loading-hardware.md)

