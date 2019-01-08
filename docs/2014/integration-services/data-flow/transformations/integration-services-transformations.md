---
title: SQL Server Integration Services-Transformationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transformations [Integration Services], listed
- transformations [Integration Services], types
- transformations [Integration Services]
- data flow [Integration Services], transformations
- business intelligence transformations [Integration Services]
- join transformations
- split transformations [Integration Services]
- custom transformations [Integration Services]
- row transformations [Integration Services]
- rowset transformations [Integration Services]
ms.assetid: c70c4f6e-82dd-4948-b923-fd5193f67f7e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 76157486751a08d17cf46de312f63e6e41dc3cb1
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52785232"
---
# <a name="integration-services-transformations"></a>SQL Server Integration Services-Transformationen
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Transformationen handelt es sich um die Komponenten im Datenfluss eines Pakets, mit denen Daten aggregiert, zusammengeführt, verteilt und geändert werden. Mit Transformationen können auch Suchvorgänge ausgeführt und Stichprobendatasets generiert werden. In diesem Abschnitt werden die Transformationen von [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] beschrieben. Darüber hinaus wird deren Funktionsweise erklärt.  
  
## <a name="business-intelligence-transformations"></a>Business Intelligence-Transformationen  
 Die folgenden Transformationen führen Business Intelligence-Vorgänge aus, wie z. B. das Bereinigen von Daten, Text Mining und das Ausführen von Data Mining-Vorhersageabfragen.  
  
|Transformation|Description|  
|--------------------|-----------------|  
|[Transformation für langsam veränderliche Dimensionen](slowly-changing-dimension-transformation.md)|Diese Transformation konfiguriert das Aktualisieren einer langsam veränderlichen Dimension.|  
|[Transformation für Fuzzygruppierung](fuzzy-grouping-transformation.md)|Diese Transformation standardisiert Werte in Spaltendaten.|  
|[Transformation für Fuzzysuche](lookup-transformation.md)|Diese Transformation sucht Werte in einer Verweistabelle mithilfe einer Fuzzyübereinstimmung.|  
|[Transformation für Ausdrucksextrahierung](term-extraction-transformation.md)|Diese Transformation extrahiert Ausdrücke aus dem Text.|  
|[Transformation für Ausdruckssuche](term-lookup-transformation.md)|Diese Transformation sucht Ausdrücke in einer Verweistabelle und zählt die aus dem Text extrahierten Ausdrücke.|  
|[Transformation für Data Mining-Abfragen](data-mining-query-transformation.md)|Diese Transformation führt Data Mining-Vorhersageabfragen aus.|  
|[DQS-Bereinigungstransformation](dqs-cleansing-transformation.md)|Diese Transformation korrigiert die Daten einer verbundenen Datenquelle durch Anwenden von Regeln, die für die Datenquelle erstellt wurden.|  
  
## <a name="row-transformations"></a>Zeilentransformationen  
 Mit den folgenden Transformationen werden Spaltenwerte aktualisiert und neue Spalten erstellt. Die Transformation wird auf jede Zeile in der Transformationseingabe angewendet.  
  
|Transformation|Description|  
|--------------------|-----------------|  
|[Transformation zum Zuordnen der Zeichen](character-map-transformation.md)|Diese Transformation wendet Zeichenfolgenfunktionen auf Zeichendaten an.|  
|[Transformation für das Kopieren von Spalten](copy-column-transformation.md)|Diese Transformation fügt der Transformationsausgabe Kopien von Eingabespalten hinzu.|  
|[Transformation für Datenkonvertierung](data-conversion-transformation.md)|Diese Transformation konvertiert den Datentyp einer Spalte in einen anderen Datentyp.|  
|[Transformation für abgeleitete Spalten](derived-column-transformation.md)|Diese Transformation füllt Spalten mit den Ergebnissen von Ausdrücken auf.|  
|[Transformation für das Exportieren von Spalten](export-column-transformation.md)|Diese Transformation fügt Daten aus einem Datenfluss in eine Datei ein.|  
|[Transformation für das Importieren von Spalten](import-column-transformation.md)|Diese Transformation liest Daten aus einer Datei und fügt sie einem Datenfluss hinzu.|  
|[Skriptkomponente](script-component.md)|Diese Transformation verwendet ein Skript zum Extrahieren, Transformieren oder Laden von Daten.|  
|[Transformation für OLE DB-Befehl](ole-db-command-transformation.md)|Diese Transformation führt SQL-Befehle für jede Zeile in einem Datenfluss aus.|  
  
## <a name="rowset-transformations"></a>Rowsettransformationen  
 Mit den folgenden Transformationen werden neue Rowsets erstellt. Rowsets schließen Aggregatwerte und sortierte Werte, Stichprobenrowsets oder pivotierte bzw. nicht pivotierte Rowsets ein.  
  
|Transformation|Description|  
|--------------------|-----------------|  
|[Transformation für das Aggregieren](aggregate-transformation.md)|Diese Transformation führt Aggregationen aus, wie z. B. AVERAGE, SUM und COUNT.|  
|[Transformation zum Sortieren](sort-transformation.md)|Diese Transformation sortiert Daten.|  
|[Transformation für Prozentwert-Stichproben](percentage-sampling-transformation.md)|Diese Transformation erstellt ein Stichprobendataset mithilfe eines Prozentwerts, um die Stichprobengröße anzugeben.|  
|[Transformation für Zeilenstichproben](row-sampling-transformation.md)|Diese Transformation erstellt ein Stichprobendataset, indem die Anzahl von Zeilen in der Stichprobe angegeben wird.|  
|[Transformation für Pivot](pivot-transformation.md)|Diese Transformation erstellt eine weniger normalisierte Version einer normalisierten Tabelle.|  
|[Entpivotierungstransformation](unpivot-transformation.md)|Diese Transformation erstellt eine stärker normalisierte Version einer nicht normalisierten Tabelle.|  
  
## <a name="split-and-join-transformations"></a>Transformationen für Teilen und Verknüpfen  
 Mit den folgenden Transformationen werden Zeilen an verschiedene Ausgaben verteilt, Kopien der Transformationseingaben erstellt, mehrere Eingaben zu einer einzigen Ausgabe verknüpft sowie Suchvorgänge ausgeführt.  
  
|Transformation|Description|  
|--------------------|-----------------|  
|[Transformation für bedingtes Teilen](conditional-split-transformation.md)|Diese Transformation routet Datenzeilen an andere Ausgaben.|  
|[Transformation für Multicast](multicast-transformation.md)|Diese Transformation verteilt Datasets an mehrere Ausgaben.|  
|[Transformation für UNION ALL](union-all-transformation.md)|Diese Transformation führt mehrere Datasets zusammen.|  
|[Transformation für Zusammenführen](merge-transformation.md)|Diese Transformation führt zwei sortierte Datasets zusammen.|  
|[Transformation für Zusammenführungsjoin](merge-join-transformation.md)|Diese Transformation verknüpft zwei Datasets mithilfe eines FULL-, LEFT- oder INNER-Joins.|  
|[Transformation für Suche](lookup-transformation.md)|Diese Transformation sucht Werte in einer Verweistabelle mithilfe einer genauen Übereinstimmung.|  
|[Cachetransformation](cache-transform.md)|Die Transformation, die Daten aus einer verbundenen Datenquelle im Datenfluss in einen Cacheverbindungs-Manager schreibt, der die Daten in einer Cachedatei speichert. Die Transformation für Suche führt Suchvorgänge in den Daten der Cachedatei aus.|  
|[Balanced Data Distributor (BDD)-Transformation](balanced-data-distributor-transformation.md)|Die Transformation verteilt Puffer mit eingehenden Zeilen gleichmäßig auf Ausgaben für separate Threads, um die Leistung von SSIS-Paketen zu verbessern, die auf Mehrkern- und Mehrprozessorservern ausgeführt werden.|  
  
## <a name="auditing-transformations"></a>Überwachen von Transformationen  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] enthält die folgenden Transformationen, um Überwachungsinformationen hinzuzufügen und Zeilen zu zählen.  
  
|Transformation|Description|  
|--------------------|-----------------|  
|[Überwachungstransformation](audit-transformation.md)|Diese Transformation stellt dem Datenfluss in einem Paket Informationen zur Umgebung zur Verfügung.|  
|[Transformation für Zeilenanzahl](row-count-transformation.md)|Diese Transformation zählt die Zeilen in einem Datenfluss und speichert die endgültige Anzahl in einer Variablen.|  
  
## <a name="custom-transformations"></a>Benutzerdefinierte Transformationen  
 Sie können auch benutzerdefinierte Transformationen erstellen. Weitere Informationen finden Sie unter [Entwickeln einer benutzerdefinierten Transformationskomponente mit synchronen Ausgaben](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md) und [Entwickeln einer benutzerdefinierten Transformationskomponente mit asynchronen Ausgaben](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md).  
  
  
