---
title: Springen zu einem Datensatz | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- record jumping [ADO]
- jumping to record [ADO]
ms.assetid: 6caf6299-2eea-4d34-9b0e-b75aab07b740
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7185dca3db146e7c17f41cb0f0c5376274fe3634
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747868"
---
# <a name="jumping-to-a-record"></a>Springen zu einem Datensatz
Die [verschieben](../../../ado/reference/ado-api/move-method-ado.md) Methode können Sie in vorwärts oder rückwärts bewegen der **Recordset** eine angegebene Anzahl von Datensätzen mithilfe der folgenden Syntax:  
  
```  
oRs.Move NumRecords, Start  
```  
  
## <a name="remarks"></a>Hinweise  
 Die **verschieben** -Methode wird für alle unterstützt **Recordset** Objekte.  
  
 Wenn die *NumRecords* Argument ist größer als 0 (null), die Position des aktuelle Datensatzes wird vorwärts verschoben (gegen Ende der **Recordset**). Wenn *NumRecords* ist kleiner als 0 (null), die Position des aktuelle Datensatzes verschiebt diesen rückwärts (bis zum Anfang der **Recordset**).  
  
 Wenn die **verschieben** aufrufen würde die Position des aktuelle Datensatzes auf einen Zeitpunkt vor dem ersten Datensatz verschoben, ADO legt den aktuellen Datensatz auf die Position vor dem ersten Datensatz in die **Recordset** (**BOF** ist **"true"**). Der Versuch, verschieben Abwärtskompatibilität bei der **BOF** Eigenschaft ist bereits **"true"** wird ein Fehler generiert.  
  
 Wenn die **verschieben** Aufruf wird die Position des aktuelle Datensatzes zu einem Zeitpunkt nach dem letzten Datensatz verschieben, ADO legt den aktuellen Datensatz auf die Position hinter dem letzten Datensatz in die **Recordset** (**EOF** ist **"true"**). Der Versuch, forward When Verschieben der **EOF** Eigenschaft ist bereits **"true"** wird ein Fehler generiert.  
  
 Aufrufen der **verschieben** Methode aus einer leeren **Recordset** Objekt wird ein Fehler generiert.  
  
 Wenn Sie ein Lesezeichen im übergeben die *starten* Argument der Verschiebevorgang ist relativ zu dem Datensatz mit diesem Lesezeichen, vorausgesetzt die **Recordset** -Objekt Lesezeichen unterstützt. Ein Lesezeichen wird abgerufen, indem Sie mit der [Lesezeichen](../../../ado/reference/ado-api/bookmark-property-ado.md) Eigenschaft. Wenn nicht angegeben, ist die Verschiebung, relativ zum aktuellen Datensatz.  
  
 Bei Verwendung der **CacheSize** Eigenschaft lokal Datensätze aus den Anbieter übergeben Zwischenspeichern einer *NumRecords* Argument, das die Position des aktuelle Datensatzes außerhalb der aktuellen Gruppe der zwischengespeicherten Einträge verschiebt Erzwingt, dass ADO zum Abrufen einer neuen Gruppe von Datensätzen aus dem Zieldatensatz ab. Die **CacheSize** Eigenschaft bestimmt die Größe der Gruppe "neu abgerufener", und der Zieldatensatz ist der erste Datensatz abgerufen.
