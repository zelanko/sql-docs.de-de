---
title: Erstellen von Primärschlüsseln | Microsoft-Dokumentation
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
- primary keys [SQL Server], creating
ms.assetid: 85c623ca-4656-4d70-a9db-ee4d897cd214
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 180dac17cd2aa504c7fd253761fd636e1baa5166
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060679"
---
# <a name="create-primary-keys"></a>Erstellen von Primärschlüsseln
  Sie können mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] einen Primärschlüssel in [!INCLUDE[tsql](../../includes/tsql-md.md)]definieren. Beim Erstellen eines Primärschlüssels wird automatisch ein zugehöriger eindeutiger, gruppierter oder nicht gruppierter Index erstellt.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So erstellen Sie einen Primärschlüssel mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Eine Tabelle kann nur eine PRIMARY KEY-Einschränkung enthalten.  
  
-   Alle Spalten, für die eine PRIMARY KEY-Einschränkung definiert wurde, müssen als NOT NULL definiert sein. Falls weder NULL noch NOT NULL angegeben ist, wird für alle Spalten, auf die eine PRIMARY KEY-Einschränkung angewendet wird, die NULL-Zulässigkeit auf NOT NULL festgelegt.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Zum Erstellen einer neuen Tabelle mit einem primären Schlüssel sind die CREATE TABLE-Berechtigung für die Datenbank und die ALTER-Berechtigung für das Schema erforderlich, in dem die Tabelle erstellt wird.  
  
 Zum Erstellen eines Primärschlüssels für eine vorhandene Tabelle ist die ALTER-Berechtigung für die Tabelle erforderlich.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-primary-key"></a>So erstellen Sie einen Primärschlüssel  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Tabelle, der Sie eine UNIQUE-Einschränkung hinzufügen möchten, und klicken Sie auf **Entwerfen**.  
  
2.  Klicken Sie im **Tabellen-Designer**auf den Zeilenselektor für die Datenbankspalte, die Sie als Primärschlüssel definieren möchten. Wenn Sie mehrere Spalten auswählen möchten, halten Sie STRG gedrückt, und klicken Sie auf die Zeilenselektoren für die anderen Spalten.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Zeilenselektor für die Spalte, und wählen Sie **Primärschlüssel festlegen**aus.  
  
> [!CAUTION]  
>  Wenn Sie den Primärschlüssel neu definieren möchten, müssen Sie zunächst alle Beziehungen mit dem vorhandenen Primärschlüssel löschen, da erst dann der neue Primärschlüssel erstellt werden kann. In einer Warnmeldung werden Sie informiert, dass vorhandene Beziehungen bei diesem Prozess automatisch gelöscht werden.  
  
 Sie können eine Primärschlüsselspalte am Primärschlüsselsymbol erkennen, das im Zeilenselektor angezeigt wird.  
  
 Wenn ein Primärschlüssel aus mehreren Spalten besteht, können Werte in einer Spalte doppelt vorkommen. Die Kombination der Werte in allen Spalten des Primärschlüssels muss jedoch eindeutig sein.  
  
 Wenn Sie einen Verbundschlüssel definieren, stimmt die Spaltenreihenfolge im Primärschlüssel mit der Spaltenreihenfolge überein, die in der Tabelle angezeigt wird. Sie können die Spaltenreihenfolge jedoch nach Erstellen des Primärschlüssels ändern. Weitere Informationen finden Sie unter [Ändern von Primärschlüsseln](modify-primary-keys.md).  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-primary-key-in-an-existing-table"></a>So erstellen Sie einen Primärschlüssel in einer vorhandenen Tabelle  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im Beispiel wird ein Primärschlüssel für die Spalte `TransactionID`erstellt.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Production.TransactionHistoryArchive   
    ADD CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID);  
    GO  
  
    ```  
  
#### <a name="to-create-a-primary-key-in-a-new-table"></a>So erstellen Sie einen Primärschlüssel in einer neuen Tabelle  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im Beispiel wird eine Tabelle erstellt und ein Primärschlüssel für die Spalte `TransactionID` definiert.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive1  
    (  
       TransactionID int NOT NULL,  
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID)  
    );  
    GO  
  
    ```  
  
     Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) und [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).  
  
###  <a name="TsqlExample"></a>  
