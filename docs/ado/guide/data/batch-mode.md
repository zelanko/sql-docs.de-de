---
title: Batchmodus | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: c25cd688b5d74e4514e1af645f7917059ce4d445
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472834"
---
# <a name="batch-mode"></a>Batchmodus
Batchmodus ist gültig, wenn der **LockType** -Eigenschaftensatz auf **AdLockBatchOptimistic** und BatchUpdates wird vom Anbieter unterstützt. Bestimmte Einstellungen für Sperren sind nicht verfügbar, abhängig von der Cursorposition. Z. B. ein pessimistische Sperren ist nicht verfügbar, wenn die **CursorLocation** nastaven NA hodnotu **AdUseClient**. Umgekehrt kann kein Anbieter optimistische unterstützt, wenn die Cursorposition auf dem Server befindet. Verwenden Sie Batch mit einem Keyset oder static-Cursor wird aktualisiert.  
  
 Die **UpdateBatch** Methode dient zum Senden von **Recordset** Änderungen, die im Kopierpuffer an den Server zum Aktualisieren der Datenquelle gespeichert. Im folgenden Abschnitt, öffnen wir eine **Recordset** im Modus "Batch", nehmen Sie Änderungen an den Kopierpuffer aus, und senden unsere Änderungen an die Datenquelle, die über einen Aufruf an **UpdateBatch**.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Senden der Updates: UpdateBatch-Methode](../../../ado/guide/data/sending-the-updates-updatebatch-method.md)  
  
-   [Filtern nach aktualisierten Datensätzen](../../../ado/guide/data/filtering-for-updated-records.md)  
  
-   [Umgang mit fehlerhaften Updates](../../../ado/guide/data/dealing-with-failed-updates.md)  
  
-   [Erkennen und Lösen von Konflikten](../../../ado/guide/data/detecting-and-resolving-conflicts.md)  
  
-   [Trennen und erneutes Herstellen einer Verbindung des Recordsets](../../../ado/guide/data/disconnecting-and-reconnecting-the-recordset.md)  
  
-   [Aktualisieren von verknüpften Ergebnissen: Eindeutige Tabelle](../../../ado/guide/data/updating-joined-results-unique-table.md)
