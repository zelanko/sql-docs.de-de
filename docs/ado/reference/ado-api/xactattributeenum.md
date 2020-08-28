---
description: XactAttributeEnum
title: XactAttributeEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- XactAttributeEnum
helpviewer_keywords:
- XactAttributeEnum enumeration [ADO]
ms.assetid: e7dcecd3-7dc7-445c-b922-f700c3067fbc
author: rothja
ms.author: jroth
ms.openlocfilehash: bb2a1391e813fd80c394bd685eff07e06015dd5b
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987691"
---
# <a name="xactattributeenum"></a>XactAttributeEnum
Gibt die Transaktions Attribute eines [Verbindungs](./connection-object-ado.md) Objekts an.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adxactabortregewahrsam**|262144|Führt beibehaltende Abbrüche durch Aufrufen von [RollbackTrans](./begintrans-committrans-and-rollbacktrans-methods-ado.md) aus, um automatisch eine neue Transaktion zu starten. Dieses Verhalten wird nicht von allen Anbietern unterstützt.|  
|**adxactcommitbehält**|131072|Führt beibehaltende Commits durch Aufrufen von [CommitTrans](./begintrans-committrans-and-rollbacktrans-methods-ado.md) aus, um automatisch eine neue Transaktion zu starten. Dieses Verhalten wird nicht von allen Anbietern unterstützt.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoreums. xactattribute. abortretribute|  
|Adoumums. xactattribute. commitbehält|  
  
## <a name="applies-to"></a>Gilt für  
 [Attributes-Eigenschaft (ADO)](./attributes-property-ado.md)