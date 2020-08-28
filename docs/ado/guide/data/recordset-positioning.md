---
description: Positionieren von Recordsets
title: Positionierung von Recordsets | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- record positioning [ADO]
- Recordset object [ADO]
- repositioning record [ADO]
- AbsolutePosition property [ADO]
ms.assetid: c8f6fbcb-6675-4133-b37e-430de43949c1
author: rothja
ms.author: jroth
ms.openlocfilehash: 1f97f5b9c9a947362edffaa88f878c96d63b270f
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979881"
---
# <a name="recordset-positioning"></a>Positionieren von Recordsets
Verwenden Sie die **AbsolutePosition** -Eigenschaft, um zu einem Datensatz zu wechseln, der auf seiner Ordinalposition im **Recordset** -Objekt basiert, oder, um die Ordinalposition des aktuellen Datensatzes zu bestimmen. Der Anbieter muss die entsprechende Funktionalität unterstützen, damit diese Eigenschaft verfügbar ist.  
  
 **AbsolutePosition** ist 1-basiert und entspricht 1, wenn der aktuelle Datensatz der erste Datensatz im **Recordset**ist. Wie bereits erwähnt, können Sie die Gesamtanzahl der Datensätze im **Recordset** -Objekt aus der **RecordCount** -Eigenschaft abrufen.  
  
 Wenn Sie die **AbsolutePosition** -Eigenschaft festlegen, auch wenn Sie sich in einem Datensatz im aktuellen Cache befindet, lädt ADO den Cache mit einer neuen Gruppe von Datensätzen neu, beginnend mit dem von Ihnen angegebenen Datensatz. Die **CacheSize** -Eigenschaft bestimmt die Größe dieser Gruppe.  
  
> [!NOTE]
>  Sie sollten die **AbsolutePosition** -Eigenschaft nicht als Ersatz Zeichendaten Satz Nummer verwenden. Die Position eines angegebenen Datensatzes ändert sich, wenn Sie einen vorangehenden Datensatz löschen. Außerdem ist nicht sichergestellt, dass ein bestimmter Datensatz dieselbe **AbsolutePosition** hat, wenn das **Recordset** -Objekt angefordert oder erneut geöffnet wird. Lesezeichen sind die empfohlene Methode zum beibehalten und zurückkehren zu einer bestimmten Position und sind die einzige Möglichkeit, über alle Typen von **recordsetobjekten** hinweg zu positionieren.
