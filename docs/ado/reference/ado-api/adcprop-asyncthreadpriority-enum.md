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
ms.openlocfilehash: 22a8cd4bb8d1bdddbaaa68e92349d9c728557ac0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67921466"
---
# <a name="adcprop_asyncthreadpriority_enum"></a>ADCPROP_ASYNCTHREADPRIORITY_ENUM
Gibt für ein [](../../../ado/reference/ado-api/recordset-object-ado.md) RDS-Recordsetobjekt die Ausführungs Priorität des asynchronen Threads an, der Daten abruft.  
  
 Verwenden Sie diese Konstanten mit **der dynamischen** %% amp; quot;**Background Thread Priority**-Eigenschaft, auf die im ADO-to-OLE DB Dynamic Property Index verwiesen wird und der im [Microsoft Cursor-Dienst für OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) Dokumentation dokumentiert ist.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adpriorityabovenormal**|4|Legt die Priorität zwischen normal und höchste Priorität fest.|  
|**adprioritybelownormal**|2|Legt die Priorität zwischen dem niedrigsten und dem normalen fest.|  
|**adpriorityhighest**|5|Legt die Priorität auf den höchstmöglichen Wert fest.|  
|**Adpriorityniedrigste**|1|Legt die Priorität auf die geringstmögliche fest.|  
|**adprioritynormal**|3|Legt die Priorität auf Normal fest.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Dauerhaft|  
|--------------|  
|Adoumums. adcpropasyncthreadpriority. AboveNormal|  
|AdoEnums. adcpropasyncthreadpriority. BelowNormal|  
|Adoumums. adcpropasyncthreadpriority. Highest|  
|Adoumums. adcpropasyncthreadpriority. niedrigste|  
|AdoEnums. adcpropasyncthreadpriority. Normal|
