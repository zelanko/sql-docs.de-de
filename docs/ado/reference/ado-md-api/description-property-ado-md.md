---
description: Description-Eigenschaft (ADO MD)
title: Description-Eigenschaft (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Member::Description
- Level::Description
- CubeDef::Description
- Hierarchy::Description
- Description
- Dimension::Description
helpviewer_keywords:
- Description property [ADO MD]
ms.assetid: 6d626d35-0bf3-4f24-9934-ad9c9c91273a
author: rothja
ms.author: jroth
ms.openlocfilehash: 726a49da64c36b487868068affad65164b9b3c5e
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986901"
---
# <a name="description-property-ado-md"></a>Description-Eigenschaft (ADO MD)
Gibt eine Text Erklärung des aktuellen-Objekts zurück.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **Zeichenfolge** zurück und ist schreibgeschützt.  
  
## <a name="remarks"></a>Bemerkungen  
 Bei Element Objekten gilt die **Beschreibung** nur für Measure-und Formula- [Member](./member-object-ado-md.md) . **Description** gibt eine leere Zeichenfolge ("") für alle anderen Typen von Membern zurück. Weitere Informationen zu den verschiedenen Typen von Membern finden Sie unter der [Type](./type-property-ado-md.md) -Eigenschaft.  
  
 Diese Eigenschaft wird nur für **Member** -Objekte unterstützt, die zu einem [Ebenenobjekt](./level-object-ado-md.md) gehören. Ein Fehler tritt auf, **Wenn von Element** Objekten, die zu einem [Positions](./position-object-ado-md.md) Objekt gehören, auf diese Eigenschaft verwiesen wird.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [CubeDef-Objekt (ADO MD)](./cubedef-object-ado-md.md)  
        [Dimension-Objekt (ADO MD)](./dimension-object-ado-md.md)  
    :::column-end:::
    :::column:::
        [Hierarchy-Objekt (ADO MD)](./hierarchy-object-ado-md.md)  
        [Level-Objekt (ADO MD)](./level-object-ado-md.md)  
    :::column-end:::
    :::column:::
        [Member-Objekt (ADO MD)](./member-object-ado-md.md)  
    :::column-end:::
:::row-end:::