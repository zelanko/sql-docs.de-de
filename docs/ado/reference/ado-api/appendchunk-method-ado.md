---
title: AppendChunk-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f9d575460daf0f801f6d6dd2e80b0c67f4886dc7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67920565"
---
# <a name="appendchunk-method-ado"></a>AppendChunk-Methode (ADO)
Fügt Daten an eine große Text- oder Binärdaten [Feld](../../../ado/reference/ado-api/field-object.md), oder auf eine [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.AppendChunk Data  
```  
  
#### <a name="parameters"></a>Parameter  
 *object*  
 Ein **Feld** oder **Parameter** Objekt.  
  
 *Daten*  
 Ein **Variant** enthält die Daten, auf das Objekt angefügt werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **AppendChunk** Methode für eine **Feld** oder **Parameter** Objekt, das mit dem lange Binär-oder Zeichendatentypen zu füllen. In Situationen, in dem Systemspeicher beschränkt ist, können Sie die **AppendChunk** Methode, um lange Werte in Teilen und nicht in ihrer Gesamtheit zu bearbeiten.  
  
## <a name="field"></a>Feld  
 Wenn die **AdFldLong** bit im der [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) Eigenschaft eine **Feld** Objekt nastaven NA hodnotu **"true"** , können Sie die  **AppendChunk** Methode für dieses Feld.  
  
 Die erste **AppendChunk** rufen Sie für eine **Feld** Objekt schreibt Daten in das Feld, dass alle vorhandenen Daten. Nachfolgende **AppendChunk** Aufrufe an die vorhandenen Daten hinzufügen. Wenn von Daten auf ein Feld anfügen sind, und klicken Sie dann festlegen oder Lesen Sie den Wert eines anderen Felds im aktuellen Datensatz, wird das ADO davon ausgegangen, dass Sie die Daten an das erste Feld anfügen abgeschlossen haben. Aufrufen der **AppendChunk** Methode für das erste Feld in diesem Fall ADO interpretiert den Aufruf als eine neue **AppendChunk** Vorgang und die vorhandenen Daten überschrieben. Beim Zugriff auf Felder in anderen [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekte, die nicht Klonen des ersten **Recordset** Objekt wird nicht unterbrochen. **AppendChunk** Vorgänge.  
  
 Wenn kein aktueller Datensatz vorhanden, beim Aufrufen ist **AppendChunk** auf eine **Feld** Objekt, ein Fehler auftritt.  
  
> [!NOTE]
>  Die **AppendChunk** Methode führt keine Vorgänge für **Feld** Objekte eine [Datensatz für Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md) Objekt. Es ist keine Vorgänge ausführen und einen Laufzeitfehler erzeugt.  
  
## <a name="parameter"></a>Parameter  
 Wenn die **AdParamLong** bit im der **Attribute** Eigenschaft eine **Parameter** Objekt nastaven NA hodnotu **"true"** , können Sie die  **AppendChunk** Methode für diesen Parameter.  
  
 Die erste **AppendChunk** rufen Sie für eine **Parameter** Objekt schreibt Daten in der Parameter, dass alle vorhandenen Daten. Nachfolgende **AppendChunk** Ruft für ein **Parameter** Objekt hinzuzufügen, zu vorhandenen Parameterdaten. Ein **AppendChunk** Aufruf, der einen null-Wert übergibt verwirft alle der Parameterdaten.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Field-Objekt](../../../ado/reference/ado-api/field-object.md)|[Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [AppendChunk und GetChunk-Methoden – Beispiel (VB)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [AppendChunk und GetChunk-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [Attributes-Eigenschaft (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)   
 [GetChunk-Methode (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
