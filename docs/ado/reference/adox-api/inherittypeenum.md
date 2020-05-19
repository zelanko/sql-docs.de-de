---
title: Ererttypep | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- InheritTypeEnum
helpviewer_keywords:
- InheritTypeEnum enumeration [ADOX]
ms.assetid: c2f6ce79-c4b3-4d40-ac95-21025208f991
author: rothja
ms.author: jroth
ms.openlocfilehash: f420d7d49ad24188f5210001af1209427478f3f6
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82746681"
---
# <a name="inherittypeenum"></a>InheritTypeEnum
Gibt an, wie Objekte Berechtigungen erben, die mit [setberechtigungen](../../../ado/reference/adox-api/setpermissions-method-adox.md)festgelegt sind.  
  
|Konstante|Wert|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adgeerbt both**|3|Beide Objekte und andere Container, die im primären Objekt enthalten sind, erben den Eintrag.|  
|**adgeerbt-Container**|2|Andere Container, die im primären Objekt enthalten sind, erben den Eintrag.|  
|**adgeerbt None**|0|Standard. Es erfolgt keine Vererbung.|  
|**advererbt nopropagate**|4|Die Flags **advereritobjects** und **adgeerbt Containers** werden nicht an einen geerbten Eintrag weitergegeben.|  
|**advereritobjects**|1|Nicht-Container-Objekte im Container erben die Berechtigungen.|  
  
## <a name="applies-to"></a>Gilt für  
 [SetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
