---
title: DROP INDEX-Anweisung | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DROP INDEX [ODBC]
- SQL grammar [ODBC], DROP INDEX
ms.assetid: cd0ff767-9254-413b-bd1a-bed26c6774f5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 638bae6491c020519a0123ff56fe31e9a9ca1cf7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303431"
---
# <a name="drop-index-statement"></a>DROP INDEX-Anweisung
Wenn der Treiber Microsoft Access, dBASE oder Paradox verwendet wird, lautet die Syntax der DROP INDEX-Anweisung "DROP INDEX a on b", wobei "a" der Name des Index und "b" der Name der Tabelle (nicht DROP INDEX *Indexname*) ist.  
  
 Wenn der Paradox-Treiber verwendet wird, löscht die DROP INDEX-Anweisung die sekundären Paradox-Indexdateien.  
  
 Die DROP INDEX-Anweisung wird für die Microsoft Excel- oder Texttreiber nicht unterstützt.
