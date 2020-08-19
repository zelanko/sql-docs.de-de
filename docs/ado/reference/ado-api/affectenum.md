---
description: AffectEnum
title: Affectenum | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 551c2ec7b8351ed17841ed1a4073c1a411dc77d0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451292"
---
# <a name="affectenum"></a>AffectEnum
Gibt an, welche Datensätze von einem Vorgang betroffen sind.  
  
|Konstant|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adaffechoch**|3|Wenn kein [Filter](../../../ado/reference/ado-api/filter-property.md) auf das **Recordset**angewendet wird, wirkt sich dies auf alle Datensätze aus.<br /><br /> Wenn die **Filter** -Eigenschaft auf ein Zeichen folgen Kriterium (z. b. "Author = ' Smith '") festgelegt ist, wirkt sich der Vorgang auf sichtbare Datensätze im aktuellen Kapitel aus.<br /><br /> Wenn die **Filter** -Eigenschaft auf einen Member von [filtergroupum](../../../ado/reference/ado-api/filtergroupenum.md) oder ein Array von Lesezeichen festgelegt ist, wirkt sich der Vorgang auf alle Zeilen des **Recordsets**aus. **Hinweis: adaffectall** ist in der Visual Basic Objektkatalog ausgeblendet.|  
|**adaffectallchapter**|4|Wirkt sich auf alle Datensätze in allen gleich geordneten Kapiteln des **Recordsets**aus, einschließlich derjenigen, die nicht über einen aktuell angewendeten **Filter** sichtbar sind.|  
|**adaffectcurrent**|1|Wirkt sich nur auf den aktuellen Datensatz aus.|  
|**adAffectGroup**|2|Wirkt sich nur auf Datensätze aus, die die aktuelle [Filter](../../../ado/reference/ado-api/filter-property.md) Eigenschaften Einstellung erfüllen. Um diese Option verwenden zu können, müssen Sie die **Filter** -Eigenschaft auf einen **filtergroupum** -Wert oder ein Array von **Lesezeichen** festlegen.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstant|  
|--------------|  
|Adoumums. Auswirkung. all|  
|Adoumums. Auswirkung. allchapters|  
|Adoumums. Auswirkung. Current|  
|AdoEnums. Auswirkung. Group|  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [CancelBatch-Methode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)  
        [Delete-Methode (ADO-Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)  
    :::column-end:::
    :::column:::
        [Resync-Methode](../../../ado/reference/ado-api/resync-method.md)  
        [UpdateBatch-Methode](../../../ado/reference/ado-api/updatebatch-method.md)  
    :::column-end:::
:::row-end:::
