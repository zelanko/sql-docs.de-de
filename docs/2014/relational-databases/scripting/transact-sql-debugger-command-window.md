---
title: Befehlsfenster | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b69735b5c2a2750ab34bc34d5a7f3c3e46bba16
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253792"
---
# <a name="command-window"></a>Befehlsfenster
  Im **Befehlsfenster** können Sie für den Code im gerade gedebuggten [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Abfrage-Editor-Fenster Befehle ausführen, wie z.B. Debug- und Bearbeitungsbefehle. Um das **Befehlsfenster**zu verwenden, müssen Sie sich im Debugmodus befinden. Der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger unterstützt zahlreiche Befehle, die auch im [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Command** window. Weitere Informationen finden Sie unter [Visual Studio-Befehlsfenster](http://go.microsoft.com/fwlink/?LinkId=112007).  
  
## <a name="task-list"></a>Aufgabenliste  
 **So greifen Sie auf das Befehlsfenster zu**  
  
-   Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
 **So geben Sie den Wert einer Variablen aus**  
  
-   Geben Sie im **Befehlsfenster** **Debug.Print \<Variablenname>** ein, und drücken Sie dann die EINGABETASTE.  
  
 **So listen Sie Informationen zum aktuellen Thread auf**  
  
-   In der **CommandWindow**, Typ `Debug.ListThread`, und drücken Sie dann die EINGABETASTE.  
  
 **So fügen Sie dem Fenster Schnellüberwachung eine Variable hinzu**  
  
-   Geben Sie im **Befehlsfenster** **Debug.QuickWatch \<Variablenname>** ein, und drücken Sie dann die EINGABETASTE.  
  
## <a name="see-also"></a>Siehe auch  
 [Transact-SQL-Debugger](transact-sql-debugger.md)  
  
  
