---
title: Eigenschaften der Ebene | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- user hierarchies [Analysis Services]
- hierarchies [Analysis Services], user
ms.assetid: dabb7335-887b-442a-b67c-4901ba1242b7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1edce09247d89b8b87c8d03a637f84ed42e2292c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075120"
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
  
  
