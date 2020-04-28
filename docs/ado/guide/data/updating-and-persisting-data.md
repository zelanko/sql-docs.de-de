---
title: Aktualisieren und persistente Speicherung von Daten | Microsoft-Dokumentation
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
ms.openlocfilehash: 26fabdc205018b8e94575cfb5bd5e945a8fb28ca
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67923723"
---
# <a name="updating-and-persisting-data"></a>Aktualisieren und Beibehalten von Daten
In den obigen Kapiteln wurde erläutert, wie ADO verwendet wird, um Daten in einer Datenquelle zu erhalten, wie die Daten verschoben werden und wie die Daten bearbeitet werden können. Wenn das Ziel Ihrer Anwendung darin besteht, Benutzern Änderungen an den Daten zu ermöglichen, müssen Sie natürlich wissen, wie Sie diese Änderungen speichern können. Sie können entweder die Änderungen an den **Recordsets** in einer Datei **Speichern** , indem Sie die Save-Methode verwenden, oder Sie können die Änderungen mithilfe der **Update** -oder **UpdateBatch** -Methoden an die Datenquelle für den Speicher zurücksenden.  
  
 In den vorstehenden Kapiteln haben Sie die Daten in mehreren Zeilen des **Recordsets**geändert. ADO unterstützt zwei grundlegende Konzepte im Zusammenhang mit dem Hinzufügen, löschen und Ändern von Daten Zeilen.  
  
 Der erste Gedanke ist, dass Änderungen nicht sofort am **Recordset**vorgenommen werden. Stattdessen werden Sie an einem internen *Kopier Puffer*erstellt. Wenn Sie sich entscheiden, dass Sie die Änderungen nicht wünschen, werden die Änderungen im Kopier Puffer verworfen. Wenn Sie die Änderungen beibehalten möchten, werden die Änderungen im Kopier Puffer auf das **Recordset**angewendet.  
  
 Das zweite Konzept ist, dass Änderungen an die Datenquelle weitergegeben werden, sobald Sie die Arbeit für eine Zeile vollständig (also den *unmittelbaren* Modus) deklarieren oder alle Änderungen an einem Satz von Zeilen gesammelt werden, bis Sie die Arbeit für den vollständigen Satz deklarieren (also den *Batch* Modus). Die **LockType** -Eigenschaft bestimmt, wann die Änderungen an der zugrunde liegenden Datenquelle vorgenommen werden. **adlockoptimistisch** oder **adlockpessimigibt** den unmittelbaren Modus an, während **adlockbatchoptimiden** Batch Modus angibt. Die **Cursor Location** -Eigenschaft kann sich darauf auswirken, welche **LockType** -Einstellungen verfügbar sind. Beispielsweise wird die Einstellung **adlockpessiminicht** unterstützt, wenn die Eigenschaft **Cursor Location** auf **adUseClient**festgelegt ist.  
  
 Im unmittelbaren Modus gibt jeder Aufruf der **Update** -Methode die Änderungen an die Datenquelle weiter. Im Batch Modus speichert jeder Aufruf von **Update** oder Bewegung der aktuellen Zeilen Position die Änderungen am Kopier Puffer, aber nur die **UpdateBatch** -Methode gibt die Änderungen an die Datenquelle weiter.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Aktualisieren von Daten](../../../ado/guide/data/updating-data.md)  
  
-   [Beibehalten von Daten](../../../ado/guide/data/persisting-data.md)
