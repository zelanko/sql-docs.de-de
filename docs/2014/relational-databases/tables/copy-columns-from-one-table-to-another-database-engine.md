---
title: Kopieren von Spalten von einer Tabelle in eine andere Tabelle (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- copying columns
- columns [SQL Server], copying
ms.assetid: 5f5e70dc-69f9-44b8-bc48-b5d51ac20d77
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3d2654485acdebdf3e7e79b23dadd533617ea937
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137520"
---
# <a name="copy-columns-from-one-table-to-another-database-engine"></a>Kopieren von Spalten von einer Tabelle in eine andere Tabelle (Datenbank-Engine)
  In diesem Thema wird beschrieben, wie Sie Spalten einer Tabelle in eine andere Tabelle kopieren. Dabei kopieren Sie entweder nur die Spaltendefinition oder die Definition und Daten in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , indem Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]verwenden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So kopieren Sie Spalten mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
 Wenn Sie eine Spalte mit einem Aliasdatentyp aus einer Datenbank in eine andere kopieren, steht der Aliasdatentyp in der Zieldatenbank möglicherweise nicht zur Verfügung. In diesem Fall wird der Spalte der ähnlichste Grunddatentyp zugewiesen, der in der Datenbank verfügbar ist.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-copy-column-definitions-from-one-table-to-another"></a>So kopieren Sie Spaltendefinitionen von einer Tabelle in eine andere  
  
1.  Öffnen Sie die Tabelle mit den zu kopierenden Spalten und diejenige, in die Sie die Spalten kopieren möchten, indem Sie mit der rechten Maustaste auf die Tabellen und dann auf **Entwerfen**klicken.  
  
2.  Klicken Sie auf die Registerkarte für die Tabelle mit den zu kopierenden Spalten, und wählen Sie diese Spalten aus.  
  
3.  Klicken Sie im Menü **Bearbeiten** auf den Befehl **Kopieren**.  
  
4.  Klicken Sie auf die Registerkarte der Tabelle, in die Sie die Spalten kopieren möchten.  
  
5.  Wählen Sie die Spalte aus, die den eingefügten Spalten folgen soll, und klicken Sie im Menü **Bearbeiten** auf **Einfügen**.  
  
#### <a name="to-copy-data-from-one-table-to-another"></a>So kopieren Sie Daten von einer Tabelle in eine andere  
  
1.  Befolgen Sie die obigen Anweisungen zum Kopieren von Spaltendefinitionen.  
  
    > [!NOTE]  
    >  Bevor Sie Daten von einer Tabelle in eine andere kopieren, stellen Sie sicher, dass die Datentypen in den Zielspalten mit denen der Quellspalten kompatibel sind.  
  
2.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Knoten **Sichten** , und klicken Sie dann auf **Neue Sicht**.  
  
3.  Zeigen Sie im Menü **Abfrage-Designer** auf **Typ ändern**, und klicken Sie dann auf **Ergebnisse einfügen**.  
  
4.  Wählen Sie im Dialogfeld **Zieltabelle für Anfügeabfrage auswählen** die Tabelle aus, in die Sie die Daten kopieren möchten, und klicken Sie dann auf **OK**.  
  
     Wenn Sie Zeilen innerhalb einer Tabelle kopieren, können Sie die Quelltabelle als Zieltabelle hinzufügen.  
  
    > [!NOTE]  
    >  Der**Abfrage-Designer** kann nicht im Voraus bestimmen, welche Tabellen und Sichten Sie aktualisieren können. Daher werden im Dialogfeld **Zieltabelle für Anfügeabfrage auswählen** in der Tabellenliste alle in der abgefragten Datenverbindung verfügbaren Tabellen und Sichten angezeigt, d. h. auch diejenigen, in die möglicherweise keine Zeilen kopiert werden können.  
  
5.  Klicken Sie mit der rechten Maustaste auf den Diagrammbereich und dann im Kontextmenü auf **Tabelle zu Diagramm hinzufügen**.  
  
6.  Wählen Sie im Dialogfeld **Tabelle hinzufügen** alle Tabellen aus, aus denen Sie Daten kopieren möchten. Klicken Sie auf **Hinzufügen**und dann auf **Schließen**.  
  
     Die Tabellen werden in abgekürzter Form im Diagrammbereich angezeigt.  
  
7.  Aktivieren Sie in den abgekürzten Tabellen die einzelnen Kontrollkästchen für die Spalten, aus denen Sie Daten kopieren möchten.  
  
8.  Wählen Sie Im Kriterienbereich in der Spalte **Anfügen** für jede Zielspalte eine Spalte aus, aus der Sie Daten kopieren möchten.  
  
9. Legen Sie im Kriterienbereich durch Eingabe von Suchbedingungen fest, welche Zeilen kopiert werden sollen. Weitere Informationen finden Sie unter [Angeben von Suchbedingungen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).  
  
     Wenn Sie keine Suchbedingung festlegen, werden alle Zeilen der Quelltabelle in die Zieltabelle kopiert.  
  
10. Geben Sie unter **Gruppieren nach** Gruppierungsoptionen an, wenn Sie Kurzinformationen kopieren möchten. Weitere Informationen finden Sie unter [Wertzusammenfassung oder -aggregation für alle Zeilen in einer Tabelle &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md).  
  
11. Klicken Sie auf die Schaltfläche **SQL ausführen** , um die Abfrage auszuführen.  
  
     Beim Ausführen einer Abfrage zum Einfügen von Ergebnissen werden im [Ergebnisbereich](../../ssms/visual-db-tools/results-pane-visual-database-tools.md)keine Ergebnisse angezeigt. Stattdessen wird eine Meldung mit der Anzahl der kopierten Zeilen ausgegeben.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-copy-column-definitions-from-one-table-to-another"></a>So kopieren Sie Spaltendefinitionen von einer Tabelle in eine andere  
  
1.  Anhand von Transact-SQL-Anweisungen können Sie keine einzelnen Spalten aus einer Tabelle in eine andere vorhandene Tabelle kopieren. Mit SELECT INTO können Sie jedoch eine neue Tabelle in der Standarddateigruppe erstellen, und die Ergebniszeilen aus der Abfrage werden darin eingefügt. Weitere Informationen finden Sie unter [INTO-Klausel &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-into-clause-transact-sql).  
  
#### <a name="to-copy-data-from-one-table-to-another"></a>So kopieren Sie Daten von einer Tabelle in eine andere  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE dbo.EmployeeSales  
    ( BusinessEntityID   varchar(11) NOT NULL,  
      SalesYTD money NOT NULL  
    );  
    GO  
    INSERT INTO dbo.EmployeeSales  
        SELECT BusinessEntityID, SalesYTD   
        FROM Sales.SalesPerson;  
    GO  
    ```  
  
  
