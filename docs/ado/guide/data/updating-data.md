---
description: Aktualisieren von Daten
title: Aktualisieren von Daten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], about data updates
- updating data [ADO], about updating data
ms.assetid: 6508e4e9-e33a-4dad-b340-5d632fd78a91
author: rothja
ms.author: jroth
ms.openlocfilehash: 5ea884479e7353b822e8b679a0fff34d70c3fd93
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452642"
---
# <a name="updating-data"></a>Aktualisieren von Daten
Das Aktualisierungs Verhalten und die Funktionalität sind größtenteils abhängig vom Aktualisierungs Modus (Sperrtyp), vom Cursortyp und von der Cursorposition.  
  
 Verwenden Sie die **Update** -Methode, um alle Änderungen zu speichern, die Sie an dem aktuellen Datensatz eines **Recordset** -Objekts vorgenommen haben, seit der **AddNew** -Methode aufgerufen wurde oder wenn Feldwerte in einem vorhandenen Datensatz geändert werden. Das **Recordset** -Objekt muss Updates unterstützen.  
  
 Wenn das **Recordset** -Objekt die Batch Aktualisierung unterstützt, können Sie mehrere Änderungen an einem oder mehreren Datensätzen lokal zwischenspeichern, bis Sie die **UpdateBatch** -Methode aufrufen. Wenn Sie den aktuellen Datensatz bearbeiten oder einen neuen Datensatz hinzufügen, wenn Sie die **UpdateBatch** -Methode aufrufen, ruft ADO automatisch die **Update** -Methode auf, um ausstehende Änderungen am aktuellen Datensatz zu speichern, bevor die Batch Änderungen an den Anbieter übertragen werden.  
  
 Der aktuelle Datensatz bleibt nach dem Aufrufen der **Update** -oder **UpdateBatch** -Methode aktuell.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Unmittelbarer Modus](../../../ado/guide/data/immediate-mode.md)  
  
-   [Batchmodus](../../../ado/guide/data/batch-mode.md)  
  
-   [Verarbeiten von Transaktionen](../../../ado/guide/data/transaction-processing.md)
