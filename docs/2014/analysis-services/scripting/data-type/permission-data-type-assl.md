---
title: Permission-Datentyp (ASSL) | Microsoft Docs
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
- Permission Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Permission
helpviewer_keywords:
- Permission data type
ms.assetid: 5f309544-59f8-4432-b1eb-b7c1a049f8df
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ff5fb67e4f7989fb329e60a106ea8e6d0c734c97
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046990"
---
# <a name="permission-data-type-assl"></a>Permission-Datentyp (ASSL)
  Definiert einen abstrakten, Grunddatentyp, der Informationen über eine individuelle Berechtigung darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Permission>  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreateTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <RoleID>...</RoleID>  
   <Description>...</Description>  
   <Process>...</Process>  
   <ReadDefinition>...</ReadDefinition>  
   <Read>...</Read>  
   <Write>...</Write>  
   <Annotations>...</Annotations>  
</Permission>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|InclusionThresholdSetting|  
|Abgeleitete Datentypen|[CubePermission](../objects/cubepermission-element-assl.md), [DatabasePermission](../objects/databasepermission-element-assl.md), [DimensionPermission](permission-data-type-assl.md), [MiningModelPermission](../objects/miningmodelpermission-element-assl.md), [miningstructurepermission-Objekte](../objects/miningstructurepermission-element-assl.md)|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[Anmerkungen](../collections/annotations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [Beschreibung](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [Namen](../properties/name-element-assl.md), [Prozess](../properties/process-element-assl.md), [lesen](../properties/read-element-assl.md), [ReadDefinition](../properties/readdefinition-element-assl.md), [RoleID](../properties/roleid-element-assl.md), [schreiben](../properties/write-element-assl.md)|  
|Abgeleitete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 `Permission` fungiert als abstrakter Basistyp für eine Anzahl abgeleiteter Berechtigungstypen, die in einer Instanz von verwendet [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Diesem Datentyp sind unter dem DeploymentMode-Wert 2 (tabellarischer Servermodus) die folgenden Überprüfungen zugeordnet:  
  
-   *Prozess* Standardwert des Attributs wird festgelegt, um `False`, außer wenn der Benutzer über die **aktualisieren** Berechtigung. Für Benutzer mit der **aktualisieren** Berechtigung der *Prozess* Attributwert wird festgelegt, um `True`.  
  
-   *ReadDefinition* Attributwert wird festgelegt, um `None`; jeder andere Wert wird ein Fehler generiert.  
  
-   *Lesen* Attributwert wird festgelegt, um `Allowed` für Benutzer mit der **Benutzer** Berechtigung und `None` Wenn der Benutzer zugewiesen werden, die **aktualisieren** Berechtigung; Wenn ein Benutzer sowohl **Benutzer** und **aktualisieren** verfügt, wird das Attribut wird festgelegt, um `Allowed`. Für Benutzer mit Administratorrechten wird der Attributwert auf `Allowed` festgelegt.  
  
-   *Schreiben von* Attributwert wird festgelegt, um `None`; jeder andere Wert wird ein Fehler generiert.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Role-Element &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  