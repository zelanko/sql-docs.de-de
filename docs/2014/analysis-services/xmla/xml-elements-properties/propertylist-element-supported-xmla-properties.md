---
title: Unterstützte XMLA-Eigenschaften (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- properties [XML for Analysis]
- XML for Analysis, properties
- XMLA, properties
ms.assetid: 5745f7b4-6b96-44d5-b77c-f2831a898e5e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7d7898c0f7263bf5355934ec072511bfd8483028
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48215920"
---
# <a name="supported-xmla-properties-xmla"></a>Unterstützte XMLA-Eigenschaften (XMLA)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] die in der folgenden Tabelle aufgeführten Servereigenschaften unterstützt. Sie verwenden diese aufgelisteten Eigenschaften in der [Eigenschaften](properties-element-xmla.md) Element der [Discover](../xml-elements-methods-discover.md) und [Execute](../xml-elements-methods-execute.md) Methoden.  
  
|Name|Element|  
|----------|-------------|  
|AxisFormat|*Verwendung*<br /> Optionale, lesegeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Bestimmt das Format, die innerhalb einer [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) Resultset, das die Achsen des mehrdimensionalen Datasets beschreiben. Diese Eigenschaft kann einen der in der folgenden Tabelle aufgeführten Werte haben.|  
  
|value|Description|  
|-----------|-----------------|  
|*' Clusterformat '*|Die `MDDataSet` Achse besteht aus einem oder mehreren [CrossProduct](crossproduct-element-xmla.md) Elemente.|  
|*CustomFormat*|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verwendet die *TupleFormat* Format dieser Einstellung.|  
|*' TupleFormat '*|(Standard) Die `MDDataSet` Achse enthält ein oder mehrere [Tupel](tuple-element-xmla.md) Elemente.|  
  
 Diese Eigenschaft kann mit der `Execute`-Methode verwendet werden.  
  
|Name|Element|  
|----------|-------------|  
|BeginRange|*Verwendung*<br /> Optionale, lesegeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Enthält einen nullbasierten ganzzahligen Wert, der einem `CellOrdinal`-Attributwert entspricht. (Die `CellOrdinal` Attribut ist Bestandteil der [Zelle](cell-element-mddataset-xmla.md) Element in der [CellData](celldata-element-xmla.md) Teil `MDDataSet`.)<br /><br /> In Verwendung mit der `EndRange`-Eigenschaft kann die Clientanwendung diese Eigenschaft nutzen, um einen OLAP-Dataset einzuschränken, der durch einen Befehl zu einem bestimmten Zellbereich zurückgegeben wurde. Wenn -1 angegeben ist, werden alle Zellen bis zu der Zelle, die in der `EndRange`-Eigenschaft festgelegt ist, zurückgegeben.<br /><br /> Der Standardwert für diese Eigenschaft ist-1.<br /><br /> Diese Eigenschaft kann mit der `Execute`-Methode verwendet werden.|  
|Katalog|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Beim Aufbau einer Sitzung mit einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz für das Senden eines XMLA-Befehls entspricht diese Eigenschaft der OLE DB-Eigenschaft DBPROP_INIT_CATALOG.<br /><br /> Wenn Sie diese Eigenschaft während einer Sitzung einrichten, um die aktuelle Datenbank für die Sitzung zu ändern, entspricht diese Eigenschaft der OLE DB-Eigenschaft DBPROP_CURRENTCATALOG.<br /><br /> Der Standardwert für diese Eigenschaft ist eine leere Zeichenfolge.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|CatalogLocation|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_CATALOGLOCATION.<br /><br /> Der Standardwert für diese Eigenschaft ist null (0). Dies entspricht DBPROPVAL_CL_START.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|ClientProcessID|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Enthält den Bezeichner (ID) des Prozessthreads für die aktuelle Sitzung.<br /><br /> Der Standardwert dieser Eigenschaft ist null (0).<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|CommitTimeout|*Verwendung*<br /> Optionale, lesegeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Bestimmt, wie lange in Sekunden die Commitphase eines derzeit laufenden XMLA-Befehls wartet, bevor ein Rollback eintritt. Die Commitphase entspricht XMLA-Befehlen wie z. B. [Anweisung](../xml-elements-commands/statement-element-xmla.md) oder [Prozess](../xml-elements-commands/process-element-xmla.md).<br /><br /> Der Wert null (0) gibt an, dass die Instanz unbegrenzt wartet.<br /><br /> Der Standardwert dieser Eigenschaft ist null (0).<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|Inhalt|*Verwendung*<br /> Optionale, lesegeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Bestimmt den Typ von Daten, die von den Methoden `Discover` und `Execute` zurückgegeben werden. Diese Eigenschaft kann einen der in der folgenden Tabelle aufgeführten Werte haben.|  
  
|value|Description|  
|-----------|-----------------|  
|*Keine*|Ermöglicht die Überprüfung der Struktur des Befehls, aber nicht die Ausführung.|  
|*Schema*|Gibt das XML-Schema zurück, das sich auf den angeforderten Befehl bezieht. Das XML-Schema gibt Spalten und andere Informationen an.|  
|*Daten*|Gibt nur die Daten zurück, die angefordert wurden.|  
|*SchemaData*|(Standard) gibt die Schemainformationen und die Daten zurück.|  
  
 Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.  
  
|Name|Element|  
|----------|-------------|  
|Cube|*Verwendung*<br /> Optionale, lesegeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Enthält den Namen des Cubes, der den Kontext für den Befehl festlegt. Wenn der Befehl selbst einen Cubenamen, wie z. B. in der FROM-Klausel von einer MDX (Multidimensional Expressions) enthält [wählen](/sql/mdx/mdx-data-manipulation-select) -Anweisung, die Einstellung dieser Eigenschaft wird ignoriert.<br /><br /> Der Standardwert für diese Eigenschaft ist eine leere Zeichenfolge.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DataSourceInfo|*Verwendung*<br /> Erforderliche `String`-Eigenschaft mit Lese-/Schreibzugriff<br /><br /> *Beschreibung*<br /> Enthält die Informationen, beispielsweise den Instanznamen, die erforderlich sind, um eine Verbindung mit der Datenquelle herzustellen.<br /><br /> Clientanwendungen sollten den Inhalt der `DataSourceInfo`-Eigenschaft nicht erstellen, um zu einer Instanz zu senden. Stattdessen sollte die Clientanwendung mithilfe von vom Anbieter unterstützten Datenquellen finden die `Discover` Methode zum Abrufen der [DISCOVER_DATASOURCES](../../schema-rowsets/xml/discover-datasources-rowset.md) Rowset. Die Clientanwendung sendet dann den gleichen Wert für die `DataSourceInfo`-Eigenschaft zurück, die der Client vom DISCOVER_DATASOURCES-Rowset abgerufen hat.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropCatalogTerm|*Verwendung*<br /> Optionale, schreibgeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_CATALOGTERM.<br /><br /> Der Standardwert dieser Eigenschaft ist "Database".<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropCatalogUsage|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_CATALOGUSAGE.<br /><br /> Der Standardwert dieser Eigenschaft ist null (0).<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropColumnDefinition|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_COLUMNDEFINITION.<br /><br /> Der Standardwert dieser Eigenschaft ist null (0).<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropConcatNullBehavior|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_CONCATNULLBEHAVIOR.<br /><br /> Der Standardwert für diese Eigenschaft ist 1. Dies entspricht DBPROPVAL_CB_NULL.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropDataSourceReadOnly|*Verwendung*<br /> Optionale, schreibgeschützte `Boolean` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_DATASOURCEREADONLY.<br /><br /> Der Standardwert für diese Eigenschaft ist FALSE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropGroupBy|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_GROUPBY.<br /><br /> Der Standardwert für diese Eigenschaft ist 2. Dies entspricht DBPROPVAL_GB_EQUALS_SELECT.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropHeterogeneousTables|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_HETEROGENEOUSTABLES.<br /><br /> Der Standardwert dieser Eigenschaft ist null (0).<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropIdentifierCase|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft, DBPROP_IDENTIFIERCASE.<br /><br /> Der Standardwert für diese Eigenschaft ist 8. Dies entspricht DBPROPVAL_IC_MIXED.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropInitMode|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_INIT_MODE.<br /><br /> Die einzigen unterstützten Werte für diese Eigenschaft sind DB_MODE_READWRITE und DB_MODE_READ.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropMaxIndexSize|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_MAXINDEXSIZE.<br /><br /> Der Standardwert dieser Eigenschaft ist null (0).<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropMaxOpenChapters|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_MAXOPENCHAPTERS.<br /><br /> Der Standardwert dieser Eigenschaft ist null (0).<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropMaxRowSize|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_MAXROWSIZE.<br /><br /> Der Standardwert dieser Eigenschaft ist null (0).<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropMaxRowSizeIncludeBlob|*Verwendung*<br /> Optionale, schreibgeschützte `Boolean`-Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_MAXROWSIZEINCLUDESBLOB.<br /><br /> Der Standardwert dieser Eigenschaft ist TRUE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropMaxTablesInSelect|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_MAXTABLESINSELECT.<br /><br /> Der Standardwert für diese Eigenschaft ist 1.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropMsmdAutoexists|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Bestimmt das Verhalten von Autoexists. Diese Eigenschaft kann einen der in der folgenden Tabelle aufgeführten Werte haben.|  
  
|value|Description|  
|-----------|-----------------|  
|*0*|Standardwert, entspricht 1.|  
|*1*|Anwenden von tiefen Autoexists für Abfrageachsen und benannte Mengen. Schließt WHERE-Klauseln und untergeordnete SELECT-Ausdrücke ein.|  
|*2*|Anwenden von tiefen Autoexists für Abfrageachsen und Ausschließen von benannten Mengen aus Autoexists. Schließt WHERE-Klauseln und untergeordnete SELECT-Ausdrücke ein.|  
|*3*|Keine Autoexists für benannte Mengen mit WHERE-Klausel anwenden. Anwenden von flachen Autoexists für Abfrageachsen mit WHERE-Klausel. Anwenden von tiefen Autoexists für Abfrageachsen mit untergeordneten SELECT-Ausdrücken und benannte Mengen mit untergeordneten SELECT-Ausdrücken.|  
  
 0 (null) oder leer sind die Standardwerte für diese Eigenschaft. Dies ist eine Sitzungseigenschaft, die nur festgelegt werden kann, wenn die Sitzung erstellt wird.  
  
|Name|Element|  
|----------|-------------|  
|DbpropMsmdCacheMode|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Zur künftigen Verwendung reserviert.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropMsmdCachePolicy|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Zur künftigen Verwendung reserviert.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropMsmdCacheRatio|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Zur künftigen Verwendung reserviert.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropMsmdCacheRatio2|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Double` Eigenschaft<br /><br /> *Beschreibung*<br /> Zur künftigen Verwendung reserviert.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropMsmdCompareCaseNotSensitiveStringFlags|*Verwendung*<br /> Optionale `Integer`-Eigenschaft mit Lese-/Schreibzugriff<br /><br /> *Beschreibung*<br /> Bestimmt Groß-/Kleinschreibung beachtenden Zeichenfolgenvergleich und Sortierreihenfolgenfunktionalität. Diese Eigenschaft kontrolliert, wie Vergleiche in Zeichensätzen vorgenommen werden, die keine Groß-/Kleinschreibung unterstützen, wie beispielsweise Katakana-Zeichen für Japanisch und Hindi. Der Wert dieser Eigenschaft wird in der ersten Verbindung des Prozessthreads gesetzt und beeinflusst alle nachfolgenden Verbindungen in diesem Prozessthread.<br /><br /> Bestimmen Sie mithilfe der folgenden Tabelle, welche Flags verwendet werden müssen.|  
  
|Name|value|Description|  
|----------|-----------|-----------------|  
|NORM_IGNORECASE|*0 x 00000001*|Groß-/Kleinschreibung wird ignoriert.|  
|Nicht verfügbar|*0 x 00000002*|Binärer Vergleich. Zeichen werden basierend auf dem ihnen zugrunde liegenden Wert im Zeichensatz verglichen, nicht nach ihrer Reihenfolge im Alphabet.|  
|NORM_IGNORENONSPACE|*0 x 00000010*|Zeichen ohne Zwischenraum werden ignoriert.|  
|NORM_IGNORESYMBOLS|*0 x 00000100*|Symbole werden ignoriert.|  
|NORM_IGNOREKANATYPE|*0 x 00001000*|Es wird keine Differenzierung zwischen Hiragana- und Katakana-Zeichen vorgenommen. Beim Vergleich werden die entsprechenden Hiragana- und Katakana-Zeichen als gleich angesehen.|  
|NORM_IGNOREWIDTH|*0 x 00010000*|Es wird keine Differenzierung zwischen Einzel- und Doppelbyteversionen des gleichen Zeichens vorgenommen.|  
|SORT_STRINGSORT|*0x00100000*|Die Interpunktion wird wie Symbole behandelt.|  
  
 Weitere Informationen über den Vergleich von Zeichenfolgen in OLE DB finden Sie, indem Sie im Bereich "Platform SDK" der MSDN Library nach "CompareString" suchen.  
  
 Es gibt keinen Standardwert für diese Eigenschaft.  
  
 Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.  
  
|Name|Element|  
|----------|-------------|  
|DbpropMsmdCompareCaseSensitiveStringFlags|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Bestimmt Groß-/Kleinschreibung nicht beachtenden Zeichenfolgenvergleich und Sortierreihenfolgenfunktionalität. Diese Eigenschaft kontrolliert, wie Vergleiche in Zeichensätzen vorgenommen werden, die keine Groß-/Kleinschreibung unterstützen, wie beispielsweise Katakana-Zeichen für Japanisch und Hindi. Der Wert dieser Eigenschaft wird in der ersten Verbindung des Prozessthreads gesetzt und beeinflusst alle nachfolgenden Verbindungen in diesem Prozessthread.<br /><br /> Bestimmen Sie mithilfe der folgenden Tabelle, welche Flags verwendet werden müssen.|  
  
|Name|value|Description|  
|----------|-----------|-----------------|  
|NORM_IGNORECASE|*0 x 00000001*|Groß-/Kleinschreibung wird ignoriert.|  
|Nicht verfügbar|*0 x 00000002*|Binärer Vergleich. Zeichen werden basierend auf dem ihnen zugrunde liegenden Wert im Zeichensatz verglichen, nicht nach ihrer Reihenfolge im Alphabet.|  
|NORM_IGNORENONSPACE|*0 x 00000010*|Zeichen ohne Zwischenraum werden ignoriert.|  
|NORM_IGNORESYMBOLS|*0 x 00000100*|Symbole werden ignoriert.|  
|NORM_IGNOREKANATYPE|*0 x 00001000*|Es wird keine Differenzierung zwischen Hiragana- und Katakana-Zeichen vorgenommen. Beim Vergleich werden die entsprechenden Hiragana- und Katakana-Zeichen als gleich angesehen.|  
|NORM_IGNOREWIDTH|*0 x 00010000*|Es wird keine Differenzierung zwischen Einzel- und Doppelbyteversionen des gleichen Zeichens vorgenommen.|  
|SORT_STRINGSORT|*0x00100000*|Die Interpunktion wird wie Symbole behandelt.|  
  
 Weitere Informationen über den Vergleich von Zeichenfolgen in OLE DB finden Sie, indem Sie im Bereich "Platform SDK" der MSDN Library nach "CompareString" suchen.  
  
 Es gibt keinen Standardwert für diese Eigenschaft.  
  
 Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.  
  
|Name|Element|  
|----------|-------------|  
|DbpropMsmdDebugMode|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Zur künftigen Verwendung reserviert.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropMsmdDynamicDebugLimit|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Zur künftigen Verwendung reserviert.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropMsmdFlattened2|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Boolean` Eigenschaft<br /><br /> *Beschreibung*<br /> Gibt alle Elemente einer Über-/Unterordnungshierarchie in einer einzelnen Tabellenspalte im vereinfachten Ergebnis aus, es sei denn, die Über-/Unterordnungshierarchie wird auf Achse 0 angefordert. Die Ebenenvorlage für Ausgabespalten wird nicht verwendet.<br /><br /> Der Standardwert für diese Eigenschaft ist FALSE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropMsmdMDXCompatibility|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Bestimmt, wie Platzhalterelemente in einer unregelmäßigen oder unausgeglichenen Hierarchie behandelt werden. Diese Eigenschaft kann einen der in der folgenden Tabelle aufgeführten Werte haben.|  
  
|value|Description|  
|-----------|-----------------|  
|*0*|Für Kompatibilität mit früheren Versionen von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] entspricht dieser Wert 1.|  
|*1*|Hierarchien in Dimensionen mit unterschiedlichen Rollen empfangen eine Beschriftung, die den Dimensionsnamen und den Hierarchienamen einschließt. Die Beschriftung weist folgendes Format auf:<br /><br /> [Dimension].[Hierarchie]<br /><br /> Die Platzhalterelemente werden verfügbar gemacht.|  
|*2*|Hierarchien in Dimensionen mit unterschiedlichen Rollen empfangen eine Beschriftung, die den Dimensionsnamen und den Hierarchienamen einschließt. Die Beschriftung weist folgendes Format auf:<br /><br /> [Dimension].[Hierarchie]<br /><br /> Die Platzhalterelemente werden nicht verfügbar gemacht.|  
|*3*|(Standard) Die Platzhalterelemente werden nicht verfügbar gemacht.|  
  
 Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.  
  
|Name|Element|  
|----------|-------------|  
|DbpropMsmdMDXUniqueNameStyle|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Bestimmt den Algorithmus für die Generierung der eindeutigen Namen von Elementen in einer Dimension. Diese Eigenschaft kann einen der in der folgenden Tabelle aufgeführten Werte haben.<br /><br /> Der Standardwert für diese Eigenschaft ist 6.|  
  
|value|Description|  
|-----------|-----------------|  
|*0*|Für Kompatibilität mit früheren Versionen von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] entspricht dieser Wert 2.|  
|*1*|Verwendet einen Schlüsselpfadalgorithmus:<br /><br /> [Dim].&[Key1].&[Key2]|  
|*2*|Verwendet einen Namenpfadalgorithmus:<br /><br /> [Dim].[Name1].&[Name2]|  
|*3*|Verwendet garantierte eindeutige Namen, die die Zeit über stabil sind.|  
  
 Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.  
  
|Name|Element|  
|----------|-------------|  
|DbpropMsmdSQLCompatibility|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Zur künftigen Verwendung reserviert.<br /><br /> Der Standardwert dieser Eigenschaft ist null (0).<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropMsmdSubQueries|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Eine Bitmaske, die das Verhalten von Unterabfragen bestimmt. Diese Eigenschaft kann einen der in der folgenden Tabelle aufgeführten Werte haben.|  
  
|value|Description|  
|-----------|-----------------|  
|*0*|Standardwert, mit früheren Versionen von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] kompatibel.<br /><br /> Berechnete Elemente oder berechnete Mengen sind in untergeordneten SELECT-Ausdrücken oder Teilcubes nicht zulässig.|  
|*1*|Berechnete Elemente oder berechnete Mengen sind in untergeordneten SELECT-Ausdrücken oder Teilcubes zulässig. Vorgänger des berechneten Elements werden nicht in den Raum des untergeordneten SELECT-Ausdrucks oder Teilcubes eingeschlossen.|  
|*2*|Berechnete Elemente oder berechnete Mengen sind in untergeordneten SELECT-Ausdrücken oder Teilcubes zulässig. Vorgänger des berechneten Elements werden in den Raum des untergeordneten SELECT-Ausdrucks oder Teilcubes eingeschlossen.|  
  
 0 (null) oder leer sind die Standardwerte für diese Eigenschaft.  
  
 Dies ist eine Sitzungseigenschaft, die nur festgelegt werden kann, wenn die Sitzung erstellt wird.  
  
 Finden Sie unter [berechnete Elemente in untergeordneten SELECT-Ausdrücken und Teilcubes](../../multidimensional-models/mdx/calculated-members-in-subselects-and-subcubes.md) für eine ausführliche Erklärung des Verhaltens von berechneten Elementen oder berechneten Sätzen in untergeordneten SELECT-Ausdrücken und Teilcubes.  
  
|Name|Element|  
|----------|-------------|  
|DbpropMsmdUseFormulaCache|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Zur künftigen Verwendung reserviert.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropMultiTableUpdate|*Verwendung*<br /> Optionale, schreibgeschützte `Boolean` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_MULTITABLEUPDATE.<br /><br /> Der Standardwert für diese Eigenschaft ist FALSE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropNullCollation|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_NULLCOLLATION.<br /><br /> Der Standardwert für diese Eigenschaft ist 4. Dies entspricht DBPROPVAL_NC_LOW.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropOrderByColumnsInSelect|*Verwendung*<br /> Optionale, schreibgeschützte `Boolean` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_ORDERBYCOLUMNSINSELECT.<br /><br /> Der Standardwert für diese Eigenschaft ist FALSE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropOutputParameterAvailable|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_OUTPUTPARAMETERAVAILABILITY.<br /><br /> Der Standardwert für diese Eigenschaft ist 1. Dies entspricht DBPROPVAL_OA_NOTSUPPORTED.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropPersistentIdType|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_PERSISTENTIDTYPE.<br /><br /> Der Standardwert für diese Eigenschaft ist 4. Dies entspricht DBPROPVAL_PT_NAME.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropPrepareAbortBehavior|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_PREPAREABORTBEHAVIOR.<br /><br /> Der Standardwert für diese Eigenschaft ist 1. Dies entspricht DBPROPVAL_CB_DELETE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropPrepareCommitBehavior|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_PREPARECOMMITBEHAVIOR.<br /><br /> Der Standardwert für diese Eigenschaft ist 1. Dies entspricht DBPROPVAL_CB_DELETE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropProcedureTerm|*Verwendung*<br /> Optionale, schreibgeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_PROCEDURETERM.<br /><br /> Der Standardwert für diese Eigenschaft ist "Berechnetes Element".<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropQuotedIdentifierCase|*Verwendung*<br /> Optionale, schreibgeschützte `Integer`-Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_QUOTEDIDENTIFIERCASE.<br /><br /> Der Standardwert für diese Eigenschaft ist 8. Dies entspricht DBPROPVAL_IC_MIXED.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropSchemaUsage|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_SCHEMAUSAGE.<br /><br /> Der Standardwert dieser Eigenschaft ist null (0).<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropSqlSupport|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_SQLSUPPORT.<br /><br /> Der Standardwert für diese Eigenschaft ist 512. Dies entspricht DBPROPVAL_SQL_SUBMINIMUM.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropSubqueries|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_SUBQUERIES.<br /><br /> **Hinweis!** Während DMX (Data Mining Extensions) Unterabfragen unterstützt, verweist diese Eigenschaft auf Unterabfrageunterstützung in SQL.<br /><br /> Der Standardwert dieser Eigenschaft ist null (0).<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropSupportedTxnDdl|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_SUPPORTEDTXNDDL.<br /><br /> Der Standardwert für diese Eigenschaft ist null (0). Dies entspricht DBPROPVAL_TC_NONE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropSupportedTxnIsoLevels|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_SUPPORTEDTXNISOLEVELS.<br /><br /> Der Standardwert für diese Eigenschaft ist 4096. Dies entspricht DBPROPVAL_TI_READCOMMITTED.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropSupportedTxnIsoRetain|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_SUPPORTEDTXNISORETAIN.<br /><br /> Der Standardwert für diese Eigenschaft ist 292. Dies entspricht einer Kombination aus DBPROPVAL_TR_ABORT_NO, DBPROPVAL_TR_COMMIT_NO und DBPROPVAL_TR_NONE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|DbpropTableTerm|*Verwendung*<br /> Optionale, schreibgeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_TABLETERM.<br /><br /> Der Standardwert dieser Eigenschaft ist "Cube".<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|Dialect|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Erstellt den in den folgenden Situationen verwendeten Dialekt:<br /><br /> – Der Dialekt, dass der Anbieter verwendet die erste Zeit, die der Anbieter versucht, eine Abfrage auszuführen.<br />– Der Dialekt für die Ausführungsfehler als Folge von Abfragefehlern zurückgegeben.<br /><br /> Sie können die `Dialect`-Eigenschaft nutzen, wenn Sie erwarten, dass die meisten Abfragen einen bestimmten Dialekt verwenden werden.<br /><br /> Die Abfragesyntax kann für Sprachdialekte, wie beispielsweise DMX und SQL, ähnlich sein. Da die Syntax ähnlich sein kann, ist [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] möglicherweise nicht in der Lage, den Dialekt aus der Abfragesyntax abzuleiten. Wenn eine Abfrage nicht in einem Dialekt ausgeführt werden kann, kann die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz möglicherweise versuchen, die Abfrage in einem anderen Dialekt auszuführen.<br /><br /> Wenn die `Dialect`-Eigenschaft eingerichtet ist, gibt [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Abfrageausführungsfehler in dem Dialekt zurück, der Vorrang hat, auch wenn der Anbieter versucht, die Abfrage in einem anderen Dialekt auszuführen. Beispiel: Die `Dialect`-Eigenschaft ist auf MDGUID_DM eingerichtet. Der Anbieter versucht zunächst, die Abfrage als Data Mining-Abfrage auszuführen, aber diese Abfrage schlägt fehl. Der Anbieter sendet dann die Abfrage als SQL-Abfrage erneut ab. Aber diese SQL-Abfrage schlägt auch fehl. Da der Wert der `Dialect`-Eigenschaft MDGUID_DM ist, gibt [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] eine Data Mining-Fehlermeldung zurück und keine SQL-Fehlermeldung.<br /><br /> Wenn die `Dialect`-Eigenschaft nicht festgelegt wird, gibt [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Abfrageausführungsfehler im zuletzt verwendeten Dialekt zurück. Beispiel: Die `Dialect`-Eigenschaft ist nicht festgelegt und eine Data Mining-Abfrage schlägt fehl. Der Anbieter sendet dann die Abfrage als SQL erneut ab. Die SQL-Abfrage schlägt auch fehl. Da die `Dialect`-Eigenschaft nicht festgelegt ist, gibt der Anbieter eine SQL-Fehlermeldung anstelle einer Data Mining-Fehlermeldung zurück.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.<br /><br /> Die für diese Eigenschaft verfügbaren Dialekte werden in der folgenden Tabelle aufgelistet.|  
  
|Name|value|Description|  
|----------|-----------|-----------------|  
|DBGUID_SQL|*C8B522D7-5CF3-11CE-ADE5-00AA0044773D*|Der SQL-Parser hat Vorrang.|  
|MDGUID_DM|*62C58FED-CCA5-44F1-83B6-7B45682B3904*|Der DMX-Parser hat Vorrang.|  
|MDGUID_MDX|*A07CCCD0-8148-11D0-87BB-00C04FC33942*|Der MDX-Parser hat Vorrang.|  
  
|Name|Element|  
|----------|-------------|  
|Disable Prefetch Facts|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Boolean` -Eigenschaft<br /><br /> *Beschreibung*<br /> Wenn diese Eigenschaft auf True festgelegt ist, unternimmt die Engine während der Dauer der Sitzung keine weiteren Versuche, Werte vorab abzurufen.<br /><br /> Der Standardwert für diese Eigenschaft ist `False`.|  
|EffectiveRoles|*Verwendung*<br /> Optionale, lesegeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Zur künftigen Verwendung reserviert.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|EffectiveUserName|*Verwendung*<br /> Optionale, lesegeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Legt den Namen eines Kontos fest, der verwendet wird, um einen Benutzernamen bei Verbindungsaufbau zu einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz zu überschreiben. Der Wert der Eigenschaft ist nicht normalisiert; das heißt MDX [Benutzername](/sql/mdx/username-mdx) Funktion gibt den literalen Wert zurück, wenn diese Eigenschaft verwendet wird. Diese Eigenschaft kann nur von Serveradministratoren verwendet werden.<br /><br /> Diese Eigenschaft unterstützt die folgenden SID-Typen: Benutzer, Gruppe, Alias, WellKnownGroup, Computer.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|EndRange|*Verwendung*<br /> Optionale, lesegeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Legt einen nullbasierten ganzzahligen Wert fest, der einem `CellOrdinal`-Attributwert entspricht. (Das `CellOrdinal`-Attribut ist Teil des `Cell`-Elements im `CellData`-Abschnitt von `MDDataSet`).<br /><br /> In Verwendung mit der `BeginRange`-Eigenschaft kann die Clientanwendung diese Eigenschaft nutzen, um einen OLAP-Dataset einzuschränken, der durch einen Befehl zu einem bestimmten Zellbereich zurückgegeben wurde. Wenn -1 angegeben ist, werden alle Zellen ab der Zelle, die in der `BeginRange`-Eigenschaft festgelegt ist, zurückgegeben.<br /><br /> Der Standardwert für diese Eigenschaft ist-1.<br /><br /> Diese Eigenschaft kann mit der `Execute`-Methode verwendet werden.|  
|ExecutionMode|*Verwendung*<br /> Optionale, lesegeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Zur künftigen Verwendung reserviert.<br /><br /> Der Standardwert für diese Eigenschaft ist *Execute*.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|ForceCommitTimeout|*Verwendung*<br /> Optionale, lesegeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Bestimmt, wie lange in Sekunden die Commitphase eines derzeit laufenden XMLA-Befehls wartet, bevor ein Rollback für zuvor herausgegebene Befehle erzwungen wird. Die Commitphase entspricht XMLA-Befehlen wie `Statement` oder `Process`.<br /><br /> Der Wert null (0) gibt an, dass die Instanz unbegrenzt wartet.<br /><br /> Der Standardwert dieser Eigenschaft ist null (0).<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|Format|*Verwendung*<br /> Optionale, lesegeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Bestimmt den Typ von Resultset, der von den Methoden `Discover` und `Execute` zurückgegeben wird. Diese Eigenschaft kann einen der in der folgenden Tabelle aufgeführten Werte haben.|  
  
 Der Standardwert für diese Eigenschaft ist *Native*.  
  
 Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.  
  
|value|Description|  
|-----------|-----------------|  
|*Tabellarisch*|Gibt ein Resultset mit den [Rowset](../xml-data-types/rowset-data-type-xmla.md) -Datentyp.|  
|*Mehrdimensionale*|Gibt ein Rowset mit der [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) -Datentyp.|  
|*Native*|Kein Format wird explizit angegeben. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] gibt das entsprechende Format für den Befehl zurück. Der tatsächliche Ergebnistyp wird vom Namespace des Ergebnisses identifiziert.|  
  
|Name|Element|  
|----------|-------------|  
|ImpactAnalysis|*Verwendung*<br /> Optionale, lesegeschützte `Boolean` Eigenschaft<br /><br /> *Beschreibung*<br /> Zur künftigen Verwendung reserviert.<br /><br /> Der Standardwert dieser Eigenschaft ist null (0).<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|LocaleIdentifier|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Liest den von der `Discover`-Methode oder `Execute`-Methode verwendeten Gebietsschemabezeichner (LCID) oder legt diesen fest. Eine vollständige hexadezimale Liste der Sprachen-IDs finden Sie unter dem Suchbegriff "Language Identifiers" in der MSDN Library.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MaximumRows|*Verwendung*<br /> Optionale, lesegeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Zur künftigen Verwendung reserviert.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropAggregateCellUpdate|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_AGGREGATECELL_UPDATE.<br /><br /> Der Standardwert für diese Eigenschaft ist 4. Dies entspricht MDPROPVAL_AU_SUPPORTED.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropAxes|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_AXES.<br /><br /> Der Standardwert für diese Eigenschaft ist 2147483647.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropDrillFunctions|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Gibt die Unterstützung für Drillingfunktionen auf dem Server an. Die folgenden Werte werden verwendet, um eine gültige Bitmaske zu erstellen:<br /><br /> MDPROPVAL_MDF_BASIC (0x01)<br /><br /> MDPROPVAL_MDF_ASYMMETRIC (0x02)<br /><br /> MDPROPVAL_MDF_CALC_MEMBERS (0x04)<br /><br /> Die Standardwerte lauten wie folgt:<br /><br /> 3 für SQL Server 2008<br /><br /> 7 für SQL Server 2008 R2 und [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropFlatteningSupport|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_FLATTENING_SUPPORT.<br /><br /> Der Standardwert für diese Eigenschaft ist 1. Dies entspricht MDPROPVAL_FS_FULL_SUPPORT.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropMdxCaseSupport|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_MDX_CASESUPPORT.<br /><br /> Der Standardwert dieser Eigenschaft ist null (0).<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropMdxDescFlags|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_MDX_DESCFLAGS.<br /><br /> Der Standardwert für diese Eigenschaft ist 7. Dies entspricht MDPROPVAL_MD_BEFORE, MDPROPVAL_MD_AFTER und MDPROPVAL_MD_SELF.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropMdxFormulas|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_MDX_FORMULAS.<br /><br /> Der Standardwert für diese Eigenschaft ist 63. Dies entspricht einer Kombination aus MDPROPVAL_MF_WITH_CALCMEMBERS, MDPROPVAL_MF_WITH_NAMEDSETS, MDPROPVAL_MF_CREATE_CALCMEMBERS, MDPROPVAL_MF_CREATE_NAMEDSETS, MDPROPVAL_MF_SCOPE_SESSION und MDPROPVAL_MF_SCOPE_GLOBAL.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropMdxJoinCubes|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_MDX_JOINCUBES.<br /><br /> Der Standardwert für diese Eigenschaft ist 1. Dies entspricht MDPROPVAL_MJC_SINGLECUBE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropMdxMemberFunctions|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_MDX_MEMBER_FUNCTIONS.<br /><br /> Der Standardwert für diese Eigenschaft ist 15. Dies entspricht einer Kombination aus allen verfügbaren OLE DB-Werten.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropMdxNamedSets|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Eine Bitmaske aus in der folgenden Tabelle aufgelisteten Werten.|  
  
|value|Description|  
|-----------|-----------------|  
|*0 x 01*|MDPROPVAL_MNS_BASIC.|  
|*0 x 02*|MDPROPVAL_MNS_DYNAMIC.|  
|*0 x 04*|MDPROPVAL_MNS_DISPLAYFOLDER.|  
|*0 x 08*|MDPROPVAL_MNS_CAPTION.|  
  
 Der Standardwert für diese Eigenschaft beträgt 15.  
  
|Name|Element|  
|----------|-------------|  
|MdpropMdxNonMeasureExpressions|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_MDX_NONMEASURE_EXPRESSIONS.<br /><br /> Der Standardwert für diese Eigenschaft ist null (0). Dies entspricht MDPROPVAL_NME_ALLDIMENSIONS.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropMdxNumericFunctions|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_MDX_NUMERIC_FUNCTIONS.<br /><br /> Der Standardwert für diese Eigenschaft ist 2047. Dies entspricht einer Kombination aus MDPROPVAL_MNF_MEDIAN, MDPROPVAL_MNF_VAR, MDPROPVAL_MNF_STDDEV, MDPROPVAL_MNF_RANK, MDPROPVAL_MNF_AGGREGATE, MDPROPVAL_MNF_COVARIANCE, MDPROPVAL_MNF_CORRELATION, MDPROPVAL_MNF_LINREGSLOPE, MDPROPVAL_MNF_LINREGVARIANCE, MDPROPVAL_MNF_LINREG2 und MDPROPVAL_MNF_LINREGPOINT.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropMdxObjQualification|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_MDX_OBJQUALIFICATION.<br /><br /> Der Standardwert dieser Eigenschaft ist 496. Dies entspricht einer Kombination aus MDPROPVAL_MOQ_DIM_HIER, MDPROPVAL_MOQ_DIMHIER_LEVEL, MDPROPVAL_MOQ_DIMHIER_MEMBER, MDPROPVAL_MOQ_LEVEL_MEMBER und MDPROPVAL_MOQ_MEMBER_MEMBER.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropMdxOuterReference|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_MDX_OUTERREFERENCE.<br /><br /> Der Standardwert dieser Eigenschaft ist null (0).<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropMdxQueryByProperty|*Verwendung*<br /> Optionale, schreibgeschützte `Boolean` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_MDX_QUERYBYPROPERTY.<br /><br /> Der Standardwert dieser Eigenschaft ist TRUE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropMdxRangeRowset|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_MDX_RANGEROWSET.<br /><br /> Der Standardwert für diese Eigenschaft ist 4. Dies entspricht MDPROPVAL_RR_UPDATE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropMdxSetFunctions|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_MDX_SET_FUNCTIONS.<br /><br /> Der Standardwert für diese Eigenschaft ist 524287. Dies entspricht einer Kombination aus MDPROPVAL_MSF_TOPPERCENT, MDPROPVAL_MSF_BOTTOMPERCENT, MDPROPVAL_MSF_TOPSUM, MDPROPVAL_MSF_BOTTOMSUM, MDPROPVAL_MSF_PERIODSTODATE, MDPROPVAL_MSF_LASTPERIODS, MDPROPVAL_MSF_YTD, MDPROPVAL_MSF_QTD, MDPROPVAL_MSF_MTD, MDPROPVAL_MSF_WTD, MDPROPVAL_MSF_DRILLDOWNMEMBER, MDPROPVAL_MSF_DRILLDOWNLEVEL, MDPROPVAL_MSF_DRILLDOWNMEMBERTOP, MDPROPVAL_MSF_DRILLDOWNMEMBERBOTTOM, MDPROPVAL_MSF_DRILLDOWNLEVEL, MDPROPVAL_MSF_DRILLDOWNLEVELTOP, MDPROPVAL_MSF_DRILLDOWNLEVELBOTTOM, MDPROPVAL_MSF_DRILLUPMEMBER, MDPROPVAL_MSF_DRILLUPLEVEL und MDPROPVAL_MSF_TOGGLEDRILLSTATE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropMdxSlicer|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_MDX_SLICER.<br /><br /> Der Standardwert für diese Eigenschaft ist 2. Dies entspricht MDPROPVAL_MS_SINGLETUPLE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropMdxStringCompop|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_MDX_STRING_COMPOP.<br /><br /> Der Standardwert für diese Eigenschaft ist 15. Dies entspricht einer Kombination aus MDPROPVAL_MSC_LESSTHAN, MDPROPVAL_MSC_GREATERTHAN, MDPROPVAL_MSC_LESSTHANEQUAL und MDPROPVAL_MSC_GREATERTHANEQUAL.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdpropMdxSubQueries|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Der Standardwert für diese Eigenschaft in SQL Server 2014 ist 63.<br /><br /> Der Standardwert für diese Eigenschaft in SQL Server 2008 R2 und [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ist 31.<br /><br /> Der Standardwert für diese Eigenschaft in SQL Server 2008 ist 15.<br /><br /> Gibt die Ebene der Unterstützung für Unterabfragen in MDX an. Eine Bitmaske aus in der folgenden Tabelle aufgelisteten Werten.|  
  
|value|Description|  
|-----------|-----------------|  
|*0 x 01*|MDPROPVAL_MSQ_BASIC.|  
|*0 x 02*|MDPROPVAL_MSQ_ARBITRARYSHAPE.|  
|*0 x 04*|MDPROPVAL_MSQ_NONVISUAL.|  
|*0 x 08*|MDPROPVAL_MSQ_CALCMEMBERS.|  
  
|||  
|-|-|  
|*0 x 10*|MDPROPVAL_MSQ_CALCMEMBERS2|  
  
|Name|Element|  
|----------|-------------|  
|MdpropNamedLevels|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_NAMED_LEVELS.<br /><br /> Der Standardwert für diese Eigenschaft ist 3. Dies entspricht einer Kombination aus MDPROPVAL_NL_NAMEDLEVELS und MDPROPVAL_NL_NUMBEREDLEVELS.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|MdxMissingMemberMode|*Verwendung*<br /> Optionale, lesegeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Gibt an, ob fehlende Elemente in MDX-Anweisungen ignoriert werden.<br /><br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_MDX_MISSING_MEMBER_MODE.<br /><br /> Der Standardwert für diese Eigenschaft ist *Standard*.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.<br /><br /> Diese Eigenschaft kann einen der in der folgenden Tabelle aufgeführten Werte haben.|  
  
|value|Description|  
|-----------|-----------------|  
|*Standardwert*|Von der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz generierten Wert verwenden.|  
|*Fehler*|Fehler erzeugen.|  
|*Ignorieren*|Fehlende Elemente immer ignorieren.|  
  
|Name|Element|  
|----------|-------------|  
|MDXSupport|*Verwendung*<br /> Optionale, schreibgeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Gibt eine Enumeration an, die den Grad der MDX-Unterstützung beschreibt.<br /><br /> `Value` = *Core* alle MDX-Optionen werden unterstützt.<br /><br /> Der einzige Wert, der die Enumeration enthält derzeit ist *Core*. In zukünftigen Versionen werden andere Werte für diese Enumeration definiert.<br /><br /> Der Standardwert für diese Eigenschaft ist *Core*.<br /><br /> Diese Eigenschaft kann mit der `Discover`-Methode verwendet werden.|  
|NonEmptyThreshold|*Verwendung*<br /> Optionale `Integer`-Eigenschaft mit Lese-/Schreibzugriff<br /><br /> *Beschreibung*<br /> Zur künftigen Verwendung reserviert.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|Kennwort|**Diese Eigenschaft wird nicht mehr unterstützt.**<br /><br /> *Verwendung*<br /> Optionale, lesegeschützte `String`-Eigenschaft<br /><br /> *Beschreibung*<br /> Für Rückwärtskompatibilität wird diese Eigenschaft bei Verwendung der `Execute`- oder `Discover`-Methode ignoriert, ohne dass ein Fehler generiert wird.|  
|ProviderName|*Verwendung*<br /> Optionale, schreibgeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_DBMSNAME.<br /><br /> Der Standardwert dieser Eigenschaft ist "OLAP Server".<br /><br /> Diese Eigenschaft kann mit der `Discover`-Methode verwendet werden.|  
|ProviderType|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_DATASOURCE_TYPE.<br /><br /> Der Standardwert für diese Eigenschaft ist 6.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|ProviderVersion|*Verwendung*<br /> Optionale, schreibgeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_DBMSVER.<br /><br /> Der Standardwert für diese Eigenschaft ist die Version der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz.<br /><br /> Diese Eigenschaft kann mit der `Discover`-Methode verwendet werden.|  
|ReadOnlySession|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Zur künftigen Verwendung reserviert.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|RealTimeOlap|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Boolean` Eigenschaft<br /><br /> *Beschreibung*<br /> Gibt, wenn auf TRUE gesetzt, an, dass alle Partitionen, die Tabellenbenachrichtigungen überwachen, in Echtzeit abgefragt werden müssen, wobei das Caching umgangen wird. Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_MSMD_REAL_TIME_OLAP.<br /><br /> Der Standardwert für diese Eigenschaft ist FALSE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|ReturnCellProperties|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Boolean` Eigenschaft<br /><br /> *Beschreibung*<br /> Der Standardwert für diese Eigenschaft ist FALSE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|Rollen|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Legt eine durch Trennzeichen getrennte Zeichenfolge der Rollennamen fest, unter denen eine Clientanwendung eine Verbindung zu einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz herstellt. Mit dieser Eigenschaft kann ein Benutzer eine Verbindung mithilfe einer anderen Rolle als der vom Benutzer derzeit verwendeten herstellen. Beispielsweise möchte ein Serveradministrator eine Verbindung zu einem Cube als Element einer Rolle herstellen, um Berechtigungen zu prüfen, die dieser Rolle zugewiesen wurden. Dieser Benutzer muss ein Element der Rolle sein, das angegeben wird, um mit dieser Eigenschaft eine Verbindung herzustellen.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.<br /><br /> **Hinweis!** Bei Namen von Rollen muss die Groß- und Kleinschreibung beachtet werden. **Verwenden Sie keine** Leerzeichen zwischen der durch Trennzeichen getrennten Rollennamen. Andernfalls werden Fehler und unerwartete Ergebnisse möglicherweise von Abfragen an gesicherte Zellensätze zurückgegeben.|  
|SafetyOptions|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Bestimmt, ob unsichere Bibliotheken registriert und von Clientanwendungen geladen werden können.<br /><br /> Der Wert dieser Eigenschaft bestimmt auch, ob das PASSTHROUGH-Schlüsselwort in lokalen Cubes zugelassen wird. In den folgenden Situationen tritt ein Fehler auf:<br /><br /> – Wenn eine Clientanwendung versucht, einen lokalen Cube mit einer INSERT INTO-Anweisung zu erstellen, die das Passthrough-Schlüsselwort enthält.<br />– Wenn eine Clientanwendung versucht, einen lokalen Cube zu aktualisieren, der INSERT INTO-Anweisung enthält, die das Passthrough-Schlüsselwort verwendet.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.<br /><br /> Diese Eigenschaft kann einen der in der folgenden Tabelle aufgeführten Werte haben.|  
  
|Name|value|Description|  
|----------|-----------|-----------------|  
|DBPROPVAL_MSMD_SAFETY_OPTIONS_DEFAULT|*0*|Dieser Wert wird als DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_SAFE behandelt.<br /><br /> Für Verbindungen zu einem lokalen Cube hängt dieser Wert davon ab, ob die CREATECUBE-Eigenschaft der Verbindungszeichenfolge verwendet wird. Wenn die CREATECUBE-Eigenschaft der Verbindungszeichenfolge verwendet wird, entspricht dieser Wert DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_ALL. Anderenfalls entspricht der Wert DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_SAFE.|  
|DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_ALL|*1*|Dieser Wert aktiviert alle benutzerdefinierten Funktionsbibliotheken, ohne zu überprüfen, ob diese für Initialisierung und Skripterstellung sicher sind. Für Verbindungen zu lokalen Cubes ermöglicht dieser Wert die Verwendung von gespeicherten Prozeduren und des PASSTHROUGH-Schlüsselworts in den INSERT INTO-Anweisungen.<br /><br /> **Wir empfehlen diese Option nicht**.|  
|DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_SAFE|*2*|Dieser Wert stellt sicher, dass alle Klassen für eine bestimmte benutzerdefinierte Funktionsbibliothek überprüft werden, um sicherzustellen, dass diese für Initialisierung und Skripterstellung sicher sind. Für Verbindungen zu lokalen Cubes verhindert dieser Wert die Verwendung des PASSTHROUGH-Schlüsselworts in INSERT INTO-Anweisungen und von gespeicherten Prozeduren, bei denen die PermissionSet-Eigenschaft nicht auf "Safe" gesetzt ist.<br /><br /> Dieser Wert entfernt auch Aktionen in der [MDSCHEMA_ACTIONS](../../schema-rowsets/ole-db-olap/mdschema-actions-rowset.md) Schemarowset, das entweder den Wert HTML oder Befehl in der ACTION_TYPE-Spalte oder einen Wert URL in der ACTION_TYPE-Spalte und einen Wert in Spalte "Inhalt", die nicht der Fall ist mit "http://" oder "https://" beginnen.|  
|DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_NONE|*3*|Dieser Wert verhindert, dass benutzerdefinierte Funktionen während der Sitzung verwendet werden. Für Verbindungen zu lokalen Cubes verhindert dieser Wert die Verwendung aller gespeicherter Prozeduren und des PASSTHROUGH-Schlüsselworts in den INSERT INTO-Anweisungen.<br /><br /> Dieser Wert entfernt auch alle Aktionen im MDSCHEMA_ACTIONS-Schemarowset.|  
  
|Name|Element|  
|----------|-------------|  
|SecuredCellValue|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Legt den Fehlercode und die Werte für die `Value`- und `Formatted Value`-Zelleigenschaften fest, die zurückgegeben werden, wenn ein Zugriff auf eine geschützte Zelle versucht wird.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.<br /><br /> Diese Eigenschaft kann einen der in der folgenden Tabelle aufgeführten Werte haben.|  
  
|value|Description|  
|-----------|-----------------|  
|*0*|(Standard) Kompatibilität mit früheren Versionen, dieser Wert ist identisch mit *1*. Die Bedeutung dieses Standardwerts unterliegt in zukünftigen Versionen Änderung.|  
|*1*|Gibt zurück: HRESULT = NO_ERROR<br /><br /> Die `Value`-Eigenschaft der Zelle enthält das Ergebnis als Variantendatentyp. Die Zeichenfolge "#N/A" wird in der `Formatted Value`-Eigenschaft zurückgegeben.|  
|*2*|Gibt einen Fehler als Wert von HRESULT zurück.|  
|*3*|Gibt NULL in den Eigenschaften `Value` und `Formatted Value` zurück.|  
|*4*|Gibt eine numerische null (0) in der `Value`-Eigenschaft zurück und gibt eine formatierte null in der `Formatted Value`-Eigenschaft zurück. Beispiel: In der `Formatted Value`-Eigenschaft wird für eine Zelle, deren `Format`-Eigenschaft "#.##" ist, 0.00 zurückgegeben.|  
|*5*|Gibt die Zeichenfolge "#SEC" in den Eigenschaften `Value` und `Formatted Value` zurück.|  
  
|Name|Element|  
|----------|-------------|  
|ServerName|*Verwendung*<br /> Optionale, schreibgeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_SERVERNAME.<br /><br /> Der Standardwert für diese Eigenschaft ist der Name der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|ShowHiddenCubes|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Boolean` Eigenschaft<br /><br /> *Beschreibung*<br /> Zur künftigen Verwendung reserviert.<br /><br /> Der Standardwert für diese Eigenschaft ist FALSE.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|SQLQueryMode|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Bestimmt, ob Berechnungen in SQL-Abfragen enthalten sind.<br /><br /> Der Standardwert für diese Eigenschaft ist *berechnete*.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.<br /><br /> Diese Eigenschaft kann einen der in der folgenden Tabelle aufgeführten Werte haben.|  
  
|value|Description|  
|-----------|-----------------|  
|*Daten*|Es werden keine Berechnungen eingeschlossen.|  
|*Berechnet*|Berechnungen werden zurückgegeben.|  
|*IncludeEmpty*|Berechnungen und leere Zeilen werden zurückgegeben.|  
  
|Name|Element|  
|----------|-------------|  
|SQLSupport|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Der Standardwert für diese Eigenschaft ist 512.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|SspropInitAppName|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Enthält den Namen der Clientanwendung.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|SspropInitPacketsize|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Enthält die ID der Clientanwendung.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|SspropInitWsid|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Enthält die ID der Clientarbeitsstation.<br /><br /> Es gibt keinen Standardwert für diese Eigenschaft.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|StateSupport|*Verwendung*<br /> Optionale, schreibgeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Gibt den Grad der Unterstützung für die Statusbehaftung an.<br /><br /> *Keine* = <br />                        Statusbehaftung wird nicht unterstützt.<br /><br /> *Sitzungen* = Statusbehaftung wird durch sitzungsunterstützung bereitgestellt.<br /><br /> Weitere Informationen über statusbehaftung und sitzungsunterstützung finden Sie unter [Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).<br /><br /> Der Standardwert für diese Eigenschaft ist *Sitzungen*.<br /><br /> Diese Eigenschaft kann mit der `Discover`-Methode verwendet werden.|  
|Timeout|*Verwendung*<br /> Optional, Lese-/Schreibzugriff `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Legt die maximale Zeit in Sekunden fest, die die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz darauf warten sollte, dass eine Anforderung erfolgreich war, bevor ein Fehler zurückgegeben wird. Diese Eigenschaft bestimmt darüber hinaus die maximale Zeit, die die Instanz darauf warten sollte, dass ein Update einer Rückschreibetabelle erfolgreich war, bevor ein Fehler ausgegeben wird (entsprechend Rückschreibetimeout-Eigenschaft der Verbindungszeichenfolge).<br /><br /> Der Standardwert dieser Eigenschaft ist null (0).<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|TransactionDDL|*Verwendung*<br /> Optionale, schreibgeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Zur künftigen Verwendung reserviert.<br /><br /> Der Standardwert für diese Eigenschaft ist 0.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
|UserName|Diese Eigenschaft wird nicht mehr unterstützt.<br /><br /> *Verwendung*<br /> Optionale, schreibgeschützte `String` Eigenschaft<br /><br /> *Beschreibung*<br /> Gibt eine Zeichenfolge an, die den Benutzernamen zurückgibt, den die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz dem Befehl zuordnet. Für Rückwärtskompatibilität wird diese Eigenschaft bei Verwendung der `Execute`- oder `Discover`-Methode ignoriert, ohne dass ein Fehler generiert wird. Diese Eigenschaft entspricht der OLE DB-Eigenschaft DBPROP_USERNAME.<br /><br /> Der Standardwert für diese Eigenschaft ist der Benutzername, der die aktuelle Sitzung oder die Verbindung geöffnet hat.<br /><br /> Diese Eigenschaft kann mit der `Execute`-Methode verwendet werden.|  
|VisualMode|*Verwendung*<br /> Optionale, lesegeschützte `Integer` Eigenschaft<br /><br /> *Beschreibung*<br /> Diese Eigenschaft entspricht der OLE DB-Eigenschaft MDPROP_VISUALMODE.<br /><br /> Der Standardwert für diese Eigenschaft ist null (0). Dies entspricht DBPROPVAL_VISUAL_MODE_DEFAULT.<br /><br /> Diese Eigenschaft kann mit den Methoden `Discover` und `Execute` verwendet werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [PropertyList-Element &#40;XMLA&#41;](propertylist-element-xmla.md)  
  
  
