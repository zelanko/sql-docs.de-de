---
title: Anhalten einer Ablaufverfolgung (SQL Server Profiler) | Microsoft Docs
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
- pausing traces
- temporarily stopping traces
- traces [SQL Server], pausing
- stopping traces
ms.assetid: 432b9b0c-b5e7-47f3-a71b-310fb3bf2445
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e31b59bf2a71054f03982278b45e7b9e373f48e3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049813"
---
# <a name="pause-a-trace-sql-server-profiler"></a>Anhalten einer Ablaufverfolgung (SQL Server Profiler)
  Durch Anhalten einer Ablaufverfolgung wird verhindert, dass weitere Ereignisdaten vor dem Neustarten der Ablaufverfolgung aufgezeichnet werden.  
  
 Durch Anhalten einer Ablaufverfolgung wird verhindert, dass Ereignisdaten vor dem Neustarten der Ablaufverfolgung aufgezeichnet werden. Durch das Neustarten einer Ablaufverfolgung werden die Ablaufverfolgungsvorgänge fortgesetzt. Zuvor aufgezeichnete Daten gehen nach einem Neustart nicht verloren. Wird die Ablaufverfolgung neu gestartet, wird die Aufzeichnung der Daten von diesem Punkt an fortgesetzt. Während eine Ablaufverfolgung angehalten wird, können Sie den Namen, Ereignisse, Spalten und Filter ändern. Es ist allerdings nicht möglich, die Ziele, an die Sie die Ablaufverfolgungsdaten senden, oder die Serververbindung zu ändern.  
  
### <a name="to-pause-a-trace"></a>So halten Sie eine Ablaufverfolgung an  
  
1.  Wählen Sie ein Fenster aus, das eine derzeit ausgeführte Ablaufverfolgung enthält.  
  
2.  Klicken Sie im Menü **Datei** auf **Ablaufverfolgung anhalten**.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  