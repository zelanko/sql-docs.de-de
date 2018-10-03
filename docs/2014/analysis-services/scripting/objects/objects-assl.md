---
title: Objekte (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- ASSL, objects
- objects [Analysis Services Scripting Language]
- Analysis Services Scripting Language, objects
ms.assetid: 0f672b93-c317-47e5-b44d-ecea9b587c98
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 302ad689a3e54a7a9937929b9c20f975fc3cd98f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079610"
---
# <a name="objects-assl"></a>Objekte (ASSL)
  In diesem Referenzabschnitt finden Sie Syntax- und Nutzungsinformationen für jedes Element, das im ASSL-Schema (Analysis Services Scripting Language) als Objekt agiert.  
  
 Obwohl das ASSL-Schema nur XML-Elemente, aus der Sicht eines Entwicklers, enthält die Elemente, die in diesem Abschnitt beschriebenen entsprechen für Objekte, z. B. `Database`, `Cube`, und `Dimension` Objekte, in der Hierarchie der Objekte ein Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Objekte sind niemals Blattebenenelemente im ASSL-Schema, sondern besitzen untergeordnete Elemente und Elemente, die Objekteigenschaften entsprechen.  
  
 In einigen Fällen wird ein Blattebenenelement im Schema, das eine Eigenschaft zu sein scheint, als Objekt klassifiziert, da der Typ des Elements ein Objekttyp ist. Beispielsweise ist die `Source` eines `Dimension`-Objekts vom Typ `DimensionBinding`.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Element|Description|  
|-------------|-----------------|  
|[Konto Element &#40;ASSL&#41;](account-element-assl.md)|Enthält Details über einen Kontotyp innerhalb einer [Datenbank](database-element-assl.md) Element.|  
|[Action-Element &#40;ASSL&#41;](action-element-assl.md)|Enthält Informationen über eine Aktion in einem [Cube](cube-element-assl.md) Element oder ein [Perspektive](perspective-element-assl.md) Element.|  
|[Aggregation-Element &#40;ASSL&#41;](aggregation-element-assl.md)|Definiert eine einzelne Aggregation für eine [Partition](partition-element-assl.md) Element.|  
|[AggregationDesign-Element &#40;ASSL&#41;](aggregationdesign-element-assl.md)|Definiert einen Satz von Aggregationsdefinitionen, die für mehrere Partitionen in einer Datenbank freigegeben sein können.|  
|[AggregationInstance-Element &#40;ASSL&#41;](aggregationinstance-element-assl.md)|Definiert für eine Partition eine Aggregationsinstanz.|  
|[AlgorithmParameter-Element &#40;ASSL&#41;](algorithmparameter-element-assl.md)|Definiert einen Parameter für den Algorithmus ein, die eine [MiningModel](miningmodel-element-assl.md) Element.|  
|[AllMemberTranslation-Element &#40;ASSL&#41;](translation-element-assl.md)|Enthält eine Übersetzung für die Beschriftung des alle-Elements ein [Hierarchie](hierarchy-element-assl.md) Element.|  
|[Annotation-Element &#40;ASSL&#41;](annotation-element-assl.md)|Enthält Elemente, die verwendet werden, um das ASSL-Schema zu erweitern.|  
|[Assembly-Element &#40;ASSL&#41;](assembly-element-assl.md)|Stellt eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Assembly oder eine COM-dynamic Link Library (DLL) zugeordnet eine [Server](server-element-assl.md) Element oder ein [Datenbank](database-element-assl.md) Element.|  
|[-Attribut des Elements &#40;ASSL&#41;](attribute-element-assl.md)|Enthält die Beschreibung eines Attributs.|  
|[AttributeAllMemberTranslation-Element &#40;ASSL&#41;](attributeallmembertranslation-element-assl.md)|Enthält eine Übersetzung für die Beschriftung des alle-Elements ein [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) Element.|  
|[AttributePermission-Element &#40;ASSL&#41;](attributepermission-element-assl.md)|Definiert den Berechtigungen, die Elemente einer [Rolle](role-element-assl.md) Element verfügen, für die Attribute einer individuellen Dimension in einem [Cube](cube-element-assl.md) Element.|  
|[AttributeRelationship-Element &#40;ASSL&#41;](attributerelationship-element-assl.md)|Bietet Details über die Beziehung zwischen zwei Attributen.|  
|[Element sperren &#40;ASSL&#41;](block-element-assl.md)|Enthält alles oder einen Teil des binären Inhalts eine [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) Element.|  
|[Calculation-Element &#40;ASSL&#41;](calculation-element-assl.md)|Weist eine Berechnung einem [Perspektive](perspective-element-assl.md) Element.|  
|[CalculationProperty-Element &#40;ASSL&#41;](calculationproperty-element-assl.md)|Enthält eine Auflistung von Benutzeroberflächeneigenschaften für eine Berechnung, die in verwendet eine [MdxScript](mdxscript-element-assl.md) Element.|  
|[CaptionColumn-Element &#40;ASSL&#41;](column-element-assl.md)|Definiert die Spalte, die die Beschriftung für das Attribut bereitstellt.|  
|[CellPermission-Element &#40;ASSL&#41;](cellpermission-element-assl.md)|Beschreibt den Berechtigungen der Elemente einer [Rolle](role-element-assl.md) Element verfügen, für einzelne Zellen innerhalb einer [Cube](cube-element-assl.md) Element.|  
|[Column-Element &#40;ASSL&#41;](column-element-assl.md)|Beschreibt eine Spalte in der Auflistung der Spalten, die mit dem übergeordneten Element verknüpft ist.|  
|[Befehl Element &#40;ASSL&#41;](command-element-assl.md)|Definiert einen Befehl, der im Kontext des übergeordneten Elements der Befehlsauflistung verfügbar ist.|  
|[Cube-Element &#40;ASSL&#41;](cube-element-assl.md)|Definiert einen regulären, virtuellen oder verknüpften Cube in einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] [Datenbank](database-element-assl.md) Element.|  
|[CubePermission-Element &#40;ASSL&#41;](cubepermission-element-assl.md)|Definiert die Berechtigungen der Elemente eines bestimmten [Rolle](role-element-assl.md) Element in einer bestimmten [Cube](cube-element-assl.md) Element.|  
|[CustomRollupColumn-Element &#40;ASSL&#41;](customrollupcolumn-element-assl.md)|Definiert die Details der Spalte, die eine benutzerdefinierte Rollupformel enthält.|  
|[CustomRollupPropertiesColumn-Element &#40;ASSL&#41;](customrolluppropertiescolumn-element-assl.md)|Definiert die Details einer Spalte, die die Eigenschaften einer benutzerdefinierten Rollupformel bereitstellen.|  
|[Datenelement &#40;ASSL&#41;](data-element-assl.md)|Enthält (in der Auflistung der untergeordneten `Block` Elemente) die binären Inhalte eine [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) Element.|  
|[Database-Element &#40;ASSL&#41;](database-element-assl.md)|Definiert eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Datenbank.|  
|[DatabasePermission-Element &#40;ASSL&#41;](databasepermission-element-assl.md)|Definiert die Standardberechtigungen in einem [Datenbank](database-element-assl.md) -Element für einen bestimmten [Rolle](role-element-assl.md) Element.|  
|[DataSource-Element &#40;ASSL&#41;](datasource-element-assl.md)|Definiert eine Datenquelle in einem [Datenbank](database-element-assl.md) Element.|  
|[DataSourcePermission-Element &#40;ASSL&#41;](datasourcepermission-element-assl.md)|Definiert die Standardberechtigungen in einem [DataSource](../data-type/datasource-data-type-assl.md) -Datentyp für eine bestimmte [Rolle](role-element-assl.md) Element.|  
|[DataSourceView-Element &#40;ASSL&#41;](datasourceview-element-assl.md)|Definiert eine Datenquellensicht ein, die eine [Datenbank](database-element-assl.md) Element.|  
|[Dimension-Element &#40;ASSL&#41;](dimension-element-assl.md)|Definiert eine Dimension.|  
|[DimensionPermission-Element &#40;ASSL&#41;](dimensionpermission-element-assl.md)|Definiert die Berechtigungen, die zu einem bestimmten [Role](role-element-assl.md) -Element für eine spezifische Datenbank- oder Cubedimension gehören.|  
|[ErrorConfiguration-Element &#40;ASSL&#41;](errorconfiguration-element-assl.md)|Gibt Einstellungen für den Umgang mit Fehlern an, die auftreten können, wenn das übergeordnete Element verarbeitet wird.|  
|[Event-Element &#40;ASSL&#41;](event-element-assl.md)|Definiert ein Ereignis als Teil des erfasst werden sollen eine [Ablaufverfolgung](trace-element-assl.md) Element.|  
|[File Element &#40;ASSL&#41;](file-element-assl.md)|Definiert eine der Dateien, aus denen ein [ClrAssembly](../data-type/assembly-data-type-assl.md) Element.|  
|[ForeignKeyColumn-Element &#40;ASSL&#41;](keycolumn-element-assl.md)|Identifiziert den Join zu einer übergeordneten Tabelle für eine relationale Datenquelle.|  
|[Group-Element &#40;ASSL&#41;](group-element-assl.md)|Definiert eine Gruppe von Elementen, die an ein Attribut gebunden sind.|  
|[Hierarchy-Element &#40;ASSL&#41;](hierarchy-element-assl.md)|Definiert eine Hierarchie in einer Dimension.|  
|[IncrementalProcessingNotification-Element &#40;ASSL&#41;](incrementalprocessingnotification-element-assl.md)|Enthält Informationen für die [ProactiveCaching](proactivecaching-element-assl.md) Element über eine Abfrage zum Ermitteln des Fortschritts der inkrementellen Verarbeitung ausgeführt.|  
|[KeyColumn-Element &#40;ASSL&#41;](keycolumn-element-assl.md)|Enthält die Definition einer Spalte, die der Schlüssel oder Teil eines Schlüssels für ein Attribut ist.|  
|[KPI-Element &#40;ASSL&#41;](kpi-element-assl.md)|Definiert einen Key Performance Indicator (KPI) innerhalb einer [Cube](cube-element-assl.md) Element oder ein [Perspektive](perspective-element-assl.md) Element.|  
|[Level-Element &#40;ASSL&#41;](level-element-assl.md)|Definiert eine Ebene in einer [Hierarchie](hierarchy-element-assl.md) Element.|  
|[MdxScript-Element &#40;ASSL&#41;](mdxscript-element-assl.md)|Enthält Informationen über ein Multidimensional Expressions (MDX)-Skript, das zugeordnet ist eine [Cube](cube-element-assl.md) Element.|  
|[Measure-Element &#40;ASSL&#41;](measure-element-assl.md)|Definiert ein Measure.|  
|[MeasureGroup-Element &#40;ASSL&#41;](measuregroup-element-assl.md)|Definiert auf der gleichen Ebene wie die Granularität eine Menge von Measures.|  
|[Member-Element &#40;ASSL&#41;](member-element-assl.md)|Enthält den Namen eines Mitglieds eines [Group](group-element-assl.md) - oder [Role](role-element-assl.md) -Elements.|  
|[MiningModel-Element &#40;ASSL&#41;](miningmodel-element-assl.md)|Definiert ein einzelnes Data Mining-Modell.|  
|[Miningmodelpermissions-Element &#40;ASSL&#41;](miningmodelpermission-element-assl.md)|Definiert die Berechtigungen der Elemente einer [Rolle](role-element-assl.md) Element verfügen, für ein einzelnes [MiningModel](miningmodel-element-assl.md) Element.|  
|[MiningStructure-Element &#40;ASSL&#41;](miningstructure-element-assl.md)|Definiert die Struktur für einen Satz von Miningmodellen.|  
|[Miningstructurepermissions-Element &#40;ASSL&#41;](miningstructurepermission-element-assl.md)|Definiert den Berechtigungen, die Elemente einer [Rolle](role-element-assl.md) Element verfügen, für ein einzelnes [MiningStructure](miningstructure-element-assl.md) Element.|  
|[ModelingFlag-Element &#40;ASSL&#41;](modelingflag-element-assl.md)|Enthält ein Modellierungsflag für eine Spalte in einer Miningstruktur oder einem Miningmodell.|  
|[NameColumn-Element &#40;ASSL&#41;](namecolumn-element-assl.md)|Identifiziert die Spalte, die den Namen des übergeordneten Elements bereitstellt.|  
|[NamingTemplateTranslation-Element &#40;ASSL&#41;](namingtemplatetranslation-element-assl.md)|Stellt eine lokalisierte Übersetzung der `NamingTemplate` -Element eines übergeordneten [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) -Datentyp.|  
|[Partitions-Element &#40;ASSL&#41;](partition-element-assl.md)|Definiert eine Partition einer [MeasureGroup](measuregroup-element-assl.md) Element oder eine partitionsbindung in einem Out-of-Line [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)Element.|  
|[Perspective-Element &#40;ASSL&#41;](perspective-element-assl.md)|Details für eine Perspektive definiert eine [Cube](cube-element-assl.md) Element.|  
|[ProactiveCaching-Element &#40;ASSL&#41;](proactivecaching-element-assl.md)|Definiert die Einstellungen für die proaktive Zwischenspeicherung für das übergeordnete Element.|  
|[QueryNotification-Element &#40;ASSL&#41;](querynotification-element-assl.md)|Enthält Informationen für die [ProactiveCaching](proactivecaching-element-assl.md) Element über eine Abfrage ausgeführt werden, um zu bestimmen, ob eine Datenquelle geändert wurde.|  
|[ReportFormatParameter-Element &#40;ASSL&#41;](reportformatparameter-element-asl.md)|Enthält den Namen und Wert eines Parameters, der angibt, wie eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Bericht bei der Ausführung formatiert ist.|  
|[ReportParameter-Element &#40;ASSL&#41;](reportparameter-element-assl.md)|Enthält den Namen und den Wert eines Parameters, der bei der Ausführung an einen [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Bericht weitergeleitet wird.|  
|[Role-Element &#40;ASSL&#41;](role-element-assl.md)|Enthält Informationen über eine Sicherheitsrolle.|  
|[Server-Element &#40;ASSL&#41;](server-element-assl.md)|Beschreibt Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[ServerProperty-Element &#40;ASSL&#41;](serverproperty-element-assl.md)|Definiert eine zugeordnete Servereigenschaft eine [Server](server-element-assl.md) Element.|  
|[SkippedLevelsColumn-Element &#40;ASSL&#41;](skippedlevelscolumn-element-assl.md)|Stellt die Details einer Spalte bereit, die die Anzahl der übersprungenen (leeren) Ebenen zwischen den einzelnen Elementen und den jeweils übergeordneten Elementen speichert.|  
|[SourceMeasureGroup-Element &#40;ASSL&#41;](sourcemeasuregroup-element-assl.md)|Identifiziert die Measuregruppe, die als Datenquelle für eine Miningstruktur-Spalte dient.|  
|[TableNotification-Element &#40;ASSL&#41;](tablenotification-element-assl.md)|Enthält Informationen für die [ProactiveCaching](proactivecaching-element-assl.md) -Element über eine Tabelle oder Sicht in einer Datenquelle, die geändert wurde.|  
|[Trace-Element &#40;ASSL&#41;](trace-element-assl.md)|Definiert eine Ablaufverfolgung, die abgefragt werden kann.|  
|[Translation-Element &#40;ASSL&#41;](translation-element-assl.md)|Stellt eine lokalisierte Übersetzung für das übergeordnete Element der [Translations](../collections/translations-element-assl.md) -Auflistung bereit.|  
|[UnaryOperatorColumn-Element &#40;ASSL&#41;](unaryoperatorcolumn-element-assl.md)|Definiert die Details einer Spalte, die einen unären Operator bereitstellt.|  
|[UnknownMemberTranslation-Element &#40;ASSL&#41;](unknownmembertranslation-element-assl.md)|Enthält eine Übersetzung für die Beschriftung des der [UnknownMember](../properties/unknownmember-element-assl.md) -Element für eine [Dimension](dimension-element-assl.md) Element.|  
|[ValueColumn-Element &#40;ASSL&#41;](valuecolumn-element-assl.md)|Identifiziert die Spalte, die den Wert des übergeordneten Elements bereitstellt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Element-Hierarchie &#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  
