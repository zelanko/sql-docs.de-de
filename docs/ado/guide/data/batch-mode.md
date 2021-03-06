---
description: Batchmodus
title: Batch Modus | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], batch mode
- batch mode [ADO]
- updating data [ADO], batch mode
ms.assetid: 0cb548e0-fcb4-4c49-98c8-be287911f826
author: rothja
ms.author: jroth
ms.openlocfilehash: a2cda3a14dc51532d52184f8b2101981d4f36cd3
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991601"
---
# <a name="batch-mode"></a>Batchmodus
Der Batch Modus ist wirksam, wenn die **LockType** -Eigenschaft auf **adlockbatchoptimifest** gelegt ist und die Batch Aktualisierung durch den Anbieter unterstützt wird. Bestimmte Sperrentyp Einstellungen sind in Abhängigkeit von der Cursorposition nicht verfügbar. Beispielsweise ist ein pessimistischer Sperrentyp nicht verfügbar, wenn der **Cursor Location** auf **adUseClient**festgelegt ist. Im Gegensatz dazu kann ein Anbieter eine vollständige Batch-Sperre nicht unterstützen, wenn sich die Cursorposition auf dem Server befindet. Sie sollten die Batch Aktualisierung entweder mit einem Keyset-oder STATIC-Cursor verwenden.  
  
 Die **UpdateBatch** -Methode wird verwendet, um **recordsetänderungen** im Kopier Puffer an den Server zu senden, um die Datenquelle zu aktualisieren. Im folgenden Abschnitt öffnen wir ein **Recordset** im Batch Modus, nehmen Änderungen am Kopier Puffer vor und senden dann die Änderungen an die Datenquelle mithilfe eines Aufrufens von **UpdateBatch**.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Senden der Updates: UpdateBatch-Methode](./sending-the-updates-updatebatch-method.md)  
  
-   [Filtern nach aktualisierten Datensätzen](./filtering-for-updated-records.md)  
  
-   [Umgang mit fehlerhaften Updates](./dealing-with-failed-updates.md)  
  
-   [Erkennen und Lösen von Konflikten](./detecting-and-resolving-conflicts.md)  
  
-   [Trennen und erneutes Herstellen einer Verbindung mit dem Recordset](./disconnecting-and-reconnecting-the-recordset.md)  
  
-   [Aktualisieren von verknüpften Ergebnissen: eindeutige Tabelle](./updating-joined-results-unique-table.md)