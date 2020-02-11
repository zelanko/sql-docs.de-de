---
title: Batch Modus | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], batch mode
- batch mode [ADO]
- updating data [ADO], batch mode
ms.assetid: 0cb548e0-fcb4-4c49-98c8-be287911f826
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 188a95f985ac1d578bca8c7e10ac4c4054c935c0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925956"
---
# <a name="batch-mode"></a>Batchmodus
Der Batch Modus ist wirksam, wenn die **LockType** -Eigenschaft auf **adlockbatchoptimifest** gelegt ist und die Batch Aktualisierung durch den Anbieter unterstützt wird. Bestimmte Sperrentyp Einstellungen sind in Abhängigkeit von der Cursorposition nicht verfügbar. Beispielsweise ist ein pessimistischer Sperrentyp nicht verfügbar, wenn der **Cursor Location** auf **adUseClient**festgelegt ist. Im Gegensatz dazu kann ein Anbieter eine vollständige Batch-Sperre nicht unterstützen, wenn sich die Cursorposition auf dem Server befindet. Sie sollten die Batch Aktualisierung entweder mit einem Keyset-oder STATIC-Cursor verwenden.  
  
 Die **UpdateBatch** -Methode wird verwendet, um **recordsetänderungen** im Kopier Puffer an den Server zu senden, um die Datenquelle zu aktualisieren. Im folgenden Abschnitt öffnen wir ein **Recordset** im Batch Modus, nehmen Änderungen am Kopier Puffer vor und senden dann die Änderungen an die Datenquelle mithilfe eines Aufrufens von **UpdateBatch**.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Senden der Updates: UpdateBatch-Methode](../../../ado/guide/data/sending-the-updates-updatebatch-method.md)  
  
-   [Filtern nach aktualisierten Datensätzen](../../../ado/guide/data/filtering-for-updated-records.md)  
  
-   [Umgang mit fehlerhaften Updates](../../../ado/guide/data/dealing-with-failed-updates.md)  
  
-   [Erkennen und Lösen von Konflikten](../../../ado/guide/data/detecting-and-resolving-conflicts.md)  
  
-   [Trennen und erneutes Herstellen einer Verbindung mit dem Recordset](../../../ado/guide/data/disconnecting-and-reconnecting-the-recordset.md)  
  
-   [Aktualisieren von verknüpften Ergebnissen: eindeutige Tabelle](../../../ado/guide/data/updating-joined-results-unique-table.md)
