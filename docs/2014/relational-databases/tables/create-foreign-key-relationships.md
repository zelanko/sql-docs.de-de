---
title: Erstellen von Fremdschlüssel-Beziehungen | Microsoft Dokumentation
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
- relationships [SQL Server], creating
ms.assetid: 867a54b8-5be4-46e6-9702-49ae6dabf67c
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 254cc2f7bccd634a283412d4b2acbf75f1c0cd84
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159961"
---
# <a name="create-foreign-key-relationships"></a>Erstellen von Fremdschlüssel-Beziehungen
  In diesem Thema wird beschrieben, wie Fremdschlüsselbeziehungen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]erstellt werden. Sie erstellen eine Beziehung zwischen zwei Tabellen, wenn Sie die Zeilen der einen Tabelle mit den Zeilen der anderen Tabelle verknüpfen möchten.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So erstellen Sie Fremdschlüsselbeziehungen mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Eine FOREIGN KEY-Einschränkung muss nicht notwendigerweise mit einer PRIMARY KEY-Einschränkung in einer anderen Tabelle verknüpft sein; sie kann auch so definiert werden, dass sie auf die Spalten einer UNIQUE-Einschränkung in einer anderen Tabelle verweist.  
  
-   Wenn ein anderer Wert als NULL in die Spalte einer FOREIGN KEY-Einschränkung eingegeben wird, muss der Wert in der Spalte vorhanden sein, auf die verwiesen wird; andernfalls wird eine Fremdschlüsselverletzungs-Fehlermeldung zurückgegeben. Um sicherzustellen, dass alle Werte einer zusammengesetzten FOREIGN KEY-Einschränkung überprüft werden, legen Sie NOT NULL für alle betroffenen Spalten fest.  
  
-   FOREIGN KEY-Einschränkungen können nur auf Tabellen verweisen, die sich innerhalb derselben Datenbank auf demselben Server befinden. Datenbankübergreifende referenzielle Integrität muss durch Trigger implementiert werden. Weitere Informationen finden Sie unter [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).  
  
-   FOREIGN KEY-Einschränkungen können auf eine andere Spalte in derselben Tabelle verweisen. Ein solcher Verweis wird als Eigenverweis bezeichnet.  
  
-   Eine auf Spaltenebene angegebene FOREIGN KEY-Einschränkung kann nur eine Verweisspalte auflisten. Diese Spalte muss denselben Datentyp aufweisen wie die Spalte, für die die Einschränkung definiert wurde.  
  
-   Eine auf Tabellenebene angegebene FOREIGN KEY-Einschränkung muss ebenso viele Verweisspalten haben, wie sich Spalten in der Einschränkungsspaltenliste befinden. Der Datentyp jeder Verweisspalte muss ebenfalls mit dem der entsprechenden Spalte in der Spaltenliste übereinstimmen.  
  
-   Das [!INCLUDE[ssDE](../../includes/ssde-md.md)] verfügt über keine vordefinierte Grenze hinsichtlich der Anzahl von FOREIGN KEY-Einschränkungen, die eine Tabelle, die auf andere Tabellen verweist, enthalten kann, oder hinsichtlich der Anzahl von FOREIGN KEY-Einschränkungen im Besitz anderer Tabellen, die auf eine bestimmte Tabelle verweisen. Nichtsdestotrotz ist die tatsächliche Anzahl von FOREIGN KEY-Einschränkungen , die verwendet werden können, durch die Hardwarekonfiguration und den Entwurf der Datenbank und der Anwendung begrenzt. Als Empfehlung gilt, dass eine Tabelle maximal 253 FOREIGN KEY-Einschränkungen enthalten sollte und dass maximal 253 FOREIGN KEY-Einschränkungen auf eine Tabelle verweisen sollten.  
  
-   FOREIGN KEY-Einschränkungen werden nicht auf temporäre Tabellen angewendet.  
  
-   Wenn ein Fremdschlüssel für eine Spalte eines CLR-benutzerdefinierten Typs definiert wird, muss die Implementierung des Typs eine binäre Sortierreihenfolge unterstützen. Weitere Informationen finden Sie unter [CLR User-Defined Types](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
-   Eine Spalte vom Typ `varchar(max)` kann nur dann in eine FOREIGN KEY-Einschränkung einbezogen werden, wenn der Primärschlüssel, auf den verwiesen wird, ebenfalls als `varchar(max)`-Typ definiert ist.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Zum Erstellen einer neuen Tabelle mit einem Fremdschlüssel sind die CREATE TABLE-Berechtigung für die Datenbank und die ALTER-Berechtigung für das Schema erforderlich, in dem die Tabelle erstellt wird.  
  
 Zum Erstellen eines Fremdschlüssels für eine vorhandene Tabelle ist die ALTER-Berechtigung für die Tabelle erforderlich.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-foreign-key-relationship-in-table-designer"></a>So erstellen Sie eine Fremdschlüsselbeziehung im Tabellen-Designer  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Tabelle, die sich auf der Fremdschlüsselseite der Beziehung befinden soll, und klicken Sie auf **Entwerfen**.  
  
     Die Tabelle wird im **Tabellen-Designer**geöffnet.  
  
2.  Klicken Sie im Menü **Tabellen-Designer** auf **Beziehungen**.  
  
3.  Klicken Sie im Dialogfeld **Fremdschlüsselbeziehungen** auf **Hinzufügen**.  
  
     Die Beziehung wird in der Liste **Beziehung (ausgewählt)** mit einem vom System bereitgestellten Namen im Format FK_\<*Tabellenname*>_\<*Tabellenname*> angezeigt, wobei *Tabellenname* der Name der Fremdschlüsseltabelle ist.  
  
4.  Klicken Sie in der Liste **Ausgewählte Beziehung** auf die Beziehung.  
  
5.  Klicken Sie im Datenblatt rechts auf **Tabellen- und Spaltenspezifikation** , und klicken Sie anschließend auf die rechts neben der Eigenschaft angezeigten Auslassungszeichen (**…**).  
  
6.  Wählen Sie im Dialogfeld **Tabellen und Spalten** in der Dropdownliste **Primärschlüssel** die Tabelle aus, die sich auf der Primärschlüsselseite der Beziehung befinden soll.  
  
7.  Wählen Sie im darunter angezeigten Datenblatt die Spalten aus, die für den Primärschlüssel der Tabelle verwendet werden sollen. Geben Sie in die jeweils links neben den einzelnen Spalten angrenzende Datenblattzelle die entsprechende Fremdschlüsselspalte aus der Fremdschlüsseltabelle ein.  
  
     Der**Tabellen-Designer** schlägt einen Namen für die Beziehung vor. Wenn Sie diesen Namen ändern möchten, bearbeiten Sie den Inhalt des Textfelds **Beziehungsname** .  
  
8.  Klicken Sie auf **OK** , um die Beziehung zu erstellen.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-foreign-key-in-a-new-table"></a>So erstellen Sie einen Fremdschlüssel in einer neuen Tabelle  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im Beispiel wird eine Tabelle erstellt und eine Fremdschlüsseleinschränkung für die Spalte `TempID` definiert, die auf die Spalte `SalesReasonID` in der Tabelle `Sales.SalesReason` verweist. Die Klauseln ON DELETE CASCADE und ON UPDATE CASCADE werden verwendet, um sicherzustellen, dass an der `Sales.SalesReason` -Tabelle vorgenommene Änderungen automatisch an die Tabelle `Sales.TempSalesReason` weitergegeben werden.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Sales.TempSalesReason (TempID int NOT NULL, Name nvarchar(50),   
    CONSTRAINT PK_TempSales PRIMARY KEY NONCLUSTERED (TempID),   
    CONSTRAINT FK_TempSales_SalesReason FOREIGN KEY (TempID)   
        REFERENCES Sales.SalesReason (SalesReasonID)   
        ON DELETE CASCADE  
        ON UPDATE CASCADE  
    );GO  
  
    ```  
  
#### <a name="to-create-a-foreign-key-in-an-existing-table"></a>So erstellen Sie einen Fremdschlüssel in einer vorhandenen Tabelle  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im Beispiel wird ein Fremdschlüssel für die Spalte `TempID` erstellt und auf die Spalte `SalesReasonID` in der Tabelle `Sales.SalesReason` verwiesen.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Sales.TempSalesReason   
    ADD CONSTRAINT FK_TempSales_SalesReason FOREIGN KEY (TempID)   
        REFERENCES Sales.SalesReason (SalesReasonID)   
        ON DELETE CASCADE  
        ON UPDATE CASCADE  
    ;  
    GO  
  
    ```  
  
     Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) und [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).  
  
  
