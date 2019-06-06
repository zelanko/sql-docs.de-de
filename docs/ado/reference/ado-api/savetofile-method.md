---
title: SaveToFile-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SaveToFile
- _Stream::SaveToFile
helpviewer_keywords:
- SaveToFile method [ADO]
ms.assetid: 8a8594f2-422b-4d2e-94f8-7fe337445900
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1b3a94fddf1ac439096e2e0106fb2becb79249c7
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66711338"
---
# <a name="savetofile-method"></a>SaveToFile-Methode
Speichert den binären Inhalt, der eine [Stream](../../../ado/reference/ado-api/stream-object-ado.md) in eine Datei.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.SaveToFile FileName, SaveOptions  
```  
  
#### <a name="parameters"></a>Parameter  
 *FileName*  
 Ein **Zeichenfolge** -Wert, der den vollqualifizierten Namen der Datei, die die enthält, den Inhalt der **Stream** gespeichert werden sollen. Sie können auf einen beliebigen gültigen lokalen Speicherort speichern, oder einem beliebigen Speicherort haben Sie Zugriff auf über einen UNC-Wert.  
  
 *SaveOptions*  
 Ein [SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md) Wert, der angibt, ob eine neue Datei soll, indem erstellt werden **SaveToFile**, wenn es nicht bereits vorhanden ist. Standardwert ist **AdSaveCreateNotExists**. Mit diesen Optionen können Sie angeben, dass ein Fehler auftritt, wenn die angegebene Datei nicht vorhanden ist. Sie können auch angeben, die **SaveToFile** wird der aktuelle Inhalt einer vorhandenen Datei überschrieben.  
  
> [!NOTE]
>  Wenn Sie eine vorhandene Datei überschreiben (Wenn **AdSaveCreateOverwrite** festgelegt ist), **SaveToFile** alle Bytes aus der vorhandenen Datei, die die neue folgen [EOS](../../../ado/reference/ado-api/eos-property.md).  
  
## <a name="remarks"></a>Hinweise  
 **SaveToFile** kann verwendet werden, um den Inhalt einer **Stream** Objekt in einer lokalen Datei. Es ist keine Änderung in den Inhalt oder die Eigenschaften des der **Stream** Objekt. Die **Stream** Objekt vor dem Aufruf geöffnet sein **SaveToFile**.  
  
 Diese Methode ändert nicht die Zuordnung der **Stream** Objekt an die zugrunde liegende Quelle. Die **Stream** Objekt weiterhin die ursprüngliche URL zugeordnet werden oder **Datensatz** , war die Quelle beim Öffnen.  
  
 Nach einem **SaveToFile** Vorgang, der aktuellen Position ([Position](../../../ado/reference/ado-api/position-property-ado.md)) in den Datenstrom an den Anfang des Streams (0) festgelegt ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Open Sie-Methode (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Save-Methode](../../../ado/reference/ado-api/save-method.md)
