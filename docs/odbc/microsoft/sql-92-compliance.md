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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9ac0ae5873e545afb8fcac9dd003c984b1ed303a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300700"
---
# <a name="sql-92-compliance"></a>SQL-92-Konformität
Die ODBC Desktop-Datenbanktreiber und die zugrunde liegende Microsoft Jet-Engine sind nicht SQL-92-kompatibel. Sie unterstützen viele Features, die in SQL-92 definiert wurden. Einige Features, die im Treiber unterstützt werden, werden in SQL-92 nicht unterstützt. Weitere Informationen finden Sie im *Microsoft Jet Datenbank-Engine Programmer es Guide*. Im folgenden sind die Hauptunterschiede zwischen den beiden aufgeführt:  
  
-   Die SQL-Daten, die von den Desktop-Daten Bank Treibern verwendet werden, unterstützen leistungsfähigere Ausdrücke als die von SQL-92.  
  
-   Für das between-Prädikat gelten verschiedene Regeln.  
  
-   Der von den Desktop-Daten Bank Treibern und ANSI SQL verwendete SQL unterstützt verschiedene Schlüsselwörter.  
  
 Die folgenden SQL-92-Features werden von Microsoft Jet SQL nicht unterstützt:  
  
-   Sicherheitsanweisungen, z. b. Grant und Lock.  
  
-   Unterschieden mit Aggregat Funktions verweisen.  
  
 Die folgenden Features sind Erweiterungen in SQL, die von den Desktop-Daten Bank Treibern verwendet werden, die nicht von SQL-92 angegeben werden:  
  
-   Die Transform-Anweisung, die Unterstützung für Kreuz Tabellen Abfragen bereitstellt.  
  
-   Zusätzliche Aggregatfunktionen (**StDev** und **VarP**).  
  
> [!NOTE]  
>  Die Desktop-Datenbanktreiber unterstützen die Standard-ANSI-Syntax für% (Prozent) und _ (Unterstrich), nicht * (Sternchen) und? (Fragezeichen).
