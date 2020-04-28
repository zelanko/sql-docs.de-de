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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c248139abfd136d5c79658592e0e49d5e10444aa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67949396"
---
# <a name="name-property-ado-md"></a>Name-Eigenschaft (ADO MD)
Gibt den Namen eines Objekts an.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **Zeichenfolge** zurück und ist schreibgeschützt.  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können die **Name** -Eigenschaft eines Objekts durch einen Ordinalverweis abrufen, nach dem Sie direkt auf das Objekt über den Namen verweisen können. Wenn `cdf.CubeDefs(0).Name` beispielsweise "BOSB Video Store" ergibt, können Sie diese [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) als `cdf.CubeDefs("Bobs Video Store")`bezeichnen.  
  
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
