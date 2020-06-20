---
title: Angeben einer Quellabfrage (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.providesourcequery.f1
ms.assetid: c8cbd07e-b9c3-422f-94b8-d6fc8cf31cf5
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 6da28ac9897681d963325fcaf7712f5ed4d3d88b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965516"
---
# <a name="provide-a-source-query-sql-server-import-and-export-wizard"></a>Quellabfrage angeben (SQL Server-Import/Export-Assistent)
  Verwenden Sie die Seite **Quell Abfrage angeben** , um die SQL-Anweisung einzugeben, mit der die Daten generiert werden, die aus der Datenquelle in das Ziel kopiert werden sollen.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import/Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen für das Starten des Assistenten sowie zu den Berechtigungen, die zum erfolgreichen Ausführen des Assistenten erforderlich sind, finden Sie unter [Ausführen des SQL Server-Import/Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem SQL Server-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Tastatur  
 **SQL-Anweisung**  
 Geben Sie eine Abfrageanweisung ein, um die ausgewählten Datenzeilen aus der Quelldatenbank abzurufen. Die folgende Abfrageanweisung ruft z. B. die Daten **SalesPersonID**, **SalesQuota**und **SalesYTD** aus der AdventureWorks-Datenbank für Verkäufer ab, deren Kommissionsanteil größer als 1.5 Prozent ist.  
  
```  
SELECT SalesPersonID, SalesQuota, SalesYTD  
FROM Sales.SalesPerson  
WHERE CommissionPct > 0.015  
```  
  
 **Analysieren**  
 Überprüft die Syntax der SQL-Anweisung im Textfeld **SQL-Anweisung**.  
  
> [!NOTE]  
>  Wenn die für die Prüfung der Anweisungssyntax erforderliche Zeit den Timeoutwert von 30 Sekunden überschreitet, wird die Analyse beendet und ein Fehler ausgegeben. Sie können erst nach erfolgreicher Analyse über diese Seite des Assistenten hinaus gelangen. Eine Lösung besteht darin, eine Datenbanksicht basierend auf der Abfrage zu erstellen und die Sicht vom Assistenten abzufragen, statt den Abfragetext direkt einzugeben.  
  
 **Durchsuchen**  
 Wählen Sie mithilfe des Dialog Felds **Öffnen** eine Datei aus, die eine SQL-Anweisung enthält. Durch das Auswählen einer Datei wird der Test aus der Datei in das Textfeld **Abfrageanweisung** kopiert.  
  
  
