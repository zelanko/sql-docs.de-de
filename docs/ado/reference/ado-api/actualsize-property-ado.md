---
description: ActualSize-Eigenschaft (ADO)
title: ActualSize-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::ActualSize
helpviewer_keywords:
- ActualSize property [ADO]
ms.assetid: 722803d0-cef5-4d4c-b79d-3f2f58052229
author: rothja
ms.author: jroth
ms.openlocfilehash: b08a0ce6f9b318430785938c33ce951282eafce2
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88760285"
---
# <a name="actualsize-property-ado"></a>ActualSize-Eigenschaft (ADO)
Gibt die tatsächliche Länge des Werts eines Felds in Bytes an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Gibt einen **Long** -Wert zurück.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie die **ActualSize** -Eigenschaft, um die tatsächliche Länge des Werts eines [Feld](./field-object.md) Objekts zurückzugeben. Die **ActualSize** -Eigenschaft ist für alle Felder schreibgeschützt. Wenn ADO die Länge des **Feld** Objekt Werts nicht ermitteln kann, gibt die **ActualSize** -Eigenschaft **adunknown**zurück.  
  
 Die Eigenschaften **ActualSize** und [DefinedSize](./definedsize-property.md) sind unterschiedlich, wie im folgenden Beispiel gezeigt. Ein **Feld** Objekt mit einem deklarierten Typ von **adVarChar** und eine maximale Länge von 50 Zeichen gibt einen **DefinedSize** -Eigenschafts Wert von 50 zurück, aber der Rückgabewert der **ActualSize** -Eigenschaft ist die Länge der Daten, die im Feld für den aktuellen Datensatz gespeichert sind. **Felder** mit einer **DefinedSize** größer als 255 Bytes werden als Spalten variabler Länge behandelt.  
  
## <a name="applies-to"></a>Gilt für  
 [Field-Objekt](./field-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für ActualSize und DefinedSize-Eigenschaften (VB)](./actualsize-and-definedsize-properties-example-vb.md)   
 [Beispiel für ActualSize und DefinedSize-Eigenschaften (VC + +)](./actualsize-and-definedsize-properties-example-vc.md)   
 [DefinedSize-Eigenschaft](./definedsize-property.md)