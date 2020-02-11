---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4cc9de1481cc683bddafe2f92959977319600f6a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67928635"
---
# <a name="streamwriteenum"></a>StreamWriteEnum
Gibt an, ob ein Zeilen Trennzeichen an die Zeichenfolge angefügt wird, die in ein [Streamobjekt](../../../ado/reference/ado-api/stream-object-ado.md) geschrieben wird  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adschreitechar**|0|Default. Schreibt die angegebene Text Zeichenfolge (angegeben durch den *Daten* Parameter) in das **Stream** -Objekt.|  
|**"adschreiteline"**|1|Schreibt eine Text Zeichenfolge und ein Zeilen Trennzeichen in ein Daten **Strom** Objekt. Wenn die [lineseparser](../../../ado/reference/ado-api/lineseparator-property-ado.md) -Eigenschaft nicht definiert ist, wird ein Laufzeitfehler zurückgegeben.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten haben keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [WriteText-Methode](../../../ado/reference/ado-api/writetext-method.md)
