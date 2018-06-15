---
title: AffectEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- AffectEnum
helpviewer_keywords:
- AffectEnum enumeration [ADO]
ms.assetid: 1ab921a0-6c57-43b4-9291-701b2599f3e8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 797ee0a58457848b3dec133c695d1d36dc579bbe
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35275699"
---
# <a name="affectenum"></a>AffectEnum
Gibt an, welche Datensätze von einem Vorgang betroffen sind.  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adAffectAll**|3|Besteht keine [Filter](../../../ado/reference/ado-api/filter-property.md) angewendet, um die **Recordset**, wirkt sich auf alle Datensätze.<br /><br /> Wenn die **Filter** Eigenschaft auf eine Zeichenfolgenkriterien festgelegt ist (z. B. "Autor = 'Smith'"), und klicken Sie dann der Vorgang wirkt sich die sichtbaren Datensätze im aktuellen Kapitel auf.<br /><br /> Wenn die **Filter** Eigenschaftensatz an ein Mitglied der [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md) oder ein Array von Lesezeichen, und Sie dann den Vorgang wirkt sich auf alle Zeilen von der **Recordset**. **Hinweis:****AdAffectAll** in Visual Basic-Objektkatalog ausgeblendet ist.|  
|**adAffectAllChapters**|4|Wirkt sich auf alle Datensätze in allen nebengeordneten Kapiteln der **Recordset**, einschließlich der über einen nicht sichtbaren **Filter** , die aktuell zugeordnet ist.|  
|**adAffectCurrent**|1|Wirkt sich nur den aktuellen Datensatz ein.|  
|**adAffectGroup**|2|Betrifft nur Datensätze, die das aktuelle erfüllen [Filter](../../../ado/reference/ado-api/filter-property.md) Einstellung der Eigenschaft. Müssen die **Filter** Eigenschaft, um eine **FilterGroupEnum** Wert oder ein Array von **Lesezeichen** zur Verwendung dieser Option.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.Affect.ALL|  
|AdoEnums.Affect.ALLCHAPTERS|  
|AdoEnums.Affect.CURRENT|  
|AdoEnums.Affect.GROUP|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[CancelBatch-Methode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|[Delete-Methode (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|  
|[Resync-Methode](../../../ado/reference/ado-api/resync-method.md)|[UpdateBatch-Methode](../../../ado/reference/ado-api/updatebatch-method.md)|
