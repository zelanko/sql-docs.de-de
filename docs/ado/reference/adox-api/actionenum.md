---
title: Aktionumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ActionEnum
helpviewer_keywords:
- ActionEnum enumeration [ADOX]
ms.assetid: f948febd-c885-4621-823b-421e116fec4e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fad40c6daed6fd86f93da3f658af6a21c33ca762
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67928621"
---
# <a name="actionenum"></a>ActionEnum
Gibt den Typ der Aktion an, die ausgeführt werden soll, wenn [setberechtigungen](../../../ado/reference/adox-api/setpermissions-method-adox.md) aufgerufen wird.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adaccessdeny**|3|Der Gruppe oder dem Benutzer werden die angegebenen Berechtigungen verweigert.|  
|**adaccessgrant**|1|Die Gruppe oder der Benutzer verfügt mindestens über die angeforderten Berechtigungen.|  
|**adaccesswiderruf**|4|Alle expliziten Zugriffsrechte für die Gruppe oder den Benutzer werden aufgehoben.|  
|**adaccessset**|2|Die Gruppe oder der Benutzer verfügt über genau die angeforderten Berechtigungen.|
