---
title: Änderungen am Verhalten von String-Length und Substring | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2119b7ba-2e52-44bf-ac57-82c2d46a48ff
caps.latest.revision: 9
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0261587f42bfa52f2a1db59ab76fefb0c8670be7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312880"
---
# <a name="changes-to-behavior-of-string-length-and-substring"></a>Änderungen am Verhalten von string-length und substring
  Die [String-Length-Funktion &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-string-length) und [substring-Funktion &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-substring) Funktionen möglicherweise andere Ergebnisse, wenn mit XML-Datenbanken verwendet werden, enthalten zurück Ersatzzeichen enthalten.  
  
## <a name="description"></a>Description  
 Wenn eine Datenbank festgelegt ist, als kompatibel mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], das Verhalten der [String-Length-Funktion &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-string-length) und [substring-Funktion &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-substring) Funktionen von Änderungen beim Umgang mit ergänzenden Unicode-Zeichen. Jedes ergänzende Unicode-Zeichen, das definitionsgemäß um einen Codepunkt größer als U+FFFF ist, wird von diesen Funktionen als ein Zeichen statt als zwei Zeichen (wie in früheren Versionen) gezählt.  
  
 Weitere Informationen über Ersatzzeichen finden Sie unter [Surrogates and Supplementary Characters](http://go.microsoft.com/fwlink/?LinkId=178317).  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
