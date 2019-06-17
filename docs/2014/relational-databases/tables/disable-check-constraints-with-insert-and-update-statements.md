---
title: Deaktivieren von CHECK-Einschränkungen mit den Anweisungen INSERT und UPDATE | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- CHECK constraints, disabling
- constraints [SQL Server], disabling
- disabling constraints
- constraints [SQL Server], check
ms.assetid: c7287ad1-50d2-4e80-bc0c-b5570f7e5f69
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bd49c3264857a92a9ca029a25894a5afdbeab381
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62760989"
---
# <a name="disable-check-constraints-with-insert-and-update-statements"></a>Deaktivieren von CHECK-Einschränkungen mit den Anweisungen INSERT und UPDATE
  Sie können mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine CHECK-Einschränkung für INSERT- und UPDATE-Transaktionen in [!INCLUDE[tsql](../../includes/tsql-md.md)]deaktivieren. Sobald die CHECK-Einschränkungen deaktiviert worden sind, wird die Spalte bei Einfügungen oder Aktualisierungen nicht mehr bezüglich der Einschränkungsbedingungen überprüft. Verwenden Sie diese Option, wenn Sie wissen, dass neue Daten gegen die vorhandene Einschränkung verstoßen, oder wenn die Einschränkung nur für die bereits in der Datenbank vorhandenen Daten gilt.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So deaktivieren Sie eine CHECK-Einschränkung für INSERT- und UPDATE-Anweisungen mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-disable-a-check-constraint-for-insert-and-update-statements"></a>So deaktivieren Sie eine CHECK-Einschränkung für INSERT- und UPDATE-Anweisungen  
  
1.  Erweitern Sie im **Objekt-Explorer**die Tabelle mit der Einschränkung, und erweitern Sie dann den Ordner **Einschränkungen** .  
  
2.  Klicken Sie mit der rechten Maustaste auf die Einschränkung, und wählen Sie dann **Ändern**aus.  
  
3.  Klicken Sie im Raster unter dem **Tabellen-Designer**auf **Für INSERTs und UPDATEs erzwingen** , und wählen Sie im Dropdownmenü **Nein** aus.  
  
4.  Klicken Sie auf **Schließen**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-disable-a-check-constraint-for-insert-and-update-statements"></a>So deaktivieren Sie eine CHECK-Einschränkung für INSERT- und UPDATE-Anweisungen  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie die folgenden Beispiele, fügen Sie sie in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT CK_PurchaseOrderHeader_Freight;   
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).  
  
###  <a name="TsqlExample"></a>  
