---
description: AppendChunk-Methode (ADO)
title: AppendChunk-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::AppendChunk
- Field20::AppendChunk
helpviewer_keywords:
- AppendChunk method [ADO]
ms.assetid: c648b5a8-d4f1-4d16-836e-3957feb03617
author: rothja
ms.author: jroth
ms.openlocfilehash: 260f1bddfe4433e26463bd58b594d2766ccbc531
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88976011"
---
# <a name="appendchunk-method-ado"></a>AppendChunk-Methode (ADO)
Fügt Daten an ein großes Textfeld oder ein binäres [Datenfeld](./field-object.md)oder an ein [Parameter](./parameter-object.md) Objekt an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.AppendChunk Data  
```  
  
#### <a name="parameters"></a>Parameter  
 *object*  
 Ein **Feld** -oder **Parameter** Objekt.  
  
 *Daten*  
 Eine **Variante** , die die Daten enthält, die an das-Objekt angefügt werden sollen.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **AppendChunk** -Methode für ein **Feld** oder ein **Parameter** Objekt, um Sie mit langen Binär-oder Zeichendaten auszufüllen. In Situationen, in denen der System Arbeitsspeicher eingeschränkt ist, können Sie die **AppendChunk** -Methode verwenden, um lange Werte in Teilen zu bearbeiten, anstatt sie vollständig zu verarbeiten.  
  
## <a name="field"></a>Feld  
 Wenn das **adfldlong** -Bit in der [Attribute](./attributes-property-ado.md) -Eigenschaft eines **Feld** Objekts auf " **true**" festgelegt ist, können Sie die **AppendChunk** -Methode für dieses Feld verwenden.  
  
 Der erste **AppendChunk** -Befehl für ein **Field** -Objekt schreibt Daten in das-Feld, wobei alle vorhandenen Daten überschrieben werden. Nachfolgende **AppendChunk** -Aufrufe fügen vorhandenen Daten hinzu. Wenn Sie Daten an ein Feld Anfügen und dann den Wert eines anderen Felds im aktuellen Datensatz festlegen oder lesen, geht ADO davon aus, dass Sie mit dem Anfügen von Daten an das erste Feld fertig sind. Wenn Sie die **AppendChunk** -Methode erneut für das erste Feld aufzurufen, interpretiert ADO den-Befehl als neuen **AppendChunk** -Vorgang und überschreibt die vorhandenen Daten. Durch den Zugriff auf Felder in anderen [Recordset](./recordset-object-ado.md) -Objekten, die keine Klone des ersten **Recordset** -Objekts sind, werden **AppendChunk** -Vorgänge nicht gestört.  
  
 Wenn kein aktueller Datensatz vorhanden ist, wenn Sie **AppendChunk** für ein **Feld** Objekt aufzurufen, tritt ein Fehler auf.  
  
> [!NOTE]
>  Die **AppendChunk** -Methode funktioniert nicht mit **Feld** Objekten eines ADO-Objekts [(Record Object)](./record-object-ado.md) . Er führt keinen Vorgang aus und führt zu einem Laufzeitfehler.  
  
## <a name="parameter"></a>Parameter  
 Wenn das **adparamlong** -Bit in der **Attribute** -Eigenschaft eines **Parameter** Objekts auf " **true**" festgelegt ist, können Sie die **AppendChunk** -Methode für diesen Parameter verwenden.  
  
 Der erste **AppendChunk** -Befehl für ein **Parameter** Objekt schreibt Daten in den-Parameter, wobei alle vorhandenen Daten überschrieben werden. Nachfolgende **AppendChunk** -Aufrufe für ein **Parameter** Objekt fügen vorhandenen Parameter Daten hinzu. Bei einem **AppendChunk** -Befehl, der einen NULL-Wert übergibt, werden alle Parameterdaten verworfen.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Field-Objekt](./field-object.md)  
    :::column-end:::
    :::column:::
        [Parameter-Objekt](./parameter-object.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für AppendChunk und GetChunk-Methoden (VB)](./appendchunk-and-getchunk-methods-example-vb.md)   
 [Beispiel für AppendChunk und GetChunk-Methoden (VC + +)](./appendchunk-and-getchunk-methods-example-vc.md)   
 [Attribute-Eigenschaft (ADO)](./attributes-property-ado.md)   
 [GetChunk-Methode (ADO)](./getchunk-method-ado.md)