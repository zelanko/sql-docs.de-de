---
title: Angeben des Abfrageparametrisierungsverhaltens mithilfe von Planhinweislisten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- TEMPLATE plan guide
- PARAMETERIZATION FORCED option
- PARAMETERIZATION option
- PARAMETERIZATION SIMPLE option
- parameterization [SQL Server]
- overriding parameterization behavior
- plan guides [SQL Server], parameterization
- parameterized queries [SQL Server]
ms.assetid: f0f738ff-2819-4675-a8c8-1eb6c210a7e6
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 06ed5433d23501016a0ea308c9238fcf7bc1b3c1
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2019
ms.locfileid: "67582066"
---
# <a name="specify-query-parameterization-behavior-by-using-plan-guides"></a>Angeben des Abfrageparametrisierungsverhaltens mithilfe von Planhinweislisten
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Wenn die PARAMETERIZATION-Datenbankoption auf SIMPLE festgelegt ist, kann der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abfrageoptimierer die Abfragen ggf. parametrisieren. Dies bedeutet, dass alle eventuell in einer Abfrage enthaltenen Literalwerte durch Parameter ersetzt werden. Dieses Verfahren wird als einfache Parametrisierung bezeichnet. Wenn die einfache Parametrisierung aktiviert ist, können Sie nicht steuern, welche Abfragen parametrisiert werden sollen und welche nicht. Sie können jedoch angeben, dass alle Abfragen einer Datenbank parametrisiert werden sollen, indem Sie die PARAMETERIZATION-Datenbankoption auf FORCED festlegen. Dieses Verfahren wird als erzwungene Parametrisierung bezeichnet.  
  
 Sie können das Parametrisierungsverhalten einer Datenbank überschreiben, in dem Sie Planhinweislisten verwenden. Es gibt dabei folgende Möglichkeiten:  
  
-   Wenn die PARAMETERIZATION-Datenbankoption auf SIMPLE festgelegt ist, können Sie angeben, dass für eine bestimmte Abfrageklasse die erzwungene Parametrisierung versucht werden soll. Erstellen Sie dazu eine TEMPLATE-Planhinweisliste für die parametrisierte Form der Abfrage, und geben Sie den PARAMETERIZATION FORCED-Abfragehinweis in der gespeicherten Prozedur [sp_create_plan_guide](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md) an. Betrachten Sie diese Art, Planhinweislisten zu verwenden, als Verfahren, die erzwungene Parametrisierung nur für eine bestimmte, jedoch nicht alle Abfrageklassen zu aktivieren.  
  
-   Wenn die PARAMETERIZATION-Datenbankoption auf FORCED festgelegt ist, können Sie angeben, dass für eine bestimmte Abfrageklasse nur die einfache Parametrisierung versucht werden soll, jedoch nicht die erzwungene Parametrisierung. Erstellen Sie dazu eine TEMPLATE-Planhinweisliste für die erzwungene parametrisierte Form der Abfrage, und geben Sie in **sp_create_plan_guide**den PARAMETERIZATION SIMPLE-Abfragehinweis an.  
  
 Betrachten Sie die folgende Abfrage in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank:  
  
```  
SELECT pi.ProductID, SUM(pi.Quantity) AS Total  
FROM Production.ProductModel AS pm   
    INNER JOIN Production.ProductInventory AS pi   
        ON pm.ProductModelID = pi.ProductID   
WHERE pi.ProductID = 101   
GROUP BY pi.ProductID, pi.Quantity HAVING SUM(pi.Quantity) > 50;  
```  
  
 Als Datenbankadministrator haben Sie bestimmt, dass Sie die erzwungene Parametrisierung nicht für alle Abfragen der Datenbank aktivieren möchten. Sie sind jedoch darauf bedacht, den Aufwand zu vermeiden, alle Abfragen neu zu kompilieren, obwohl sie syntaktisch mit vorherigen Abfragen gleichwertig sind und sich lediglich durch ihre konstanten Literalwerte unterscheiden. Mit anderen Worten möchten Sie solche Abfragen parametrisieren, sodass für diese Art von Abfragen ein Abfrageplan wiederverwendet wird. Führen Sie in diesem Fall die folgenden Schritte aus:  
  
1.  Rufen Sie die parametrisierte Form der Abfrage ab. Die einzig sichere Möglichkeit, diesen Wert zum Verwenden in **sp_create_plan_guide** abzurufen, besteht in der Verwendung der gespeicherten Systemprozedur [sp_get_query_template](../../relational-databases/system-stored-procedures/sp-get-query-template-transact-sql.md) .  
  
2.  Erstellen Sie die Planhinweisliste für die parametrisierte Form der Abfrage, indem Sie den PARAMETERIZATION FORCED-Abfragehinweis angeben.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

    > [!IMPORTANT]  
    >  As part of parameterizing a query, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assigns a data type to the parameters that replace the literal values, depending on the value and size of the literal. The same process occurs to the value of the constant literals passed to the **@stmt** output parameter of **sp_get_query_template**. Because the data type specified in the **@params** argument of **sp_create_plan_guide** must match that of the query as it is parameterized by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you may have to create more than one plan guide to cover the complete range of possible parameter values for the query.  
  
 Verwenden Sie das folgende Skript, um die parametrisierte Abfrage und anschließend eine Planhinweisliste dafür zu erstellen:  
  
```  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'SELECT pi.ProductID, SUM(pi.Quantity) AS Total   
      FROM Production.ProductModel AS pm   
      INNER JOIN Production.ProductInventory AS pi ON pm.ProductModelID = pi.ProductID   
      WHERE pi.ProductID = 101   
      GROUP BY pi.ProductID, pi.Quantity   
      HAVING sum(pi.Quantity) > 50',  
    @stmt OUTPUT,   
    @params OUTPUT;  
EXEC sp_create_plan_guide   
    N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
 Auf ähnliche Weise können Sie in einer Datenbank mit bereits aktivierter erzwungener Parametrisierung sicherstellen, dass die Beispielabfrage und andere, mit Ausnahme ihrer konstanten Literalwerte, syntaktisch gleichwertige Abfragen gemäß den Regeln für die einfache Parametrisierung parametrisiert werden. Geben Sie dazu in der OPTION-Klausel PARAMETERIZATION SIMPLE anstelle von PARAMETERIZATION FORCED an.  
  
> [!NOTE]  
>  Durch TEMPLATE-Planhinweislisten wird eine Übereinstimmung zwischen Anweisungen und batchweise übermittelten Abfragen hergestellt, die nur aus einer einzigen Anweisung bestehen. Für Anweisungen innerhalb von Batches mit mehreren Anweisungen können TEMPLATE-Planhinweislisten keine Übereinstimmungen herstellen.  
  
  
