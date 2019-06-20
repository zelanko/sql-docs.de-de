---
title: CacheSize-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::CacheSize
helpviewer_keywords:
- CacheSize property [ADO]
ms.assetid: 49dc9a49-af7b-433b-be36-7a14ca984fb7
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f5824141f57838f676b2e1af3e3e9c4f3041648b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718094"
---
# <a name="cachesize-property-ado"></a>CacheSize-Eigenschaft (ADO)
Gibt die Anzahl der Datensätze aus einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt, das lokal im Arbeitsspeicher zwischengespeichert werden.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **lange** -Wert, der größer als 0 sein muss. Standardwert ist 1.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **CacheSize** Eigenschaft, um zu steuern, wie viele Datensätze gleichzeitig in den lokalen Arbeitsspeicher vom Anbieter abzurufen. Z. B. wenn die **CacheSize** ist 10, nach dem ersten Öffnen der **Recordset** Objekt ist, wird der Anbieter Ruft die ersten 10 Datensätze in den lokalen Speicher ab. Beim Navigieren durch die **Recordset** Objekt, gibt der Anbieter die Daten aus dem lokalen Speicherpuffer zurück. Sobald Sie hinter dem letzten Datensatz im Cache verschieben, ruft die nächsten 10 Datensätze aus der Datenquelle mit der Anbieter in den Cache ab.  
  
> [!NOTE]
>  **CacheSize** basiert auf der **maximale Anzahl geöffneter Zeilen** -anbieterspezifische Datenquelleneigenschaft (in der **Eigenschaften** Auflistung von der **Recordset** Objekt). Sie können keine festlegen **CacheSize** auf einen Wert größer als **maximale Anzahl geöffneter Zeilen**. Zum Ändern der vom Anbieter geöffnet werden, kann der Anzahl der Zeilen festgelegt **maximale Anzahl geöffneter Zeilen**.  
  
 Der Wert des **CacheSize** angepasst werden kann, während der Lebensdauer der **Recordset** Objekt handelt, sondern durch Ändern dieses Werts wirkt sich nur auf die Anzahl der Datensätze im Cache nach der spätere Zugriffe aus der Datenquelle. Ändern den Wert der Eigenschaft allein ändert sich nicht auf den aktuellen Inhalt des Caches aus.  
  
 Wenn weniger Datensätze als abzurufenden **CacheSize** angibt, gibt der Anbieter die übrigen Datensätze zurück, und kein Fehler auftritt.  
  
 Ein **CacheSize** Einstellung von 0 (null) ist nicht zulässig, und gibt einen Fehler zurück.  
  
 Aus dem Cache abgerufenen Datensätze widerspiegeln nicht gleichzeitige Änderungen, die andere Benutzer auf die Quelldaten vorgenommen haben. Um ein Update aller zwischengespeicherten Daten zu erzwingen, verwenden die [Resync](../../../ado/reference/ado-api/resync-method.md) Methode.  
  
 Wenn **CacheSize** auf einen Wert größer als eins, die Navigationsmethoden festgelegt ist ([verschieben](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst, MoveLast, MoveNext und MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)) möglicherweise Navigation zu einem Falls der Löschvorgang, nachdem die Datensätze abgerufen wurden, wird der Datensatz, gelöscht. Nach dem Abrufen werden nachfolgende Löschvorgänge nicht in Datencache wiedergegeben werden, bis Sie versuchen, einen Datenwert aus einer gelöschten Zeile zugreifen. Festlegen von jedoch **CacheSize** auf einen beseitigt dieses Problem, da der gelöschte Zeilen nicht abgerufen werden können.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [CacheSize-Eigenschaft – Beispiel (VB)](../../../ado/reference/ado-api/cachesize-property-example-vb.md)   
 [CacheSize-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/cachesize-property-example-vc.md)   
 [CacheSize-Eigenschaft – Beispiel (JScript)](../../../ado/reference/ado-api/cachesize-property-example-jscript.md)
