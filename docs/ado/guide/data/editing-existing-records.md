---
description: Bearbeiten vorhandener Datensätze
title: Bearbeiten vorhandener Datensätze | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 3c720d43135cb54cd610ea6e9a7e32ac249c1081
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453452"
---
# <a name="editing-existing-records"></a>Bearbeiten vorhandener Datensätze
Um vorhandene Datensätze zu bearbeiten, wechseln Sie in die Zeile, die Sie bearbeiten möchten, und ändern Sie die **value** -Eigenschaft der Felder, die Sie ändern möchten. Weitere Informationen zur **value** -Eigenschaft des **Field** -Objekts finden Sie unter unter [Suchen von Daten](../../../ado/guide/data/examining-data.md). Abhängig vom Cursortyp verwenden Sie **Update** oder **UpdateBatch** , um Änderungen an die Datenquelle zurückzusenden. Weitere Informationen finden Sie unter [aktualisieren und](../../../ado/guide/data/updating-and-persisting-data.md)beibehalten von Daten.  
  
 Es ist in der Regel effizienter, eine gespeicherte Prozedur mit einem Befehls Objekt zu verwenden, um Updates auszuführen und andere Vorgänge auszuführen, da eine gespeicherte Prozedur die Erstellung eines Cursors nicht erfordert. Weitere Informationen zu Cursorn finden Sie Untergrund Legendes zu [Cursorn und Sperren](../../../ado/guide/data/understanding-cursors-and-locks.md).
