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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1313ff25791c285e1bd1f8ccb69a75700ae62be1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063370"
---
# <a name="command-window"></a>Befehlsfenster
  Im **Befehlsfenster** können Sie für den Code im gerade gedebuggten [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Abfrage-Editor-Fenster Befehle ausführen, wie z.B. Debug- und Bearbeitungsbefehle. Um das **Befehlsfenster**zu verwenden, müssen Sie sich im Debugmodus befinden. Der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Debugger unterstützt zahlreiche Befehle, die auch im **Befehlsfenster** von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] unterstützt werden. Weitere Informationen finden Sie unter [Visual Studio-Befehlsfenster](https://go.microsoft.com/fwlink/?LinkId=112007).  
  
## <a name="task-list"></a>Aufgabenliste  
 **So greifen Sie auf das Befehlsfenster zu**  
  
-   Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
 **So geben Sie den Wert einer Variablen aus**  
  
-   Geben Sie im **CommandWindow** **Debug. Print \<VariableName> **ein, und drücken Sie dann die EINGABETASTE.  
  
 **So listen Sie Informationen zum aktuellen Thread auf**  
  
-   Geben Sie in das **Befehlsfenster**ein `Debug.ListThread` , und drücken Sie dann die EINGABETASTE.  
  
 **So fügen Sie dem Fenster Schnellüberwachung eine Variable hinzu**  
  
-   Geben Sie im **CommandWindow** **Debug. quickwatch \<VariableName> **ein, und drücken Sie dann die EINGABETASTE.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transact-SQL-Debugger](transact-sql-debugger.md)  
