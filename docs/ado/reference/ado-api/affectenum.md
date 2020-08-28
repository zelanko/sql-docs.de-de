---
description: AffectEnum
title: Affectenum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 9673567c17cda79c93fba4e74b104bd0cb42edd7
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88976141"
---
# <a name="affectenum"></a>AffectEnum
Gibt an, welche Datensätze von einem Vorgang betroffen sind.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adaffechoch**|3|Wenn kein [Filter](./filter-property.md) auf das **Recordset**angewendet wird, wirkt sich dies auf alle Datensätze aus.<br /><br /> Wenn die **Filter** -Eigenschaft auf ein Zeichen folgen Kriterium (z. b. "Author = ' Smith '") festgelegt ist, wirkt sich der Vorgang auf sichtbare Datensätze im aktuellen Kapitel aus.<br /><br /> Wenn die **Filter** -Eigenschaft auf einen Member von [filtergroupum](./filtergroupenum.md) oder ein Array von Lesezeichen festgelegt ist, wirkt sich der Vorgang auf alle Zeilen des **Recordsets**aus. **Hinweis: adaffectall** ist in der Visual Basic Objektkatalog ausgeblendet.|  
|**adaffectallchapter**|4|Wirkt sich auf alle Datensätze in allen gleich geordneten Kapiteln des **Recordsets**aus, einschließlich derjenigen, die nicht über einen aktuell angewendeten **Filter** sichtbar sind.|  
|**adaffectcurrent**|1|Wirkt sich nur auf den aktuellen Datensatz aus.|  
|**adAffectGroup**|2|Wirkt sich nur auf Datensätze aus, die die aktuelle [Filter](./filter-property.md) Eigenschaften Einstellung erfüllen. Um diese Option verwenden zu können, müssen Sie die **Filter** -Eigenschaft auf einen **filtergroupum** -Wert oder ein Array von **Lesezeichen** festlegen.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoumums. Auswirkung. all|  
|Adoumums. Auswirkung. allchapters|  
|Adoumums. Auswirkung. Current|  
|AdoEnums. Auswirkung. Group|  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [CancelBatch-Methode (ADO)](./cancelbatch-method-ado.md)  
        [Delete-Methode (ADO-Recordset)](./delete-method-ado-recordset.md)  
    :::column-end:::
    :::column:::
        [Resync-Methode](./resync-method.md)  
        [UpdateBatch-Methode](./updatebatch-method.md)  
    :::column-end:::
:::row-end:::