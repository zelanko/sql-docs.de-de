---
title: Einschränkungen der DELETE-Anweisung | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303531"
---
# <a name="delete-statement-limitations"></a>Einschränkungen der DELETE-Anweisung
Die DELETE-Anweisung wird für den Treiber Microsoft Excel oder Text nicht unterstützt. Beachten Sie, dass die INSERT-Anweisung für den Texttreiber unterstützt wird.  
  
 Der dBASE-Treiber unterstützt das Packen einer Tabelle zum Entfernen "gelöschter" Werte nicht.  
  
 Damit der Paradox-Treiber eine Zeile aus einer Tabelle löschen kann, muss die Tabelle über einen eindeutigen Index (Paradox-Primärschlüssel) verfügen.
