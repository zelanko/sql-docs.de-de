---
title: Ändern von Spalten (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- modifying data types
- column data types [SQL Server]
- data types [SQL Server], columns
ms.assetid: b67b95c5-61ef-4bd8-9a3e-1640eb7583ac
author: stevestein
ms.author: sstein
ms.openlocfilehash: a73c25d91b742f1cc1f7edcc8a95cdf226b2683c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067964"
---
# <a name="modify-columns-database-engine"></a>Ändern von Spalten (Datenbank-Engine)
  Sie können den Datentyp einer Spalte in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]ändern.  
  
> [!WARNING]  
>  Das Ändern des Datentyps einer Spalte, die bereits Daten enthält, kann zu einem dauerhaften Datenverlust führen, wenn die vorhandenen Daten in den neuen Typ konvertiert werden. Außerdem können Code und Anwendungen, die von der geänderten Spalte abhängen, womöglich nicht mehr ausgeführt werden. Dies schließt Abfragen, Sichten, gespeicherte Prozeduren, benutzerdefinierte Funktionen und Clientanwendungen ein. Beachten Sie, dass dabei ein Fehler durch Verkettung weitere Fehler nach sich ziehen kann. Beispielsweise kann eine gespeicherte Prozedur, die eine von der geänderten Spalte abhängige benutzerdefinierte Funktion aufruft, möglicherweise nicht mehr ausgeführt werden. Bedenken Sie sorgfältig die Konsequenzen, bevor Sie Änderungen an einer Spalte vornehmen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So ändern Sie den Datentyp einer Spalte mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-modify-the-data-type-of-a-column"></a>So ändern Sie den Datentyp einer Spalte  
  
1.  Klicken Sie im **Objekt-Explorer**mit der rechten Maustaste auf die Tabelle mit den Spalten, für die Sie Dezimalstellen ändern möchten, und klicken Sie auf **Entwerfen**.  
  
2.  Wählen Sie die Spalte aus, deren Datentyp Sie ändern möchten.  
  
3.  Klicken Sie auf der Registerkarte **Spalteneigenschaften** auf die Datenblattzelle der Eigenschaft **Datentyp** , und wählen Sie aus der Dropdownliste einen neuen Datentyp aus.  
  
4.  Klicken Sie im Menü **Datei** auf _Tabellenname_**speichern**.  
  
> [!NOTE]  
>  Wenn Sie den Datentyp einer Spalte ändern, wendet der Tabellen-Designer die Standardlänge des neuen Datentyps an, auch wenn Sie zuvor eine andere Länge angegeben haben. Legen Sie deshalb die Datentyplänge erst nach dem Ändern des Datentyps fest.  
  
> [!WARNING]  
>  Wenn Sie versuchen, den Datentyp einer Spalte zu ändern, die sich auf andere Tabellen bezieht, fordert Tabellen-Designer Sie auf zu bestätigen, dass die Änderung auch an den Spalten in den anderen Tabellen vorgenommen werden soll.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-modify-the-data-type-of-a-column"></a>So ändern Sie den Datentyp einer Spalte  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    CREATE TABLE dbo.doc_exy (column_a INT ) ;  
    GO  
    INSERT INTO dbo.doc_exy (column_a) VALUES (10) ;  
    GO  
    ALTER TABLE dbo.doc_exy ALTER COLUMN column_a DECIMAL (5, 2) ;  
    GO  
  
    ```  
  
 Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).  
  
  
