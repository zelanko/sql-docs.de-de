---
title: SQL-92-Konformität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], SQL-92 compliance
- desktop database drivers [ODBC], SQL-92 compliance
- SQL-92 compliance [ODBC]
- ODBC desktop database drivers [ODBC], SQL-92 compliance
ms.assetid: 50c8c7df-df01-4f4d-ad62-d059cf29d73a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e5d8ed2818b466d16591be8b70478221d7ac84df
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063368"
---
# <a name="sql-92-compliance"></a>SQL-92-Konformität
Der ODBC-Desktop-Datenbanktreiber und das zugrunde liegende Microsoft Jet-Modul sind nicht die SQL-92 kompatibel. Sie unterstützen viele Funktionen, die in SQL-92 definiert wurden. Einige Funktionen, die vom Treiber unterstützt werden in SQL-92 nicht unterstützt. Weitere Informationen finden Sie unter den *Microsoft Jet-Datenbank-Engine Handbuch für Programmierer*. Es folgen die wichtigsten Unterschiede zwischen den beiden:  
  
-   Die von der Desktop-Datenbanktreiber verwendet SQL unterstützt leistungsstarke Ausdrücke als durch die SQL-92 angegeben.  
  
-   Unterschiedliche Regeln gelten für das BETWEEN-Prädikat.  
  
-   Wird von den Desktop-Datenbanktreiber und ANSI SQL SQL unterstützt andere Schlüsselwörter.  
  
 Die folgenden SQL-92-Funktionen werden von der Microsoft Jet-SQL nicht unterstützt:  
  
-   Security-Anweisungen, z. B. GRANT und SPERREN.  
  
-   DISTINCT mit Aggregatfunktion verweisen.  
  
 Die folgenden Features sind die Verbesserungen in SQL verwendet, die für die Desktop-Datenbanktreiber, die nicht von SQL-92 angegeben werden:  
  
-   Die TRANSFORM-Anweisung bieten Unterstützung für Kreuztabellenabfragen.  
  
-   Weitere Aggregatfunktionen (**StDev** und **VarP**).  
  
> [!NOTE]  
>  Die Desktop-Datenbanktreiber unterstützt die standard-ANSI-Syntax nicht für % (Prozent) und _ (Unterstrich) * (Sternchen) und? (Fragezeichen).
