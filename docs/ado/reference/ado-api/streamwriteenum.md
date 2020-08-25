---
description: StreamWriteEnum
title: Streambeschreiteenum | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 343e5fd45a32e45cda342ab01feb64f379054486
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777159"
---
# <a name="streamwriteenum"></a>StreamWriteEnum
Gibt an, ob ein Zeilen Trennzeichen an die Zeichenfolge angefügt wird, die in ein [Streamobjekt](./stream-object-ado.md) geschrieben wird  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adschreitechar**|0|Standard. Schreibt die angegebene Text Zeichenfolge (angegeben durch den *Daten* Parameter) in das **Stream** -Objekt.|  
|**"adschreiteline"**|1|Schreibt eine Text Zeichenfolge und ein Zeilen Trennzeichen in ein Daten **Strom** Objekt. Wenn die [lineseparser](./lineseparator-property-ado.md) -Eigenschaft nicht definiert ist, wird ein Laufzeitfehler zurückgegeben.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten haben keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [WriteText-Methode](./writetext-method.md)