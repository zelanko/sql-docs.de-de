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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1333cd6cd5946b7a3a70152e12f4d3decfa7fed0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138434"
---
# <a name="alter-table-statement-limitations"></a>Einschränkungen der ALTER TABLE-Anweisung
Wenn der dBASE-oder Paradox-Treiber verwendet wird, kann die Struktur der Tabelle nach dem Erstellen eines Indexes und einem hinzugefügten neuen Datensatz nicht von der ALTER TABLE-Anweisung geändert werden, es sei denn, der Index wird gelöscht und der Inhalt der Tabelle gelöscht.  
  
 ALTER TABLE-Anweisungen werden für Microsoft Excel-oder Text-Treiber nicht unterstützt.  
  
> [!NOTE]  
>  Wenn Sie den Paradox-Treiber verwenden, ohne den Borland-Datenbank-Engine zu implementieren, werden ALTER TABLE-Anweisungen nicht unterstützt. nur Lese-und Anfügen-Anweisungen sind zulässig.
