---
description: Unterschiedliche Abfragedefinitionen (Dialogfeld) (Visual Database Tools)
title: Unterschiedliche Abfragedefinitionen (Dialogfeld)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69639
- vdtsql.chm:69640
- vdt.dlgbox.querydefinitionsdiffer
ms.assetid: 90383473-2922-40e5-9682-3850849aa856
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: a2517d930333f9a17e7746db29074456281ecf9d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88313856"
---
# <a name="query-definitions-differ-dialog-box-visual-database-tools"></a>Unterschiedliche Abfragedefinitionen (Dialogfeld) (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
In diesem Dialogfeld werden Sie darauf hingewiesen, dass die Abfrage in den Bereichen Diagramm und Kriterien grafisch nicht dargestellt und daher nur im SQL-Bereich bearbeitet werden kann.  
  
Dieses Dialogfeld wird angezeigt, wenn Sie eine SQL-Anweisung im SQL-Bereich eingeben oder bearbeiten, dann zu einem anderen Bereich wechseln, die Abfrage überprüfen oder versuchen, sie auszuführen, und gleichzeitig eine der folgenden Bedingungen zutrifft:  
  
-   Die SQL-Anweisung ist unvollständig oder enthält mindestens einen Syntaxfehler.  
  
-   Die SQL-Anweisung ist gültig, wird aber von den grafischen Bereichen nicht unterstützt (z. B. eine Union-Abfrage).  
  
-   Die SQL-Anweisung ist gültig, enthält aber Syntax, die nur für die verwendete Datenverbindung gilt.  
  
> [!TIP]  
>  Sie können die Gültigkeit einer Anweisung auf der Symbolleiste **Abfrage** mithilfe der Schaltfläche **Analysieren** überprüfen.  
  
Das Dialogfeld zeigt eine Meldung mit dem Hinweis an, dass die SQL-Anweisung nicht dargestellt werden kann. Geben Sie an, wie Sie weiter vorgehen möchten.  
  
> [!NOTE]  
>  Das Dialogfeld **Unterschiedliche Abfragedefinitionen** wird nicht angezeigt, wenn die Bereiche Diagramm und Kriterien ausgeblendet sind.  
  
## <a name="options"></a>Optionen  
**Schaltfläche Ignorieren**  
Mit dieser Schaltfläche können Sie die SQL-Anweisung übernehmen, um sie weiter zu bearbeiten oder auszuführen. Wenn Sie die Anweisung übernehmen, werden die Bereiche Diagramm und Kriterien abgeblendet, um anzuzeigen, dass die Anweisung im SQL-Bereich darin nicht dargestellt wird.  
  
**Schaltfläche Rückgängig**  
Mit dieser Schaltfläche können Sie die im SQL-Bereich vorgenommenen Änderungen verwerfen.  
  
> [!NOTE]  
> Wenn die Anweisung richtig ist, aber vom Abfrage- und Sicht-Designer nicht grafisch unterstützt wird, können Sie sie ausführen, obwohl sie nicht in den Bereichen Diagramm und Kriterien dargestellt wird. Wenn Sie beispielsweise eine Union-Abfrage eingeben, kann die Anweisung ausgeführt, aber nicht in den anderen Bereichen dargestellt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
[Tools im Abfrage- und Sicht-Designer &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md)  
  
