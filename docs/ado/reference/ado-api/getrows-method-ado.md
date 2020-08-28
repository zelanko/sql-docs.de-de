---
description: GetRows-Methode (ADO)
title: GetRows-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::GetRows
- Recordset15::raw_GetRows
helpviewer_keywords:
- Getrows method [ADO]
ms.assetid: 14b92860-4171-47d9-a413-dd60dd6a8880
author: rothja
ms.author: jroth
ms.openlocfilehash: 666eabf1a375c6a86826bc94600846bd10a0ecfe
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990911"
---
# <a name="getrows-method-ado"></a>GetRows-Methode (ADO)
Ruft mehrere Datensätze eines [Recordset](./recordset-object-ado.md) -Objekts in ein Array ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array = recordset.GetRows(Rows, Start, Fields )  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **Variante** zurück, deren Wert ein zweidimensionales Array ist.  
  
#### <a name="parameters"></a>Parameter  
 *Zeilen*  
 Optional. Ein [GetRowsOptionEnum](./getrowsoptionenum.md) -Wert, der die Anzahl der abzurufenden Datensätze angibt. Der Standardwert ist **adgetrowsrest**.  
  
 *Starten*  
 Optional. Ein **Zeichen** folgen Wert oder **Variant** , der das Lesezeichen für den Datensatz ergibt, von dem der **GetRows** -Vorgang beginnen soll. Sie können auch einen [bookmarkenum](./bookmarkenum.md) -Wert verwenden.  
  
 *Felder*  
 Optional. Eine **Variante** , die einen einzelnen Feldnamen oder eine Ordinalposition darstellt, oder ein Array von Feldnamen oder ordinalpositions Nummern. ADO gibt nur die Daten in diesen Feldern zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **GetRows** -Methode, um Datensätze aus einem **Recordset** in ein zweidimensionales Array zu kopieren. Der erste Index identifiziert das Feld, und das zweite bezeichnet die Datensatznummer. Die *Array* Variable wird automatisch auf die richtige Größe dimensioniert, wenn die **GetRows** -Methode die Daten zurückgibt.  
  
 Wenn Sie keinen Wert für das *Rows* -Argument angeben, ruft die **GetRows** -Methode automatisch alle Datensätze im **Recordset** -Objekt ab. Wenn Sie mehr Datensätze anfordern, als verfügbar sind, gibt **GetRows** nur die Anzahl der verfügbaren Datensätze zurück.  
  
 Wenn das **Recordset** -Objekt Lesezeichen unterstützt, können Sie angeben, in welchem Datensatz die **GetRows** -Methode mit dem Abrufen von Daten beginnen soll, indem Sie den Wert der [Bookmark](./bookmark-property-ado.md) -Eigenschaft dieses Datensatzes im *Start* Argument übergeben.  
  
 Wenn Sie die Felder einschränken möchten, die der **GetRows** -Rückruf zurückgibt, können Sie entweder einen einzelnen Feldnamen/eine Zahl oder ein Array von Feldnamen/-Zahlen im *Fields* -Argument übergeben.  
  
 Nachdem Sie **GetRows**aufgerufen haben, wird der nächste ungelesene Datensatz zum aktuellen Datensatz, oder die [EOF](./bof-eof-properties-ado.md) -Eigenschaft wird auf **true** festgelegt, wenn keine weiteren Datensätze vorhanden sind.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine GetRows-Methode (VB)](./getrows-method-example-vb.md)   
 [GetRows-Methode – Beispiel (VC++)](./getrows-method-example-vc.md)