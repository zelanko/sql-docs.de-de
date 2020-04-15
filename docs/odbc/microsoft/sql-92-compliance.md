---
title: SQL-92-Konformität | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9ac0ae5873e545afb8fcac9dd003c984b1ed303a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300700"
---
# <a name="sql-92-compliance"></a>SQL-92-Konformität
Die ODBC-Desktopdatenbanktreiber und das zugrunde liegende Microsoft Jet-Modul sind nicht SQL-92-kompatibel. Sie unterstützen viele Funktionen, die in SQL-92 definiert wurden. Einige im Treiber unterstützte Funktionen werden in SQL-92 nicht unterstützt. Weitere Informationen finden Sie im *Microsoft Jet Database Engine Programmer es Guide*. Im Folgenden sind die hauptwichtigsten Unterschiede zwischen den beiden:  
  
-   Die von den Desktopdatenbanktreibern verwendete SQL unterstützt leistungsfähigere Ausdrücke als die von SQL-92 angegebenen.  
  
-   Für das Prädikat ZWISCHEN gelten andere Regeln.  
  
-   Die von den Desktopdatenbanktreibern und ANSI SQL verwendete SQL unterstützt verschiedene Schlüsselwörter.  
  
 Die folgenden SQL-92-Funktionen werden von Microsoft Jet SQL nicht unterstützt:  
  
-   Sicherheitsanweisungen, z. B. GRANT und LOCK.  
  
-   DISTINCT mit aggregierten Funktionsreferenzen.  
  
 Die folgenden Features sind Verbesserungen in SQL, die von den Desktopdatenbanktreibern verwendet werden und nicht von SQL-92 angegeben werden:  
  
-   Die TRANSFORM-Anweisung, die Unterstützung für Kreuztabellenabfragen bereitstellt.  
  
-   Zusätzliche Aggregatfunktionen (**StDev** und **VarP**).  
  
> [!NOTE]  
>  Die Desktopdatenbanktreiber unterstützen die standardmäßige ANSI-Syntax für % (Prozent) und _ (Unterstrich), nicht * (Sternchen) und ? (Fragezeichen).
