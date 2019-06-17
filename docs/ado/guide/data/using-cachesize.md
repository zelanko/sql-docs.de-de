---
title: Verwenden von CacheSize | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- locks [ADO], CacheSize property
- CacheSize property [ADO]
ms.assetid: ca1c3422-b6a4-4ba6-af55-54f975b698b1
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d0b6a1b83b09d504f8f3394a32ee10d556fcd18c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66699740"
---
# <a name="using-cachesize"></a>Verwenden von CacheSize
Verwenden der **CacheSize** Eigenschaft, um zu steuern, wie viele Datensätze gleichzeitig in den lokalen Arbeitsspeicher vom Anbieter abzurufen. Z. B. wenn die **CacheSize** ist 10, nach dem ersten Öffnen der **Recordset** Objekt ist, wird der Anbieter Ruft die ersten 10 Datensätze in den lokalen Speicher ab. Beim Navigieren durch die **Recordset** Objekt, gibt der Anbieter die Daten aus dem lokalen Speicherpuffer zurück. Sobald Sie hinter dem letzten Datensatz im Cache verschieben, ruft die nächsten 10 Datensätze aus der Datenquelle mit der Anbieter in den Cache ab.  
  
> [!NOTE]
>  **CacheSize** basiert auf der **maximale Anzahl geöffneter Zeilen** -anbieterspezifische Datenquelleneigenschaft (in der **Eigenschaften** Auflistung von der **Recordset** Objekt). Sie können keine festlegen **CacheSize** auf einen Wert größer als **maximale Anzahl geöffneter Zeilen.** Um die Anzahl der Zeilen zu ändern, die vom Anbieter geöffnet werden können, legen Sie **maximale Anzahl geöffneter Zeilen**.  
  
 Der Wert des **CacheSize** angepasst werden kann, während der Lebensdauer der **Recordset** Objekt handelt, sondern durch Ändern dieses Werts wirkt sich nur auf die Anzahl der Datensätze im Cache nach der spätere Zugriffe aus der Datenquelle. Ändern den Wert der Eigenschaft allein ändert sich nicht auf den aktuellen Inhalt des Caches aus.  
  
 Wenn weniger Datensätze als abzurufenden **CacheSize** angibt, gibt der Anbieter die übrigen Datensätze zurück, und kein Fehler auftritt.  
  
 Ein **CacheSize** Einstellung von 0 (null) ist nicht zulässig, und gibt einen Fehler zurück.  
  
 Datensätze, die aus dem Cache abgerufene spiegeln nicht die gleichzeitige Änderungen, die andere Benutzer auf die Quelldaten vorgenommen haben. Um ein Update aller zwischengespeicherten Daten zu erzwingen, verwenden die [Resync](../../../ado/reference/ado-api/resync-method.md) Methode.  
  
 Wenn **CacheSize** auf einen Wert größer als 1 ist, die Navigationsmethoden festgelegt wird ([verschieben](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst, MoveLast, MoveNext und MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)) kann bei der Navigation zu einer gelöschten führen Notieren Sie, falls der Löschvorgang, nachdem die Datensätze abgerufen wurden. Nach dem Abrufen werden nachfolgende Löschvorgänge nicht in Datencache wiedergegeben werden, bis Sie versuchen, einen Datenwert aus einer gelöschten Zeile zugreifen. Festlegen von jedoch **CacheSize** auf 1 beseitigt dieses Problem, da der gelöschte Zeilen nicht abgerufen werden können.
