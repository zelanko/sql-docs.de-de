---
title: StringFormatEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StringFormatEnum
helpviewer_keywords:
- StringFormatEnum enumeration [ADO]
ms.assetid: 28f7d1ec-092b-4323-a39d-d3f882c6c81a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d2740c7fb25b71e3588bebb924ea9d5f907e3560
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910899"
---
# <a name="stringformatenum"></a>StringFormatEnum
Gibt das Format an, beim Abrufen von einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) als Zeichenfolge.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adClipString**|2|Grenzt die Zeilen nach *RowDelimiter*, Spalten, indem *ColumnDelimiter*, und null-Werte von *NullExpr*. Diese drei Parameter, der die [GetString](../../../ado/reference/ado-api/getstring-method-ado.md) Methode sind nur gültig mit einer *StringFormat* von **AdClipString**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.StringFormat.CLIPSTRING|  
  
## <a name="applies-to"></a>Gilt für  
 [GetString-Methode (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)
