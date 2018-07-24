---
title: Befehlsfenster | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 11ad17e54f05b3cbb0aa9ba52ec1b57720405285
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38042028"
---
# <a name="transact-sql-debugger---command-window"></a>Transact-SQL-Debugger – Befehlsfenster
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Im **Befehlsfenster** können Sie für den Code im gerade gedebuggten [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Abfrage-Editor-Fenster Befehle ausführen, wie z.B. Debug- und Bearbeitungsbefehle. Um das **Befehlsfenster**zu verwenden, müssen Sie sich im Debugmodus befinden. Der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger unterstützt zahlreiche Befehle, die auch im [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Command** window. Weitere Informationen finden Sie unter [Visual Studio-Befehlsfenster](http://go.microsoft.com/fwlink/?LinkId=112007).  
  
## <a name="task-list"></a>Aufgabenliste  
 **So greifen Sie auf das Befehlsfenster zu**  
  
-   Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
 **So geben Sie den Wert einer Variablen aus**  
  
-   Geben Sie im **Befehlsfenster** **Debug.Print \<Variablenname>** ein, und drücken Sie dann die EINGABETASTE.  
  
 **So listen Sie Informationen zum aktuellen Thread auf**  
  
-   Geben Sie im **Befehlsfenster**die Zeichenfolge **Debug.ListThread**ein, und drücken Sie dann die EINGABETASTE.  
  
 **So fügen Sie dem Fenster Schnellüberwachung eine Variable hinzu**  
  
-   Geben Sie im **Befehlsfenster** **Debug.QuickWatch \<Variablenname>** ein, und drücken Sie dann die EINGABETASTE.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Transact-SQL-Debugger](../../relational-databases/scripting/transact-sql-debugger.md)  
  
  
