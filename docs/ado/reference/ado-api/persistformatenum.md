---
description: PersistFormatEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: c5730ca6a0d0bae791dce9327e365a9a38a9857f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442732"
---
# <a name="persistformatenum"></a>PersistFormatEnum
Gibt das Format an, in dem ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)gespeichert werden soll.  
  
|Konstant|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Gibt das Microsoft Advanced Data TableGram (ADTG)-Format an.|  
|**adpersistado**|1|Gibt an, dass das eigene Extensible Markup Language-Format (XML) verwendet wird. Dieser Wert ist identisch mit adpersistxml und wird aus Gründen der Abwärtskompatibilität eingeschlossen.|  
|**adpersistxml**|1|Gibt Extensible Markup Language (XML)-Format an.|  
|**adpersistproviderspecific**|2|Gibt an, dass der Anbieter das **Recordset** unter Verwendung seines eigenen Formats persistent speichert.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstant|  
|--------------|  
|AdoEnums. persistformat. ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>Gilt für  
 [Save-Methode](../../../ado/reference/ado-api/save-method.md)
