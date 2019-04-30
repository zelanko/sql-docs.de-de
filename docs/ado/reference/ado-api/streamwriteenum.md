---
title: StreamWriteEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamWriteEnum
helpviewer_keywords:
- StreamWriteEnum enumeration [ADO]
ms.assetid: bdbf3405-a0bd-4f02-85d4-e3fe8da3f3f7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d0f42561d7b324a13068c14d0fc7971d3d46d83b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63311775"
---
# <a name="streamwriteenum"></a>StreamWriteEnum
Gibt an, ob ein Zeilentrennzeichen, auf die Zeichenfolge geschrieben angefügt wird, um eine [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|Standard. Schreibt die angegebene Textzeichenfolge (angegeben durch die *Daten* Parameter), die **Stream** Objekt.|  
|**adWriteLine**|1|Schreibt eine Zeichenfolge und ein Zeilentrennzeichen, eine **Stream** Objekt. Wenn die [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) Eigenschaft ist nicht definiert, und gibt einen Laufzeitfehler zurück.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Diese Konstanten keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [WriteText-Methode](../../../ado/reference/ado-api/writetext-method.md)
