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
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47657718"
---
# <a name="stringformatenum"></a>StringFormatEnum
Gibt das Format an, beim Abrufen von einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) als Zeichenfolge.  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adClipString**|2|Grenzt die Zeilen nach *RowDelimiter*, Spalten, indem *ColumnDelimiter*, und null-Werte von *NullExpr*. Diese drei Parameter, der die [GetString](../../../ado/reference/ado-api/getstring-method-ado.md) Methode sind nur gültig mit einer *StringFormat* von **AdClipString**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Paket: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.StringFormat.CLIPSTRING|  
  
## <a name="applies-to"></a>Gilt für  
 [GetString-Methode (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)
