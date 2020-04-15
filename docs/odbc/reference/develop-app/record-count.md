---
title: Rekordanzahl | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281816"
---
# <a name="record-count"></a>Anzahl der Datensätze
Das SQL_DESC_COUNT Headerfeld eines Deskriptors ist der einbasierte Index des Datensatzes mit der höchsten Nummer, der Daten enthält. Dieses Feld ist nicht eine Anzahl aller Spalten oder Parameter, die gebunden sind. Wenn ein Deskriptor zugewiesen wird, ist der Anfangswert von SQL_DESC_COUNT 0.  
  
 Der Treiber ergreift alle erforderlichen Maßnahmen, um den Speicher zuzuweisen und zu verwalten, den er für die Speicherung von Deskriptorinformationen benötigt. Die Anwendung gibt weder explizit die Größe eines Deskriptors noch neue Datensätze an. Wenn die Anwendung Informationen für einen Deskriptordatensatz bereitstellt, dessen Anzahl höher als der Wert von SQL_DESC_COUNT ist, erhöht der Treiber automatisch SQL_DESC_COUNT. Wenn die Anwendung die Bindung des am höchsten nummerierten Deskriptordatensatzes aufkleben wird, verringert der Treiber automatisch SQL_DESC_COUNT, um die Nummer des höchsten verbleibenden gebundenen Datensatzes zu enthalten.
