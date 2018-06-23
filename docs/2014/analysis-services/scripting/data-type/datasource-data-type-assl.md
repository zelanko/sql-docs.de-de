---
title: DataSource-Datentyp (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DataSource Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DataSource data type
ms.assetid: 05e8de8d-452d-4128-98a6-4437df227fec
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4b30438e709f6762ae194174ae9ab2be06bfd32d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161000"
---
# <a name="datasource-data-type-assl"></a>DataSource-Datentyp (ASSL)
  Definiert einen abstrakten Grunddatentyp, der eine Datenquelle in einem [Datenbank](../objects/database-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DataSource>  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreateTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <ManagedProvider>...</ManagedProvider>  
   <ConnectionString>...</ConnectionString>  
   <ConnectionStringSecurity>...</ConnectionStringSecurity>  
   <ImpersonationInfo>...</ImpersonationInfo>  
   <Isolation>...</Isolation>  
   <MaxActiveConnections>...</MaxActiveConnections>  
   <Description>...</Description>  
   <Timeout>...</Timeout>  
   <Annotations>...</Annotations>  
   <DataSourcePermission>...</DataSourcePermission>  
</DataSource>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|InclusionThresholdSetting|  
|Abgeleitete Datentypen|[RelationalDataSource](datasource-data-type-assl.md), [OlapDataSource](olapdatasource-data-type-assl.md), [PushedDataSource](pusheddatasource-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[Annotations](../collections/annotations-element-assl.md), [ConnectionString](../properties/connectionstring-element-assl.md), [ConnectionStringSecurity](../properties/connectionstringsecurity-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [DataSourcePermission](../collections/datasourcepermissions-element-assl.md), [Description](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [ImpersonationInfo](../properties/impersonationinfo-element-assl.md), [Isolation](../properties/isolation-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [ManagedProvider](../properties/managedprovider-element-assl.md), [MaxActiveConnections](../properties/maxactiveconnections-element-assl.md), [Name](../properties/name-element-assl.md), [Timeout](../properties/timeout-element-assl.md)|  
|Abgeleitete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Beim Definieren von Out-of-Line-Bindungen ist das `Name`-Element optional. Ohne Angabe einer `Name` Element kann Datenquellen innerhalb der Bindung für Cubes, Partitionen usw. definiert werden. Für Datenquellen enthalten, die durch eine `Database` Element `Name` ist ein erforderliches Element.  
  
 Weitere Informationen zu Datenquellen finden Sie unter [Datenquellen in mehrdimensionalen Modellen](../../multidimensional-models/data-sources-in-multidimensional-models.md).  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.DataSource>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  