---
title: Aktualisieren und Speichern von Daten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- updating data [ADO]
- data updates [ADO]
- ADO, updating data
ms.assetid: 8dc27274-4f96-43d1-913c-4ff7d01b9a27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d53891b4e82b3ae391d095e8cbca2189fb201d29
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63142959"
---
# <a name="updating-and-persisting-data"></a>Aktualisieren und Beibehalten von Daten
Die vorherigen Kapitel wurde erläutert, wie ADO verwendet, um Daten in einer Datenquelle abzurufen, wie in den Daten navigieren und wie Sie die Daten bearbeiten. Wenn das Ziel Ihrer Anwendung ist, dass Benutzer Änderungen an den Daten vornehmen können, müssen Sie natürlich zu verstehen, wie diese Änderungen zu speichern. Sie können entweder beibehalten, die **Recordset** ändert sich in einer Datei mit der **speichern** -Methode, oder Sie können die Änderungen zurück an die Datenquelle für die Verwendung von Storage senden die **Update** oder  **UpdateBatch** Methoden.  
  
 In den vorangegangenen Kapiteln, Sie geändert haben die Daten in mehrere Zeilen mit den **Recordset**. ADO unterstützt zwei grundlegende Konzepte im Zusammenhang mit der Hinzufügung, löschen und Ändern von Zeilen mit Daten.  
  
 Das erste Konzept ist, dass die Änderungen werden nicht sofort an die **Recordset**; stattdessen werden sie an einer internen vorgenommen *Kopierpuffer*. Wenn Sie sich, dass Sie nicht möchten, dass die Änderungen entscheiden, werden die Änderungen im Kopierpuffer verworfen. Wenn Sie die Änderungen beibehalten möchten, gelten die Änderungen in der Kopierpuffer für die **Recordset**.  
  
 Das zweite Konzept ist, dass die Änderungen entweder an die Datenquelle weitergegeben werden, sobald Sie die Arbeit in einer Zeile vollständige deklarieren (d. h. *sofortige* Modus), oder alle Änderungen an einer Reihe von Zeilen werden gesammelt, bis Sie die Arbeit für den Satz deklarieren abgeschlossen (d. h. *Batch* Modus). Die **LockType** Eigenschaft bestimmt, wenn die Änderungen an der zugrunde liegenden Datenquelle vorgenommen werden. **AdLockOptimistic** oder **AdLockPessimistic** unmittelbarer Modus gibt an, während **AdLockBatchOptimistic** Modus "Batch" angibt. Die **CursorLocation** Eigenschaft kann beeinflussen, was **LockType** Einstellungen sind verfügbar. Z. B. die **AdLockPessimistic** Einstellung wird nicht unterstützt, wenn die **CursorLocation** -Eigenschaftensatz auf **AdUseClient**.  
  
 Im unmittelbaren Modus, jeden Aufruf des der **Update** -Methode überträgt die Änderungen an der Datenquelle. Im Modus "Batch", jeden Aufruf des **Update** oder Bewegung des die aktuelle Zeilenposition speichert die Änderungen in den Kopierpuffer, jedoch nur die **UpdateBatch** -Methode überträgt die Änderungen an der Datenquelle.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Aktualisieren von Daten](../../../ado/guide/data/updating-data.md)  
  
-   [Beibehalten von Daten](../../../ado/guide/data/persisting-data.md)
