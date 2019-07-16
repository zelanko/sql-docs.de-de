---
title: RecordCount-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7304062298a95406a223ba58026379a3bebf392f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931470"
---
# <a name="recordcount-property-ado"></a>RecordCount-Eigenschaft (ADO)

Gibt die Anzahl der Datensätze in einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.
  
## <a name="return-value"></a>Rückgabewert

Gibt eine **lange** hodnota ukazuje, die Anzahl der Datensätze in der **Recordset**.
  
## <a name="remarks"></a>Hinweise

Verwenden der **RecordCount** Eigenschaft, um herauszufinden, wie viele Datensätze sind in einem **Recordset** Objekt. Die Eigenschaft gibt-1 zurück, wenn ADO die Anzahl der Datensätze nicht bestimmen kann, oder wenn der Anbieter oder der Cursor-Typ nicht unterstützt **RecordCount**. Lesen der **RecordCount** Eigenschaft für ein geschlossenes **Recordset** verursacht einen Fehler.

#### <a name="bookmarks-or-approximate-positioning"></a>Lesezeichen oder ungefähre Positionierung

Wenn das Recordset-Objekt *ist* unterstützen entweder Lesezeichen oder Ungefährer Positionierung, diese Eigenschaft gibt die genaue Anzahl der Datensätze im Recordset. Diese Eigenschaft gibt die genaue Anzahl unabhängig davon, ob das Recordset vollständig aufgefüllt wurde.

Im Gegensatz dazu ist der Fall des Recordset-Objekts *nicht* Lesezeichen oder ungefähre Positionierung zu unterstützen, Zugriff auf diese Eigenschaft ist möglicherweise eine erhebliche Beanspruchung von Ressourcen. Der Abfluss tritt auf, da alle Datensätze müssen abgerufen und gezählt, um einen genauen RecordCount-Wert zurückgeben.

- **zulässt** im Zusammenhang mit Lesezeichen.
- **AdApproxPosition** bezieht sich auf die ungefähre Positionierung.

> [!NOTE]
> In ADO, Version 2.8 und früher, ruft der SQLOLEDB-Anbieter alle Datensätze bei Verwendung ein serverseitigen Cursors, trotz der Tatsache, die zurückgegeben **"true"** für beide **unterstützt (AdApproxPosition)** und **Unterstützt (zulässt)** .
  
Der Cursor-Datentyp, der die **Recordset** Objekt beeinflusst, ob die Anzahl der Datensätze bestimmt werden kann. Die **RecordCount** Eigenschaft gibt-1 für einen Vorwärtscursor; die tatsächliche Anzahl der für einen statischen oder Keysetcursor; und entweder-1 oder die tatsächliche Anzahl für einen dynamischen Cursor, abhängig von der Datenquelle zurück.
  
## <a name="applies-to"></a>Gilt für

[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch

[Filter und RecordCount – Beispiel (VB)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)   
[Filter und RecordCount – Beispiel (VC++)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)   
[AbsolutePosition-Eigenschaft (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
[PageCount-Eigenschaft (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
