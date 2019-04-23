---
title: Eigenschaften der Ebene | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- user hierarchies [Analysis Services]
- hierarchies [Analysis Services], user
ms.assetid: dabb7335-887b-442a-b67c-4901ba1242b7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c55a596461e03ce91a822e4578f7de56fe27f8f1
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60156527"
---
# <a name="level-properties"></a>Ebeneneigenschaften 
  In der folgenden Tabelle sind die Eigenschaften einer Ebene in einer benutzerdefinierten Hierarchie aufgelistet und beschrieben.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|Description|Enthält die Beschreibung der Ebene.|  
|HideMemberIf|Gibt an, ob und wann ein Element auf einer Ebene aus Clientanwendungen ausgeblendet werden sollte. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> Never<br /> Elemente werden nie ausgeblendet. Dies ist der Standardwert.<br /><br /> OnlyChildWithNoName<br /> Ein Element wird ausgeblendet, wenn das Element das einzige untergeordnete Element eines übergeordneten Elements ist und der Name des Elements leer ist.<br /><br /> OnlyChildWithParentName<br /> Ein Element wird ausgeblendet, wenn das Element das einzige untergeordnete Element eines übergeordneten Elements ist und der Name des Elements identisch mit dem des übergeordneten Elements ist.<br /><br /> NoName<br /> Ein Element wird ausgeblendet, wenn der Name des Elements leer ist.<br /><br /> ParentName<br /> Ein Element wird ausgeblendet, wenn der Name des Elements identisch mit dem Namen des übergeordneten Elements ist.|  
|ID|Enthält den eindeutigen Bezeichner (ID) der Ebene.|  
|Name|Enthält den Anzeigenamen der Ebene. Standardmäßig stimmt der Name einer Ebene mit dem Namen des Quellattributs überein.|  
|SourceAttribute|Enthält den Namen des Quellattributs, auf dem die Ebene basiert.|  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften der Benutzerhierarchie](user-hierarchies-properties.md)  
  
  
