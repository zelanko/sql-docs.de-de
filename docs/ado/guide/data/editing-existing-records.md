---
title: Bearbeiten vorhandener Einträge | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- editing data [ADO], existing records
ms.assetid: 17ce1263-5897-452a-9ea5-c7f96b33df65
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 64262ae52b802398fc2060092a03e7469146f063
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692888"
---
# <a name="editing-existing-records"></a>Bearbeiten vorhandener Datensätze
Um vorhandene Datensätze zu bearbeiten, verschieben, auf die Zeile, die Sie verwenden möchten, bearbeiten und ändern Sie die **Wert** -Eigenschaft der Felder, die Sie ändern möchten. Weitere Informationen zu den **Feld** des Objekts **Wert** -Eigenschaft finden Sie unter [Untersuchen von Daten](../../../ado/guide/data/examining-data.md). Verwenden Sie abhängig vom Cursortyp **Update** oder **UpdateBatch** , Änderungen an der Datenquelle zu senden. Weitere Informationen finden Sie unter [wird aktualisiert und Beibehalten von Daten](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 Es ist in der Regel effizienter, eine gespeicherte Prozedur mit einer Command-Objekt zu verwenden, um Updates auch ausgeführt werden, andere Vorgänge ausführen, da eine gespeicherte Prozedur nicht über die Erstellung eines Cursors erfordert. Weitere Informationen zu Cursorn finden Sie unter [Grundlegendes zu Cursors und Sperren](../../../ado/guide/data/understanding-cursors-and-locks.md).
