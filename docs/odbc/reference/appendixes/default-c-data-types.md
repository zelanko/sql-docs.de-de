---
title: C-Standard Datentypen | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fdb787580e1c79df805f468416ab8993a1d32a26
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307051"
---
# <a name="default-c-data-types"></a>Standardmäßige C-Datentypen
Wenn eine Anwendung SQL_C_DEFAULT in **SQLBindCol**, **SQLGetData**oder **SQLBindParameter**angibt, geht der Treiber davon aus, dass der C-Datentyp der Ausgabe oder des Eingabe Puffers dem SQL-Datentyp der Spalte oder des Parameters entspricht, an die der Puffer gebunden ist.  
  
> [!IMPORTANT]  
>  Interoperable Anwendungen sollten SQL_C_DEFAULT nicht verwenden. Stattdessen sollten Sie immer den C-Typ des Puffers angeben, den Sie verwenden. Dies liegt daran, dass Treiber den Standard-C-Typ aus den folgenden Gründen nicht immer ordnungsgemäß bestimmen können:  
  
-   Wenn das DBMS einen SQL-Datentyp einer Spalte oder eines Parameters herauf stuft, kann der Treiber den ursprünglichen SQL-Datentyp einer Spalte oder eines Parameters nicht ermitteln. Daher kann der entsprechende C-Standard Datentyp nicht bestimmt werden.  
  
-   Wenn der Treiber nicht bestimmen kann, ob eine bestimmte Spalte oder ein bestimmter Parameter signiert ist, wie es häufig der Fall ist, wenn er vom DBMS verarbeitet wird, kann der Treiber nicht ermitteln, ob der entsprechende C-Standard Datentyp signiert oder nicht signiert werden soll.  
  
     Da SQL_C_DEFAULT nur als Programmier Zweck bereitgestellt wird, verliert die Anwendung keine Funktionalität, wenn Sie den tatsächlichen C-Datentyp angibt.  
  
 Eine Tabelle, die den c-Standard Datentyp für jeden SQL-Datentyp enthält, ist in den Daten [Typen "Daten aus SQL in C" weiter](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)unten in diesem Anhang enthalten.
