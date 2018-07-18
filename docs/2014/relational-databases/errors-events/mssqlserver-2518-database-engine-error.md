---
title: MSSQLSERVER_2518 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a4fc661059240f626c9f61e3b81f4a80350680fa
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425060"
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
  
  
