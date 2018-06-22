---
title: Änderungen am Verhalten von String-Length und Substring | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2119b7ba-2e52-44bf-ac57-82c2d46a48ff
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3bdc5e23a18b1b182703a1773dc8476eda8d4b14
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149335"
---
# <a name="changes-to-behavior-of-string-length-and-substring"></a>Änderungen am Verhalten von string-length und substring
  Die [String-Length-Funktion &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-string-length) und [substring-Funktion &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-substring) Funktionen möglicherweise andere Ergebnisse, wenn mit XML-Datenbanken verwendet werden, enthalten zurück Ersatzzeichen enthalten.  
  
## <a name="description"></a>Description  
 Wenn eine Datenbank festgelegt ist, für die Kompatibilität mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], das Verhalten der [String-Length-Funktion &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-string-length) und [substring-Funktion &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-substring) Funktionen Änderungen beim Umgang mit zusätzlichen Unicode-Zeichen. Jedes ergänzende Unicode-Zeichen, das definitionsgemäß um einen Codepunkt größer als U+FFFF ist, wird von diesen Funktionen als ein Zeichen statt als zwei Zeichen (wie in früheren Versionen) gezählt.  
  
 Weitere Informationen über Ersatzzeichen finden Sie unter [Surrogates and Supplementary Characters](http://go.microsoft.com/fwlink/?LinkId=178317).  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
