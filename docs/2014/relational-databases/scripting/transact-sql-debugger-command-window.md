---
title: Befehlsfenster
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26306f8ad2adf01ebdcbf1b52169f1c2ec964920
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75243083"
---
# <a name="command-window"></a>Befehlsfenster
  Verwenden Sie das **CommandWindow** zum Ausführen von Befehlen, z. b. Debug-und Bearbeitungsbefehle, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] für den Code im gerade gedebuggten Abfrage-Editor-Fenster. Um das **Befehlsfenster**zu verwenden, müssen Sie sich im Debugmodus befinden. Der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger unterstützt zahlreiche Befehle, die auch im [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Command** window. Weitere Informationen finden Sie unter [Visual Studio-Befehlsfenster](https://go.microsoft.com/fwlink/?LinkId=112007).  
  
## <a name="task-list"></a>Aufgabenliste  
 **So greifen Sie auf das Befehlsfenster zu**  
  
-   Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
 **So drucken Sie den Wert einer Variablen**  
  
-   Geben Sie im **CommandWindow** **Debug. Print \<VariableName>** ein, und drücken Sie dann die EINGABETASTE.  
  
 **So Listen Sie Informationen zum aktuellen Thread auf**  
  
-   Geben `Debug.ListThread`Sie in das **Befehlsfenster**ein, und drücken Sie dann die EINGABETASTE.  
  
 **So fügen Sie dem Fenster schnell Überwachung eine Variable hinzu**  
  
-   Geben Sie im **CommandWindow** **Debug. quickwatch \<VariableName>** ein, und drücken Sie dann die EINGABETASTE.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transact-SQL-Debugger](transact-sql-debugger.md)  
