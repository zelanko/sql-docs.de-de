---
title: Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/21/2016
ms.prod: sql
ms.prod_service: table-view-index, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index types [SQL Server]
ms.assetid: 00863b10-e77c-44c5-8ac2-bb4ac454eec6
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 899bd7aada6364449fa71e9f87839447de73dedd
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "67909667"
---
# <a name="indexes"></a>Indizes
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

## <a name="available-index-types"></a>Verfügbare Indextypen
In der nachfolgenden Tabelle sind die Typen von Indizes aufgelistet, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügbar sind. Außerdem werden hier Links auf zusätzliche Informationen bereitgestellt.  
  
|Indextyp|BESCHREIBUNG|Zusätzliche Informationen|  
|----------------|-----------------|----------------------------|  
|Hash|Mit einem Hashindex erfolgt der Datenzugriff über eine Hashtabelle im Arbeitsspeicher. Hashindizes belegen einen festen Speicherplatz, dessen Größe eine Funktion der Bucketanzahl ist.|[Richtlinien für die Verwendung von Indizes für speicheroptimierte Tabellen](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)<br /><br /> [Hash Index Design Guidelines (Richtlinien zum Entwerfen von Hashindizes)](../../relational-databases/sql-server-index-design-guide.md#hash_index)|  
|Speicheroptimiert, nicht gruppiert|Bei speicheroptimierten, nicht gruppierten Indizes basiert die Arbeitsspeichernutzung auf der Zeilenanzahl und Größe der Indexschlüsselspalten.|[Richtlinien für die Verwendung von Indizes für speicheroptimierte Tabellen](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)<br /><br /> [Memory-Optimized Nonclustered Index Design Guideline (Richtlinien zum Entwerfen von speicheroptimierten, nicht gruppierten Indizes)](../../relational-databases/sql-server-index-design-guide.md#inmem_nonclustered_index)|  
|Gruppiert|In einem gruppierten Index werden die Datenzeilen der Tabelle oder Sicht basierend auf dem Schlüssel des gruppierten Indexes sortiert und gespeichert. Der gruppierte Index wird in Form einer B-Strukturindexstruktur implementiert, die das schnelle Abrufen der Zeilen unterstützt, basierend auf ihren Werten im gruppierten Index.|[Beschreibung von gruppierten und nicht gruppierten Indizes](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)<br /><br /> [Erstellen gruppierter Indizes](../../relational-databases/indexes/create-clustered-indexes.md)<br /><br /> [Clustered Index Design Guidelines (Richtlinien zum Entwerfen von gruppierten Indizes)](../../relational-databases/sql-server-index-design-guide.md#Clustered)|  
|Nicht gruppiert|Ein nicht gruppierter Index kann für eine Tabelle oder Sicht mit einem gruppierten Index bzw. für einen Heap definiert werden. Jede Indexzeile im nicht gruppierten Index enthält den nicht gruppierten Schlüsselwert und einen Zeilenlokator. Dieser Lokator verweist im gruppierten Index oder Heap auf die Datenzeile mit dem Schlüsselwert. Die Zeilen im Index werden in der Reihenfolge der Indexschlüsselwerte gespeichert, die Datenzeilen weisen jedoch nicht in jedem Fall eine bestimmte Reihenfolge auf, es sei denn, es wird ein gruppierter Index für die Tabelle erstellt.|[Beschreibung von gruppierten und nicht gruppierten Indizes](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)<br /><br /> [Erstellen nicht gruppierter Indizes](../../relational-databases/indexes/create-nonclustered-indexes.md)<br /><br /> [Nonclustered Index Design Guidelines (Richtlinien zum Entwerfen von nicht gruppierten Indizes)](../../relational-databases/sql-server-index-design-guide.md#Nonclustered)|  
|Eindeutig|Mit einem eindeutigen Index wird sichergestellt, dass der Indexschlüssel keine doppelten Werte enthält; jede Zeile in der Tabelle oder Sicht ist folglich eindeutig.<br /><br /> Eindeutigkeit kann eine Eigenschaft sowohl von gruppierten als auch von nicht gruppierten Indizes sein.|[Erstellen eindeutiger Indizes](../../relational-databases/indexes/create-unique-indexes.md)<br /><br /> [Unique Index Design Guidelines (Richtlinien zum Entwerfen von eindeutigen Indizes)](../../relational-databases/sql-server-index-design-guide.md#Unique)|  
|columnstore|Ein Columnstore-Index im Arbeitsspeicher speichert und verwaltet Daten durch die Verarbeitung von spaltenbasiertem Datenspeicher und spaltenbasierten Abfragen.<br /><br /> Columnstore-Indizes sind optimal für Data Warehousing-Arbeitsauslastungen geeignet, die hauptsächlich Massenladevorgänge und schreibgeschützte Abfragen ausführen. Verwenden Sie den Columnstore-Index, um eine bis zu **zehnfache Abfrageleistung** gegenüber der herkömmlichen zeilenorientierten Speicherung und eine bis zu **siebenfache Datenkomprimierung** im Vergleich zur unkomprimierten Datengröße zu erzielen.|[Beschreibung von Columnstore-Indizes](../../relational-databases/indexes/columnstore-indexes-overview.md)<br /><br /> [Columnstore Index Design Guidelines (Richtlinien zum Entwerfen von Columnstore-Indizes)](../../relational-databases/sql-server-index-design-guide.md#columnstore_index)|  
|Index mit eingeschlossenen Spalten|Ein nicht gruppierter Index, der dahingehend erweitert wird, dass er neben Schlüsselspalten auch Nichtschlüsselspalten enthält.|[Erstellen von Indizes mit eingeschlossenen Spalten](../../relational-databases/indexes/create-indexes-with-included-columns.md)|  
|Index in berechneten Spalten|Ein Index für eine Spalte, die vom Wert anderer Spalten abgeleitet wird, oder bestimmte deterministische Eingaben.|[Indizes in berechneten Spalten](../../relational-databases/indexes/indexes-on-computed-columns.md)|  
|Filtered|Ein optimierter nicht gruppierter Index, der sich besonders für Abfragen eignet, bei denen aus einer fest definierten Teilmenge von Daten ausgewählt wird. Dieser verwendet ein Filterprädikat, um einen Teil der Zeilen in der Tabelle zu indizieren. Mit einem sorgfältig entworfenen gefilterten Index können im Gegensatz zu Tabellenindizes die Abfrageleistung verbessert und der Aufwand für die Indexverwaltung und -speicherung reduziert werden.|[Erstellen gefilterter Indizes](../../relational-databases/indexes/create-filtered-indexes.md)<br /><br /> [Filtered Index Design Guidelines (Richtlinien zum Entwerfen von gefilterten Indizes)](../../relational-databases/sql-server-index-design-guide.md#Filtered)|  
|Spatial|Mit einem räumlichen Index können bestimmte Vorgänge an räumlichen Objekten (*räumliche Daten*) in einer Spalte vom Datentyp **geometry** effizienter ausgeführt werden. Der räumliche Index verringert die Anzahl von Objekten, auf die relativ aufwendige räumliche Vorgänge angewendet werden müssen.|[Übersicht über räumliche Indizes](../../relational-databases/spatial/spatial-indexes-overview.md)|  
|XML|Eine aufgeteilte und dauerhafte Darstellung der XML-BLOBS (Binary Large Objects) in der **XML**-Datentypspalte.|[XML-Indizes &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)|  
|Volltext|Ein besonderer Typ eines tokenbasierten funktionellen Indexes, der durch die Microsoft-Volltext-Engine für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt und verwaltet wird. Er stellt effiziente Unterstützung für komplexe Wortsuchvorgänge in Zeichenfolgendaten bereit.|[Auffüllen von Volltextindizes](../../relational-databases/search/populate-full-text-indexes.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Handbuch zum SQL Server Indexentwurf](../../relational-databases/sql-server-index-design-guide.md)      
 [SORT_IN_TEMPDB-Option für Indizes](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md)     
 [Deaktivieren von Indizes und Einschränkungen](../../relational-databases/indexes/disable-indexes-and-constraints.md)     
 [Aktivieren von Indizes und Einschränkungen](../../relational-databases/indexes/enable-indexes-and-constraints.md)    
 [Umbenennen von Indizes](../../relational-databases/indexes/rename-indexes.md)     
 [Festlegen von Indexoptionen](../../relational-databases/indexes/set-index-options.md)     
 [Speicherplatzanforderungen für Index-DDL-Vorgänge](../../relational-databases/indexes/disk-space-requirements-for-index-ddl-operations.md)     
 [Neuorganisieren und Neuerstellen von Indizes](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)     
 [Angeben des Füllfaktors für einen Index](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)     
 [Handbuch zur Architektur von Seiten und Blöcken](../../relational-databases/pages-and-extents-architecture-guide.md)     
 [Beschreibung von gruppierten und nicht gruppierten Indizes](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)     
  
