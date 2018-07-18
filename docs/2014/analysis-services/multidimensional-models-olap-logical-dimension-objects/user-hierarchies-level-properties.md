---
title: Eigenschaften der Ebene | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- user hierarchies [Analysis Services]
- hierarchies [Analysis Services], user
ms.assetid: dabb7335-887b-442a-b67c-4901ba1242b7
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 28c5c9149d1734f410417df1d727b81e6e86ea1a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37288046"
---
# <a name="level-properties"></a>Ebeneneigenschaften 
  In der folgenden Tabelle sind die Eigenschaften einer Ebene in einer benutzerdefinierten Hierarchie aufgelistet und beschrieben.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|Description|Enthält die Beschreibung der Ebene.|  
|HideMemberIf|Gibt an, ob und wann ein Element auf einer Ebene aus Clientanwendungen ausgeblendet werden sollte. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> Never<br /> Elemente werden nie ausgeblendet. Dies ist der Standardwert.<br /><br /> OnlyChildWithNoName<br /> Ein Element wird ausgeblendet, wenn das Element das einzige untergeordnete Element eines übergeordneten Elements ist und der Name des Elements leer ist.<br /><br /> OnlyChildWithParentName<br /> Ein Element wird ausgeblendet, wenn das Element das einzige untergeordnete Element eines übergeordneten Elements ist und der Name des Elements identisch mit dem des übergeordneten Elements ist.<br /><br /> NoName<br /> Ein Element wird ausgeblendet, wenn der Name des Elements leer ist.<br /><br /> ParentName<br /> Ein Element wird ausgeblendet, wenn der Name des Elements identisch mit dem Namen des übergeordneten Elements ist.|  
|im Elementknoten &lt;Customer ID="1"|Enthält den eindeutigen Bezeichner (ID) der Ebene.|  
|Name|Enthält den Anzeigenamen der Ebene. Standardmäßig stimmt der Name einer Ebene mit dem Namen des Quellattributs überein.|  
|SourceAttribute|Enthält den Namen des Quellattributs, auf dem die Ebene basiert.|  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften der Benutzerhierarchie](user-hierarchies-properties.md)  
  
  
