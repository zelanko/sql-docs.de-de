---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 85bef64902f014e7b5269d6df328128bc8fe8d6e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67937880"
---
# <a name="stringformatenum"></a>StringFormatEnum
Gibt das Format beim Abrufen eines [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md) als Zeichenfolge an.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adclipstring**|2|Begrenzt Zeilen nach *RowDelimiter*, Spalten nach *ColumnDelimiter*und NULL-Werte durch *nullexpr*. Diese drei Parameter der [GetString](../../../ado/reference/ado-api/getstring-method-ado.md) -Methode sind nur mit einem *StringFormat* von **adclipstring**gültig.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Dauerhaft|  
|--------------|  
|AdoEnums. StringFormat. clipstring|  
  
## <a name="applies-to"></a>Gilt für  
 [GetString-Methode (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)
