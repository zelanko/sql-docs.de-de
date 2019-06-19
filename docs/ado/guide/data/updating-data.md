---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8ea95b7d34f1395f6322d9a6ad6a0229bb8c7e45
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704565"
---
# <a name="updating-data"></a>Aktualisieren von Daten
Update-Verhaltens und der Funktionen ist größtenteils abhängig aktualisieren-Modus (Type-Sperre), Cursortyp und Cursorposition.  
  
 Verwenden der **Update** Methode zum Speichern von Änderungen Sie, um den aktuellen Datensatz des vorgenommen haben eine **Recordset** Objekt seit dem Aufrufen der **AddNew** Methode oder seit Feldwerte ändern in einem vorhandenen Datensatz. Die **Recordset** Objekt muss Updates unterstützen.  
  
 Wenn die **Recordset** Objekt unterstützt die Batch zu aktualisieren, können Sie mehrere Änderungen an einen oder mehrere Datensätze zwischenspeichern, lokal, bis Sie aufrufen, die **UpdateBatch** Methode. Wenn Sie den aktuellen Datensatz bearbeiten oder Hinzufügen eines neuen Datensatzes, beim Aufrufen der **UpdateBatch** -Methode, ADO ruft automatisch die **Update** Methode, um alle ausstehenden Änderungen am aktuellen Datensatz vor dem Speichern übertragen die im Batchmodus Änderungen an den Anbieter.  
  
 Der aktuelle Datensatz bleibt die aktuelle aufzurufen, nachdem Sie die **Update** oder **UpdateBatch** Methoden.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Immediate Mode (Immediate-Modus)](../../../ado/guide/data/immediate-mode.md)  
  
-   [Batchmodus](../../../ado/guide/data/batch-mode.md)  
  
-   [Transaktionsverarbeitung](../../../ado/guide/data/transaction-processing.md)
