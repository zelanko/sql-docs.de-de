---
title: Positionierung von Recordsets | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: e48c80c59a51b007832b8c68c8e27c66333f57dc
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760976"
---
# <a name="recordset-positioning"></a>Positionieren von Recordsets
Verwenden Sie die **AbsolutePosition** -Eigenschaft, um zu einem Datensatz zu wechseln, der auf seiner Ordinalposition im **Recordset** -Objekt basiert, oder, um die Ordinalposition des aktuellen Datensatzes zu bestimmen. Der Anbieter muss die entsprechende Funktionalität unterstützen, damit diese Eigenschaft verfügbar ist.  
  
 **AbsolutePosition** ist 1-basiert und entspricht 1, wenn der aktuelle Datensatz der erste Datensatz im **Recordset**ist. Wie bereits erwähnt, können Sie die Gesamtanzahl der Datensätze im **Recordset** -Objekt aus der **RecordCount** -Eigenschaft abrufen.  
  
 Wenn Sie die **AbsolutePosition** -Eigenschaft festlegen, auch wenn Sie sich in einem Datensatz im aktuellen Cache befindet, lädt ADO den Cache mit einer neuen Gruppe von Datensätzen neu, beginnend mit dem von Ihnen angegebenen Datensatz. Die **CacheSize** -Eigenschaft bestimmt die Größe dieser Gruppe.  
  
> [!NOTE]
>  Sie sollten die **AbsolutePosition** -Eigenschaft nicht als Ersatz Zeichendaten Satz Nummer verwenden. Die Position eines angegebenen Datensatzes ändert sich, wenn Sie einen vorangehenden Datensatz löschen. Außerdem ist nicht sichergestellt, dass ein bestimmter Datensatz dieselbe **AbsolutePosition** hat, wenn das **Recordset** -Objekt angefordert oder erneut geöffnet wird. Lesezeichen sind die empfohlene Methode zum beibehalten und zurückkehren zu einer bestimmten Position und sind die einzige Möglichkeit, über alle Typen von **recordsetobjekten** hinweg zu positionieren.
