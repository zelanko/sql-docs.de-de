---
title: Laden der Server Kapazitätsplanung
description: Mithilfe dieses Arbeitsblatts zur Kapazitätsplanung können Sie die Anforderungen für einen Lade Server zum Laden von Daten in das Data Warehouse für das Analyse-Platt Form System ermitteln. "
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 1d2c3f1c0366d2c7d3d9efe700d9cfccc688dbc9
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78171599"
---
# <a name="loading-server-capacity-planning-worksheet-for-analytics-platform-system"></a>Laden des Arbeitsblatts für die Server Kapazitätsplanung für Analytics Platform System
Mithilfe dieses Arbeitsblatts zur Kapazitätsplanung können Sie die Anforderungen für einen Lade Server zum Laden von Daten in SQL Server PDW ermitteln. Verwenden Sie diese Informationen, um Ihren Plan für den Erwerb oder die Bereitstellung vorhandener Lade Server zu erstellen.

## <a name="worksheet-notes"></a>Arbeitsblatt Hinweise

1.  Dieses Arbeitsblatt gilt für Server, die Daten mit dem Befehlszeilen-Lade Tool **"dwloader** laden.

2.  Zum Laden von Daten mit Integration Services oder einem Tool zum Laden von Drittanbietern können die Anforderungen abhängig von den Unterschieden beim Ladevorgang variieren.

3.  Die meisten der Anforderungen gelten für das Laden von komprimierten oder nicht komprimierten Datendateien. alle Unterschiede in den Anforderungen werden fett dargestellt.

## <a name="clipboard-capacity-planning-worksheet"></a>![Zwischenablage](media/clipboard-icon.png "Zwischenablage") Arbeitsblatt zur Kapazitätsplanung

Drucken Sie dieses Arbeitsblatt, und füllen Sie es mit ihren eigenen Anforderungen aus.

|Komponente|Anforderung|Füllen Sie diese Spalte mit ihren eigenen Anforderungen aus.|Empfehlungen|
|-------------|---------------|--------------------------------------------------|-------------------|
|Storage|Maximale Anzahl von Bytes, die Sie zu einem beliebigen Zeitpunkt auf dem Lade Server speichern möchten.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Um die Speicheranforderungen zu ermitteln, ermitteln Sie, wie viele Daten Sie in einem beliebigen Zeitraum auf dem Lade Server speichern möchten.  Kapazitätsanforderungen gelten nur für das Laden von Dateien; das Betriebssystem und die Auslastungs Dateien müssen sich auf unterschiedlichen Datenträger Arrays befinden.<br /><br />Wenn Sie z. b. Vorhaben, 100 GB Daten von dem Datenträger dreimal täglich zu laden, aber die Datendateien bis zum Ende der Woche nicht zu löschen, benötigen Sie mindestens 2,1 TB, um die Datendateien zu speichern. Es wird empfohlen, konservativ zu sein und ca. 30% mehr Speicher zu erhalten, um Abweichungen und Wachstum zu berücksichtigen.  In diesem Beispiel sind 2,73 TB Speicherplatz besser.|
|Auslastungs Rate|Maximale Anzahl von Bytes pro Stunde zum Laden von Daten in PDW.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Dies ist eine Schätzung. Wenn Sie diese Anforderung berechnen, gehen Sie davon aus, dass sich die Dateien bereits auf dem Lade Server befinden und dass andere Ladebedingungen so gut wie möglich sind.<br /><br />Beispiel: Es ist nicht erforderlich, die Datenkomprimierung zu berücksichtigen, da "dwloader immer unkomprimierte Daten an das PDW sendet. Es ist nicht erforderlich, die Datentyp Konvertierungen und die Größe der Ziel Tabelle zu berücksichtigen.|
|Netzwerk|Der Netzwerk Verbindungstyp.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Bestimmen Sie den optimalen Netzwerk Verbindungstyp für Ihre Anforderungen an die Auslastungsrate.<br /><br />Beispiel: InfiniBand oder 10 Gbit Ethernet bietet die optimalen Lade Raten. mit 1 Gbit-Ethernet werden die Auslastungsraten auf 360 GB pro Stunde oder weniger beschränkt.|
|E/A|Bytes pro Stunde für Lese-und Schreibvorgänge.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Zum Laden von Daten muss "dwloader alle Daten vom Datenträger lesen, bevor es an PDW gesendet wird.<br /><br />Jeder Lade Server kann Daten schneller laden, als die Appliance Daten von allen Lade Quellen empfangen kann. Um Geld zu sparen, planen Sie die e/a-Lesekapazität für den Ladevorgang so, dass die Ladekapazität des Geräts nicht überschritten wird.<br /><br />Beispiel:<br />PDW empfängt und lädt Daten mit einer maximalen Rate von 1,8 TB pro Stunde in eine 1-Rack-Appliance. Bei einer Appliance mit mindestens zwei Racks beträgt die maximale Auslastungsrate 3,6 TB pro Stunde.<br /><br />Wenn Sie planen, gleichzeitig von mehreren Lade Servern zu laden, sind die e/a-Anforderungen für die einzelnen Lade Server kleiner, als ein Server den gesamten Ladevorgang durchführt.<br /><br />Beispiel: ein Lade Server kann für ein Gerät mit 1 Rack maximal 1,8 TB pro Stunde laden. Zwei Lade Server können gleichzeitig 900 GB pro Stunde in ein 1-Rack-Gerät laden. Ein höheres Maß an Parallelität kann die Effizienz und den maximalen Durchsatz verringern.<br /><br />Berücksichtigen Sie für die e/a-Kapazität alle e/a-Vorgänge auf dem Lade Server. Wenn der Lade Server zusätzlich zu den Daten Auslastungen (z. b. beim Empfangen von Datendateien von einem ETL-Server) anderen e/a-Datenverkehr aufweist, werden die e/a-Anforderungen erhöht.<br /><br />Bei komprimierten Daten sind die e/a-Anforderungen abhängig von der datenkomprimierungsrate. die komprimierten Daten werden von "dwloader gelesen und dann vor dem Senden an den PDW deinstalkomprimiert. Je höher das Komprimierungs Verhältnis, desto weniger Daten müssen vom Lade Server vom Datenträger gelesen werden.<br /><br />Wenn die erforderliche Auslastungsrate z. b. 1,8 TB pro Stunde beträgt und die Daten auf dem Lade Server mit 2:1-Komprimierung gespeichert sind, muss der Lade Server nur 900 GB pro Stunde von der Festplatte anstelle von 1,8 TB lesen. Das Komprimierungs Verhältnis 3:1 bedeutet, dass der Lade Server 600 GB pro Stunde vom Datenträger lesen muss.|
|CPU|Anzahl der Sockets.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|Zum Laden von nicht komprimierten Daten ist "dwloader keine CPU-intensive Anwendung.  Als Mindestanforderung empfiehlt sich die Verwendung eines vor kurzem hergestellten 2-Socket-Servers.<br /><br />Zum Laden von komprimierten Daten benötigen Sie genügend CPU-Leistung, um die Daten vor dem Senden an PDW zu komprimieren. "dwloader kann 10 aktive Threads gleichzeitig ausführen. Wenn Sie 10 komprimierte Dateien gleichzeitig laden möchten, wird empfohlen, dass der Server über mindestens eine 10-Kern-CPU oder zwei CPUs mit 6 Kernen verfügt.|
|RAM|GB Arbeitsspeicher, der Windows das Zwischenspeichern von Dateien während des Ladevorgängen ermöglicht.|![Stiftsymbol](media/pencil-icon.png "Stiftsymbol")|"dwloader verwendet sehr wenig RAM auf dem Lade Server. Aus Leistungsgründen verwendet Windows Speicher, um die Dateien zu speichern, nachdem Sie vom Datenträger gelesen wurden.<br /><br />Informationen zum Ermitteln der RAM-Anforderungen finden Sie in der Windows Server-Installation und in den Anwendungsanforderungen von Drittanbietern. Es wird mindestens 32 GB empfohlen, wenn Sie keine Anforderungen aus anderen Quellen haben.<br /><br />Bei komprimierten Daten ist schnellerer RAM nützlich, da die Komprimierung beschleunigt werden kann.|

## <a name="see-also"></a>Weitere Informationen
[Abrufen und Konfigurieren eines Ladevorgangs für ein Lade Server](acquire-and-configure-loading-server.md)
[-"dwloader-Befehlszeilen Lade](dwloader.md) Modul

