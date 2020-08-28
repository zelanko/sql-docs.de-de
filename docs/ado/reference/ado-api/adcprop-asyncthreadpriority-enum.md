---
description: ADCPROP_ASYNCTHREADPRIORITY_ENUM
title: ADCPROP_ASYNCTHREADPRIORITY_ENUM | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: e01a004ded0b6ed3151ba28c747d3ea245462f92
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88976871"
---
# <a name="adcprop_asyncthreadpriority_enum"></a>ADCPROP_ASYNCTHREADPRIORITY_ENUM
Gibt für ein [Recordset](./recordset-object-ado.md) RDS-Recordsetobjekt die Ausführungs Priorität des asynchronen Threads an, der Daten abruft.  
  
 Verwenden Sie diese Konstanten mit **der dynamischen** %% amp; quot;**Background Thread Priority**-Eigenschaft, auf die im ADO-to-OLE DB Dynamic Property Index verwiesen wird und der im [Microsoft Cursor-Dienst für OLE DB](../../guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) Dokumentation dokumentiert ist.  
  
|Konstante|Wert|Beschreibung|  
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