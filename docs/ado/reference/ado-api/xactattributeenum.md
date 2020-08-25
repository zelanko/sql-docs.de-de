---
description: XactAttributeEnum
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
ms.openlocfilehash: 1c7ea7ccbf1a588458db9e213bfa57837e89898f
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776819"
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