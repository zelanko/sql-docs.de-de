---
title: Standard-C-Datentypen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307051"
---
# <a name="default-c-data-types"></a>Standardmäßige C-Datentypen
Wenn eine Anwendung SQL_C_DEFAULT in **SQLBindCol**, **SQLGetData**oder **SQLBindParameter**angibt, geht der Treiber davon aus, dass der C-Datentyp des Ausgabe- oder Eingabepuffers dem SQL-Datentyp der Spalte oder des Parameters entspricht, an den der Puffer gebunden ist.  
  
> [!IMPORTANT]  
>  Interoperable Anwendungen sollten keine SQL_C_DEFAULT verwenden. Stattdessen sollten sie immer den C-Typ des Puffers angeben, den sie verwenden. Dies liegt daran, dass Treiber den Standard-C-Typ aus den folgenden Gründen nicht immer korrekt bestimmen können:  
  
-   Wenn das DBMS einen SQL-Datentyp einer Spalte oder eines Parameters heraufbeschworen hat, kann der Treiber den ursprünglichen SQL-Datentyp einer Spalte oder eines Parameters nicht bestimmen. Daher kann der entsprechende Standard-C-Datentyp nicht ermittelt werden.  
  
-   Wenn der Treiber nicht bestimmen kann, ob eine bestimmte Spalte oder ein bestimmter Parameter signiert ist, wie dies häufig der Fall ist, wenn dies vom DBMS behandelt wird, kann der Treiber nicht bestimmen, ob der entsprechende Standard-C-Datentyp signiert oder nicht signiert werden soll.  
  
     Da SQL_C_DEFAULT nur als Programmierkomfort bereitgestellt wird, verliert die Anwendung keine Funktionalität, wenn sie den tatsächlichen C-Datentyp angibt.  
  
 Eine Tabelle mit dem Standarddatentyp C für jeden SQL-Datentyp ist in [Converting Data from SQL to C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)(später in diesem Anhang) enthalten.
