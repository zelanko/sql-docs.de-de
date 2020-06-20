---
title: Speichern eines Ausführungsplans im XML-Format | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- XML query plans [SQL Server]
- opening execution plans
- XML Showplans [SQL Server]
- execution plans [SQL Server], saving
- saving execution plans
ms.assetid: c439e53b-56f3-4442-97c6-dabd48a203d8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 84ed341d186993ed77260e8361156b324c597839
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047890"
---
# <a name="save-an-execution-plan-in-xml-format"></a>Speichern eines Ausführungsplans im XML-Format
  Verwenden Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , um Ausführungspläne als XML-Datei zu speichern und für die Anzeige zu öffnen.  
  
 Zum Verwenden der Ausführungsplanfunktion in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]oder der XML Showplan-SET-Optionen benötigen Benutzer die entsprechenden Berechtigungen, um die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfrage auszuführen, für die ein Ausführungsplan generiert wird. Den Benutzern muss auch die SHOWPLAN-Berechtigung für alle Datenbanken erteilt werden, auf die die Abfrage verweist.  
  
### <a name="to-save-a-query-plan-by-using-the-xml-showplan-set-options"></a>So speichern Sie einen Abfrageplan mit den XML Showplan-SET-Optionen  
  
1.  Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] einen Abfrage-Editor, und stellen Sie eine Verbindung mit [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Aktivieren Sie SHOWPLAN_XML mithilfe der folgenden Anweisung:  
  
    ```  
    SET SHOWPLAN_XML ON;  
    GO  
    ```  
  
     Verwenden Sie die folgende Anweisung, um STATISTICS XML zu aktivieren:  
  
    ```  
    SET STATISTICS XML ON;  
    GO  
    ```  
  
     SHOWPLAN_XML generiert für eine Abfrage zur Kompilierungszeit Informationen zum Abfrageausführungsplan, führt die Abfrage aber nicht aus. STATISTICS XML generiert für eine Abfrage zur Laufzeit Informationen zum Abfrageausführungsplan und führt die Abfrage aus.  
  
3.  Abfrage ausführen. Beispiel:  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SET SHOWPLAN_XML ON;  
    GO  
    -- Execute a query.  
    SELECT BusinessEntityID   
    FROM HumanResources.Employee  
    WHERE NationalIDNumber = '509647174';  
    GO  
    SET SHOWPLAN_XML OFF;  
    ```  
  
4.  Klicken Sie im Bereich **Ergebnisse** mit der rechten Maustaste auf den **Microsoft SQL Server XML Showplan** , der den Abfrageplan enthält, und klicken Sie dann auf **Ergebnisse speichern unter**.  
  
5.  **Save** \<Grid or Text> Klicken Sie im Dialogfeld **Ergebnisse** speichern im Feld **Dateityp** auf **alle Dateien ( \* . \* )**.  
  
6.  Geben Sie im Feld **Dateiname** einen Namen im Format \<name**> . sqlplan * * ein, und klicken Sie dann auf **Speichern**.  
  
### <a name="to-save-an-execution-plan-by-using-sql-server-management-studio-options"></a>So speichern Sie einen Ausführungsplan mithilfe der SQL Server Management Studio-Optionen  
  
1.  Generieren Sie mit [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]entweder einen geschätzten Ausführungsplan oder einen tatsächlichen Ausführungsplan. Weitere Informationen finden Sie unter [Anzeigen des geschätzten Ausführungsplans](display-the-estimated-execution-plan.md) oder [Anzeigen eines tatsächlichen Ausführungsplans](display-an-actual-execution-plan.md).  
  
2.  Klicken Sie im Ergebnisbereich auf der Registerkarte **Ausführungsplan** auf den grafischen Ausführungsplan und wählen Sie **Ausführungsplan speichern unter**.  
  
     Alternativ können Sie **Ausführungsplan speichern unter** auch im Menü **Datei** auswählen.  
  
3.  Stellen Sie im Dialogfeld **Speichern unter** sicher, dass der **Dateityp** auf **Ausführungsplandateien (\*.sqlplan)** festgelegt ist.  
  
4.  Geben Sie im Feld **Dateiname** einen Namen im Format \<name**> . sqlplan * * ein, und klicken Sie dann auf **Speichern**.  
  
### <a name="to-open-a-saved-xml-query-plan-in-sql-server-management-studio"></a>So öffnen Sie einen gespeicherten XML-Abfrageplan in SQL Server Management Studio  
  
1.  Wählen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]im Menü **Datei****Öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  Legen Sie im Dialogfeld **Datei öffnen** den **Dateityp** auf **Ausführungsplandateien (\*.sqlplan)** fest, um eine gefilterte Liste der gespeicherten XML-Abfrageplandateien zu erzeugen.  
  
3.  Wählen Sie die XML-Abfrageplandatei aus, die Sie anzeigen möchten, und klicken Sie auf **Öffnen**.  
  
     Alternativ können Sie im Windows-Explorer auf eine Datei mit der Erweiterung **.sqlplan**doppelklicken. Der Plan wird in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]geöffnet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Festlegen SHOWPLAN_XML &#40;Transact-SQL-&#41;](/sql/t-sql/statements/set-showplan-xml-transact-sql)   
 [SET STATISTICS XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-xml-transact-sql)  
  
  
