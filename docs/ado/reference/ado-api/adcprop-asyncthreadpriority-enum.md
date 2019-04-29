---
title: ADCPROP_ASYNCTHREADPRIORITY_ENUM | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM
helpviewer_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM [ADO]
ms.assetid: f0965617-17d8-41e0-98d0-f824274735a6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0b9d4e0e6f844ef2dda18e95aadfcf3b910995d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63065303"
---
# <a name="adcpropasyncthreadpriorityenum"></a>ADCPROP_ASYNCTHREADPRIORITY_ENUM
Für eine RDS [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt, gibt die Ausführungspriorität des asynchronen Threads, die Daten abruft.  
  
 Verwenden Sie diese Konstanten mit dem **Recordset** "**Hintergrundpriorität Thread**" dynamische Eigenschaft, die im Index ADO, OLE DB dynamische Eigenschaft verwiesen wird und Sie finden Sie unter der [ Microsoft Cursor Service für OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) Dokumentation.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adPriorityAboveNormal**|4|Legt die Priorität zwischen normalen und die höchste fest.|  
|**adPriorityBelowNormal**|2|Legt die Priorität zwischen dem niedrigsten und den normalen fest.|  
|**adPriorityHighest**|5|Legt Sie auf die höchstmögliche Priorität fest.|  
|**AdPriorityLowest**|1|Legt die Priorität auf den niedrigsten fest.|  
|**adPriorityNormal**|3|Legt die Priorität auf Normal fest.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.AdcPropAsyncThreadPriority.ABOVENORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.BELOWNORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.HIGHEST|  
|AdoEnums.AdcPropAsyncThreadPriority.LOWEST|  
|AdoEnums.AdcPropAsyncThreadPriority.NORMAL|
