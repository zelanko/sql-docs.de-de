---
title: Connectpromptenum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: afd5d9ca0de6b8d2ffba75f862e6ca0afb594848
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919442"
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
Gibt an, ob ein Dialogfeld angezeigt werden soll, um beim Öffnen einer Verbindung mit einer Datenquelle nach fehlenden Parametern zu suchen.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adpromptalways**|1|Fordert immer an.|  
|**adpromptcomplete**|2|Gibt an, ob weitere Informationen erforderlich sind.|  
|**adpromptcompleterequired**|3|Fordert an, wenn weitere Informationen erforderlich sind, optionale Parameter jedoch nicht zulässig sind.|  
|**adpromptnever**|4|Nie Aufforderungen.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Dauerhaft|  
|--------------|  
|Adoumums. connectprompt. Always|  
|Adoumums. connectprompt. Complete|  
|Adoumums. connectprompt. completerequired|  
|Adoumums. connectprompt. Never|  
  
## <a name="applies-to"></a>Gilt für  
 [Prompt – dynamische Eigenschaft (ADO)](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)
