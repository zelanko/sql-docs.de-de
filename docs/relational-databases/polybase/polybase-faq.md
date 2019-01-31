---
title: Häufig gestellte Fragen zu PolyBase | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
manager: ''
ms.openlocfilehash: 331ac177831b1e07cfab253c363a35f2bab42a6c
ms.sourcegitcommit: ee76381cfb1c16e0a063315c9c7005f10e98cfe6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2019
ms.locfileid: "55072878"
---
# <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

## <a name="polybase-in-big-data-clusters-vs-polybase-in-stand-alone-instances"></a>PolyBase in Big Data-Clustern im Vergleich zu PolyBase in eigenständigen Instanzen

|Funktion |Big Data-Cluster| Eigenständige Instanz|
|--------------------------|--------------------------|---------|   
|Erstellen externer Tabellen| X| X|
|Erstellen einer externen Datenquelle aus SQL Server, Oracle, Teradata und Mongo DB |X|X |
|Erstellen einer externe Datenquelle mit einem kompatiblen ODBC-Treibers eines Drittanbieters | | X|
|PolyBase-Erweiterungsgruppen | X | |
|Datenpoolinstanzen | X| |
|Speicherpoolinstanzen| X| |

>[!NOTE]
>
>Weitere Informationen zu Verbindungen mit dem generischen ODBC-Connector finden Sie in unserer [Anleitung zum Konfigurieren von generischen ODBC-Datentypen](polybase-configure-odbc-generic.md).

## <a name="whats-new-with-polybase-in-sql-server-2019"></a>Neuigkeiten bei PolyBase in SQL Server 2019 

PolyBase in SQL Server 2019 kann ab sofort Daten aus vielen verschiedenen Datenquellen lesen. Die Daten aus diesen externen Datenquellen können als externe Tabellen auf Ihrer SQL Server-Instanz gespeichert werden. Zudem unterstützt PolyBase die Berechnungsweitergabe für diese externen Datenquellen, mit Ausnahme von generischen ODBC-Typen. 

### <a name="compatible-data-sources"></a>Kompatible Datenquellen

- SQL Server
- Oracle
- Teradata
- MongoDB
- **Kompatible** generische ODBC-Typen

  > [!NOTE]
  >
  >Mit PolyBase sind jetzt Verbindungen zu externen Datenquellen über ODBC-Treiber von Drittanbietern möglich. Diese Treiber sind nicht im Lieferumfang von PolyBase enthalten und können wie vorgesehen funktionieren. Weitere Informationen finden Sie in unserer [Anleitung](polybase-configure-odbc-generic.md) zur generischen ODBC-Konfiguration in PolyBase.  

## <a name="polybase-vs-linked-servers"></a>PolyBase im Vergleich zu Verbindungsservern

|PolyBase | Verbindungsserver|
|--------------------------|--------------------------|  
|Datenbankweites Objekt|Instanzweites Objekt| 
|Verwendet ODBC-Treiber.|Verwendet OLEDB-Anbieter.| 
| Unterstützt nur schreibgeschützte Vorgänge. Wird künftig erweitert.| Unterstützt nur schreibgeschützte Vorgänge. Wird künftig erweitert.| 
|Eine horizontale Skalierung von Abfragen und die Berechnungsweitergabe werden unterstützt.|Singlethreadabfragen und die Berechnungsweitergabe werden unterstützt.|
|Es ist keine separate Konfiguration für Always On-Verfügbarkeitsgruppe erforderlich.|Es ist eine separate Konfiguration für jede Instanz in Always On-Verfügbarkeitsgruppe erforderlich.|
|Nur Standardauthentifizierung. Verbesserungen in SQL Server 2019|Grundlegende und integrierte Authentifizierung|