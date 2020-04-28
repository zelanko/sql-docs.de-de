---
title: Einschränkungen der ALTER TABLE-Anweisung | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304699"
---
# <a name="alter-table-statement-limitations"></a>Einschränkungen der ALTER TABLE-Anweisung
Wenn der dBASE-oder Paradox-Treiber verwendet wird, kann die Struktur der Tabelle nach dem Erstellen eines Indexes und einem hinzugefügten neuen Datensatz nicht von der ALTER TABLE-Anweisung geändert werden, es sei denn, der Index wird gelöscht und der Inhalt der Tabelle gelöscht.  
  
 ALTER TABLE-Anweisungen werden für Microsoft Excel-oder Text-Treiber nicht unterstützt.  
  
> [!NOTE]  
>  Wenn Sie den Paradox-Treiber verwenden, ohne den Borland-Datenbank-Engine zu implementieren, werden ALTER TABLE-Anweisungen nicht unterstützt. nur Lese-und Anfügen-Anweisungen sind zulässig.
