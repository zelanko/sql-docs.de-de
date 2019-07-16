---
title: Standard-C-Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], about pseudo-type identifiers
- pseudo-type identifiers [ODBC]
ms.assetid: 229140ae-af8f-4ec8-9ccf-1e92360e0bac
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b9e0a9b8e85967ce46344e824c03e74fe3552e7c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68130011"
---
# <a name="default-c-data-types"></a>Standardmäßige C-Datentypen
Wenn eine Anwendung SQL_C_DEFAULT in angibt **SQLBindCol**, **SQLGetData**, oder **SQLBindParameter**, der Treiber wird davon ausgegangen, dass der C-der Eingabe- oder Ausgabe Datentyp entspricht dem SQL-Datentyp der Spalte oder des Parameters an die der Puffer gebunden ist.  
  
> [!IMPORTANT]  
>  Interoperable Anwendungen ausführen können sollten nicht SQL_C_DEFAULT verwenden. Stattdessen sollten sie immer die C-Typ des Puffers angeben, die sie verwenden. Dies ist da Treiber den Standard-C-Typ aus den folgenden Gründen nicht immer richtig ermitteln können:  
  
-   Wenn das DBMS einen SQL-Datentyp einer Spalte oder Parameter fördert, kann nicht vom Treiber nicht den ursprünglichen SQL-Datentyp einer Spalte oder Parameter ermittelt. Es kann nicht aus diesem Grund den entsprechenden Standard-C-Datentyp bestimmen.  
  
-   Wenn der Treiber, ob eine bestimmte Spalte oder Parameter signiert ist, nicht ermitteln kann, wie häufig der Fall ist, wenn der Wert ist sollten vom DBMS, verarbeitet der Treiber kann nicht bestimmt werden, ob der Typ der entsprechenden Standard-C-Daten mit oder ohne Vorzeichen sein.  
  
     Da nur als eine Vereinfachung der Programmierung SQL_C_DEFAULT angegeben ist, wird die Anwendung keine Funktionalität verloren, wenn die tatsächliche C-Datentyp angegeben.  
  
 Eine Tabelle mit den Standard-C-Datentyp für jeden SQL-Datentyp befindet sich im [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)weiter unten in diesem Anhang.
