---
title: GetChunk-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::raw_GetChunk
- Field20::GetChunk
helpviewer_keywords:
- GetChunk method [ADO]
ms.assetid: fc268e22-205b-44a3-9038-ffed51e23e10
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 43c5fef08d22364b9842c58fc82d46ba4bfa00bd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918564"
---
# <a name="getchunk-method-ado"></a>GetChunk-Methode (ADO)
Gibt alle oder einen Teil des Inhalts eines großen [Textfelds](../../../ado/reference/ado-api/field-object.md) oder eines Binärdaten Feld Objekts zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
variable = field.GetChunk(Size)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **Variante**zurück.  
  
#### <a name="parameters"></a>Parameter  
 *Größe*  
 Ein **Long** -Ausdruck, der gleich der Anzahl von Bytes oder Zeichen ist, die Sie abrufen möchten.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **GetChunk** -Methode für ein **Field** -Objekt, um einen Teil oder alle langen Binär-oder Zeichendaten abzurufen. In Situationen, in denen der System Arbeitsspeicher eingeschränkt ist, können Sie die **GetChunk** -Methode verwenden, um lange Werte in Teilen zu bearbeiten, anstatt sie vollständig zu verwenden.  
  
 Die Daten, die von einem **GetChunk** -Rückruf zurückgegeben werden, werden einer *Variablen*zugewiesen. Wenn die *Größe* größer ist als die verbleibenden Daten, gibt die **GetChunk** -Methode nur die verbleibenden Daten ohne Auffüll *Variable* mit leeren Leerzeichen zurück. Wenn das Feld leer ist, gibt die **GetChunk** -Methode einen NULL-Wert zurück.  
  
 Jeder nachfolgende **GetChunk** -Befehl ruft Daten ab, von denen der vorherige **GetChunk** -Rückruf unterbrochen wurde. Wenn Sie jedoch Daten aus einem Feld abrufen und dann den Wert eines anderen Felds im aktuellen Datensatz festlegen oder lesen, geht ADO davon aus, dass Sie das Abrufen von Daten aus dem ersten Feld abgeschlossen haben. Wenn Sie die **GetChunk** -Methode erneut für das erste Feld aufrufen, interpretiert ADO den-Befehl als neuen **GetChunk** -Vorgang und beginnt mit dem Lesen vom Anfang der Daten. Durch den Zugriff auf Felder in anderen [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekten, die keine Klone des ersten **Recordset** -Objekts sind, werden keine **GetChunk** -Vorgänge unterbrochen.  
  
 Wenn das **adfldlong** -Bit in der [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) -Eigenschaft eines **Feld** Objekts auf " **true**" festgelegt ist, können Sie die **GetChunk** -Methode für dieses Feld verwenden.  
  
 Wenn kein aktueller Datensatz vorhanden ist, wenn Sie die **GetChunk** -Methode für ein **Feld** Objekt verwenden, tritt der Fehler 3021 (kein aktueller Datensatz) auf.  
  
> [!NOTE]
>  Die **GetChunk** -Methode funktioniert nicht mit **Feld** Objekten eines [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) -Objekts. Er führt keinen Vorgang aus und führt zu einem Laufzeitfehler.  
  
## <a name="applies-to"></a>Gilt für  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für AppendChunk und GetChunk-Methoden (VB)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [Beispiel für AppendChunk und GetChunk-Methoden (VC + +)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [AppendChunk-Methode (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [Attributes-Eigenschaft (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
