---
title: Name-Eigenschaft (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level::Name
- CubeDef::Name
- Member::Name
- Catalog::Name
- Dimension::Name
- Name
- Axis::Name
- Hierarchy::Name
helpviewer_keywords:
- Name property [ADO MD]
ms.assetid: 4a04380b-51dc-4aaf-8d25-123cdd589641
author: rothja
ms.author: jroth
ms.openlocfilehash: 370dc7900e5fe876ea1b1064b2621371c730f323
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765095"
---
# <a name="name-property-ado-md"></a>Name-Eigenschaft (ADO MD)
Gibt den Namen eines Objekts an.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **Zeichenfolge** zurück und ist schreibgeschützt.  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können die **Name** -Eigenschaft eines Objekts durch einen Ordinalverweis abrufen, nach dem Sie direkt auf das Objekt über den Namen verweisen können. Wenn beispielsweise `cdf.CubeDefs(0).Name` "BOSB Video Store" ergibt, können Sie diese [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) als bezeichnen `cdf.CubeDefs("Bobs Video Store")` .  
  
## <a name="applies-to"></a>Gilt für  
  
||||  
|-|-|-|  
|[Axis-Objekt (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|[Catalog-Objekt (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[CubeDef-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|  
|[Dimension-Objekt (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Hierarchy-Objekt (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|[Level-Objekt (ADO MD)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|  
|[Member-Objekt (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)|||  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog Beispiel (VB)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Caption-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/caption-property-ado-md.md)   
 [Description-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/description-property-ado-md.md)   
 [UniqueName-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)
