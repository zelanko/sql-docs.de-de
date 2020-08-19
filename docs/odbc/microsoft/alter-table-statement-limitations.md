---
description: Einschränkungen der ALTER TABLE-Anweisung
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
ms.openlocfilehash: 53f86e8d2c21fb6ea2d016610848773564d4a384
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449592"
---
# <a name="alter-table-statement-limitations"></a>Einschränkungen der ALTER TABLE-Anweisung
Wenn der dBASE-oder Paradox-Treiber verwendet wird, kann die Struktur der Tabelle nach dem Erstellen eines Indexes und einem hinzugefügten neuen Datensatz nicht von der ALTER TABLE-Anweisung geändert werden, es sei denn, der Index wird gelöscht und der Inhalt der Tabelle gelöscht.  
  
 ALTER TABLE-Anweisungen werden für Microsoft Excel-oder Text-Treiber nicht unterstützt.  
  
> [!NOTE]  
>  Wenn Sie den Paradox-Treiber verwenden, ohne den Borland-Datenbank-Engine zu implementieren, werden ALTER TABLE-Anweisungen nicht unterstützt. nur Lese-und Anfügen-Anweisungen sind zulässig.
