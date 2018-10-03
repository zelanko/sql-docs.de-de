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
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633488"
---
# <a name="streamwriteenum"></a>StreamWriteEnum
Gibt an, ob ein Zeilentrennzeichen, auf die Zeichenfolge geschrieben angefügt wird, um eine [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt.  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|Standard. Schreibt die angegebene Textzeichenfolge (angegeben durch die *Daten* Parameter), die **Stream** Objekt.|  
|**adWriteLine**|1|Schreibt eine Zeichenfolge und ein Zeilentrennzeichen, eine **Stream** Objekt. Wenn die [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) Eigenschaft ist nicht definiert, und gibt einen Laufzeitfehler zurück.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Diese Konstanten keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [WriteText-Methode](../../../ado/reference/ado-api/writetext-method.md)
