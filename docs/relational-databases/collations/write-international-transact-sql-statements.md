---
title: Schreiben internationaler Transact-SQL-Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- writing international statements
- Transact-SQL international considerations
- international considerations [SQL Server], Transact-SQL
- Database Engine international considerations [SQL Server], Transact-SQL
- statements [SQL Server], international
- database international considerations [SQL Server], Transact-SQL
- dates [SQL Server], international considerations
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4eb6cf7d397bc8fdc8ab37d17e830ad2b373882e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140815"
---
# <a name="write-international-transact-sql-statements"></a>Schreiben internationaler Transact-SQL-Anweisungen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Datenbanken und Datenbankanwendungen, die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen verwenden, können leichter von einer Sprache in eine andere übertragen werden bzw. unterstützen mehrere Sprachen, wenn die folgenden Richtlinien eingehalten werden:  

-   Wenn Sie mit [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] beginnen, verwenden Sie eher Folgendes:
    -   Die Datentypen **char**,**varchar** und **varchar(max)** mit [UTF-8-fähiger Sortierung](../../relational-databases/collations/collation-and-unicode-support.md#utf8).
    -   Die Datentypen **nchar**,**nvarchar** und **nvarchar(max)** mit [Sortierung ergänzender Zeichen](../../relational-databases/collations/collation-and-unicode-support.md#Supplementary_Characters).      

    Auf diese Weise werden Probleme mit der Codepagekonvertierung vermieden. Weitere Überlegungen finden Sie unter [Speicherunterschiede zwischen UTF-8 und UTF-16](../../relational-databases/collations/collation-and-unicode-support.md#storage_differences).  

-   Ersetzen Sie bis [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] die Datentypen **char**, **varchar** und **varchar(max)** durch **nchar**, **nvarchar** und **nvarchar(max)** . Auf diese Weise werden Probleme mit der Codepagekonvertierung vermieden. Weitere Informationen finden Sie unter [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md). 
    > [!IMPORTANT]
    > Der Datentyp **text** ist veraltet und sollte beim Entwickeln nicht verwendet werden. Konvertieren Sie **text**-Daten in **varchar(max)** .
  
-   Verwenden Sie für Vergleiche und Vorgänge für bestimmte Monate oder Wochentage die numerischen Datumseinheiten anstelle der Namenszeichenfolgen. Unterschiedliche Spracheinstellungen geben verschiedene Namen für Monate und Arbeitstage zurück. `DATENAME(MONTH,GETDATE())` gibt beispielsweise `May` zurück, wenn die Sprache auf Englisch, `Mai`, wenn die Sprache auf Deutsch und `mai`, wenn die Sprache auf Französisch festgelegt ist. Verwenden Sie stattdessen eine Funktion wie [DATEPART](../../t-sql/functions/datepart-transact-sql.md), die die Monatszahl anstelle des Namens verwendet. Verwenden Sie DATEPART-Namen, wenn Sie Resultsets erstellen, die für einen Benutzer angezeigt werden sollen, da Datumsbezeichnungen häufig aussagekräftiger sind als eine numerische Darstellung. Codieren Sie jedoch keine Logik, die davon abhängt, ob die angezeigten Namen aus einer bestimmten Programmiersprache stammen.  
  
-   Wenn Sie Datumseingaben in Vergleichen oder als Eingabe in INSERT- oder UPDATE-Anweisungen angeben, verwenden Sie Konstanten, die in allen Spracheinstellungen gleich interpretiert werden:  
  
    -   ADO-, OLE DB- und ODBC-Anwendungen sollten folgende ODBC-Timestamps und folgende ESCAPE-Klauseln für Datum und Zeit verwenden:  
  
         **{ ts'** _yyyy_ **-** _mm_ **-** _dd_ _hh_ **:** _mm_ **:** _ss_ [ **.** _fff_] **'}** Beispiel: **{ ts'1998-09-24 10:02:20'}**  
  
         **{ d'** _yyyy_ **-** _mm_ **-** _dd_ **'}** Beispiel: **{ d'1998-09-24'}**
  
         **{ t'** _hh_ **:** _mm_ **:** _ss_ **'}** Beispiel: **{ t'10:02:20'}**  
  
    -   Anwendungen, die andere APIs verwenden, oder [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts, gespeicherte Prozedure und Trigger sollten unstrukturierte Zeichenfolgen verwenden. Zum Beispiel *yyyymmdd* für 19980924.  
  
    -   Anwendungen, die andere APIs oder [!INCLUDE[tsql](../../includes/tsql-md.md)]-Skripts, gespeicherte Prozeduren und Trigger verwenden, sollten die [CONVERT](../../t-sql/functions/cast-and-convert-transact-sql.md)-Anweisung mit dem expliziten Parameter „style“ für alle Konvertierungen zwischen den Datentypen **time**, **date**, **smalldate**, **datetime**, **datetime2** und **datetimeoffset** sowie Zeichenfolgen-Datentypen verwenden. Die folgende Anweisung wird beispielsweise für alle Verbindungseinstellungen für Sprach- oder Datumsformate gleich interpretiert:  
  
        ```sql  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
## <a name="see-also"></a>Siehe auch
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)     
[DATEPART &#40;Transact-SQL&#41;](../../t-sql/functions/datepart-transact-sql.md)        
[Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)      
