---
description: GetString-Methode (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a972edd11c419c1990c78635d42c44d8c06db2c
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774909"
---
# <a name="getstring-method-ado"></a>GetString-Methode (ADO)
Gibt das [Recordset](./recordset-object-ado.md) als Zeichenfolge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Variant = recordset.GetString(StringFormat, NumRows, ColumnDelimiter, RowDelimiter, NullExpr)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt das **Recordset** als Zeichen folgen Wert **Variante** (BSTR) zurück.  
  
#### <a name="parameters"></a>Parameter  
 *StringFormat*  
 Ein [stringformatenum](./stringformatenum.md) -Wert, der angibt, wie das **Recordset** in eine Zeichenfolge konvertiert werden soll. Die Parameter " *RowDelimiter*", " *ColumnDelimiter*" und " *nullexpr* " werden nur mit einem *StringFormat* von " **adclipstring**" verwendet.  
  
 *NumRows*  
 Optional. Die Anzahl der Zeilen, die in das **Recordset**konvertiert werden sollen. Wenn *numRows* nicht angegeben wird, oder wenn es größer als die Gesamtzahl der Zeilen im **Recordset**ist, werden alle Zeilen im **Recordset** konvertiert.  
  
 *ColumnDelimiter*  
 Optional. Ein Trennzeichen, das zwischen Spalten verwendet wird, sofern angegeben, andernfalls das Tabulator Zeichen.  
  
 *RowDelimiter*  
 Optional. Ein Trennzeichen, das zwischen Zeilen verwendet wird, sofern angegeben, andernfalls das Wagen Rücklauf Zeichen.  
  
 *Nullexpr*  
 Optional. Ein Ausdruck, der anstelle eines NULL-Werts verwendet wird, sofern angegeben, andernfalls die leere Zeichenfolge.  
  
## <a name="remarks"></a>Bemerkungen  
 Zeilendaten, aber keine Schema Daten, werden in der Zeichenfolge gespeichert. Daher kann ein **Recordset** nicht mit dieser Zeichenfolge erneut geöffnet werden.  
  
 Diese Methode entspricht der RDO **GetClipString** -Methode.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [GetString-Methode – Beispiel (VB)](./getstring-method-example-vb.md)