---
title: Löschen einer gespeicherten Prozedur | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine gespeicherte Prozedur mithilfe von SQL Server Management Studio oder Transact-SQL in SQL Server 2019 (15.x) löschen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- removing stored procedures
- stored procedures [SQL Server], deleting
- deleting stored procedures
ms.assetid: 232dbf4d-392a-406f-af3a-579518cd8e46
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 742b0e7f3631f5cf262ff6e20bdc64f1ba7bea7f
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97475311"
---
# <a name="delete-a-stored-procedure"></a>Löschen einer gespeicherten Prozedur
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
    
##  <a name="this-topic-describes-how-to-delete-a-stored-procedure-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a> Dieses Thema beschreibt, wie mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine gespeicherte Prozedur in [!INCLUDE[tsql](../../includes/tsql-md.md)]gelöscht werden kann.  
  
-   **Vorbereitungen:**  [Beschränkungen](#Restrictions), [Sicherheit](#Security)  
  
-   **So löschen Sie eine Prozedur mithilfe von:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
 Das Löschen einer Prozedur kann dazu führen, dass abhängige Objekte und Skripts fehlerhaft sind, wenn diese Objekte und Skripts nicht so aktualisiert werden, dass sie Löschung der Prozedur widerspiegeln. Wird jedoch eine neue Prozedur mit demselben Namen und denselben Parametern erstellt, um die gelöschte Prozedur zu ersetzen, können andere Objekte, die darauf verweisen, weiterhin erfolgreich verarbeitet werden. Weitere Informationen finden Sie unter [Anzeigen der Abhängigkeiten einer gespeicherten Prozedur](../../relational-databases/stored-procedures/view-the-dependencies-of-a-stored-procedure.md).  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung im Schema, zu der die Prozedur gehört, oder die CONTROL-Berechtigung für die Prozedur.  
  
##  <a name="how-to-delete-a-stored-procedure"></a><a name="Procedures"></a> Vorgehensweise: Löschen einer gespeicherten Prozedur  
 Sie können eine der folgenden Anwendungen verwenden:  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 **So löschen Sie eine Prozedur im Objekt-Explorer**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, erweitern Sie die Datenbank, zu der die Prozedur gehört, und erweitern Sie dann **Programmierbarkeit**.  
  
3.  Erweitern Sie **Gespeicherte Prozeduren**, klicken Sie mit der rechten Maustaste auf die zu entfernende Prozedur, und klicken Sie dann auf **Löschen**.  
  
4.  Klicken Sie auf **Abhängigkeiten anzeigen**, um die von der Prozedur abhängigen Objekte anzuzeigen.  
  
5.  Bestätigen Sie, dass die richtige Prozedur ausgewählt wurde, und klicken Sie dann auf **OK**.  
  
6.  Entfernen Sie in allen abhängigen Objekten und Skripts die Verweise auf die Prozedur.  

###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So löschen Sie eine Prozedur im Abfrage-Editor**  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, erweitern Sie die Datenbank, in die die Prozedur gehört, oder wählen Sie in der Symbolleiste die Datenbank aus der Liste der verfügbaren Datenbanken aus.  
  
3.  Klicken Sie im Menü Datei auf **Neue Abfrage**.  
  
4.  Rufen Sie den Namen der gespeicherten Prozedur ab, der aus der aktuellen Datenbank entfernt werden soll. Erweitern Sie im Objekt-Explorer **Programmierbarkeit** , und erweitern Sie dann **Gespeicherte Prozeduren**. Führen Sie stattdessen im Abfrage-Editor die folgende Anweisung aus.  
  
    ```sql  
    SELECT name AS procedure_name   
        ,SCHEMA_NAME(schema_id) AS schema_name  
        ,type_desc  
        ,create_date  
        ,modify_date  
    FROM sys.procedures;  
    ```  
  
5.  Kopieren und fügen Sie das folgende Beispiel in den Abfrage-Editor ein, und fügen Sie einen Namen der gespeicherten Prozedur ein, der aus der aktuellen Datenbank gelöscht werden soll.  
  
    ```sql  
    DROP PROCEDURE <stored procedure name>;  
    GO  
    ```  
  
6.  Entfernen Sie in allen abhängigen Objekten und Skripts die Verweise auf die Prozedur.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer gespeicherten Prozedur](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [Ändern einer gespeicherten Prozedur](../../relational-databases/stored-procedures/modify-a-stored-procedure.md)   
 [Umbenennen einer gespeicherten Prozedur](../../relational-databases/stored-procedures/rename-a-stored-procedure.md)   
 [Anzeigen der Definition einer gespeicherten Prozedur](../../relational-databases/stored-procedures/view-the-definition-of-a-stored-procedure.md)   
 [Anzeigen der Abhängigkeiten einer gespeicherten Prozedur](../../relational-databases/stored-procedures/view-the-dependencies-of-a-stored-procedure.md)   
 [DROP PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-procedure-transact-sql.md)  
  
  
