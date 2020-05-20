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
author: rothja
ms.author: jroth
ms.openlocfilehash: 479bc032cf779752f11dccca73ee56fc05a8ebdd
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759566"
---
# <a name="streamwriteenum"></a>StreamWriteEnum
Gibt an, ob ein Zeilen Trennzeichen an die Zeichenfolge angefügt wird, die in ein [Streamobjekt](../../../ado/reference/ado-api/stream-object-ado.md) geschrieben wird  
  
|Konstante|Wert|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adschreitechar**|0|Standard. Schreibt die angegebene Text Zeichenfolge (angegeben durch den *Daten* Parameter) in das **Stream** -Objekt.|  
|**"adschreiteline"**|1|Schreibt eine Text Zeichenfolge und ein Zeilen Trennzeichen in ein Daten **Strom** Objekt. Wenn die [lineseparser](../../../ado/reference/ado-api/lineseparator-property-ado.md) -Eigenschaft nicht definiert ist, wird ein Laufzeitfehler zurückgegeben.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten haben keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [WriteText-Methode](../../../ado/reference/ado-api/writetext-method.md)
