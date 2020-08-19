---
description: Verwenden von CacheSize
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 5514f7b3a08d212e435a40341fc32033ec226c78
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452582"
---
# <a name="using-cachesize"></a>Verwenden von CacheSize
Verwenden Sie die **CacheSize** -Eigenschaft, um zu steuern, wie viele Datensätze gleichzeitig vom Anbieter in den lokalen Speicher abgerufen werden sollen. Wenn die **CacheSize** z. b. 10 ist, ruft der Anbieter nach dem ersten Öffnen des **Recordset** -Objekts die ersten 10 Datensätze in den lokalen Arbeitsspeicher ab. Wenn Sie durch das **Recordset** -Objekt wechseln, gibt der Anbieter die Daten aus dem lokalen Speicherpuffer zurück. Sobald Sie mit dem letzten Datensatz im Cache fortfahren, ruft der Anbieter die nächsten 10 Datensätze aus der Datenquelle in den Cache ab.  
  
> [!NOTE]
>  **CacheSize** basiert auf der maximalen Anzahl von **Open Rows** -anbieterspezifischen Eigenschaften (in der **Properties** -Auflistung des **Recordset** -Objekts). Sie können **CacheSize** nicht auf einen Wert festlegen, der größer ist als die **Maximale Anzahl offener Zeilen.** Um die Anzahl der Zeilen zu ändern, die vom Anbieter geöffnet werden können, legen Sie die **Maximale Anzahl geöffneter Zeilen**fest.  
  
 Der Wert von **CacheSize** kann während der Lebensdauer des **Recordset** -Objekts angepasst werden. Wenn Sie diesen Wert jedoch ändern, wirkt sich dies nur auf die Anzahl der Datensätze im Cache aus, nachdem nachfolgende Abruf Abbilder aus der Datenquelle abgerufen wurden. Wenn Sie den Eigenschafts Wert alleine ändern, wird der aktuelle Inhalt des Caches nicht geändert.  
  
 Wenn weniger Datensätze abgerufen werden müssen, als **CacheSize** angibt, gibt der Anbieter die verbleibenden Datensätze zurück, und es tritt kein Fehler auf.  
  
 Eine **CacheSize** -Einstellung von 0 (null) ist nicht zulässig und gibt einen Fehler zurück.  
  
 Datensätze, die aus dem Cache abgerufen werden, spiegeln keine gleichzeitigen Änderungen wider, die andere Benutzer an den Quelldaten vorgenommen haben. Verwenden Sie die [Resync](../../../ado/reference/ado-api/resync-method.md) -Methode, um ein Update aller zwischengespeicherten Daten zu erzwingen.  
  
 Wenn **CacheSize** auf einen Wert größer als 1 festgelegt ist, können die Navigationsmethoden ([Move](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst, MoveLast, MoveNext und MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)) zur Navigation zu einem gelöschten Datensatz führen, wenn der Löschvorgang nach dem Abrufen der Datensätze erfolgt. Nach dem ersten Abruf werden nachfolgende Löschvorgänge nicht in Ihren Daten Cache übernommen, bis Sie versuchen, auf einen Datenwert aus einer gelöschten Zeile zuzugreifen. Wenn Sie **CacheSize** jedoch auf 1 festlegen, wird dieses Problem dadurch vermieden, dass gelöschte Zeilen nicht abgerufen werden können.
