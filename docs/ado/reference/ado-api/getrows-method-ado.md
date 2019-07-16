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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67918453"
---
# <a name="getrows-method-ado"></a>GetRows-Methode (ADO)
Ruft mehrere Datensätze aus einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt in ein Array.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array = recordset.GetRows(Rows, Start, Fields )  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **Variant** , deren Wert ist ein zweidimensionales Array.  
  
#### <a name="parameters"></a>Parameter  
 *Zeilen*  
 Optional. Ein [GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md) Wert, der die Anzahl der abzurufenden Datensätze angibt. Der Standardwert ist **AdGetRowsRest**.  
  
 *Start*  
 Dies ist optional. Ein **Zeichenfolge** Wert oder **Variant** , ausgewertet wird, zu dem Lesezeichen für den Datensatz aus der die **GetRows** Vorgang beginnen soll. Sie können auch eine [BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md) Wert.  
  
 *Felder*  
 Dies ist optional. Ein **Variant** , die einen einzelnen Feldnamen oder Ordnungsposition oder ein Array von Feldnamen oder Ordnungsposition Zahlen darstellt. ADO werden nur die Daten in diesen Feldern zurück.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **GetRows** Methode zum Kopieren der Datensätze aus einer **Recordset** in ein zweidimensionales Array. Der erste Index identifiziert das Feld und die zweite die Datensatznummer. Die *Array* Variable automatisch der richtige dimensioniert ist Größe, wenn die **GetRows** Methode gibt die Daten zurück.  
  
 Wenn Sie einen Wert für nicht angeben der *Zeilen* -Argument, das **GetRows** Methode übernimmt automatisch alle Datensätze in der **Recordset** Objekt. Wenn Sie mehrere Datensätze als verfügbar sind, anfordern **GetRows** gibt nur die Anzahl der verfügbaren Datensätze zurück.  
  
 Wenn die **Recordset** Objekt unterstützt, Lesezeichen, Sie können angeben, bei welchem Datensatz der **GetRows** Methode beginnen soll, das Abrufen von Daten durch Übergeben des Werts für diesen Datensatz des [Lesezeichen](../../../ado/reference/ado-api/bookmark-property-ado.md)-Eigenschaft in der *starten* Argument.  
  
 Wenn Sie die Felder beschränken möchten, die die **GetRows** Aufruf zurückgegeben wird, können Sie entweder ein einzelnes Feld/-Nummer oder ein Array von Feldnamen/Nummern in übergeben die *Felder* Argument.  
  
 Nach dem Aufruf von **GetRows**, die nächste ungelesene Datensatz zum aktuellen Datensatz oder das [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) -Eigenschaftensatz auf **"true"** , wenn keine weitere Datensätze vorhanden sind.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetRows-Methode – Beispiel (VB)](../../../ado/reference/ado-api/getrows-method-example-vb.md)   
 [GetRows-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/getrows-method-example-vc.md)   
