---
title: Parameter Markierungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- parameter markers [ODBC]
ms.assetid: 07213d04-cd31-45fd-a8c8-2e16e09eeaf4
author: David-Engel
ms.author: v-daenge
ms.reviewer: ''
ms.openlocfilehash: 132473de586094f79dd34c999d44f6dd59aefaef
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303571"
---
# <a name="parameter-markers"></a>Parametermarker
In Übereinstimmung mit der SQL-92-Spezifikation kann eine Anwendung keine Parametermarker an den folgenden Speicherorten platzieren. Eine umfassendere Liste finden Sie in der SQL-92-Spezifikation.  
  
-   In einer **Auswahl** Liste  
  
-   Als beide *Ausdrücke* in einem *Vergleichs-Prädikat*  
  
-   Als beide Operanden eines binären Operators  
  
-   Sowohl der erste als auch der zweite Operanden eines **between** -Vorgangs.  
  
-   Sowohl der erste als auch der dritte Operanden eines **between** -Vorgangs.  
  
-   Sowohl der Ausdruck als auch der erste Wert eines **in** -Vorgangs.  
  
-   Als Operand eines unären +-oder-Vorgangs  
  
-   Als Argument eines *Satzes-Funktions Verweises*  
  
 Weitere Informationen zu Parameter Markierungen finden Sie in der SQL-92-Spezifikation. Weitere Informationen zu Parametern finden Sie unter [Anweisungs Parameter](../../../odbc/reference/develop-app/statement-parameters.md).
