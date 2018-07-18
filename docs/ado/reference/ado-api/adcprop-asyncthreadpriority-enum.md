---
title: ADCPROP_ASYNCTHREADPRIORITY_ENUM | Microsoft Docs
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
- ADCPROP_ASYNCTHREADPRIORITY_ENUM
helpviewer_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM [ADO]
ms.assetid: f0965617-17d8-41e0-98d0-f824274735a6
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7857e3b176191ba5b9c98a40c7f02abe666edec8
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35275229"
---
# <a name="adcpropasyncthreadpriorityenum"></a>ADCPROP_ASYNCTHREADPRIORITY_ENUM
Für eine RDS [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt, gibt die Ausführungspriorität des asynchronen Threads, die Daten abruft.  
  
 Verwenden Sie diese Konstanten mit der **Recordset** "**Background Thread Priorität**" dynamische Eigenschaft, die im Index ADO, OLE DB-dynamische Eigenschaft verwiesen wird und die dokumentiert, die der [ Microsoft Cursor Service für OLE DB-](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) Dokumentation.  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adPriorityAboveNormal**|4|Legt die Priorität zwischen normalen und höchsten fest.|  
|**adPriorityBelowNormal**|2|Legt die Priorität zwischen dem niedrigsten und "normal" fest.|  
|**adPriorityHighest**|5|Legt die Priorität auf die höchstmögliche fest.|  
|**AdPriorityLowest**|1|Legt die Priorität auf den niedrigsten fest.|  
|**adPriorityNormal**|3|Legt die Priorität auf Normal fest.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.AdcPropAsyncThreadPriority.ABOVENORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.BELOWNORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.HIGHEST|  
|AdoEnums.AdcPropAsyncThreadPriority.LOWEST|  
|AdoEnums.AdcPropAsyncThreadPriority.NORMAL|
