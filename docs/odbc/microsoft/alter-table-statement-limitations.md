---
title: ALTER TABLE-Anweisung Einschränkungen | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 02ce530385cdc911250a81d831dd2fdb81873f76
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63301975"
---
# <a name="alter-table-statement-limitations"></a>Einschränkungen der ALTER TABLE-Anweisung
Wenn die dBASE- oder einer Paradox-Treiber verwendet wird, nachdem ein Index erstellt wurde und ein neuer Datensatz hinzugefügt, die die Struktur der Tabelle an, die von der ALTER TABLE-Anweisung geändert werden kann, es sei denn, der Index gelöscht wird, und der Inhalt der Tabelle gelöscht werden.  
  
 ALTER TABLE-Anweisungen werden nicht für die Treiber für Microsoft Excel- oder Textdateien unterstützt.  
  
> [!NOTE]  
>  Wenn Sie die Paradox-Treiber verwenden, ohne Sie zu der Datenbank-Engine für Borland implementieren, werden die ALTER TABLE-Anweisungen nicht unterstützt. Nur Lese- und anfügeereignisse-Anweisungen sind zulässig.
