---
title: Erstellen einer Datenbank (Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tutorial creating a database
ms.assetid: e1e2c83f-dfad-4bb8-aa7a-09d3f69517ae
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 99d5439c289b5d4e71786d4c6734f158f6bba371
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048534"
---
# <a name="creating-a-database-tutorial"></a>Erstellen einer Datenbank (Lernprogramm)
  Wie viele [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen verfügt auch die CREATE DATABASE-Anweisung über einen erforderlichen Parameter: den Namen der Datenbank. CREATE DATABASE verfügt auch über viele optionale Parameter wie den Speicherort auf dem Datenträger, an den Sie die Datenbankdateien kopieren möchten. Wenn Sie CREATE DATABASE ohne optionale Parameter ausführen, werden von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standardwerte für viele dieser Parameter verwendet. In diesem Lernprogramm werden nur wenige der optionalen Syntaxparameter verwendet.  
  
### <a name="to-create-a-database"></a>So erstellen Sie eine Datenbank  
  
1.  Geben Sie in einem Fenster des Abfrage-Editors den folgenden Code ein, aber führen Sie ihn nicht aus:  
  
    ```  
    CREATE DATABASE TestData  
    GO  
    ```  
  
2.  Verwenden Sie den Zeiger, um die Wörter `CREATE DATABASE`auszuwählen, und drücken Sie dann **F1**. Das CREATE DATABASE-Thema in der SQL Server-Onlinedokumentation sollte geöffnet werden. Sie können dieses Verfahren verwenden, um die vollständige Syntax für CREATE DATABASE und für die anderen in diesem Lernprogramm verwendeten Anweisungen zu finden.  
  
3.  Drücken Sie im Abfrage-Editor **F5** , um die Anweisung auszuführen und eine Datenbank mit Namen `TestData`zu erstellen.  
  
 Wenn Sie eine Datenbank erstellen, wird von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] eine Kopie der **model** -Datenbank erstellt und die Kopie in den Namen der Datenbank umbenannt. Dieser Vorgang dauert nur einige Sekunden, es sei denn, Sie geben eine große Anfangsgröße der Datenbank als optionalen Parameter an.  
  
> [!NOTE]  
>  Das GO-Schlüsselwort trennt Anweisungen, wenn mehrere Anweisungen in einem einzelnen Batch gesendet werden. GO ist optional, wenn der Batch nur eine Anweisung enthält.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Erstellen einer Tabelle &#40;Tutorial&#41;](lesson-1-2-creating-a-table.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
