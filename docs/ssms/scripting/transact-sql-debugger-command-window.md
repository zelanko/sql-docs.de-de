---
title: Befehlsfenster | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f884fedf974e863636de39c126c583498564d79e
ms.sourcegitcommit: 40c3b86793d91531a919f598dd312f7e572171ec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53328500"
---
# <a name="transact-sql-debugger---command-window"></a>Transact-SQL-Debugger – Befehlsfenster
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Im **Befehlsfenster** können Sie für den Code im gerade gedebuggten [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Abfrage-Editor-Fenster Befehle ausführen, wie z.B. Debug- und Bearbeitungsbefehle. Um das **Befehlsfenster**zu verwenden, müssen Sie sich im Debugmodus befinden. Der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger unterstützt zahlreiche Befehle, die auch im [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Command** window. Weitere Informationen finden Sie unter [Visual Studio-Befehlsfenster](https://go.microsoft.com/fwlink/?LinkId=112007).  
  
## <a name="task-list"></a>Aufgabenliste  
 **So greifen Sie auf das Befehlsfenster zu**  
  
-   Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
 **So geben Sie den Wert einer Variablen aus**  
  
-   Geben Sie im **Befehlsfenster** **Debug.Print \<Variablenname>** ein, und drücken Sie dann die EINGABETASTE.  
  
 **So listen Sie Informationen zum aktuellen Thread auf**  
  
-   Geben Sie im **Befehlsfenster**die Zeichenfolge **Debug.ListThread**ein, und drücken Sie dann die EINGABETASTE.  
  
 **So fügen Sie dem Fenster Schnellüberwachung eine Variable hinzu**  
  
-   Geben Sie im **Befehlsfenster** **Debug.QuickWatch \<Variablenname>** ein, und drücken Sie dann die EINGABETASTE.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transact-SQL-Debugger](../../relational-databases/scripting/transact-sql-debugger.md)  
