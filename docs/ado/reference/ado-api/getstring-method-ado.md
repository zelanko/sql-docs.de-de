---
title: GetString-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::raw_GetString
- Recordset20::GetString
helpviewer_keywords:
- GetString method [ADO]
ms.assetid: 92452940-b2a7-456e-94fc-3780c71da33c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 14bb7fd2e4a6dd8e6eb8f369342923ce1a9728c9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66697617"
---
# <a name="getstring-method-ado"></a>GetString-Methode (ADO)
Gibt die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) als Zeichenfolge.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Variant = recordset.GetString(StringFormat, NumRows, ColumnDelimiter, RowDelimiter, NullExpr)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt die **Recordset** als eine Zeichenfolge ausgewertet **Variant** (BSTR).  
  
#### <a name="parameters"></a>Parameter  
 *StringFormat*  
 Ein [StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md) Wert, der angibt, wie die **Recordset** in eine Zeichenfolge konvertiert werden sollen. Die *RowDelimiter*, *ColumnDelimiter*, und *NullExpr* Parameter werden verwendet, nur mit einem *StringFormat* von  **AdClipString**.  
  
 *NumRows*  
 Optional. Die Anzahl der Zeilen in konvertiert werden die **Recordset**. Wenn *NumRows* nicht angegeben ist, oder ist größer als die Gesamtzahl der Zeilen in der **Recordset**, klicken Sie dann alle Zeilen in der **Recordset** konvertiert werden.  
  
 *ColumnDelimiter*  
 Optional. Ein Trennzeichen zwischen Spalten verwendet werden, wenn angegeben, andernfalls das Tabstoppzeichen.  
  
 *RowDelimiter*  
 Optional. Ein Trennzeichen zwischen Zeilen verwendet werden, wenn angegeben, andernfalls das Wagenrücklaufzeichen.  
  
 *NullExpr*  
 Optional. Ein Ausdruck, der anstelle von einen null-Wert verwendet werden, wenn angegeben, andernfalls die leere Zeichenfolge.  
  
## <a name="remarks"></a>Hinweise  
 Zeilendaten, aber keine Schemadaten wird in der Zeichenfolge gespeichert. Aus diesem Grund eine **Recordset** kann nicht mithilfe dieser Zeichenfolge erneut geöffnet werden.  
  
 Diese Methode entspricht dem RDO **GetClipString** Methode.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetString-Methode – Beispiel (VB)](../../../ado/reference/ado-api/getstring-method-example-vb.md)
