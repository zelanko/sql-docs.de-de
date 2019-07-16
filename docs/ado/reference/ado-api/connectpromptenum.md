---
title: ConnectPromptEnum | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67919442"
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
Gibt an, ob ein Dialogfeld angezeigt werden soll, für die fehlenden Parameter aufgefordert, beim Öffnen einer Verbindung mit einer Datenquelle.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adPromptAlways**|1|Immer aufgefordert.|  
|**adPromptComplete**|2|Werden Sie aufgefordert, wenn weitere Informationen erforderlich sind.|  
|**adPromptCompleteRequired**|3|Werden Sie aufgefordert, wenn weitere Informationen erforderlich sind, aber optionale Parameter sind nicht zulässig.|  
|**adPromptNever**|4|Fordert nie auf.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.ConnectPrompt.ALWAYS|  
|AdoEnums.ConnectPrompt.COMPLETE|  
|AdoEnums.ConnectPrompt.COMPLETEREQUIRED|  
|AdoEnums.ConnectPrompt.NEVER|  
  
## <a name="applies-to"></a>Gilt für  
 [Dynamische Eigenschaft Prompt (ADO)](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)
