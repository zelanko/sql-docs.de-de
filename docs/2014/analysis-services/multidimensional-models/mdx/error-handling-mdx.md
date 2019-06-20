---
title: Fehlerbehandlung (MDX) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 611e7636f9a5cd6393da4a8412b6c02bcc9ddaf8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66074680"
---
# <a name="error-handling-mdx"></a>Fehlerbehandlung (MDX)
  Jeder Cube kann steuern, wie Fehler in einem MDX-Skript (Multidimensional Expressions) behandelt werden. Die Fehlerbehandlung erfolgt über den `ScriptErrorHandlingMode`-Enumerator. Für diesen Enumerator sind folgende Werte möglich:  
  
 `IgnoreNone`  
 Veranlasst den Server, einen Fehler auszulösen, wenn [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] einen Fehler im MDX-Skript gefunden hat.  
  
 `IgnoreAll`  
 Veranlasst den Server dazu, alle Befehle im MDX-Skript zu ignorieren, die einen Fehler (Syntaxfehler, Fehler bei der Namensauflösung usw.) enthalten.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
