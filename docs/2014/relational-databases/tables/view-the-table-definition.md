---
title: Anzeigen der Tabellendefinition | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- showing table properties
- displaying table properties
- tables [SQL Server], properties
- viewing table properties
ms.assetid: 1865fb7c-f480-4100-9007-df5364cd002a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ff052e606045f004064c86c5cbec2248a2998c2e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222180"
---
# <a name="view-the-table-definition"></a>Anzeigen der Tabellendefinition
  Sie können die Eigenschaften einer Tabelle in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]anzeigen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So zeigen Sie Tabelleneigenschaften an mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Sie können nur Eigenschaften in einer Tabelle sehen, wenn Sie entweder die Tabelle besitzen oder Ihnen Berechtigungen für diese Tabelle gewährt wurden.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-show-table-properties-in-the-properties-window"></a>So zeigen Sie Tabelleneigenschaften im Eigenschaftenfenster an  
  
1.  Wählen Sie im Objekt-Explorer die Tabelle aus, deren Eigenschaften Sie anzeigen möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Tabelle und wählen Sie im Kontextmenü die Option **Eigenschaften** aus. Weitere Informationen finden Sie unter [Table Properties](table-properties-ssms.md).  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-show-table-properties"></a>So zeigen Sie Tabelleneigenschaften an  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel werden alle Spalten der `sys.tables`-Katalogsicht für das angegebene Objekt zurückgegeben.  
  
    ```  
    SELECT * FROM sys.tables  
    WHERE object_id = 1973582069;  
  
    ```  
  
 Weitere Informationen finden Sie unter [sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql).  
  
###  <a name="TsqlExample"></a>  
