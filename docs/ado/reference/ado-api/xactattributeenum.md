---
title: XactAttributeEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: d645c648b6e1410f96beb567d7fb496e5fdae2d2
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764421"
---
# <a name="xactattributeenum"></a>XactAttributeEnum
Gibt die Transaktions Attribute eines [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekts an.  
  
|Konstante|Wert|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adxactabortregewahrsam**|262144|Führt beibehaltende Abbrüche durch Aufrufen von [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) aus, um automatisch eine neue Transaktion zu starten. Dieses Verhalten wird nicht von allen Anbietern unterstützt.|  
|**adxactcommitbehält**|131072|Führt beibehaltende Commits durch Aufrufen von [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) aus, um automatisch eine neue Transaktion zu starten. Dieses Verhalten wird nicht von allen Anbietern unterstützt.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoreums. xactattribute. abortretribute|  
|Adoumums. xactattribute. commitbehält|  
  
## <a name="applies-to"></a>Gilt für  
 [Attributes-Eigenschaft (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
