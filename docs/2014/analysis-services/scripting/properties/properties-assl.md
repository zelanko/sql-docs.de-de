---
title: Eigenschaften (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- properties [Analysis Services Scripting Language]
- Analysis Services Scripting Language, properties
- ASSL, properties
ms.assetid: 9a38cdc9-a210-421a-90e9-6391876765fa
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8a000f4f4c9a73698f04a0bd88882db55b8661e1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37173501"
---
# <a name="properties-assl"></a>Eigenschaften (ASSL)
  In diesem Referenzabschnitt finden Sie Syntax- und Nutzungsinformationen für jedes Element, das im ASSL-Schema (Analysis Services Scripting Language) als Objekteigenschaft agiert.  
  
 Obwohl das ASSL-Schema nur XML-Elemente enthält, entsprechen die Elemente, die in diesem Abschnitt beschrieben werden, aus der Sicht eines Entwicklers Eigenschaften, die Objekte beschreiben.  
  
 Eigenschaften sind Blattebenenelemente im ASSL-Schema und besitzen keine untergeordneten Elemente oder Elemente, die wiederum eigenen Eigenschaften entsprechen.  
  
 In einigen Fällen wird ein Blattebenenelement im Schema, das eine Eigenschaft zu sein scheint, als Objekt klassifiziert, da der Typ des Elements ein Objekttyp ist. Beispielsweise ist die `Source` eines `Dimension`-Objekts vom Typ `DimensionBinding`.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Element|Description|  
|-------------|-----------------|  
|[Zugriff auf Element &#40;ASSL&#41;](access-element-assl.md)|Gibt die Zugriffsebene übergeben, um eine [CellPermission](../objects/cellpermission-element-assl.md) Element.|  
|[Konto Element &#40;ImpersonationInfo&#41; &#40;ASSL&#41;](account-element-impersonationinfo-assl.md)|Enthält den Namen des Benutzerkontos für den [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md) -Datentyp.|  
|[AccountType-Element &#40;ASSL&#41;](accounttype-element-assl.md)|Enthält den Namen des definierten Kontotyps ein [Datenbank](../objects/database-element-assl.md) Element.|  
|[ActionID-Element &#40;ASSL&#41;](id-element-assl.md)|Enthält den Namen des ein [Aktion](../objects/action-element-assl.md) Element definiert eine [Cube](../objects/cube-element-assl.md) Element, das in zur Verfügung gestellt wird eine [Perspektive](../objects/perspective-element-assl.md) Element als ein [PerspectiveAction](../data-type/action-data-type-assl.md) Element.|  
|[Administer-Element &#40;ASSL&#41;](administer-element-assl.md)|Gibt an, ob die zugeordnete Berechtigung das Recht einschließt, ein `Database`-Element zu verwalten.|  
|[AggregateFunction-Element &#40;ASSL&#41;](aggregatefunction-element-assl.md)|Definiert den Typ der Aggregatfunktion, die ein, die eine [Measure](../objects/measure-element-assl.md) Element.|  
|[AggregationDesignID-Element &#40;ASSL&#41;](aggregationdesignid-element-assl.md)|Identifiziert die [AggregationDesign](../objects/aggregationdesign-element-assl.md) zugeordnete Element der [Partition](../objects/partition-element-assl.md) Element.|  
|[AggregationFunction-Element &#40;ASSL&#41;](aggregationfunction-element-assl.md)|Enthält die Aggregationsfunktion, die für den Kontotyp zu verwenden ist.|  
|[AggregationID-Element &#40;ASSL&#41;](aggregationid-element-assl.md)|Identifiziert die Aggregationsdefinition vom `AggregationDesign`-Element, die verwendet wird, um die Aggregationsinstanz zu erstellen.|  
|[AggregationInstanceSource-Element &#40;ASSL&#41;](aggregationinstancesource-element-assl.md)|Identifiziert die Quelle der Daten für benutzerdefinierte Aggregationsinstanzen, die an ein `Partition`-Element gebunden sind.|  
|[AggregationPrefix-Element &#40;ASSL&#41;](aggregationprefix-element-assl.md)|Definiert das gemeinsame Präfix, das innerhalb des zugeordneten übergeordneten Elements für die Aggregationsnamen verwendet wird.|  
|[AggregationStorage-Element &#40;ASSL&#41;](aggregationstorage-element-assl.md)|Identifiziert die Speichermethode für Aggregationen.|  
|[AggregationType-Element &#40;ASSL&#41;](aggregationtype-element-assl.md)|Definiert den Typ von Aggregation, der vom `Partition`-Element gespeichert wird.|  
|[AggregationUsage-Element &#40;ASSL&#41;](aggregationusage-element-assl.md)|Steuerelemente wie der Aggregations-Designer in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Aggregationen entwirft.|  
|[Algorithm-Element &#40;ASSL&#41;](algorithm-element-assl.md)|Definiert den Algorithmus ein, die eine [MiningModel](../objects/miningmodel-element-assl.md) Element.|  
|[Alias-Element &#40;ASSL&#41;](alias-element-assl.md)|Definiert einen Alias für eine [Konto](../objects/account-element-assl.md) Element.|  
|[AllMemberAggregationUsage-Element &#40;ASSL&#41;](allmemberaggregationusage-element-assl.md)|Steuert, wie der Aggregations-Designer in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Aggregationen entwirft.|  
|[AllMemberName-Element &#40;ASSL&#41;](name-element-assl.md)|Enthält die Beschriftung in der Standardsprache für alle-Elements ein [Hierarchie](../objects/hierarchy-element-assl.md) Element.|  
|[AllowBrowsing-Element &#40;ASSL&#41;](allowbrowsing-element-assl.md)|Definiert, ob die Mitglieder einer [Rolle](../objects/role-element-assl.md) Element Browse-Berechtigung für eine `MiningModel` Element.|  
|[AllowDrillThrough-Element &#40;ASSL&#41;](allowdrillthrough-element-assl.md)|Bestimmt, ob Drillthrough auf dem übergeordneten Element erlaubt wird.|  
|[AllowDuplicateNames-Element &#40;ASSL&#41;](allowduplicatenames-element-assl.md)|Bestimmt, ob doppelte Namen in einem `Hierarchy`-Element zulässig sind.|  
|[AllowedSet-Element &#40;ASSL&#41;](allowedset-element-assl.md)|Enthält einen Mengenausdruck, der die Menge zulässiger Berechtigungen für ein `Role`-Element auf einem Attribut definiert.|  
|[Anwendungselement &#40;ASSL&#41;](application-element-assl.md)|Identifiziert die Anwendung, die einem `Action`-Element zugeordnet ist.|  
|[AssociatedMeasureGroupID-Element &#40;ASSL&#41;](measuregroupid-element-assl.md)|Enthält den Bezeichner (ID) der der [MeasureGroup](../objects/group-element-assl.md) zugeordnete Element eine [CalculationProperty](../objects/calculationproperty-element-assl.md) Element oder ein [Kpi](../objects/kpi-element-assl.md) Element.|  
|[AttributeAllMemberName-Element &#40;ASSL&#41;](attributeallmembername-element-assl.md)|Enthält die Beschriftung in der Standardsprache für alle Elemente der Dimension.|  
|[AttributeHierarchyDisplayFolder-Element &#40;ASSL&#41;](displayfolder-element-assl.md)|Gibt den Ordner an, in dem die zugeordnete Attributhierarchie angezeigt wird.|  
|[AttributeHierarchyEnabled-Element &#40;ASSL&#41;](enabled-element-assl.md)|Bestimmt, ob eine Attributhierarchie für das Attribut aktiviert ist.|  
|[AttributeHierarchyOptimizedState-Element &#40;ASSL&#41;](state-element-assl.md)|Bestimmt die Optimierungsebene, die auf die Attributhierarchie angewendet wird.|  
|[AttributeHierarchyOrdered-Element &#40;ASSL&#41;](attributehierarchyordered-element-assl.md)|Legt fest, ob die verknüpfte Attributhierarchie geordnet wird.|  
|[AttributeHierarchyVisible-Element &#40;ASSL&#41;](visible-element-assl.md)|Bestimmt, ob die Attributhierarchie für Clientanwendungen sichtbar ist.|  
|[AttributeID-Element &#40;ASSL&#41;](attributeid-element-assl.md)|Enthält die ID des Attributs, das dem übergeordneten Element zugeordnet ist.|  
|[Element Überwachen &#40;ASSL&#41;](audit-element-assl.md)|Gibt an, dass eine [Ablaufverfolgung](../objects/trace-element-assl.md) Element kann keine Ereignisse löschen, auch wenn dies eine verminderte Leistung auf dem Server.|  
|[AutoRestart-Element &#40;ASSL&#41;](autorestart-element-assl.md)|Bestimmt, ob ein `Trace`-Element automatisch neu starten sollte, wenn ein [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Dienst beendet und neu gestartet wird.|  
|[BackColor-Element &#40;ASSL&#41;](backcolor-element-assl.md)|Beschreibt farbbezogene Anzeigeeigenschaften des übergeordneten Elements.|  
|[CacheMode-Element &#40;ASSL&#41;](cachemode-element-assl.md)|Bestimmt den Zwischenspeichermechanismus, der für Trainingsdaten verwendet wird, die während der Verarbeitung einer Miningstruktur abgerufen wurden.|  
|[CalculationReference-Element &#40;ASSL&#41;](calculationreference-element-assl.md)|Enthält den Namen der benannten Menge oder berechneten Zelle, auf die das `CalculationProperty`-Element verweist.|  
|[CalculationType-Element &#40;ASSL&#41;](calculationtype-element-assl.md)|Beschreibt den Berechnungstyp, der im zugeordneten `CalculationProperty`-Element definiert wird.|  
|[CalendarEndDate-Element &#40;ASSL&#41;](calendarenddate-element-assl.md)|Definiert das Enddatum des Kalenderzeitraums für ein [TimeBinding](../data-type/binding-data-type-assl.md) Element.|  
|[CalendarLanguage-Element &#40;ASSL&#41;](language-element-assl.md)|Definiert die für das `TimeBinding`-Element verwendete Kalendersprache.|  
|[CalendarStartDate-Element &#40;ASSL&#41;](calendarstartdate-element-assl.md)|Definiert das Anfangsdatum des Kalenderzeitraums für das `TimeBinding`-Element.|  
|[Caption-Element &#40;ASSL&#41;](caption-element-assl.md)|Enthält die Beschriftung für das zugeordnete übergeordnete Element.|  
|[CaptionIsMdx-Element &#40;ASSL&#41;](captionismdx-element-assl.md)|Definiert, ob die Beschriftung für das `Action`-Element ein MDX-Ausdruck (Multidimensional Expressions) ist.|  
|[Cardinality-Element &#40;ASSL&#41;](cardinality-element-assl.md)|Gibt die Kardinalität der Beziehung beschrieben ein [AttributeRelationship](../objects/attributerelationship-element-assl.md) oder [RegularMeasureGroupDimension](../data-type/dimension-data-type-assl.md).|  
|[CaseCubeDimensionID-Element &#40;ASSL&#41;](dimensionid-element-assl.md)|Enthält die ID der Cubedimension, die die Data Mining-Dimension mit der Measuregruppe verknüpft.|  
|[ClassifiedColumnID-Element &#40;ASSL&#41;](classifiedcolumnid-element-assl.md)|Enthält die ID einer verknüpften Spalte, die von klassifiziert ist die [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) Element.|  
|[Collation-Element &#40;ASSL&#41;](collation-element-assl.md)|Bestimmt die vom übergeordneten Element verwendete Sortierung.|  
|[ColumnID-Element &#40;ColumnBinding&#41; &#40;ASSL&#41;](columnid-element-columnbinding-assl.md)|Enthält die ID der Spalte innerhalb der Tabelle, an die das Datenelement gebunden ist.|  
|[ColumnID-Element &#40;EventColumn&#41; &#40;ASSL&#41;](columnid-element-eventcolumn-assl.md)|Enthält die ID der Spalte mit den Informationen, die für ein Ereignis als Teil eines `Trace`-Elements aufgezeichnet werden sollen.|  
|[Element für die erste Bedingung &#40;ASSL&#41;](condition-element-assl.md)|Enthält einen MDX-Ausdruck, der bestimmt, ob das übergeordnete `Action`-Element für das Ziel gilt.|  
|[ConnectionString-Element &#40;ASSL&#41;](connectionstring-element-assl.md)|Enthält die verschlüsselte Verbindungszeichenfolge für eine [DataSource](../objects/datasource-element-assl.md) Element.|  
|[ConnectionStringSecurity-Element &#40;ASSL&#41;](connectionstringsecurity-element-assl.md)|Gibt an, ob das Kennwort des Benutzers von der Datenquellenverbindungszeichenfolge aus Sicherheitsgründen gelöscht wird.|  
|[Content-Element &#40;ASSL&#41;](content-element-assl.md)|Beschreibt den Inhalt der Spalte in der [MiningStructure](../objects/miningstructure-element-assl.md) Element.|  
|[CreatedTimestamp-Element &#40;ASSL&#41;](createdtimestamp-element-assl.md)|Enthält den schreibgeschützten Erstellungszeitstempel des übergeordneten Elements.|  
|[CubeDimensionID-Element &#40;ASSL&#41;](cubedimensionid-element-assl.md)|Identifiziert die [CubeDimension](../data-type/cubedimension-data-type-assl.md) Element, das mit dem übergeordneten Element gehört.|  
|[CubeID-Element &#40;ASSL&#41;](cubeid-element-assl.md)|Identifiziert die `Cube` zugeordnete Element eine [Bindung](../data-type/binding-data-type-assl.md) Element.|  
|[CurrentStorageMode-Element &#40;ASSL&#41;](storagemode-element-assl.md)|Bestimmt den aktuellen Speichermodus für das übergeordnete Element.|  
|[CurrentTimeMember-Element &#40;ASSL&#41;](../objects/member-element-assl.md)|Definiert das aktuelle Element einer Zeitdimension, das einem `Kpi`-Element zugeordnet wird.|  
|[DataAggregation-Element &#40;ASSL&#41;](../objects/aggregation-element-assl.md)|Bestimmt, ob die Instanz persistente Daten oder zwischengespeicherte Daten für die `MeasureGroup` aggregieren kann.|  
|[DatabaseID-Element &#40;ASSL&#41;](databaseid-element-assl.md)|Identifiziert das `Database`-Element, das zu einem Out-of-Line-`Binding`-Element gehört.|  
|[DataSize-Element &#40;ASSL&#41;](datasize-element-assl.md)|Enthält die Größe in Bytes ein [DataItem](../data-type/dataitem-data-type-assl.md) Element.|  
|[DataSourceID-Element &#40;ASSL&#41;](datasourceid-element-assl.md)|Identifiziert das `DataSource`-Element, das dem übergeordneten Element zugeordnet ist.|  
|[DataSourceImpersonationInfo-Element &#40;ASSL&#41;](impersonationinfo-element-assl.md)|Enthält die Informationen, die verwendet werden, um beim Verbinden der Datenquelle eines `Database`-Elements das Identitätswechselverhalten zu bestimmen.|  
|[DataSourceViewID-Element &#40;ASSL&#41;](datasourceviewid-element-assl.md)|Identifiziert die [DataSourceView](../objects/datasourceview-element-assl.md) zugeordnete Element der `Binding` übergeordneten Elements.|  
|[DataType-Element &#40;ASSL&#41;](datatype-element-assl.md)|Definiert den Datentyp des zugeordneten Elements.|  
|[DbSchemaName-Element &#40;ASSL&#41;](dbschemaname-element-assl.md)|Enthält den Namen des Schemas ein, die das übergeordnete Element in der Tabelle durch identifiziert die [DbTableName](dbtablename-element-assl.md) Element.|  
|[DbTableName-Element &#40;ASSL&#41;](dbtablename-element-assl.md)|Enthält den Namen der Tabelle, an die das übergeordnete Element gebunden ist.|  
|[Default-Element &#40;ASSL&#41;](default-element-assl.md)|Bestimmt, ob `DrillThroughAction` die Standard-Drillthroughaktion ist.|  
|[DefaultMeasure-Element &#40;ASSL&#41;](defaultmeasure-element-assl.md)|Enthält einen MDX Language-Ausdruck, der das Standardmeasure für ein `Cube` oder `Perspective`-Element definiert.|  
|[DefaultMember-Element &#40;ASSL&#41;](defaultmember-element-assl.md)|Enthält einen MDX-Ausdruck, der das Standardelement des übergeordneten Elements identifiziert.|  
|[DefaultScript-Element &#40;ASSL&#41;](defaultscript-element-assl.md)|Identifiziert das Standard- [MdxScript](../objects/mdxscript-element-assl.md) Element in der [MdxScripts](../collections/mdxscripts-element-assl.md) Auflistung.|  
|[DefaultValue-Element &#40;ASSL&#41;](value-element-assl.md)|Enthält den schreibgeschützten Standardwert des zugeordneten [ServerProperty](../objects/serverproperty-element-assl.md) Element.|  
|[DeniedSet-Element &#40;ASSL&#41;](deniedset-element-assl.md)|Enthält einen Mengenausdruck, der die Liste von Berechtigungen definiert, die auf dem zugeordneten Attribut verweigert werden.|  
|[DependsOnDimensionID-Element &#40;ASSL&#41;](dependsondimensionid-element-assl.md)|Enthält die ID einer anderen Dimension, von der die übergeordnete Dimension abhängt.|  
|[Description-Element &#40;ASSL&#41;](description-element-assl.md)|Enthält die Beschreibung des übergeordneten Elements.|  
|[DimensionID-Element &#40;ASSL&#41;](dimensionid-element-assl.md)|Enthält die ID der Dimension.|  
|[DiscretizationBucketCount-Element &#40;ASSL&#41;](discretizationbucketcount-element-assl.md)|Enthält die Anzahl der Buckets, in denen diskretisiert werden soll.|  
|[DiscretizationMethod-Element &#40;ASSL&#41;](discretizationmethod-element-assl.md)|Definiert die zu verwendende Diskretisierungsmethode.|  
|[DisplayFlag-Element &#40;ASSL&#41;](displayflag-element-assl.md)|Enthält einen schreibgeschützten Hinweis, der angibt, ob Benutzeroberflächenkomponenten das zugeordnete `ServerProperty`-Element anzeigen sollten.|  
|[DisplayFolder-Element &#40;ASSL&#41;](displayfolder-element-assl.md)|Gibt den Ordner an, in dem das übergeordnete Element aufgelistet werden soll. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Anwendungen für Entwickler und Administratoren können die Verwendung von Anzeigeordnern für die visuelle Kategorisierung mehrerer Elemente unterstützen.|  
|[Distribution-Element &#40;ASSL&#41;](distribution-element-assl.md)|Enthält einen anbieterspezifischen Wert, der beschreibt, wie skalare Werte innerhalb einer Spalte eines `MiningStructure`-Elements verteilt werden.|  
|[Edition-Element &#40;ASSL&#41;](edition-element-assl.md)|Enthält die schreibgeschützte Edition der Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] dargestellt durch die [Server](../objects/server-element-assl.md) Element.|  
|[Element aktiviert &#40;ASSL&#41;](enabled-element-assl.md)|Gibt an, ob das übergeordnete Element aktiviert ist.|  
|[EndOfData-Element &#40;ASSL&#41;](../objects/data-element-assl.md)|Gibt das Ende der Daten von einem [PushedDataSource](../data-type/datasource-data-type-assl.md) Element.|  
|[EstimatedCount-Element &#40;ASSL&#41;](estimatedcount-element-assl.md)|Enthält die geschätzte Anzahl der Elemente eines Attributs.|  
|[EstimatedPerformanceGain-Element &#40;ASSL&#41;](estimatedperformancegain-element-assl.md)|Enthält den schreibgeschützten Prozentwert des geschätzten Leistungsgewinns für die Partition.|  
|[EstimatedRows-Element &#40;ASSL&#41;](estimatedrows-element-assl.md)|Enthält die geschätzte Anzahl der durch das übergeordnete Element dargestellten Zeilen.|  
|[EstimatedSize-Element &#40;ASSL&#41;](estimatedsize-element-assl.md)|Enthält die schreibgeschützte geschätzte Größe des übergeordneten Elements (in Byte).|  
|[EventID-Element &#40;ASSL&#41;](eventid-element-assl.md)|Eindeutig identifiziert eine [Ereignis](../objects/event-element-assl.md) -Element, das als Teil des aufgezeichnet werden eine `Trace` Element.|  
|[Expression-Element &#40;ASSL&#41;](expression-element-assl.md)|Enthält einen MDX-Ausdruck, der den Inhalt des übergeordneten Elements definiert.|  
|[Filter-Element &#40;Bindung&#41; &#40;ASSL&#41;](filter-element-binding-assl.md)|Enthält einen MDX-Ausdruck, der die Inhalte des übergeordneten Elements filtert.|  
|[Filter-Element &#40;Ablaufverfolgung&#41; &#40;ASSL&#41;](filter-element-trace-assl.md)|Enthält ein XML-Dokument-Fragment, das den `Trace`-Filter beschreibt.|  
|[FirstDayOfWeek-Element &#40;ASSL&#41;](firstdayofweek-element-assl.md)|Definiert den ersten Tag der Woche für ein `TimeBinding`-Element.|  
|[FiscalFirstDayOfMonth-Element &#40;ASSL&#41;](fiscalfirstdayofmonth-element-assl.md)|Definiert den ersten Tag des Geschäftsmonats für ein `TimeBinding`-Element.|  
|[FiscalFirstMonth-Element &#40;ASSL&#41;](fiscalfirstmonth-element-assl.md)|Definiert den ersten Monat des Geschäftszeitraums für ein `TimeBinding`-Element.|  
|[FiscalYearName-Element &#40;ASSL&#41;](fiscalyearname-element-assl.md)|Definiert die Namenskonvention für den Namen des Geschäftsjahrs für ein `TimeBinding`-Element.|  
|[FontFlags-Element &#40;ASSL&#41;](fontflags-element-assl.md)|Beschreibt schriftartbezogene Anzeigeeigenschaften der übergeordneten Elemente `CalculationProperty` oder `Measure`.|  
|[FontName-Element &#40;ASSL&#41;](fontname-element-assl.md)|Beschreibt schriftartbezogene Anzeigeeigenschaften der übergeordneten Elemente `CalculationProperty` oder `Measure`.|  
|[FontSize-Element &#40;ASSL&#41;](fontsize-element-assl.md)|Beschreibt schriftartbezogene Anzeigeeigenschaften der übergeordneten Elemente `CalculationProperty` oder `Measure`.|  
|[ForceRebuildInterval-Element &#40;ASSL&#41;](forcerebuildinterval-element-assl.md)|Bestimmt, wie viel Zeit nach dem Verfügbarwerden eines neuen multidimensionalen OLAP-Image (MOLAP) vergehen muss, bevor das MOLAP-Imaging unbedingt beginnt.|  
|[ForeColor-Element &#40;ASSL&#41;](forecolor-element-assl.md)|Beschreibt farbbezogene Anzeigeeigenschaften der übergeordneten Elemente `CalculationProperty` oder `Measure`.|  
|[Element formatieren &#40;ASSL&#41;](format-element-assl.md)|Enthält das erforderliche Format des `DataItem`-Elements.|  
|[FormatString-Element &#40;ASSL&#41;](formatstring-element-assl.md)|Beschreibt das Anzeigeformat für ein `CalculationProperty`-Element oder ein `Measure`-Element.|  
|[Goal-Element &#40;ASSL&#41;](goal-element-assl.md)|Identifiziert das gewünschte Ziel in einem `Kpi`-Element.|  
|[GranularityAttributeID-Element &#40;ASSL&#41;](granularityattributeid-element-assl.md)|Enthält die ID des Attributs mit dem übergeordneten Element [MeasureGroupAttributeBinding](../data-type/measuregroupattributebinding-data-type-out-of-line-assl.md) -Datentyp.|  
|[HideMemberIf-Element &#40;ASSL&#41;](hidememberif-element-assl.md)|Gibt an, ob und wann ein Element auf einer Ebene aus Clientanwendungen ausgeblendet werden sollte.|  
|[HierarchyID-Element &#40;ASSL&#41;](hierarchyid-element-assl.md)|Enthält die ID für eine [CubeHierarchy](../data-type/hierarchy-data-type-assl.md), [MeasureGroupHierarchy](../data-type/measuregrouphierarchy-data-type-assl.md), oder [PerspectiveHierarchy](../data-type/perspectivehierarchy-data-type-assl.md) Element.|  
|[HierarchyUniqueNameStyle-Element &#40;ASSL&#41;](hierarchyuniquenamestyle-element-assl.md)|Bestimmt, wie eindeutige Namen für Hierarchien generiert werden, die in der `CubeDimension` enthalten sind.|  
|[ID-Element &#40;ASSL&#41;](id-element-assl.md)|Enthält die eindeutige ID des übergeordneten Elements.|  
|[IgnoreUnrelatedDimensions-Element &#40;ASSL&#41;](../collections/dimensions-element-assl.md)|Bestimmt, ob nicht verknüpfte Dimensionen auf ihre höchste Ebene gezwungen werden, wenn Elemente von Dimensionen, die nicht mit der Measuregruppe verknüpft sind, in eine Abfrage eingeschlossen werden.|  
|[ImpersonationInfo-Element &#40;ASSL&#41;](impersonationinfo-element-assl.md)|Enthält die Informationen, die verwendet werden, um das Identitätswechselverhalten beim Zugriff oder Ausführen einer Assembly zu bestimmen.|  
|[ImpersonationInfoSecurity-Element &#40;ASSL&#41;](impersonationinfosecurity-element-assl.md)|Enthält einen schreibgeschützten Wert, der angibt, ob die Sicherheitsanmeldeinformationen, die im `ImpersonationInfo`-Datentyp geliefert werden, geändert wurden.|  
|[ImpersonationMode-Element &#40;ASSL&#41;](impersonationmode-element-assl.md)|Enthält einen Wert, der die Identitätswechselmethode für Elemente angibt, die aus dem `ImpersonationInfo`-Datentyp abgeleitet wurden.|  
|[InstanceSelection-Element &#40;ASSL&#41;](instanceselection-element-assl.md)|Stellt einen Hinweis für Clientanwendungen bezüglich der Anzeige einer Liste von Elementen bereit, der auf der erwarteten Anzahl von Elementen in der Liste basiert.|  
|[IntermediateCubeDimensionID-Element &#40;ASSL&#41;](intermediatecubedimensionid-element-assl.md)|Enthält die ID der Dimension, die eine Referenzdimension mit einer Measuregruppe verknüpft.|  
|[IntermediateGranularityAttributeID-Element &#40;ASSL&#41;](intermediategranularityattributeid-element-assl.md)|Enthält die ID des Granularitätsattributs in der Zwischencubedimension, die verwendet wird, um eine Bezugsdimension mit einer Zwischendimension zu verknüpfen.|  
|[InvalidXmlCharacters-Element &#40;ASSL&#41;](invalidxmlcharacters-element-assl.md)|Gibt die Behandlungsmethode für ungültige XML-Zeichen in den Quelldaten an.|  
|[Invocation-Element &#40;ASSL&#41;](invocation-element-assl.md)|Gibt an, wie ein `Action` aufgerufen werden sollte.|  
|[IsAggregatable-Element &#40;ASSL&#41;](isaggregatable-element-assl.md)|Gibt an, ob die Werte der [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) -Elements aggregiert werden können.|  
|[IsKey-Element &#40;ASSL&#41;](iskey-element-assl.md)|Gibt an, ob die Spalte den Schlüssel für den Fall in einem `MiningStructure`-Element bereitstellt.|  
|[Isolation-Element &#40;ASSL&#41;](isolation-element-assl.md)|Gibt die Isolationsstufe für ein Element, das von abgeleitet ist die [DataSource](../data-type/datasource-data-type-assl.md) -Datentyp.|  
|[KeyDuplicate-Element &#40;ASSL&#41;](keyduplicate-element-assl.md)|Bestimmt, wie [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] einen doppelten Schlüssel-Fehler behandelt, wenn einer während der Verarbeitung auftritt.|  
|[KeyErrorAction-Element &#40;ASSL&#41;](keyerroraction-element-assl.md)|Gibt die Aktion an, die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] beim Auftreten eines Fehlers in einem Schlüssel ergreift.|  
|[KeyErrorLimit-Element &#40;ASSL&#41;](keyerrorlimit-element-assl.md)|Enthält die Anzahl der Fehler, die während der Verarbeitung zulässig sind.|  
|[KeyErrorLimitAction-Element &#40;ASSL&#41;](keyerrorlimitaction-element-assl.md)|Gibt die Aktion an, die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ausführt, wenn die schlüsselfehlerzahl, wird angegeben, der [KeyErrorLimit](keyerrorlimit-element-assl.md) -Element erreicht wird.|  
|[KeyErrorLogFile-Element &#40;ASSL&#41;](../objects/file-element-assl.md)|Enthält den Dateinamen für die Protokollierung von Verarbeitungsfehlern.|  
|[KeyNotFound-Element &#40;ASSL&#41;](keynotfound-element-assl.md)|Gibt die Reaktion von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] auf Fehler in der referentiellen Integrität an.|  
|[KeyUniquenessGuarantee-Element &#40;ASSL&#41;](keyuniquenessguarantee-element-assl.md)|Gibt an, ob die Beziehung zwischen dem Attributschlüssel und seinem Namen und die Beziehung zu verknüpften Attributen garantiert gültig ist.|  
|[KpiID-Element &#40;ASSL&#41;](kpiid-element-assl.md)|Enthält eine ID, die ein `Kpi`-Element einem `Perspective`-Element zuordnet.|  
|[Language-Element &#40;ASSL&#41;](language-element-assl.md)|Enthält den Sprachenbezeichner des übergeordneten Elements.|  
|[LastProcessed-Element &#40;ASSL&#41;](lastprocessed-element-assl.md)|Enthält den schreibgeschützten Zeitstempel, der angibt, wann die Datenbank, die das übergeordnete Element enthält, zuletzt verarbeitet wurde.|  
|[LastSchemaUpdate-Element &#40;ASSL&#41;](lastschemaupdate-element-assl.md)|Enthält den schreibgeschützten Zeitstempel für die Metadatenaktualisierung des übergeordneten Elements.|  
|[LastUpdate-Element &#40;ASSL&#41;](lastupdate-element-assl.md)|Enthält einen schreibgeschützten Zeitstempel, der den Zeitpunkt der letzten Änderung an der zugehörigen `Database` oder jeglichen anderen Hauptobjekten, die in der Datenbank enthalten sind, angibt.|  
|[Latency-Element &#40;ASSL&#41;](latency-element-assl.md)|Definiert die "Kulanzfrist" zwischen der frühesten Benachrichtigung und dem Zeitpunkt, wenn der MOLAP-Images zerstört werden.|  
|[LogFileAppend-Element &#40;ASSL&#41;](logfileappend-element-assl.md)|Bestimmt, ob das `Trace`-Element seine Protokollierungsausgabe an die vorhandene Protokolldatei anfügt oder sie überschreibt.|  
|[LogFileName-Element &#40;ASSL&#41;](logfilename-element-assl.md)|Enthält den Dateinamen der Protokolldatei des `Trace`-Elements.|  
|[LogFileRollover-Element &#40;ASSL&#41;](logfilerollover-element-assl.md)|Gibt an, ob die Protokollierung `Trace` Ausgabe sollte in eine neue Datei übergeben oder beendet, wenn die maximale Protokolldateigröße, muss angegeben werden, [LogFileSize](logfilesize-element-assl.md) erreicht ist.|  
|[LogFileSize-Element &#40;ASSL&#41;](logfilesize-element-assl.md)|Gibt die maximale Protokolldateigröße in MB an.|  
|[ManagedProvider-Element &#40;ASSL&#41;](managedprovider-element-assl.md)|Enthält den Namen des verwalteten Anbieters, der von einem Element verwendet wird, das vom `DataSource`-Datentyp abgeleitet ist.|  
|[ManufacturingExtraMonthQuarter-Element &#40;ASSL&#41;](manufacturingextramonthquarter-element-assl.md)|Definiert den Monat des Produktionszeitraums, dem ein zusätzlicher Monat für ein `TimeBinding`-Element zugeordnet wird.|  
|[ManufacturingFirstMonth-Element &#40;ASSL&#41;](manufacturingfirstmonth-element-assl.md)|Definiert den ersten Produktionsmonat für ein `TimeBinding`-Element.|  
|[ManufacturingFirstWeekOfMonth-Element &#40;ASSL&#41;](manufacturingfirstweekofmonth-element-assl.md)|Definiert die erste Woche des Produktionsmonats für ein `TimeBinding`-Element.|  
|[MasterDatasourceID-Element &#40;ASSL&#41;](masterdatasourceid-element-assl.md)|Enthält die Masterdatenquellen-ID für ein `Database`-Element.|  
|[Materialization-Element &#40;ASSL&#41;](materialization-element-assl.md)|Gibt den Typ der Beziehung zwischen der Measuregruppe und der Referenzdimension an.|  
|[MaxActiveConnections-Element &#40;ASSL&#41;](maxactiveconnections-element-assl.md)|Enthält die maximale Anzahl gleichzeitiger Verbindungen, die für ein Element zulässig sind, abgeleitet vom `DataSource`-Datentyp.|  
|[MdxMissingMemberMode-Element &#40;ASSL&#41;](mdxmissingmembermode-element-assl.md)|Legt die Verarbeitung fehlender Elemente in MDX-Anweisungen fest.|  
|[MeasureExpression-Element &#40;ASSL&#41;](measureexpression-element-assl.md)|Enthält den MDX-Ausdruck, der ein Measure definiert.|  
|[MeasureGroupID-Element &#40;ASSL&#41;](measuregroupid-element-assl.md)|Ordnet dem übergeordneten Element, der Bindung oder Out-of-Line-Bindung eine `MeasureGroup` zu.|  
|[MeasureID-Element &#40;ASSL&#41;](measureid-element-assl.md)|Ordnet dem übergeordneten Element ein `Measure`-Element zu.|  
|[MeasureQualificaton-Element &#40;ASSL&#41;](measurequalificaton-element-assl.md)|Bestimmt, ob die Measures in der `MeasureGroup` ein Präfix erhalten.|  
|[MemberNamesUnique-Element &#40;ASSL&#41;](membernamesunique-element-assl.md)|Bestimmt, ob Elementnamen im übergeordneten Element eindeutig sein müssen.|  
|[MemberUniqueNameStyle-Element &#40;ASSL&#41;](memberuniquenamestyle-element-assl.md)|Bestimmt, wie eindeutige Namen für Elemente in Hierarchien generiert werden, die im `CubeDimension`-Element enthalten sind.|  
|[MembersWithData-Element &#40;ASSL&#41;](memberswithdata-element-assl.md)|Bestimmt, ob Nichtblatt-Datenelemente im übergeordneten Attribut angezeigt werden.|  
|[MembersWithDataCaption-Element &#40;ASSL&#41;](memberswithdatacaption-element-assl.md)|Stellt eine Vorlagenzeichenfolge bereit, die zum Erstellen von Beschriftungen für die vom System generierten Datenelemente verwendet wird.|  
|[MimeType-Element &#40;ASSL&#41;](mimetype-element-assl.md)|Enthält, falls anwendbar, den MIME-Typ (Multipurpose Internet Mail Extensions) der Daten, die vom übergeordneten `DataItem`-Element dargestellt werden.|  
|[MiningModelID-Element &#40;ASSL&#41;](miningmodelid-element-assl.md)|Ordnet einer Data Mining-Dimension ein Miningmodell zu.|  
|[Namen von Element &#40;ASSL&#41;](name-element-assl.md)|Enthält den Namen des übergeordneten Elements.|  
|[NamingTemplate-Element &#40;ASSL&#41;](namingtemplate-element-assl.md)|Definiert, wie Ebenen in einer Über-/Unterordnungshierarchie, die vom übergeordneten `DimensionAttribute`-Element erstellt wurden, benannt werden.|  
|[NonEmptyBehavior-Element &#40;ASSL&#41;](nonemptybehavior-element-assl.md)|Bestimmt das Verhalten für nicht leere, dem übergeordneten Element des `CalculationProperty`-Elements zugeordnete Elemente.|  
|[NotificationTechnique-Element &#40;ASSL&#41;](notificationtechnique-element-assl.md)|Gibt an, ob [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oder eine externe Clientanwendung die Benachrichtigungen verarbeitet.|  
|[NullKeyConvertedToUnknown-Element &#40;ASSL&#41;](nullkeyconvertedtounknown-element-assl.md)|Gibt die Aktion an, die beim Auftreten eines NULL-Konvertierungsfehlers ergriffen werden soll.|  
|[NullKeyNotAllowed-Element &#40;ASSL&#41;](nullkeynotallowed-element-assl.md)|Legt fest, wie die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Verarbeitungs-Engine einen NULL-Schlüsselfehler handhabt, der während der Verarbeitung aufgetreten ist.|  
|[NullProcessing-Element &#40;ASSL&#41;](nullprocessing-element-assl.md)|Definiert, wie NULL-Werte verarbeitet werden.|  
|[OnlineMode-Element &#40;ASSL&#41;](onlinemode-element-assl.md)|Gibt an, ob die Datenbank sofort nach dem Initiieren der Cache-Neuerstellung oder erst nach Abschluss der Cache-Neuerstellung wieder online geschaltet wird.|  
|[OptimizedState-Element &#40;ASSL&#41;](state-element-assl.md)|Bestimmt die Optimierungsebene, die auf die Hierarchie angewendet wird.|  
|[Optionality-Element &#40;ASSL&#41;](optionality-element-assl.md)|Gibt die Optionalität der Elemente eines `AttributeRelationship`-Elements an.|  
|[OrderBy-Element &#40;ASSL&#41;](orderby-element-assl.md)|Beschreibt das Anordnen der im Attribut enthaltenen Elemente.|  
|[OrderByAttributeID-Element &#40;ASSL&#41;](orderbyattributeid-element-assl.md)|Identifiziert ein anderes Attribut, um die Mitglieder der Reihenfolge der [Dimension](../data-type/dimensionattribute-data-type-assl.md) Attribut.|  
|[Ordinal-Element &#40;ASSL&#41;](ordinal-element-assl.md)|Gibt die Ordinalzahl an, an die in Auflistungen wie Schlüsseln und Übersetzungen gebunden wird.|  
|[OverrideBehavior-Element &#40;ASSL&#41;](overridebehavior-element-assl.md)|Zeigt das Verhalten in Bezug auf das Überschreiben von der Beziehung an, die durch ein `AttributeRelationship`-Element beschrieben wird.|  
|[PartitionID-Element &#40;ASSL&#41;](partitionid-element-assl.md)|Ordnet einem übergeordneten Element, der Bindung oder Out-of-Line-Bindung ein `Partition`-Element zu.|  
|[Password-Element &#40;ASSL&#41;](password-element-assl.md)|Enthält das Kennwort des Benutzerkontos für das `ImpersonationInfo`-Element.|  
|[Pfadelement &#40;ASSL&#41;](path-element-assl.md)|Der Pfad enthält, gemäß Bereitstellung durch eine Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], eines Berichts ein, die die [ReportAction](../data-type/reportaction-data-type-assl.md) Element.|  
|[PendingValue-Element &#40;ASSL&#41;](pendingvalue-element-assl.md)|Enthält den schreibgeschützten ausstehenden Wert des zugeordneten `ServerProperty`-Elements.|  
|[PermissionsSet-Element &#40;ASSL&#41;](permissionset-element-assl.md)|Identifiziert den zugeordneten Berechtigungssatz ein [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework-Assembly.|  
|[Persistence-Element &#40;ASSL&#41;](persistence-element-assl.md)|Bestimmt, welche Teile der gebundenen Quelldaten dynamisch sind und mithilfe der vom angegebenen Häufigkeit auf Updates überprüft werden die [RefreshPolicy](refreshpolicy-element-assl.md) Element.|  
|[Element verarbeiten &#40;ASSL&#41;](process-element-assl.md)|Bestimmt, ob ein Benutzer Zugriff auf den Besitzer eines übergeordneten Elements hat.|  
|[ProcessingMode-Element &#40;ASSL&#41;](processingmode-element-assl.md)|Gibt an, ob die Instanz während oder nach der Verarbeitung indizieren und aggregieren soll.|  
|[ProcessingPriority-Element &#40;ASSL&#41;](processingpriority-element-assl.md)|Bestimmt die Verarbeitungspriorität des übergeordneten Objekts während Hintergrundvorgängen wie verzögerter Aggregation, Indizierung oder Clustererstellung.|  
|[ProcessingQuery-Element &#40;ASSL&#41;](query-element-assl.md)|Enthält den parametrisierten Text der Abfrage, die für eine Benachrichtigung über den inkrementellen Verarbeitungsstatus ausgeführt werden muss.|  
|[ProductName-Element &#40;ASSL&#41;](productname-element-assl.md)|Enthält den schreibgeschützten Produktnamen der Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], die einem `Server`-Element zugeordnet wird.|  
|[Abfrageelement &#40;ASSL&#41;](query-element-assl.md)|Enthält den Text der Abfrage, die für die Benachrichtigung ausgeführt werden muss.|  
|[QueryDefinition-Element &#40;ASSL&#41;](querydefinition-element-assl.md)|Enthält einen nicht transparenten Ausdruck für eine zugeordnete Abfrage ein `DataSource` Element in eine [QueryBinding](../data-type/querybinding-data-type-assl.md) Element.|  
|[Element lesen &#40;ASSL&#41;](read-element-assl.md)|Bestimmt, ob Daten oder Metadaten für gelesen werden, kann eine bestimmte [CubeDimensionPermission](../data-type/permission-data-type-assl.md) oder [Berechtigung](../data-type/permission-data-type-assl.md) Element.|  
|[ReadDefinition-Element &#40;ASSL&#41;](readdefinition-element-assl.md)|Bestimmt, ob Elemente die Datenbankdefinition oder die Definition der Objekte in der Datenbank lesen können.|  
|[ReadSourceData-Element &#40;ASSL&#41;](readsourcedata-element-assl.md)|Bestimmt, wie eindeutige Namen für Hierarchien generiert werden, die in der `CubePermission` enthalten sind.|  
|[RefreshInterval-Element &#40;ASSL&#41;](refreshinterval-element-assl.md)|Gibt das Intervall an, in dem die gebundenen Daten, die dem übergeordneten Element zugeordnet sind, aktualisiert werden.|  
|[RefreshPolicy-Element &#40;ASSL&#41;](refreshpolicy-element-assl.md)|Bestimmt, wie oft im dynamischen Teil der Dimension oder Measuregruppe (gemäß der [Persistenz](persistence-element-assl.md) Element) wird auf Änderungen überprüft.|  
|[RelationshipType-Element &#40;ASSL&#41;](relationshiptype-element-assl.md)|Gibt an, ob die Elementbeziehungen einer `AttributeRelationship` geändert werden können.|  
|[RemoteDatasourceID-Element &#40;ASSL&#41;](remotedatasourceid-element-assl.md)|Gibt die ID der OLAP-Datenquelle an, die auf die Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verweist, auf der die Remotepartition gespeichert ist.|  
|[ReportingFirstMonth-Element &#40;ASSL&#41;](reportingfirstmonth-element-assl.md)|Definiert den ersten Berichtsmonat des `TimeBinding`-Elements.|  
|[ReportingFirstWeekOfMonth-Element &#40;ASSL&#41;](reportingfirstweekofmonth-element-assl.md)|Definiert die erste Woche des Berichtsmonats des `TimeBinding`-Elements.|  
|[ReportingWeekToMonthPattern-Element &#40;ASSL&#41;](reportingweektomonthpattern-element-assl.md)|Definiert das Woche-auf-Monats-Berichtsmuster für das `TimeBinding`-Element.|  
|[ReportServer-Element &#40;ASSL&#41;](reportserver-element-assl.md)|Enthält den Namen der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Instanz, die von `ReportAction` verwendet wird.|  
|[RequiresRestart-Element &#40;ASSL&#41;](requiresrestart-element-assl.md)|Enthält einen schreibgeschützten Wert, der einem `ServerProperty`-Element zugeordnet ist, das bestimmt, ob eine Änderung des Werts der Servereigenschaft es erforderlich macht, dass für ein Inkrafttreten der Änderung die Instanz neu gestartet wird.|  
|[RoleID-Element &#40;ASSL&#41;](roleid-element-assl.md)|Identifiziert die Rolle, für die Berechtigungen definiert werden.|  
|[Root-Element &#40;ASSL&#41;](root-element-assl.md)|Enthält die Daten (Rowset) für eine Datenquelle.|  
|[RootMemberIf-Element &#40;ASSL&#41;](rootmemberif-element-assl.md)|Bestimmt, wie das Stammelement oder die Elemente eines übergeordneten Attributs identifiziert werden.|  
|[Schema-Element &#40;ASSL&#41;](schema-element-assl.md)|Enthält das Schema der Datenquellensicht.|  
|[ScriptCacheProcessingMode-Element &#40;ASSL&#41;](scriptcacheprocessingmode-element-assl.md)|Gibt an, ob der Server den Skriptcache während oder nach der Verarbeitung erstellen soll.|  
|[SilenceInterval-Element &#40;ASSL&#41;](silenceinterval-element-assl.md)|Definiert die Mindestdauer, die die Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] vor dem Starten des MOLAP-Imagingprozesses anhält.|  
|[SilenceOverrideInterval-Element &#40;ASSL&#41;](silenceoverrideinterval-element-assl.md)|Definiert, wie viel Zeit nach dem Empfang der ursprünglichen Benachrichtigung vergehen muss, bis das MOLAP-Imaging unbedingt beginnt.|  
|[Slice-Element &#40;ASSL&#41;](slice-element-assl.md)|Enthält einen MDX-Ausdruck, der den in einer Partition enthaltenen Slice definiert.|  
|[SolveOrder-Element &#40;ASSL&#41;](solveorder-element-assl.md)|Gibt die Lösungsreihenfolge an, in der das `CalculationProperty`-Element auf ein berechnetes Element oder eine berechnete Zelldefinition angewendet wird.|  
|[Source-Element &#40;Bindung&#41; &#40;ASSL&#41;](source-element-binding-assl.md)|Identifiziert die Datenquelle, an die das übergeordnete Element gebunden ist.|  
|[Source-Element &#40;ComAssembly&#41; &#40;ASSL&#41;](source-element-comassembly-assl.md)|Enthält den Dateinamen oder den programmtechnischen Bezeichner (ProgID) für eine COM-Komponente (Component Object Model).|  
|[Source-Element &#40;Measure&#41; &#40;ASSL&#41;](source-element-measure-assl.md)|Enthält die Details der Quelle, die den Wert des `Measure`-Elements enthält.|  
|[SourceAttributeID-Element &#40;ASSL&#41;](sourceattributeid-element-assl.md)|Enthält die ID des Quellattributs, auf denen die [Ebene](../objects/level-element-assl.md) -Element basiert.|  
|[SourceColumnID-Element &#40;ASSL&#41;](sourcecolumnid-element-assl.md)|Enthält die ID der Quellminingstrukturspalte im `MiningStructure`-Vorgängerelement.|  
|[Status des Elements &#40;ASSL&#41;](state-element-assl.md)|Enthält einen schreibgeschützten Wert, der den aktuellen Verarbeitungsstatus des übergeordneten Elements beschreibt.|  
|[Status-Element &#40;ASSL&#41;](status-element-assl.md)|Enthält einen MDX-Ausdruck, der für ein `Kpi`-Element einen Statusindikator zurückgibt.|  
|[StatusGraphic-Element &#40;ASSL&#41;](statusgraphic-element-assl.md)|Enthält die empfohlene grafische Darstellung des Status des `Kpi`-Elements.|  
|[StopTime-Element &#40;ASSL&#41;](stoptime-element-assl.md)|Gibt das Datum und die Zeit an, zu denen ein `Trace`-Element beendet werden sollte.|  
|[StorageLocation-Element &#40;ASSL&#41;](storagelocation-element-assl.md)|Enthält den Speicherort des Dateisystems für den Inhalt des übergeordneten Elements.|  
|[StorageMode-Element &#40;ASSL&#41;](storagemode-element-assl.md)|Bestimmt den Speichermodus für das übergeordnete Element.|  
|[TableID-Element &#40;ASSL&#41;](tableid-element-assl.md)|Enthält die ID der Tabelle (vom `DataSourceView`-Element), die dem übergeordneten Element zugeordnet ist.|  
|[Target-Element &#40;ASSL&#41;](target-element-assl.md)|Identifiziert das Ziel des `Action`-Elements.|  
|[TargetType-Element &#40;ASSL&#41;](targettype-element-assl.md)|Kennzeichnet den Elementtyp des Elements, der der [Ziel](target-element-assl.md) Element.|  
|[Text-Element &#40;ASSL&#41;](text-element-assl.md)|Enthält den Text einer [Befehl](../objects/command-element-assl.md) Element.|  
|[Timeout-Element &#40;ASSL&#41;](timeout-element-assl.md)|Gibt die Zeit in Sekunden an, nach der ein Datenabfrageversuch einen Timeout meldet.|  
|[Trend-Element &#40;ASSL&#41;](trend-element-assl.md)|Enthält einen MDX-Ausdruck, der für ein `Kpi`-Element einen Trendindikator zurückgibt.|  
|[TrendGraphic-Element &#40;ASSL&#41;](trendgraphic-element-assl.md)|Enthält die empfohlene grafische Darstellung des Trends des `Kpi`-Elements.|  
|[Trimming-Element &#40;ASSL&#41;](trimming-element-assl.md)|Gibt an, wie die Daten der Datenquelle eingeschränkt werden.|  
|[Type-Element &#40;Aktion&#41; &#40;ASSL&#41;](type-element-action-assl.md)|Enthält den Typ des `Action`-Elements.|  
|[Type-Element &#40;Bindung&#41; &#40;ASSL&#41;](type-element-binding-assl.md)|Enthält den Typ der Attributbindung.|  
|[Type-Element &#40;ClrAssemblyFile&#41; &#40;ASSL&#41;](type-element-clrassemblyfile-assl.md)|Gibt den Dateityp von einer der Dateien, die zu .NET Framework-Assembly gehören.|  
|[Type-Element &#40;Dimension&#41; &#40;ASSL&#41;](type-element-dimension-assl.md)|Stellt Informationen über den Inhalt der Dimension bereit.|  
|[Type-Element &#40;DimensionAttribute&#41; &#40;ASSL&#41;](type-element-dimensionattribute-assl.md)|Enthält den Typ des Attributs.|  
|[Type-Element &#40;MeasureGroup&#41; &#40;ASSL&#41;](type-element-measuregroup-assl.md)|Gibt den Typ der `MeasureGroup` an.|  
|[Type-Element &#40;MeasureGroupAttribute&#41; &#40;ASSL&#41;](type-element-measuregroupattribute-assl.md)|Enthält den Typ des eine [MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md) Element.|  
|[Type-Element &#40;MiningStructureColumn&#41; &#40;ASSL&#41;](type-element-miningstructurecolumn-assl.md)|Enthält den Typ des der [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) Element.|  
|[Type-Element &#40;Partition&#41; &#40;ASSL&#41;](type-element-partition-assl.md)|Enthält den Typ des `Partition`-Elements.|  
|[Type-Element &#40;PerspectiveCalculation&#41; &#40;ASSL&#41;](type-element-perspectivecalculation-assl.md)|Gibt den Typ des der [PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md) Element.|  
|[UnknownMember-Element &#40;ASSL&#41;](unknownmember-element-assl.md)|Gibt an, ob das unbekannte Element sichtbar ist.|  
|[UnknownMemberName-Element &#40;ASSL&#41;](unknownmembername-element-assl.md)|Enthält die Beschriftung in der standardmäßigen Sprache der Dimension für das unbekannte Element der Dimension.|  
|[Usage-Element &#40;DimensionAttribute&#41; &#40;ASSL&#41;](usage-element-dimensionattribute-assl.md)|Beschreibt die Verwendung eines Attributs.|  
|[Usage-Element &#40;MiningModelColumn&#41; &#40;ASSL&#41;](usage-element-miningmodelcolumn-assl.md)|Beschreibt, wie die zugeordnete Spalte im übergeordneten `MiningStructure` verwendet wird.|  
|[Wert der Elements &#40;ASSL&#41;](value-element-assl.md)|Enthält den Wert des übergeordneten Elements.|  
|[Version-Element &#40;ASSL&#41;](version-element-assl.md)|Enthält die schreibgeschützte Versionsnummer der Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], die vom `Server`-Element dargestellt wird.|  
|[Visibility-Element &#40;ASSL&#41;](visibility-element-assl.md)|Definiert die Sichtbarkeit einer [Anmerkung](../objects/annotation-element-assl.md) Element.|  
|[Visible-Element &#40;ASSL&#41;](visible-element-assl.md)|Bestimmt die Sichtbarkeit des übergeordneten Elements.|  
|[VisualTotals-Element &#40;ASSL&#41;](visualtotals-element-assl.md)|Enthält einen MDX-Ausdruck, der bestimmt, ob sichtbare Gesamtwerte für Elemente dieses Attributs angezeigt werden.|  
|[Write-Element &#40;ASSL&#41;](write-element-assl.md)|Bestimmt, ob für ein bestimmtes `CubeDimensionPermission`- oder `Permission`-Element Daten oder Metadaten geschrieben werden können.|  
|[WriteEnabled-Element &#40;ASSL&#41;](writeenabled-element-assl.md)|Gibt an, ob das Rückschreiben von Dimensionen unterstützt wird (unterliegt den Sicherheitsberechtigungen).|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Element-Hierarchie &#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  
