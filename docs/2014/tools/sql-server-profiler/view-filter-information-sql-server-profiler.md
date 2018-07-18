---
title: Anzeigen von Filterinformationen (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7936ad4df64746697b5c9d0ff8f2be1c7a5cbef1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057996"
---
# <a name="view-filter-information-sql-server-profiler"></a>Anzeigen von Filterinformationen (SQL Server Profiler)
  In diesem Thema wird beschrieben, wie Filter von Datenspalten für Ereignisklassen mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]angezeigt werden können.  
  
### <a name="to-view-filter-information"></a>So zeigen Sie Filterinformationen an  
  
1.  Öffnen Sie eine Ablaufverfolgungsdatei, eine Ablaufverfolgungstabelle oder ein SQL-Skript, und klicken Sie im Menü **Datei** auf **Eigenschaften**. Wenn Sie eine Ablaufverfolgungsvorlage bearbeiten oder eine neue Ablaufverfolgung erstellen, können Sie diesen Schritt auslassen.  
  
2.  Klicken Sie auf der Registerkarte **Ereignisauswahl** mit der rechten Maustaste auf den Namen der Datenspalte für den anzuzeigenden Filter, und klicken Sie dann auf **Spaltenfilter bearbeiten**.  
  
3.  Erweitern Sie im Dialogfeld **Filter bearbeiten** die Vergleichsoperatoren für den Filter, um den zugewiesenen Wert für das angegebene Kriterium anzuzeigen. Wiederholen Sie Schritt 2 und 3 für alle Spalten, für die Sie Filterinformationen anzeigen möchten.  
  
> [!NOTE]  
>  Vergleichsoperatoren mit zugewiesenen Werten sind fett formatiert.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  