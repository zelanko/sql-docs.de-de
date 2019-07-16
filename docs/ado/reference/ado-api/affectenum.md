---
title: AffectEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- AffectEnum
helpviewer_keywords:
- AffectEnum enumeration [ADO]
ms.assetid: 1ab921a0-6c57-43b4-9291-701b2599f3e8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a936eb39583afff34dd317b85bc4198022b15e7f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67920755"
---
# <a name="affectenum"></a>AffectEnum
Gibt an, welche Datensätze von einem Vorgang betroffen sind.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adAffectAll**|3|Wenn keine vorhanden ist eine [Filter](../../../ado/reference/ado-api/filter-property.md) angewendet werden, um die **Recordset**, wirkt sich auf alle Datensätze.<br /><br /> Wenn die **Filter** -Eigenschaftensatz auf eine Zeichenfolgenkriterien (wie z. B. "Autor ="Smith""), und klicken Sie dann der Vorgang wirkt sich die sichtbaren Datensätze in das aktuelle Kapitel auf.<br /><br /> Wenn die **Filter** -Eigenschaftensatz auf einen Member der [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md) oder ein Array von Lesezeichen, und klicken Sie dann auf den Vorgang wirkt sich auf alle Zeilen der **Recordset**. **Hinweis: AdAffectAll** wird ausgeblendet, im Objektkatalog Visual Basic.|  
|**adAffectAllChapters**|4|Wirkt sich auf alle Datensätze in der alle gleichgeordneten Kapiteln die **Recordset**, einschließlich derjenigen, die über einen nicht sichtbaren **Filter** , die derzeit angewendet wird.|  
|**adAffectCurrent**|1|Betrifft nur den aktuellen Datensatz.|  
|**adAffectGroup**|2|Betrifft nur die Datensätze, die die aktuelle erfüllen [Filter](../../../ado/reference/ado-api/filter-property.md) Einstellung der Eigenschaft. Müssen Sie festlegen, die **Filter** Eigenschaft, um eine **FilterGroupEnum** Wert oder ein Array von **Lesezeichen** auf diese Option verwenden.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
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
