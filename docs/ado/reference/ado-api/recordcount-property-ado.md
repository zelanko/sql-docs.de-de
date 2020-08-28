---
description: RecordCount-Eigenschaft (ADO)
title: RecordCount-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::RecordCount
- Recordset15::GetRecordCount
- Recordset15::get_RecordCount
helpviewer_keywords:
- RecordCount property [ADO]
ms.assetid: 834f0121-394a-44d4-ad7d-999b43a6fe63
author: rothja
ms.author: jroth
ms.openlocfilehash: 2c2fbd70c1195d0fedf5041a672b704f4bf482d3
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989831"
---
# <a name="recordcount-property-ado"></a>RecordCount-Eigenschaft (ADO)

Gibt die Anzahl der Datensätze in einem [Recordset](./recordset-object-ado.md) -Objekt an.
  
## <a name="return-value"></a>Rückgabewert

Gibt einen **Long** -Wert zurück, der die Anzahl der Datensätze im **Recordset**angibt.
  
## <a name="remarks"></a>Bemerkungen

Verwenden Sie die **RecordCount** -Eigenschaft, um herauszufinden, wie viele Datensätze in einem **Recordset** -Objekt enthalten sind. Die-Eigenschaft gibt-1 zurück, wenn ADO die Anzahl der Datensätze nicht ermitteln kann oder wenn der Anbieter oder Cursortyp **RecordCount**nicht unterstützt. Das Lesen der **RecordCount** -Eigenschaft für ein geschlossenes **Recordset** verursacht einen Fehler.

#### <a name="bookmarks-or-approximate-positioning"></a>Lesezeichen oder ungefähre Positionierung

Wenn das Recordset-Objekt entweder Lesezeichen oder eine ungefähre *Positionierung unterstützt* , gibt diese Eigenschaft die genaue Anzahl der Datensätze im Recordset zurück. Diese Eigenschaft gibt die genaue Anzahl zurück, unabhängig davon, ob das Recordset vollständig aufgefüllt wurde.

Wenn dagegen das Recordset-Objekt weder Lesezeichen noch eine ungefähre *Positionierung unterstützt* , kann der Zugriff auf diese Eigenschaft eine erhebliche Ableitung von Ressourcen sein. Die Ableitung tritt auf, weil alle Datensätze abgerufen und gezählt werden müssen, um einen exakten RecordCount-Wert zurückzugeben.

- **adbookmark** im Zusammenhang mit Lesezeichen.
- **adapproxposition** bezieht sich auf die ungefähre Positionierung.

> [!NOTE]
> In den ADO-Versionen 2,8 und früher ruft der SQLOLEDB-Anbieter bei Verwendung eines serverseitigen Cursors alle Datensätze ab, trotz der Tatsache, dass er **true** für beide **Unterstützung (adapproxposition)** und **unterstützt (adbookmark)** zurückgibt.
  
Der Cursortyp des **Recordset** -Objekts wirkt sich darauf aus, ob die Anzahl der Datensätze bestimmt werden kann. Die **RecordCount** -Eigenschaft gibt-1 für einen Vorwärts Cursor zurück. die tatsächliche Anzahl für einen statischen oder Keysetcursor. und entweder-1 oder die tatsächliche Anzahl für einen dynamischen Cursor, abhängig von der Datenquelle.
  
## <a name="applies-to"></a>Gilt für

[Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen

[Filter-und RecordCount-Eigenschaften (Beispiel) (VB)](./filter-and-recordcount-properties-example-vb.md)   
[Filter-und RecordCount-Eigenschaften (Beispiel) (VC + +)](./filter-and-recordcount-properties-example-vc.md)   
[AbsolutePosition-Eigenschaft (ADO)](./absoluteposition-property-ado.md)   
[PageCount-Eigenschaft (ADO)](./pagecount-property-ado.md)