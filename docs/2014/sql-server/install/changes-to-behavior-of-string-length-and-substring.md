---
title: Änderungen am Verhalten von String-length und Teil Zeichenfolge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2119b7ba-2e52-44bf-ac57-82c2d46a48ff
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1188823a877b4c5dc9cef13431492dfe3b303e23
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85045003"
---
# <a name="changes-to-behavior-of-string-length-and-substring"></a>Änderungen am Verhalten von string-length und substring
  Die [String-length-Funktion &#40;XQuery-&#41;](/sql/xquery/functions-on-string-values-string-length) und die [Teil Zeichenfolge-Funktion &#40;XQuery-&#41;](/sql/xquery/functions-on-string-values-substring) Funktionen können unterschiedliche Ergebnisse zurückgeben, wenn Sie mit XML-Datenbanken mit Ersatz Zeichen verwendet werden.  
  
## <a name="description"></a>BESCHREIBUNG  
 Wenn eine Datenbank für die Kompatibilität mit festgelegt ist [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , ändert sich das Verhalten der [String-length-Funktion &#40;XQuery-&#41;](/sql/xquery/functions-on-string-values-string-length) und die [Teil Zeichenfolge-Funktion &#40;XQuery-&#41;](/sql/xquery/functions-on-string-values-substring) Functions beim Umgang mit ergänzenden Unicode-Zeichen. Jedes ergänzende Unicode-Zeichen, das definitionsgemäß um einen Codepunkt größer als U+FFFF ist, wird von diesen Funktionen als ein Zeichen statt als zwei Zeichen (wie in früheren Versionen) gezählt.  
  
 Weitere Informationen zu Ersatz Zeichen finden Sie unter [Surrogates und ergänzende Zeichen](https://go.microsoft.com/fwlink/?LinkId=178317).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](https://docs.microsoft.com/sql/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
