---
title: Getschemaobject-Modell (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- GetSchemaObject
- Cellset::GetSchemaObject
helpviewer_keywords:
- GetSchemaObject method [ADO MD]
ms.assetid: 36b754b4-6b17-4dd1-a925-bca46938b7c4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 690c81a46c62c8844780e82b5c82a0ff7301105d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67949767"
---
# <a name="getschemaobject-method-ado-md"></a>GetSchemaObject-Modell (ADO MD)
Ruft ein Objekt der ADO MD-Schema ([Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [Hierarchie](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [Ebene](../../../ado/reference/ado-md-api/level-object-ado-md.md), oder [Member](../../../ado/reference/ado-md-api/member-object-ado-md.md)) von seiner [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set object = CubeDef.GetSchemaObject (ObjType, UniqueName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *ObjType*  
 Ein [SchemaObjectTypeEnum](../../../ado/reference/ado-md-api/schemaobjecttypeenum.md) Wert, der den Typ des Schemaobjekts (Dimension, Hierarchie, Ebene oder Member) zum Abrufen angibt.  
  
 *UniqueName*  
 Ein **Zeichenfolge** angeben der **UniqueName** Eigenschaftswert des Objekts abgerufen.  
  
## <a name="remarks"></a>Hinweise  
 **GetSchemaObject** werden Objekte, die über ihren eindeutigen Namen, laut der **UniqueName** Eigenschaft. Die Namen der übergeordneten Objekte müssen nicht bekannt sein, und die übergeordnete Sammlungen müssen nicht aufgefüllt werden, um ein Objekt abzurufen.  
  
## <a name="applies-to"></a>Gilt für  
 [CubeDef-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)  
  
## <a name="see-also"></a>Siehe auch  
 [CubeDef-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)
