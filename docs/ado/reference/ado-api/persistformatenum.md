---
title: Persistformatumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PersistFormatEnum
helpviewer_keywords:
- PersistFormatEnum enumeration [ADO]
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2a26fd370e80cb288ee62b0fc53ed6670300172e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917614"
---
# <a name="persistformatenum"></a>PersistFormatEnum
Gibt das Format an, in dem ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)gespeichert werden soll.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Gibt das Microsoft Advanced Data TableGram (ADTG)-Format an.|  
|**adpersistado**|1|Gibt an, dass das eigene Extensible Markup Language-Format (XML) verwendet wird. Dieser Wert ist identisch mit adpersistxml und wird aus Gründen der Abwärtskompatibilität eingeschlossen.|  
|**adpersistxml**|1|Gibt Extensible Markup Language (XML)-Format an.|  
|**adpersistproviderspecific**|2|Gibt an, dass der Anbieter das **Recordset** unter Verwendung seines eigenen Formats persistent speichert.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|AdoEnums. persistformat. ADTG|  
|AdoEnums. persistformat. XML|  
  
## <a name="applies-to"></a>Gilt für  
 [Save-Methode](../../../ado/reference/ado-api/save-method.md)
