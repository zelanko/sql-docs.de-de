---
description: Anzahl der Datensätze
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
ms.openlocfilehash: 3d329ca3638f964244cea8c28f7e07e171887fb9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465670"
---
# <a name="record-count"></a>Anzahl der Datensätze
Das SQL_DESC_COUNT Header-Feld eines Deskriptors ist der 1-basierte Index des höchsten Datensatzes, der Daten enthält. Dieses Feld zählt nicht zu allen Spalten oder Parametern, die gebunden sind. Wenn ein Deskriptor zugeordnet wird, ist der Anfangswert von SQL_DESC_COUNT 0.  
  
 Der Treiber übernimmt alle erforderlichen Maßnahmen zum Zuordnen und Verwalten des Speichers, der zum Speichern der Deskriptorinformationen erforderlich ist. Die Anwendung gibt nicht explizit die Größe eines Deskriptors an und weist keine neuen Datensätze zu. Wenn die Anwendung Informationen für einen Deskriptordatensatz bereitstellt, dessen Anzahl höher als der Wert von SQL_DESC_COUNT ist, erhöht der Treiber automatisch SQL_DESC_COUNT. Wenn die Anwendung die Bindung des mit dem höchsten Wert nummerierten deskriptordaten Satzes aufhebt, verringert der Treiber automatisch SQL_DESC_COUNT, sodass er die Nummer des höchsten verbleibenden Datensatzes enthält.
