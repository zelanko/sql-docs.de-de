---
title: ALTER TABLE-Anweisungsbeschränkungen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, ALTER TABLE statement limitations
- ALTER TABLE statement limitations [ODBC]
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19afa8b07b0051de9ce45ec652ea337c0f689f52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304699"
---
# <a name="alter-table-statement-limitations"></a>Einschränkungen der ALTER TABLE-Anweisung
Wenn der treiber dBASE oder Paradox verwendet wird, kann die Struktur der Tabelle nach dem Erstellen eines Indexes und dem Neuen Datensatz nicht durch die ALTER TABLE-Anweisung geändert werden, es sei denn, der Index wird gelöscht und der Inhalt der Tabelle gelöscht.  
  
 ALTER TABLE-Anweisungen werden für die Microsoft Excel- oder Texttreiber nicht unterstützt.  
  
> [!NOTE]  
>  Wenn Sie den Paradox-Treiber verwenden, ohne die Borland Database Engine zu implementieren, werden ALTER TABLE-Anweisungen nicht unterstützt. nur Lese- und Anhängensanweisungen sind zulässig.
