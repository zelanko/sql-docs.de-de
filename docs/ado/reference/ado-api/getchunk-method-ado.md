---
description: GetChunk-Methode (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: dcf021282d4fce049cd89a154c2d00186b3cbee1
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775079"
---
# <a name="getchunk-method-ado"></a>GetChunk-Methode (ADO)
Gibt alle oder einen Teil des Inhalts eines großen [Textfelds](./field-object.md) oder eines Binärdaten Feld Objekts zurück.  
  
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
  
 Jeder nachfolgende **GetChunk** -Befehl ruft Daten ab, von denen der vorherige **GetChunk** -Rückruf unterbrochen wurde. Wenn Sie jedoch Daten aus einem Feld abrufen und dann den Wert eines anderen Felds im aktuellen Datensatz festlegen oder lesen, geht ADO davon aus, dass Sie das Abrufen von Daten aus dem ersten Feld abgeschlossen haben. Wenn Sie die **GetChunk** -Methode erneut für das erste Feld aufrufen, interpretiert ADO den-Befehl als neuen **GetChunk** -Vorgang und beginnt mit dem Lesen vom Anfang der Daten. Durch den Zugriff auf Felder in anderen [Recordset](./recordset-object-ado.md) -Objekten, die keine Klone des ersten **Recordset** -Objekts sind, werden keine **GetChunk** -Vorgänge unterbrochen.  
  
 Wenn das **adfldlong** -Bit in der [Attribute](./attributes-property-ado.md) -Eigenschaft eines **Feld** Objekts auf " **true**" festgelegt ist, können Sie die **GetChunk** -Methode für dieses Feld verwenden.  
  
 Wenn kein aktueller Datensatz vorhanden ist, wenn Sie die **GetChunk** -Methode für ein **Feld** Objekt verwenden, tritt der Fehler 3021 (kein aktueller Datensatz) auf.  
  
> [!NOTE]
>  Die **GetChunk** -Methode funktioniert nicht mit **Feld** Objekten eines [Datensatz](./record-object-ado.md) -Objekts. Er führt keinen Vorgang aus und führt zu einem Laufzeitfehler.  
  
## <a name="applies-to"></a>Gilt für  
 [Field-Objekt](./field-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für AppendChunk und GetChunk-Methoden (VB)](./appendchunk-and-getchunk-methods-example-vb.md)   
 [Beispiel für AppendChunk und GetChunk-Methoden (VC + +)](./appendchunk-and-getchunk-methods-example-vc.md)   
 [AppendChunk-Methode (ADO)](./appendchunk-method-ado.md)   
 [Attributes-Eigenschaft (ADO)](./attributes-property-ado.md)