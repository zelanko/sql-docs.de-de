---
description: ConnectPromptEnum
title: Connectpromptenum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ConnectPromptEnum
helpviewer_keywords:
- ConnectPromptEnum enumeration [ADO]
ms.assetid: 21026e24-62b7-4cc9-8aef-62c1fc6cba75
author: rothja
ms.author: jroth
ms.openlocfilehash: 171cc7706cc00b48c3373a0e40d5de221d4d00ce
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974681"
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
Gibt an, ob ein Dialogfeld angezeigt werden soll, um beim Öffnen einer Verbindung mit einer Datenquelle nach fehlenden Parametern zu suchen.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adpromptalways**|1|Fordert immer an.|  
|**adpromptcomplete**|2|Gibt an, ob weitere Informationen erforderlich sind.|  
|**adpromptcompleterequired**|3|Fordert an, wenn weitere Informationen erforderlich sind, optionale Parameter jedoch nicht zulässig sind.|  
|**adpromptnever**|4|Nie Aufforderungen.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoumums. connectprompt. Always|  
|Adoumums. connectprompt. Complete|  
|Adoumums. connectprompt. completerequired|  
|Adoumums. connectprompt. Never|  
  
## <a name="applies-to"></a>Gilt für  
 [Prompt – dynamische Eigenschaft (ADO)](./prompt-property-dynamic-ado.md)