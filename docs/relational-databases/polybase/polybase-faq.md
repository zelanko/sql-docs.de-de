---
title: Häufig gestellte Fragen zu PolyBase | Microsoft-Dokumentation
ms.date: 04/23/2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
ms.reviewer: mikeray
manager: craigg
ms.openlocfilehash: 0d2afed9961881fe46ae9fcd4ebe2441910deee7
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67730322"
---
# <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

## <a name="polybase-vs-linked-servers"></a>PolyBase im Vergleich zu Verbindungsservern
In der folgenden Tabelle werden die Unterschiede zwischen PolyBase und Verbindungsserverfunktionen hervorgehoben:

|PolyBase | Verbindungsserver|
|--------------------------|--------------------------|  
|Datenbankweites Objekt|Instanzweites Objekt|
|Verwendet ODBC-Treiber.|Verwendet OLEDB-Anbieter.|
|Unterstützt schreibgeschützte Vorgänge für alle Datenquellen und Einfügevorgänge nur für HADOOP- und Datenpool-Datenquellen|Unterstützt sowohl Lese- als auch Schreibvorgänge|
|Abfragen einer Remotedatenquelle über eine einzige Verbindung lassen sich horizontal skalieren |Abfragen einer Remotedatenquelle über eine einzige Verbindung lassen sich nicht horizontal skalieren|
|Weitergabe von Prädikaten wird unterstützt|Weitergabe von Prädikaten wird unterstützt|
|Es ist keine separate Konfiguration für die Verfügbarkeitsgruppe erforderlich|Es ist eine separate Konfiguration für jede Instanz in der Verfügbarkeitsgruppe erforderlich|
|Nur Standardauthentifizierung|Standard- und integrierte Authentifizierung|
|Geeignet für Analyseabfragen, die eine große Anzahl von Zeilen verarbeiten|Geeignet für OLTP-Abfragen, die einzelne oder wenige Zeilen zurückgeben|
|Abfragen, die externe Tabellen verwenden, können nicht an der verteilten Transaktion teilnehmen|Verteilte Abfragen können an verteilter Transaktion teilnehmen|

## <a name="whats-new-in-polybase-2019"></a>Neuerungen in PolyBase 2019 

PolyBase in [!INCLUDE[sssqlv15](../../includes/sssqlv15-md.md)] kann ab sofort Daten aus vielen verschiedenen Datenquellen lesen. Die Daten aus diesen externen Datenquellen können als externe Tabellen auf Ihrer SQL Server-Instanz gespeichert werden. Zudem unterstützt PolyBase die Berechnungsweitergabe für diese externen Datenquellen, mit Ausnahme von generischen ODBC-Typen.

### <a name="compatible-data-sources"></a>Kompatible Datenquellen

- SQL Server
- Oracle
- Teradata
- MongoDB
- Kompatible generische ODBC-Typen
  
> [!NOTE]
> Mit PolyBase sind jetzt Verbindungen zu externen Datenquellen über ODBC-Treiber von Drittanbietern möglich. Diese Treiber sind nicht im Lieferumfang von PolyBase enthalten und funktionieren ggf. nicht wie vorgesehen. Weitere Informationen finden Sie in unserer [Anleitung](../../relational-databases/polybase/polybase-configure-odbc-generic.md) zur generischen ODBC-Konfiguration in PolyBase.  

## <a name="polybase-in-big-data-clusters-vs-polybase-in-stand-alone-instances"></a>PolyBase in Big Data-Clustern im Vergleich zu PolyBase in eigenständigen Instanzen

Die folgende Tabelle zeigt die Features von PolyBase, die in der eigenständigen Installation von [!INCLUDE[sssqlv15](../../includes/sssqlv15-md.md)] und im Big Data-Cluster von [!INCLUDE[sssqlv15](../../includes/sssqlv15-md.md)] verfügbar sind:

|Funktion |Big Data-Cluster|Eigenständige Instanz|
|--------------------------|--------------------------|---------|   
|Erstellen einer externen Datenquelle für SQL Server, Oracle, Teradata und Mongo DB |X|X |
|Erstellen einer externe Datenquelle mit einem kompatiblen ODBC-Treibers eines Drittanbieters | | X|
|Erstellen einer externen Datenquelle für Hadoop-Datenquelle | X| X|
|Erstellen einer externen Datenquelle für Azure Blob Storage | X| X|
|Erstellen einer externen Tabelle für einen SQL Server-Datenpool | X| |
|Erstellen einer externen Tabelle für einen SQL Server-Speicherpool | X| |
|Horizontale Skalierung der Abfrageausführung | X| X|

> [!NOTE]
>In der Tabelle ist nicht die Funktionalität beschrieben, die im neuesten [!INCLUDE[sssqlv15](../../includes/sssqlv15-md.md)] CTP verfügbar ist. Die verfügbaren Funktionen finden Sie in den Versionshinweisen. Weitere Informationen zu Verbindungen mit dem generischen ODBC-Connector finden Sie in unserer [Anleitung zum Konfigurieren von generischen ODBC-Datentypen](polybase-configure-odbc-generic.md).