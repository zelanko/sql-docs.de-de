---
title: Anzahl der Datensätze | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- record count [ODBC]
- descriptors [ODBC], record count
ms.assetid: 46eec3cc-0ecc-4980-9020-fb74a9af5730
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 28e503ae4602d87fc9138ed018ee1e95f135ec57
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81281816"
---
# <a name="record-count"></a>Anzahl der Datensätze
Das SQL_DESC_COUNT Header-Feld eines Deskriptors ist der 1-basierte Index des höchsten Datensatzes, der Daten enthält. Dieses Feld zählt nicht zu allen Spalten oder Parametern, die gebunden sind. Wenn ein Deskriptor zugeordnet wird, ist der Anfangswert von SQL_DESC_COUNT 0.  
  
 Der Treiber übernimmt alle erforderlichen Maßnahmen zum Zuordnen und Verwalten des Speichers, der zum Speichern der Deskriptorinformationen erforderlich ist. Die Anwendung gibt nicht explizit die Größe eines Deskriptors an und weist keine neuen Datensätze zu. Wenn die Anwendung Informationen für einen Deskriptordatensatz bereitstellt, dessen Anzahl höher als der Wert von SQL_DESC_COUNT ist, erhöht der Treiber automatisch SQL_DESC_COUNT. Wenn die Anwendung die Bindung des mit dem höchsten Wert nummerierten deskriptordaten Satzes aufhebt, verringert der Treiber automatisch SQL_DESC_COUNT, sodass er die Nummer des höchsten verbleibenden Datensatzes enthält.
