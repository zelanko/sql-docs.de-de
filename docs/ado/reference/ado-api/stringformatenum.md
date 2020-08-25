---
description: StringFormatEnum
title: Stringformatumum | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 90c6214caa0adc1c11cdc0660b65795624919e51
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777139"
---
# <a name="stringformatenum"></a>StringFormatEnum
Gibt das Format beim Abrufen eines [Recordsets](./recordset-object-ado.md) als Zeichenfolge an.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adclipstring**|2|Begrenzt Zeilen nach *RowDelimiter*, Spalten nach *ColumnDelimiter*und NULL-Werte durch *nullexpr*. Diese drei Parameter der [GetString](./getstring-method-ado.md) -Methode sind nur mit einem *StringFormat* von **adclipstring**gültig.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|AdoEnums. StringFormat. clipstring|  
  
## <a name="applies-to"></a>Gilt für  
 [GetString-Methode (ADO)](./getstring-method-ado.md)