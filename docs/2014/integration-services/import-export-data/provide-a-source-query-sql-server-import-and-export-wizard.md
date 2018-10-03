---
title: Angeben einer Quellabfrage (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.providesourcequery.f1
ms.assetid: c8cbd07e-b9c3-422f-94b8-d6fc8cf31cf5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3abb49fa9e2e73ae5c610b5e940a6deba5079d62
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069860"
---
# <a name="provide-a-source-query-sql-server-import-and-export-wizard"></a>Quellabfrage angeben (SQL Server-Import/Export-Assistent)
  Verwenden der **Quellabfrage** Seite Geben Sie die SQL-Anweisung, die die zu kopierenden Daten aus der Datenquelle an das Ziel Daten generieren.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import / Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen zum Starten des Assistenten als auch die Berechtigungen erforderlich, um den Assistenten erfolgreich ausführen, finden Sie unter [führen Sie die SQL Server-Import / Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
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
 Wählen Sie eine Datei mit einer SQL-Anweisung mithilfe der **öffnen** Dialogfeld. Durch das Auswählen einer Datei wird der Test aus der Datei in das Textfeld **Abfrageanweisung** kopiert.  
  
  
