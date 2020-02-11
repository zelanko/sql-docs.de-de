---
title: GetRows-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d96b7968c7aba8d1249db2f43b53fc8a22596419
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918453"
---
# <a name="getrows-method-ado"></a>GetRows-Methode (ADO)
Ruft mehrere Datensätze eines [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekts in ein Array ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array = recordset.GetRows(Rows, Start, Fields )  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **Variante** zurück, deren Wert ein zweidimensionales Array ist.  
  
#### <a name="parameters"></a>Parameter  
 *Zeilen*  
 Optional. Ein [GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md) -Wert, der die Anzahl der abzurufenden Datensätze angibt. Der Standardwert ist **adgetrowsrest**.  
  
 *Starten*  
 Optional. Ein **Zeichen** folgen Wert oder **Variant** , der das Lesezeichen für den Datensatz ergibt, von dem der **GetRows** -Vorgang beginnen soll. Sie können auch einen [bookmarkenum](../../../ado/reference/ado-api/bookmarkenum.md) -Wert verwenden.  
  
 *Fields*  
 Optional. Eine **Variante** , die einen einzelnen Feldnamen oder eine Ordinalposition darstellt, oder ein Array von Feldnamen oder ordinalpositions Nummern. ADO gibt nur die Daten in diesen Feldern zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **GetRows** -Methode, um Datensätze aus einem **Recordset** in ein zweidimensionales Array zu kopieren. Der erste Index identifiziert das Feld, und das zweite bezeichnet die Datensatznummer. Die *Array* Variable wird automatisch auf die richtige Größe dimensioniert, wenn die **GetRows** -Methode die Daten zurückgibt.  
  
 Wenn Sie keinen Wert für das *Rows* -Argument angeben, ruft die **GetRows** -Methode automatisch alle Datensätze im **Recordset** -Objekt ab. Wenn Sie mehr Datensätze anfordern, als verfügbar sind, gibt **GetRows** nur die Anzahl der verfügbaren Datensätze zurück.  
  
 Wenn das **Recordset** -Objekt Lesezeichen unterstützt, können Sie angeben, in welchem Datensatz die **GetRows** -Methode mit dem Abrufen von Daten beginnen soll, indem Sie den Wert der [Bookmark](../../../ado/reference/ado-api/bookmark-property-ado.md) -Eigenschaft dieses Datensatzes im *Start* Argument übergeben.  
  
 Wenn Sie die Felder einschränken möchten, die der **GetRows** -Rückruf zurückgibt, können Sie entweder einen einzelnen Feldnamen/eine Zahl oder ein Array von Feldnamen/-Zahlen im *Fields* -Argument übergeben.  
  
 Nachdem Sie **GetRows**aufgerufen haben, wird der nächste ungelesene Datensatz zum aktuellen Datensatz, oder die [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) -Eigenschaft wird auf **true** festgelegt, wenn keine weiteren Datensätze vorhanden sind.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine GetRows-Methode (VB)](../../../ado/reference/ado-api/getrows-method-example-vb.md)   
 [GetRows-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/getrows-method-example-vc.md)   
