---
title: Einschränkungen der DELETE-Anweisung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE statement limitations [ODBC]
- ODBC SQL grammar, DELETE statement limitations
ms.assetid: 084761fe-e65b-4f38-ba4f-69884b2a7700
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 365b54ab8c0678253e184b397f1f71e39aed3b9b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303531"
---
# <a name="delete-statement-limitations"></a>Einschränkungen der DELETE-Anweisung
Die DELETE-Anweisung wird für den Microsoft Excel-oder Text-Treiber nicht unterstützt. Beachten Sie, dass die INSERT-Anweisung für den Text Treiber unterstützt wird.  
  
 Der dBase-Treiber unterstützt das Packen einer Tabelle zum Entfernen von "gelöschten" Werten nicht.  
  
 Damit der Paradox-Treiber eine Zeile aus einer Tabelle löschen kann, muss die Tabelle über einen eindeutigen Index verfügen (Paradox-Primärschlüssel).
