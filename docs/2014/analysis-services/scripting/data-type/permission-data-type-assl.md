---
title: Permission-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8d12fb71a8ed19ca083e8ec506fba6338f6b58a7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48101941"
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
|Basisdatentypen|None|  
|Abgeleitete Datentypen|[CubePermission](../objects/cubepermission-element-assl.md), [DatabasePermission](../objects/databasepermission-element-assl.md), [DimensionPermission](permission-data-type-assl.md), [MiningModelPermission](../objects/miningmodelpermission-element-assl.md), [MiningStructurePermission](../objects/miningstructurepermission-element-assl.md)|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[Anmerkungen](../collections/annotations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [Beschreibung](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [Namen](../properties/name-element-assl.md), [Prozess](../properties/process-element-assl.md), [lesen](../properties/read-element-assl.md), [ReadDefinition](../properties/readdefinition-element-assl.md), [RoleID](../properties/roleid-element-assl.md), [schreiben](../properties/write-element-assl.md)|  
|Abgeleitete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 `Permission` fungiert als abstrakter Basistyp für eine Anzahl abgeleiteter Berechtigungstypen, die in einer Instanz von verwendet [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Diesem Datentyp sind unter dem DeploymentMode-Wert 2 (tabellarischer Servermodus) die folgenden Überprüfungen zugeordnet:  
  
-   *Prozess* Standardwert des Attributs wird festgelegt, um `False`, außer wenn der Benutzer über die **aktualisieren** Berechtigung. Für Benutzer mit der **aktualisieren** Berechtigung der *Prozess* -Attributwert auf `True`.  
  
-   *ReadDefinition* -Attributwert auf `None`; jeder andere Wert wird ein Fehler generiert.  
  
-   *Lesen* -Attributwert auf `Allowed` für Benutzer mit der **Benutzer** Berechtigung und `None` Wenn die Benutzern zugewiesen sind die **aktualisieren** Berechtigung, wenn ein Benutzer sowohl **Benutzer** und **aktualisieren** verfügt, wird das Attribut nastaven NA hodnotu `Allowed`. Für Benutzer mit Administratorrechten wird der Attributwert auf `Allowed` festgelegt.  
  
-   *Schreiben von* -Attributwert auf `None`; jeder andere Wert wird ein Fehler generiert.  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Role-Element &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
