---
title: Erstellen von Abfragen mit unbenannten Parametern (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- unnamed parameters
- parameters [SQL Server], unnamed
ms.assetid: 5f4b664b-3d3d-4d07-a0e7-791d78743504
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5200924d784d8d28f99c83bca7ee1dca4a5787c4
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43817686"
---
# <a name="create-queries-with-unnamed-parameters-visual-database-tools"></a>Erstellen von Abfragen mit unbenannten Parametern (Visual Database Tools)
  Sie können eine Abfrage mit einem unbenannten Parameter erstellen, indem Sie ein Fragezeichen (?) als Platzhalter für den Literalwert angeben. Der Abfrage- und Sicht-Designer weist dann einen temporären Namen zu. In der Abfrage können beliebig viele unbenannte Parameter festgelegt werden.  
  
 Wenn Sie die Abfrage im Abfrage- und Sicht-Designer ausführen, wird das Dialogfeld Abfrageparameter mit dem temporären Namen angezeigt.  
  
### <a name="to-specify-an-unnamed-parameter"></a>So geben Sie einen unbenannten Parameter an  
  
1.  Fügen Sie dem [Kriterienbereich](visual-database-tools.md)die Spalten oder Ausdrücke hinzu, nach denen gesucht werden soll. Wenn in den Abfrageergebnissen keine Suchspalten bzw. Suchausdrücke angezeigt werden sollen, entfernen Sie die entsprechenden Ausgabespalten.  
  
2.  Wechseln Sie zu der Zeile, die die Datenspalte oder den Ausdruck für die Suche enthält, und geben Sie in der Datenblattspalte **Filter** ein Fragezeichen (?) ein.  
  
     Der Abfrage- und Sicht-Designer fügt standardmäßig den Operator "=" hinzu. Sie können die Zelle jedoch so bearbeiten, dass dafür ">", "<" oder ein beliebiger anderer SQL-Vergleichsoperator eingesetzt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen mit Parametern &#40;Visual Database Tools&#41;](query-with-parameters-visual-database-tools.md)  
  
  
