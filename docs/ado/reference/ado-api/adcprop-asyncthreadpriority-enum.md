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
author: rothja
ms.author: jroth
ms.openlocfilehash: ecdc80a2f1e1ace36170a9b4527ba01f0b02ee11
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760656"
---
# <a name="adcprop_asyncthreadpriority_enum"></a>ADCPROP_ASYNCTHREADPRIORITY_ENUM
Gibt für ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) RDS-Recordsetobjekt die Ausführungs Priorität des asynchronen Threads an, der Daten abruft.  
  
 Verwenden Sie diese Konstanten mit **der dynamischen** %% amp; quot;**Background Thread Priority**-Eigenschaft, auf die im ADO-to-OLE DB Dynamic Property Index verwiesen wird und der im [Microsoft Cursor-Dienst für OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) Dokumentation dokumentiert ist.  
  
|Konstante|Wert|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adpriorityabovenormal**|4|Legt die Priorität zwischen normal und höchste Priorität fest.|  
|**adprioritybelownormal**|2|Legt die Priorität zwischen dem niedrigsten und dem normalen fest.|  
|**adpriorityhighest**|5|Legt die Priorität auf den höchstmöglichen Wert fest.|  
|**Adpriorityniedrigste**|1|Legt die Priorität auf die geringstmögliche fest.|  
|**adprioritynormal**|3|Legt die Priorität auf Normal fest.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoumums. adcpropasyncthreadpriority. AboveNormal|  
|AdoEnums. adcpropasyncthreadpriority. BelowNormal|  
|Adoumums. adcpropasyncthreadpriority. Highest|  
|Adoumums. adcpropasyncthreadpriority. niedrigste|  
|AdoEnums. adcpropasyncthreadpriority. Normal|
