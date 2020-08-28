---
description: ActionEnum
title: Aktionumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 02422de45f3e0ec28901678528468dc72f021549
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985921"
---
# <a name="actionenum"></a>ActionEnum
Gibt den Typ der Aktion an, die ausgeführt werden soll, wenn [setberechtigungen](./setpermissions-method-adox.md) aufgerufen wird.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adaccessdeny**|3|Der Gruppe oder dem Benutzer werden die angegebenen Berechtigungen verweigert.|  
|**adaccessgrant**|1|Die Gruppe oder der Benutzer verfügt mindestens über die angeforderten Berechtigungen.|  
|**adaccesswiderruf**|4|Alle expliziten Zugriffsrechte für die Gruppe oder den Benutzer werden aufgehoben.|  
|**adaccessset**|2|Die Gruppe oder der Benutzer verfügt über genau die angeforderten Berechtigungen.|