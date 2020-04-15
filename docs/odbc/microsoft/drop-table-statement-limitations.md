---
title: Einschränkungen der DROP TABLE-Anweisung | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, DROP TABLE statement limitations
- DROP TABLE statement limitations [ODBC]
ms.assetid: 0a1c80f5-c9f2-4655-9bfd-0131b2f015a9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c296108b9ab26a6361d12ad71a1f21b21d5bea1e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303401"
---
# <a name="drop-table-statement-limitations"></a>Einschränkungen der DROP TABLE-Anweisung
Wenn der Treiber Microsoft Excel 5.0, 7.0 oder 97 verwendet wird, löscht die DROP TABLE-Anweisung das Arbeitsblatt, löscht jedoch nicht den Arbeitsblattnamen. Da der Arbeitsblattname weiterhin in der Arbeitsmappe vorhanden ist, kann kein anderes Arbeitsblatt mit demselben Namen erstellt werden.
