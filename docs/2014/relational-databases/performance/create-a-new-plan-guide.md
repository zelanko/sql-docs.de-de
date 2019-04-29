---
title: Erstellen einer neuen Planhinweisliste | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.designer.newplanguide.f1
helpviewer_keywords:
- creating plan guides
- plan guides [SQL Server]. creating
ms.assetid: e1ad78bb-4857-40ea-a0c6-dcf5c28aef2f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9fa024e9e744fd955e4ccc323919cb22a97b7dd3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63151194"
---
# <a name="create-a-new-plan-guide"></a>Erstellen einer neuen Planhinweisliste
  Sie können in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]eine Planhinweisliste erstellen. Planhinweislisten beeinflussen die Abfrageoptimierung, indem Abfragehinweise oder ein fester Abfrageplan an die Abfragen angefügt werden. In der Planhinweisliste geben Sie die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung an, die optimiert werden soll, sowie entweder eine OPTION-Klausel mit den zu verwendenden Abfragehinweisen oder einen spezifischen Abfrageplan, der für die Optimierung der Abfrage verwendet werden soll. Wenn die Abfrage ausgeführt wird, vergleicht der Abfrageoptimierer die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung mit der Planhinweisliste und fügt der Abfrage entweder zur Laufzeit die OPTION-Klausel hinzu oder verwendet den angegebenen Abfrageplan.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So erstellen Sie eine Planhinweisliste mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Die Argumente für sp_create_plan_guide müssen in der angezeigten Reihenfolge bereitgestellt werden. Wenn Sie Werte für die Parameter von `sp_create_plan_guide` angeben, müssen entweder alle oder überhaupt keine Parameternamen explizit angegeben werden. Wird z. B. `@name =` angegeben, müssen auch `@stmt =` , `@type =` usw. angegeben werden. Ebenso dürfen, wenn `@name =` nicht angegeben und nur der Parameterwert bereitgestellt wird, die übrigen Parameterwerte ebenfalls nicht angegeben und nur ihre Werte bereitgestellt werden. Argumentnamen dienen nur zu Beschreibungszwecken, zum besseren Verständnis der Syntax. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] überprüft nicht, ob der angegebene Parametername mit dem Namen des Parameters an der Position übereinstimmt, an der der Name verwendet wird.  
  
-   Sie können mehr als eine Planhinweisliste des Typs OBJECT oder SQL für dieselbe Abfrage und den Batch oder das Modul erstellen. Es kann jedoch nur jeweils eine Planhinweisliste aktiviert sein.  
  
-   Planhinweislisten vom Typ OBJECT können nicht für einen @module_or_batch-Wert erstellt werden, der auf eine gespeicherte Prozedur, Funktion oder einen DML-Trigger verweist, in der bzw. dem die WITH ENCRYPTION-Klausel angegeben wird oder die bzw. der temporär ist.  
  
-   Das Löschen oder Ändern einer Funktion, einer gespeicherten Prozedur oder eines DML-Triggers, auf die bzw. den in einer Planhinweisliste verwiesen wird, verursacht einen Fehler. Auch der Versuch, eine Tabelle mit einem Trigger zu löschen, auf den eine Planhinweisliste verweist, führt zu einem Fehler.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Zum Erstellen einer Planhinweisliste vom Typ OBJECT wird die ALTER-Berechtigung für das Objekt benötigt, auf das verwiesen wird. Zum Erstellen einer Planhinweisliste vom Typ SQL oder TEMPLATE wird die ALTER-Berechtigung für die aktuelle Datenbank benötigt.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-plan-guide"></a>Erstellen einer Planhinweisliste  
  
1.  Klicken Sie auf das Pluszeichen, um die Datenbank zu erweitern, in der Sie eine Planhinweisliste erstellen möchten, und klicken Sie dann auf das Pluszeichen, um den Ordner **Programmierbarkeit** zu erweitern.  
  
2.  Mit der rechten Maustaste die **Planhinweislisten** Ordner, und wählen **neue Planhinweisliste...** .  
  
3.  Geben Sie im Dialogfeld **Neue Planhinweisliste** im Feld **Name** den Namen der Planhinweisliste ein.  
  
4.  Geben Sie im Feld **Anweisung** die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung ein, auf die die Planhinweisliste angewendet werden soll.  
  
5.  Wählen Sie in der Liste **Bereichstyp** den Entitätstyp aus, mit dem die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung angezeigt wird. Dies gibt den Kontext zum Abgleich der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung mit der Planhinweisliste an. Mögliche Werte sind **OBJECT**, **SQL**und **TEMPLATE**.  
  
6.  Geben Sie im Feld **Bereichsbatch** den Batchtext ein, mit dem die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung angezeigt wird. Der Batchtext darf keine USE``*Datenbank* -Anweisung enthalten. Das Feld **Bereichsbatch** ist nur verfügbar, wenn **SQL** als Bereichstyp ausgewählt ist. Wenn bei Verwendung von SQL als Bereichstyp im Feld Bereichsbatch kein Wert angegeben wird, wird der Wert des Batchtexts auf den gleichen Wert wie im Feld **Anweisung** festgelegt.  
  
7.  Geben Sie in der Liste **Name von Bereichsschema** den Namen des Schemas ein, in dem sich das Objekt befindet. Das Feld **Name von Bereichsschema** ist nur verfügbar, wenn **Objekt** als Bereichstyp ausgewählt ist.  
  
8.  Geben Sie im Feld **Name von Bereichsobjekt** den Namen der gespeicherten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Prozedur, der benutzerdefinierten Skalarfunktion, der aus mehreren Anweisungen bestehenden Tabellenwertfunktion oder des DML-Triggers ein, worin die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung enthalten ist. Das Feld **Name von Bereichsobjekt** ist nur verfügbar, wenn **Objekt** als Bereichstyp ausgewählt ist.  
  
9. Geben Sie im Feld **Parameter** den Parameternamen und Datentyp aller Parameter ein, die in die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung eingebettet sind.  
  
     Parameter sind nur dann anwendbar, wenn eine der folgenden Aussagen zutrifft:  
  
    -   Der Bereichstyp lautet **SQL** oder **TEMPLATE**. Bei **TEMPLATE**dürfen Parameter nicht NULL sein.  
  
    -   Die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung wird mithilfe von sp_executesql übermittelt und für den Parameter ein Wert festgelegt, oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] übermittelt eine Anweisung intern, nachdem sie parametrisiert wurde.  
  
10. Geben Sie im Feld **Hinweise** die Abfragehinweise oder den Abfrageplan ein, die bzw. der auf die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung angewendet werden soll. Geben Sie eine gültige OPTION-Klausel ein, um einen oder mehrere Abfragehinweise festzulegen.  
  
11. Klicken Sie auf **OK**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-plan-guide"></a>Erstellen einer Planhinweisliste  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- creates a plan guide named Guide1 based on a SQL statement  
    EXEC sp_create_plan_guide   
        @name = N'Guide1',   
        @stmt = N'SELECT TOP 1 *   
                  FROM Sales.SalesOrderHeader   
                  ORDER BY OrderDate DESC',   
        @type = N'SQL',  
        @module_or_batch = NULL,   
        @params = NULL,   
        @hints = N'OPTION (MAXDOP 1)';  
  
    ```  
  
 Weitere Informationen finden Sie unter [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql).  
  
  
