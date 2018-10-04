---
title: Allgemeine Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- external metadata column properties [Integration Services]
- output properties [Integration Services]
- data types [Integration Services], properties
- input properties [Integration Services]
- component properties [Integration Services]
ms.assetid: 51973502-5cc6-4125-9fce-e60fa1b7b796
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5d9d641ccb2a0e261ea899f4fc086d4ad8de0643
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48160642"
---
# <a name="common-properties"></a>Allgemeine Eigenschaften
  Die Datenflussobjekte im [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Objektmodell verfügen über allgemeine Eigenschaften und benutzerdefinierte Eigenschaften auf der Komponentenebene, der Eingabe- und Ausgabeebene und der Ebene der Eingabe- und Ausgabespalten. Viele Eigenschaften verfügen über schreibgeschützte Werte, für die zur Laufzeit eine Zuweisung über die Datenfluss-Engine erfolgt.  
  
 In diesem Thema werden die allgemeinen Eigenschaften von Datenflussobjekten aufgelistet und beschrieben.  
  
-   [Komponenten](#components)  
  
-   [Eingaben](#inputs)  
  
-   [Input columns](#inputcolumns)  
  
-   [Ausgaben](#outputs)  
  
-   [Ausgabespalten](#outputcolumns)  
  
 Informationen zu benutzerdefinierten Eigenschaften finden Sie unter folgenden Themen  
  
-   [Benutzerdefinierte Eigenschaften von ADO.NET](data-flow/ado-net-custom-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften des CDC-Steuerungstasks](control-flow/cdc-control-task-custom-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften der CDC-Quelle](data-flow/cdc-source-custom-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften des Ziels des Data Mining-Modelltrainings](data-flow/data-mining-model-training-destination-custom-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften des DataReader-Ziels](data-flow/datareader-destination-custom-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften des Ziels für Dimensionsverarbeitung](data-flow/dimension-processing-destination-custom-properies.md)  
  
-   [Benutzerdefinierte Eigenschaften von Excel](data-flow/excel-custom-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften der Flatfile](data-flow/flat-file-custom-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften von ODBC-Zielen](data-flow/odbc-destination-custom-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften der ODBC-Quelle](data-flow/odbc-source-custom-properties.md)  
  
-   [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md)Benutzerdefinierte Eigenschaften für OLE DB  
  
-   [Benutzerdefinierte Eigenschaften des Ziels für Partitionsverarbeitung](data-flow/partition-processing-destination-custom-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften der Rohdatendatei](data-flow/raw-file-custom-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften des Recordsetziels](data-flow/recordset-destination-custom-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften des Ziels für SQL Server Compact Edition](data-flow/sql-server-compact-edition-destination-custom-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften des SQL Server-Ziels](data-flow/sql-server-destination-custom-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften von Transformationen](data-flow/transformations/transformation-custom-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften der XML-Quelle](data-flow/xml-source-custom-properties.md)  
  
##  <a name="components"></a> Eigenschaften der softwareupdatepunktkomponente  
 Im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Objektmodell implementiert eine Komponente im Datenfluss die Schnittstelle <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>.  
  
 Die folgende Tabelle beschreibt die Eigenschaften der Komponenten in einem Datenfluss. Einige Eigenschaften verfügen über schreibgeschützte Werte, für die zur Laufzeit eine Zuweisung über die Datenfluss-Engine erfolgt.  
  
|Eigenschaft|Datentyp|Description|  
|--------------|---------------|-----------------|  
|ComponentClassID|Zeichenfolge|Die CLSID der Komponente.|  
|ContactInfo|Zeichenfolge|Kontaktinformationen für den Entwickler einer Komponente.|  
|Description|Zeichenfolge|Die Beschreibung der Datenflusskomponente. Der Standardwert dieser Eigenschaft entspricht dem Namen der Datenflusskomponente.|  
|im Elementknoten &lt;Customer ID="1"|Integer|Ein Wert, der diese Instanz der Komponente eindeutig identifiziert.|  
|IdentificationString|Zeichenfolge|Identifiziert die Komponente.|  
|IsDefaultLocale|Boolean|Gibt an, ob die Komponente das Gebietsschema des Datenflusstasks verwendet, zu dem es gehört.|  
|LocaleID|Integer|Das Gebietsschema, das die Datenflusskomponente verwendet, wenn das Paket ausgeführt wird. Alle Windows-Gebietsschemas sind zur Verwendung in Datenflusskomponenten verfügbar.|  
|Name|Zeichenfolge|Der Name der Datenflusskomponente.|  
|PipelineVersion|Integer|Die Version des Datenflusstasks, innerhalb derer eine Komponente zur Ausführung entworfen wird.|  
|UsesDispositions|Boolean|Gibt an, ob eine Komponente über eine Fehlerausgabe verfügt.|  
|ValidateExternalMetadata|Boolean|Gibt an, ob die Metadaten externer Spalten überprüft werden. Der Standardwert dieser Eigenschaft ist `True`.|  
|Version|Integer|Die Version einer Komponente.|  
  
##  <a name="inputs"></a> Eingabeeigenschaften  
 Im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Objektmodell verfügen Transformationen und Ziele über Eingaben. Eine Eingabe einer Komponente im Datenfluss implementiert die Schnittstelle <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>.  
  
 Die folgende Tabelle beschreibt die Eigenschaften der Eingaben von Komponenten in einem Datenfluss. Einige Eigenschaften verfügen über schreibgeschützte Werte, für die zur Laufzeit eine Zuweisung über die Datenfluss-Engine erfolgt.  
  
|Eigenschaft|Datentyp|Description|  
|--------------|---------------|-----------------|  
|Description|Zeichenfolge|Die Beschreibung der Eingabe.|  
|ErrorOrTruncationOperation|Zeichenfolge|Eine optionale Zeichenfolge, die die Fehlertypen oder abgeschnittene Daten angibt, die bei der Verarbeitung einer Zeile auftreten können.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Ein Wert, der die Behandlung von Fehlern angibt. Die Werte sind `Fail component`, `Ignore failure`, und `Redirect row`.|  
|HasSideEffects|Boolean|Gibt an, ob eine Komponente aus dem Ausführungsplan des Datenflusses entfernt werden kann, wenn diese nicht an eine downstreamkomponente angefügt ist und wenn `RunInOptimizedMode` ist `true`.|  
|im Elementknoten &lt;Customer ID="1"|Integer|Ein Wert, der die Eingabe eindeutig identifiziert.|  
|IdentificationString|Zeichenfolge|Eine Zeichenfolge, die die Eingabe identifiziert.|  
|IsSorted|Boolean|Gibt an, ob die Daten in der Eingabe sortiert werden.|  
|Name|Zeichenfolge|Der Name der Eingabe.|  
|SourceLocale|Integer|Die Gebietsschema-ID (Locale ID, LCID) der Eingabedaten.|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Ein Wert, der bestimmt, wie die Komponente das Abschneiden von Daten behandelt, das bei der Verarbeitung von Zeilen auftritt. . Die Werte sind `Fail component`, `Ignore failure`, und `Redirect row`.|  
  
 Ziele und einige Transformationen unterstützen keine Fehlerausgaben, und die Eigenschaften ErrorRowDisposition und TruncationRowDisposition dieser Komponenten sind schreibgeschützt.  
  
###  <a name="inputcolumns"></a> Eigenschaften der Eingabespalten  
 Im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Objektmodell enthält eine Eingabe eine Auflistung von Eingabespalten. Eine Eingabespalte einer Komponente im Datenfluss implementiert die Schnittstelle <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInputColumn100>.  
  
 Die folgende Tabelle beschreibt die Eigenschaften der Eingabespalten von Komponenten in einem Datenfluss. Einige Eigenschaften verfügen über schreibgeschützte Werte, für die zur Laufzeit eine Zuweisung über die Datenfluss-Engine erfolgt.  
  
|Eigenschaft|Datentyp|Description|  
|--------------|---------------|-----------------|  
|ComparisonFlags|Integer|Eine Gruppe von Flags, die den Vergleich von Spalten angeben, die über einen Zeichendatentyp verfügen. Weitere Informationen finden Sie unter [Comparing String Data](data-flow/comparing-string-data.md).|  
|Description|Zeichenfolge|Beschreibt die Eingabespalte.|  
|ErrorOrTruncationOperation|Zeichenfolge|Eine optionale Zeichenfolge, die die Fehlertypen oder abgeschnittene Daten angibt, die bei der Verarbeitung einer Zeile auftreten können.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Ein Wert, der die Behandlung von Fehlern angibt. Die Werte sind `Fail component`, `Ignore failure`, und `Redirect row`.|  
|ExternalMetadataColumnID|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100>|Die ID der externen Metadatenspalte, die einer Eingabespalte zugewiesen ist.|  
|im Elementknoten &lt;Customer ID="1"|Integer|Ein Wert, der die Eingabespalte eindeutig identifiziert.|  
|IdentificationString|Zeichenfolge|Eine Zeichenfolge, die die Eingabespalte identifiziert.|  
|LineageID|Integer|Die ID der Upstreamspalte.|  
|Name|Zeichenfolge|Der Name der Eingabespalte.|  
|SortKeyPosition|Integer|Ein Wert, der anzeigt, ob eine Spalte sortiert ist, und der die zugehörige Sortierreihenfolge und die Reihenfolge, in der mehrere Spalten sortiert werden, angibt. Der Wert **0** weist darauf hin, dass die Spalte nicht sortiert ist.  Weitere Informationen finden Sie unter [Sortieren von Daten für die Transformationen für Zusammenführen und Zusammenführungsjoin](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Ein Wert, der bestimmt, wie die Komponente das Abschneiden von Daten behandelt, das bei der Verarbeitung von Zeilen auftritt. Die Werte sind `Fail component`, `Ignore failure`, und `Redirect row`.|  
|UpstreamComponentName|Zeichenfolge|Der Name der Upstreamkomponente.|  
|UsageType|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSUsageType>|Ein Wert, der bestimmt, wie eine Eingabespalte von der Komponente verwendet wird.|  
  
 Eingabespalten verfügen auch über die Datentypeigenschaften, die unter "Datentypeigenschaften" beschrieben sind.  
  
##  <a name="outputs"></a> Ausgabeeigenschaften  
 Im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Objektmodell verfügen Quellen und Transformationen über Ausgaben. Eine Ausgabe einer Komponente im Datenfluss implementiert die Schnittstelle <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>.  
  
 Die folgende Tabelle beschreibt die Eigenschaften der Ausgaben von Komponenten in einem Datenfluss. Einige Eigenschaften verfügen über schreibgeschützte Werte, für die zur Laufzeit eine Zuweisung über die Datenfluss-Engine erfolgt.  
  
|Eigenschaft|Datentyp|Description|  
|--------------|---------------|-----------------|  
|DeleteOutputOnPathDetached|Boolean|Ein Wert, der bestimmt, ob eine Datenfluss-Engine die Ausgabe löscht, wenn sie von einem Pfad getrennt wird.|  
|Description|Zeichenfolge|Beschreibt die Ausgabe.|  
|ErrorOrTruncationOperation|Zeichenfolge|Eine optionale Zeichenfolge, die die Fehlertypen oder abgeschnittene Daten angibt, die bei der Verarbeitung einer Zeile auftreten können.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Ein Wert, der die Behandlung von Fehlern angibt. Die Werte sind `Fail component`, `Ignore failure`, und `Redirect row`.|  
|ExclusionGroup|Integer|Ein Wert, der eine Gruppe sich gegenseitig ausschließender Ausgaben identifiziert.|  
|HasSideEffects|Boolean|Ein Wert, der angibt, ob eine Komponente aus dem Ausführungsplan des Datenflusses entfernt werden kann, wenn diese nicht an eine Upstreamkomponente angefügt ist und `RunInOptimizedMode` auf `true` gesetzt ist.|  
|im Elementknoten &lt;Customer ID="1"|Integer|Ein Wert, der die Ausgabe eindeutig identifiziert.|  
|IdentificationString|Zeichenfolge|Eine Zeichenfolge, die die Ausgabe identifiziert.|  
|IsErrorOut|Boolean|Gibt an, ob es sich bei der Ausgabe um eine Fehlerausgabe handelt.|  
|IsSorted|Boolean|Gibt an, ob die Ausgabe sortiert wird. Der Standardwert lautet `False`.<br /><br /> **\*\* Wichtige \* \***  Festlegung des Werts für die `IsSorted` Eigenschaft `True` werden die Daten nicht sortiert. Diese Eigenschaft ist lediglich ein Hinweis für die Downstreamkomponenten, dass die Daten vorher sortiert wurden. Weitere Informationen finden Sie unter [Sortieren von Daten für die Transformationen für Zusammenführen und Zusammenführungsjoin](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).|  
|Name|Zeichenfolge|Der Name der Ausgabe.|  
|SynchronousInputID|Integer|Die ID einer Eingabe, die zur Ausgabe synchron ist.|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Ein Wert, der bestimmt, wie die Komponente das Abschneiden von Daten behandelt, das bei der Verarbeitung von Zeilen auftritt. Die Werte sind `Fail component`, `Ignore failure`, und `Redirect row`.|  
  
###  <a name="outputcolumns"></a> Eigenschaften der Ausgabespalten  
 Im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Objektmodell enthält eine Ausgabe eine Auflistung von Ausgabespalten. Eine Ausgabespalte einer Komponente im Datenfluss implementiert die Schnittstelle <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100>.  
  
 Die folgende Tabelle beschreibt die Eigenschaften der Ausgabespalten von Komponenten in einem Datenfluss. Einige Eigenschaften verfügen über schreibgeschützte Werte, für die zur Laufzeit eine Zuweisung über die Datenfluss-Engine erfolgt.  
  
|Eigenschaft|Datentyp|Description|  
|--------------|---------------|-----------------|  
|ComparisonFlags|Integer|Eine Gruppe von Flags, die den Vergleich von Spalten angeben, die über einen Zeichendatentyp verfügen. Weitere Informationen finden Sie unter [Comparing String Data](data-flow/comparing-string-data.md).|  
|Description|Zeichenfolge|Beschreibt die Ausgabespalte.|  
|ErrorOrTruncationOperation|Zeichenfolge|Eine optionale Zeichenfolge, die die Fehlertypen oder abgeschnittene Daten angibt, die bei der Verarbeitung einer Zeile auftreten können.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Ein Wert, der die Behandlung von Fehlern angibt. Die Werte sind `Fail component`, `Ignore failure`, und `Redirect row`. Der Standardwert lautet `Fail component`.|  
|ExternalMetadataColumnID|Integer|Die ID der externen Metadatenspalte, die einer Eingabespalte zugewiesen ist.|  
|im Elementknoten &lt;Customer ID="1"|Integer|Ein Wert, der die Ausgabespalte eindeutig identifiziert.|  
|IdentificationString|Zeichenfolge|Eine Zeichenfolge, die die Ausgabespalte identifiziert.|  
|LineageID|Integer|Die ID der Ausgabespalte. Downstreamkomponenten verweisen auf die Spalte, indem sie diesen Wert verwenden.|  
|Name|Zeichenfolge|Der Name der Ausgabespalte.|  
|SortKeyPosition|Integer|Ein Wert, der anzeigt, ob eine Spalte sortiert ist, und der die zugehörige Sortierreihenfolge und die Reihenfolge, in der mehrere Spalten sortiert werden, angibt. Der Wert **0** weist darauf hin, dass die Spalte nicht sortiert ist. Weitere Informationen finden Sie unter [Sortieren von Daten für die Transformationen für Zusammenführen und Zusammenführungsjoin](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).|  
|SpecialFlags|Integer|Ein Wert, der die speziellen Flags der Ausgabespalte enthält.|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Ein Wert, der bestimmt, wie die Komponente das Abschneiden von Daten behandelt, das bei der Verarbeitung von Zeilen auftritt. Die Werte sind `Fail component`, `Ignore failure`, und `Redirect row`. Der Standardwert lautet `Fail component`.|  
  
 Ausgabespalten schließen auch eine Gruppe von Datentypeigenschaften ein.  
  
## <a name="external-metadata-column-properties"></a>Eigenschaften externer Metadatenspalten  
 Im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Objektmodell können Eingaben und Ausgaben eine Auflistung externer Metadatenspalten enthalten. Eine externe Metadatenspalte einer Komponente im Datenfluss implementiert die Schnittstelle <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100>.  
  
 Die folgende Tabelle beschreibt die Eigenschaften der externen Metadatenspalten von Komponenten in einem Datenfluss. Einige Eigenschaften verfügen über schreibgeschützte Werte, für die zur Laufzeit eine Zuweisung über die Datenfluss-Engine erfolgt.  
  
|Eigenschaft|Datentyp|Description|  
|--------------|---------------|-----------------|  
|Description|Zeichenfolge|Beschreibt die externe Spalte.|  
|im Elementknoten &lt;Customer ID="1"|Integer|Ein Wert, der die Spalte eindeutig identifiziert.|  
|IdentificationString|Zeichenfolge|Eine Zeichenfolge, die die Spalte identifiziert.|  
|Name|Zeichenfolge|Der Name der externen Spalte.|  
  
 Externe Metadatenspalten schließen auch eine Gruppe von Datentypeigenschaften ein.  
  
## <a name="data-type-properties"></a>Datentypeigenschaften  
 Ausgabespalten und externe Metadatenspalten schließen eine Gruppe von Datentypeigenschaften ein. Je nach dem Datentyp der Spalte können Eigenschaften einen Lese-/Schreibzugriff oder einen Schreibschutz festlegen.  
  
 Die folgende Tabelle beschreibt die Datentypeigenschaften von Ausgabespalten und externen Metadatenspalten.  
  
|Eigenschaft|Datentyp|Description|  
|--------------|---------------|-----------------|  
|CodePage|Integer|Gibt die Codepage für Zeichenfolgendaten an, bei denen es sich nicht um Unicode handelt.|  
|DataType|Ganze Zahl (Enumeration)|Der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Datentyp der Spalte. Weitere Informationen finden Sie unter [Integration Services Datentypen](data-flow/integration-services-data-types.md).|  
|Länge|Integer|Die Länge der Zeichen in einer Spalte.|  
|Genauigkeit|Integer|Die Genauigkeit einer numerischen Spalte.|  
|Dezimalstellen|Integer|Die Dezimalstellen einer numerischen Spalte.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datenfluss](data-flow/data-flow.md)   
 [Benutzerdefinierte Eigenschaften der Transformation](data-flow/transformations/transformation-custom-properties.md)   
 [Pfadeigenschaften](../../2014/integration-services/path-properties.md)   
 [Data Flow-Eigenschaften, die mithilfe von Ausdrücken festgelegt werden können](../../2014/integration-services/data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  
