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
ms.openlocfilehash: cead84eed4e7689d6b5df907b6a61ef07ab74e8a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924930"
---
# <a name="jumping-to-a-record"></a>Springen zu einem Datensatz
Die [Move](../../../ado/reference/ado-api/move-method-ado.md) -Methode ermöglicht es Ihnen, im **Recordset** eine angegebene Anzahl von Datensätzen vorwärts oder rückwärts zu verschieben, indem Sie die folgende Syntax verwenden:  
  
```  
oRs.Move NumRecords, Start  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Move** -Methode wird für alle **Recordset** -Objekte unterstützt.  
  
 Wenn das *numrecords* -Argument größer als 0 (null) ist, wird die aktuelle Daten Satz Position nach vorne verschoben (am Ende des **Recordsets**). Wenn *numrecords* kleiner als 0 (null) ist, wird die aktuelle Daten Satz Position rückwärts (am Anfang des **Recordsets**) verschoben.  
  
 Wenn der **Verschiebungs Versuch die** aktuelle Daten Satz Position an einen Punkt vor dem ersten Datensatz verschiebt, legt ADO den aktuellen Datensatz auf die Position vor dem ersten Datensatz im **Recordset** (**BOF** ist **true**) fest. Ein Versuch, rückwärts zu wechseln, wenn die **BOF** -Eigenschaft bereits **true** ist, generiert einen Fehler.  
  
 Wenn der **Verschiebungs Versuch die** aktuelle Daten Satz Position an einen Punkt nach dem letzten Datensatz verschiebt, legt ADO den aktuellen Datensatz auf die Position hinter dem letzten Datensatz im **Recordset fest** (**EOF** ist **true**). Ein Versuch, vorwärts zu wechseln, wenn die **EOF** -Eigenschaft bereits **true** ist, generiert einen Fehler.  
  
 Wenn Sie die **Move** -Methode von einem leeren **Recordset** -Objekt aufrufen, wird ein Fehler generiert.  
  
 Wenn Sie ein Lesezeichen im *Start* Argument übergeben, ist der Verschiebe Vorgang relativ zum Datensatz mit diesem Lesezeichen, vorausgesetzt, das **Recordset** -Objekt unterstützt Lesezeichen. Ein Lesezeichen wird mithilfe der [Bookmark](../../../ado/reference/ado-api/bookmark-property-ado.md) -Eigenschaft abgerufen. Wenn nicht angegeben, ist der Verschiebe Vorgang relativ zum aktuellen Datensatz.  
  
 Wenn Sie die **CacheSize** -Eigenschaft verwenden, um Datensätze vom Anbieter lokal zwischenzuspeichern, wird durch das Übergeben eines *numrecords* -Arguments, das die aktuelle Daten Satz Position außerhalb der aktuellen Gruppe von zwischengespeicherten Datensätzen verschiebt, erzwungen, dass ADO eine neue Gruppe von Datensätzen aus dem Zieldatensatz abruft Die **CacheSize** -Eigenschaft bestimmt die Größe der neu abgerufenen Gruppe, und der Zieldatensatz ist der erste Datensatz, der abgerufen wird.
