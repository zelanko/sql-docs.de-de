---
title: Transact-SQL-Breakpoints
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoints
ms.assetid: c234430f-bd94-4d0d-9e74-2bf11681fa50
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 024f079d28c5ce144282bf09fff675fd308a8173
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75243144"
---
# <a name="transact-sql-breakpoints"></a>Transact-SQL-Breakpoints
  Haltepunkte legen fest, dass der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger die Ausführung bei einer bestimmten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung unterbricht. Sie können dann den Status der Codeelemente an diesem Punkt anzeigen.  
  
## <a name="breakpoints"></a>Breakpoints  
 Wenn Sie den [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger ausführen, können Sie einen Haltepunkt auf bestimmten Anweisungen umschalten. Wenn die Ausführung eine Anweisung mit einem Haltepunkt erreicht, hält der Debugger die Ausführung an, damit Sie Debuginformationen anzeigen können, z. B. die in Variablen und Parametern vorhandenen Werte.  
  
 Sie können Haltepunkte im Editorfenster einzeln verwalten, oder alle zusammen im Fenster **Haltepunkte** . Sie können Haltepunkte bearbeiten, um bestimmte Elemente festzulegen, wie z. B. die speziellen Bedingungen, unter denen der Haltepunkt die Ausführung anhalten soll, oder die Aktionen, die beim Ausführen des Haltepunkts durchgeführt werden sollen.  
  
## <a name="breakpoint-tasks"></a>Haltepunkttasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt, wie die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung angegeben wird, bei der der Debugger angehalten werden soll.|[Umschalten eines Breakpoints](../spatial/point.md)|  
|Beschreibt, wie ein Haltepunkt vorübergehend deaktiviert und später erneut aktiviert wird. Beschreibt darüber hinaus, wie ein Haltepunkt gelöscht wird.|[Aktivieren, deaktivieren und Löschen von Breakpoints](enable-disable-and-delete-breakpoints.md)|  
|Beschreibt, wie eine Bedingung angegeben wird, die definiert, ob Haltepunkte auf Grundlage der Auswertung eines angegebenen Transact-SQL-Ausdrucks unterbrochen werden.|[Festlegen einer Haltepunkt Bedingung](specify-a-breakpoint-condition.md)|  
|Beschreibt, wie eine Trefferanzahl festgelegt wird, die dazu führt, dass ein Haltepunkt nur dann unterbrochen wird, wenn die Anweisung, die den Haltepunkt enthält, mit einer festgelegten Häufigkeit ausgeführt wurde.|[Angeben einer Treffer Anzahl](specify-a-hit-count.md)|  
|Beschreibt, wie ein Filter festgelegt wird, der bewirkt, dass ein Haltepunkt nur für angegebene Prozesse oder Threads unterbrochen wird.|[Haltepunkt Filter angeben](specify-a-breakpoint-filter.md)|  
|Beschreibt, wie eine **Bei Treffer** -Aktion festgelegt wird, bei der es sich um einen Vorgang handelt, der beim Ausführen der Haltepunktanweisung durchgeführt wird. Ein Beispiel hierfür ist das Drucken einer Meldung.|[Haltepunkt Aktion angeben](specify-a-breakpoint-action.md)|  
|Beschreibt, wie die Position eines Haltepunkts bearbeitet wird.|[Bearbeiten einer breakpointposition](edit-a-breakpoint-location.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Transact-SQL-Debugger](transact-sql-debugger-information.md)  
  
  
