---
title: Parameter-Marker | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303571"
---
# <a name="parameter-markers"></a>Parametermarker
Gemäß der SQL-92-Spezifikation kann eine Anwendung keine Parametermarkierungen an den folgenden Speicherorten platzieren. Eine umfassendere Liste finden Sie in der SQL-92-Spezifikation.  
  
-   In einer **SELECT-Liste**  
  
-   Da beide *Ausdrücke* in einem *Vergleichsprädikat*  
  
-   Als beide Operanden eines binären Operators  
  
-   Als erster und zweiter Operand eines **BETWEEN-Betriebs**  
  
-   Als erster und dritter Operand eines **BETWEEN-Betriebs**  
  
-   Da sowohl der Ausdruck als auch der erste Wert eines **IN-Vorgangs**  
  
-   Als Operand einer unären + oder - Operation  
  
-   Als Argument eines *set-function-reference*  
  
 Weitere Informationen zu Parametermarkierungen finden Sie in der SQL-92-Spezifikation. Weitere Informationen zu Parametern finden Sie unter [Anweisungsparameter](../../../odbc/reference/develop-app/statement-parameters.md).
