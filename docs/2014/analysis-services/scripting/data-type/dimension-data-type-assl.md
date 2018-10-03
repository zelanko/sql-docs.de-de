---
title: Dimension-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Dimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Dimension data type
ms.assetid: 3fe6adc2-5206-44c3-a689-a731705f43ca
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: af61be445ec8b8a0ce71de56d17391ef4c30304b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48093440"
---
# <a name="dimension-data-type-assl"></a>Dimension-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der eine Datenbankdimension darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Dimension>  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreatedTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <Description>...</Description>  
   <Source>...</Source>  
   <MiningModelID>...</MiningModelID>  
   <Type>...</Type>  
   <UnknownMember>...</UnknownMember>  
   <MdxMissingMemberMode>...</MdxMissingMemberMode>  
   <ErrorConfiguration>...</ErrorConfiguration>  
   <StorageMode>...</StorageMode>  
   <WriteEnabled>...</WriteEnabled>  
   <ProcessingPriority>...</ProcessingPriority>  
   <LastProcessed>...</LastProcessed>  
   <DimensionPermissions>...</DimensionPermissions>  
   <DependsOnDimensionID>...</DependsOnDimensionID>  
   <Language>...</Language>  
   <Collation>...</Collation>  
   <UnknownMemberName>...</UnknownMemberName>  
   <UnknownMemberTranslations>...</UnknownMemberTranslations>  
   <State>...</State>  
   <ProactiveCaching>...</ProactiveCaching>  
   <ProcessingMode>...</ProcessingMode>  
   <CurrentStorageMode>...</CurrentStorageMode>  
   <Translations>...</Translations>  
   <Attributes>...</Attributes>  
   <AttributeAllMemberName>...</AttributeAllMemberName>  
   <AttributeAllMemberTranslations>...</AttributeAllMemberTranslations>  
   <Hierarchies>...</Hierarchies>  
   <Relationships>...</Annotations>  
   <Annotations>...</Annotations>  
</Dimension>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|None|  
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[Anmerkungen](../collections/annotations-element-assl.md), [AttributeAllMemberName](../properties/name-element-assl.md), [AttributeAllMemberTranslations](../collections/translations-element-assl.md), [Attribute](../collections/attributes-element-assl.md), [Auflistung](../properties/collation-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [CurrentStorageMode](../properties/storagemode-element-assl.md), [DependsOnDimensionID](../properties/id-element-assl.md), [Beschreibung](../properties/description-element-assl.md), [DimensionPermissions](../collections/dimensionpermissions-element-assl.md), [ErrorConfiguration](../objects/errorconfiguration-element-assl.md), [Hierarchien](../collections/hierarchies-element-assl.md), [ID](../properties/id-element-assl.md), [Sprache](../properties/language-element-assl.md), [LastProcessed](../properties/lastprocessed-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [MdxMissingMemberMode](../properties/mdxmissingmembermode-element-assl.md), [MiningModelID](../properties/miningmodelid-element-assl.md), [Name](../properties/name-element-assl.md), [ProactiveCaching](../objects/proactivecaching-element-assl.md), [ProcessingMode](../properties/processingmode-element-assl.md), [ProcessingPriority](../properties/processingpriority-element-assl.md), [Beziehungen](../collections/relationships-element-assl.md), [Quelle](../properties/source-element-binding-assl.md), [Status](../properties/state-element-assl.md), [StorageMode](../properties/storagemode-element-assl.md), [Übersetzungn](../collections/translations-element-assl.md), [Typ](../properties/type-element-dimension-assl.md), [UnknownMember](../objects/member-element-assl.md), [UnknownMemberName](../properties/unknownmembername-element-assl.md), [UnknownMemberTranslations](../collections/unknownmembertranslations-element-assl.md), [WriteEnabled](../properties/enabled-element-assl.md)|  
|Abgeleitete Elemente|[Dimension](../objects/dimension-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Dieser Datentyp verfügt über die folgenden Überprüfungen unter den DeploymentMode-Werten 1 (SharePoint) und 2 (Tabelle).  
  
-   *WriteEnabled* untergeordnetes Element muss festgelegt werden `False`  
  
-   *UnknownMember* untergeordnetes Element muss festgelegt werden `AutomaticNull`  
  
-   Alle eindeutigen Attribute müssen *NullProcessing* untergeordnetes Element festgelegt `Error`  
  
 Die folgenden untergeordneten Attribute werden nicht unter den DeploymentMode-Werten 1 (SharePoint) und 2 (Tabelle) unterstützt.  
  
-   *DimensionPermissions*  
  
-   *MiningModelID*  
  
-   *ProactiveCaching*  
  
 Die entsprechenden Elemente im Analysis Management Objects (AMO)-Objektmodell sind <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.AggregationDimension>, <xref:Microsoft.AnalysisServices.AggregationDesignDimension>, <xref:Microsoft.AnalysisServices.CubeDimension>, <xref:Microsoft.AnalysisServices.MeasureGroupDimension>, und <xref:Microsoft.AnalysisServices.PerspectiveDimension>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
