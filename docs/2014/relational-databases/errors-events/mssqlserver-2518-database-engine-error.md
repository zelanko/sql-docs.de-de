---
title: MSSQLSERVER_2518 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f40eb8fe404479f5a2bcd68881aec4b2b2d84613
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058709"
---
# <a name="mssqlserver2518"></a>MSSQLSERVER_2518
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2518|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED|  
|Meldungstext|Objekt-ID O_ID (Objekt "O_NAME"): Berechnete Spalten und benutzerdefinierte Typen können für dieses Objekt nicht überprüft werden, da Common Language Runtime (CLR) deaktiviert ist.|  
  
## <a name="explanation"></a>Erklärung  
 Diese Informationsmeldung gibt an, dass der Abfrageprozessor DBCC kein internes Objekt bereitstellen konnte, um die Auswertung berechneter Spalten und CLR-benutzerdefinierter Typen (Common Language Runtime) zu ermöglichen. Dieses Problem ist aufgetreten, weil eine der Spalten CLR beinhaltet, aber CLR nicht aktiviert ist. Das interne Objekt deckt alle Spalten ab. Daher verhindert das Unvermögen, eine einzelne Spalte auszuwerten, das Erstellen des internen Objekts. Das bedeutet, dass berechnete Spalten nicht auf Richtigkeit überprüft werden oder verwendet werden, wenn DBCC die Konsistenz zwischen Indizes und Basistabellen überprüft.  
  
## <a name="user-action"></a>Benutzeraktion  
 Aktivieren Sie CLR, und führen Sie die DBCC-Anweisung erneut aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren der CLR-Integration](../clr-integration/clr-integration-enabling.md)  
  
  