---
title: Positionieren von Recordsets | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c01d24a5f92b4bca1e5b41a0cbece980237fd961
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701681"
---
# <a name="recordset-positioning"></a>Positionieren von Recordsets
Verwenden der **AbsolutePosition** -Eigenschaft zum Verschieben auf einen Datensatz, basierend auf der Ordnungsposition in der **Recordset** -Objekt, oder um die Ordinalposition des aktuellen Datensatzes zu bestimmen. Der Anbieter muss die entsprechende Funktionalität für diese Eigenschaft zur Verfügung stehen unterstützen.  
  
 **AbsolutePosition** ist 1-basiert und entspricht 1, wenn der aktuelle Datensatz den ersten Datensatz in ist die **Recordset**. Wie bereits erwähnt, erhalten Sie die Gesamtzahl der Datensätze in der **Recordset** -Objekt aus der **RecordCount** Eigenschaft.  
  
 Beim Festlegen der **AbsolutePosition** -Eigenschaft, auch wenn es zu einem Datensatz im aktuellen Cache ist ADO lädt den Cache mit einer neuen Gruppe von Datensätzen, die mit dem angegebenen Datensatz ab. Die **CacheSize** Eigenschaft bestimmt die Größe dieser Gruppe.  
  
> [!NOTE]
>  Verwenden Sie nicht die **AbsolutePosition** -Eigenschaft, wie ein Ersatzzeichen Datensatznummer. Die Position eines bestimmten Datensatzes geändert wird, wenn Sie einen vorherigen Datensatz zu löschen. Gibt es auch ist nicht garantiert, dass ein bestimmter Datensatz die gleiche hat **AbsolutePosition** Wenn die **Recordset** Objekts erneut abgefragt oder geöffnet wird. Lesezeichen sind das empfohlene Verfahren zurückzukehren, klicken Sie auf einer bestimmten Position und sind die einzige Möglichkeit der Positionierung für alle Arten von **Recordset** Objekte.
