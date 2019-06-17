---
title: PersistFormatEnum | Microsoft-Dokumentation
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
manager: jroth
ms.openlocfilehash: 7167067d0dc5942bc898c4cc2f01cad2a44ec559
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703476"
---
# <a name="persistformatenum"></a>PersistFormatEnum
Gibt das Format zum Speichern einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Microsoft Advanced Data TableGram (ADTG)-Format angibt.|  
|**adPersistADO**|1|Gibt an, dass die ADO-Extensible Markup Language (XML)-Format verwendet wird. Dieser Wert ist AdPersistXML und Gründen der Abwärtskompatibilität enthalten.|  
|**adPersistXML**|1|Extensible Markup Language (XML)-Format angibt.|  
|**adPersistProviderSpecific**|2|Gibt an, dass der Anbieter beibehalten, werden die **Recordset** mit einem eigenen Format.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>Gilt für  
 [Save-Methode](../../../ado/reference/ado-api/save-method.md)
