---
title: MSSQLSERVER_1505 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 1505 (Database Engine error)
ms.assetid: ef4df75d-0f36-4c8b-b36c-e427f65f91ca
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fb8dea2a6e5b768dd0fc11aa49cd8dc73fe4f9bc
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver1505"></a>MSSQLSERVER_1505
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1505|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DUP_KEY|  
|Meldungstext|Die CREATE UNIQUE INDEX-Anweisung wurde beendet, weil ein doppelter Schlüssel für den Objektnamen '%.*ls' und den Indexnamen '%.\*ls' gefunden wurde.  Der doppelte Schlüsselwert ist %ls.|  
  
## <a name="explanation"></a>Erklärung  
Dieser Fehler tritt auf, wenn Sie versuchen, einen eindeutigen Index zu erstellen, und der angegebene doppelte Wert in mehreren Zeilen in der Tabelle enthalten ist. Ein eindeutiger Index wird erstellt, wenn Sie einen Index erstellen und das UNIQUE-Schlüsselwort angeben oder wenn Sie eine UNIQUE-Einschränkung erstellen. Die Tabelle darf keine Zeilen mit doppelten Werten in den Spalten enthalten, die im Index oder in der Einschränkung definiert sind.  
  
Nehmen Sie als Beispiel die Daten aus der folgenden **Employee**-Tabelle:  
  
|LastName|FirstName|JobTitle|HireDate|  
|------------|-------------|------------|------------|  
|Walters|Rob|Senior Tool Designer|2004-11-19|  
|Brown|Kevin|Marketing Assistant|NULL|  
|Brown|Jo|Design Engineer|NULL|  
|Walters|Rob|Tool Designer|2001-08-09|  
  
Für die Spaltenkombinationen **LastName** oder **LastName**, **FirstName** kann aufgrund doppelter Werte in den Zeilen kein eindeutiger Index erstellt werden.  
  
Schwieriger zu erkennen ist der Verstoß gegen die Eindeutigkeit in der Spalte **HireDate**. Beim Erstellen von Indizes werden NULL-Werte als "gleich" betrachtet. Daher können Sie keinen eindeutigen Index bzw. keine eindeutige Einschränkung erstellen, wenn die Schlüsselwerte mehrerer Zeilen NULL-Werte enthalten. Mit den oben genannten Daten kann für die Spaltenkombinationen **HireDate** oder **LastName**, **HireDate** kein eindeutiger Index erstellt werden.  
  
Fehlermeldung 1505 gibt die erste Zeile zurück, in der ein Verstoß gegen die Eindeutigkeitseinschränkung vorliegt. Es gibt möglicherweise weitere doppelte Zeilen in der Tabelle. Führen Sie zum Ermitteln aller doppelten Zeilen eine Abfrage der angegebenen Tabelle mit der GROUP BY-Klausel und der HAVING-Klausel aus, um die doppelten Zeilen zu melden. Mit folgender Abfrage werden beispielsweise die Zeilen aus der **Employee**-Tabelle zurückgegeben, die doppelte Vor- und Nachnamen aufweisen.  
  
SELECT LastName, FirstName, count(*) FROM dbo.Employee GROUP BY LastName, FirstName HAVING count(\*) > 1;  
  
## <a name="user-action"></a>Benutzeraktion  
Ziehen Sie die folgenden Lösungen in Betracht:  
  
-   Fügen Sie der Index- oder Einschränkungsdefinition Spalten hinzu, oder entfernen Sie Spalten, um eine eindeutige Zusammensetzung zu erstellen. Im vorhergehenden Beispiel könnte das Problem gelöst werden, indem Sie der Index- oder Einschränkungsdefinition eine **MiddleName**-Spalte hinzufügen.  
  
-   Wählen Sie die als NOT NULL definierten Spalten aus, wenn Sie die Spalten für einen eindeutigen Index bzw. eine eindeutige Einschränkung auswählen. Damit können Sie die Möglichkeit eines Verstoßes gegen die Eindeutigkeit vermeiden, wenn die Schlüsselwerte mehrerer Zeilen NULL-Werte enthalten.  
  
-   Wenn die doppelten Werte durch Dateneingabefehler entstanden sind, korrigieren Sie die Daten manuell, und erstellen Sie dann den Index bzw. die Einschränkung. Informationen zum Entfernen von doppelten Zeilen aus einer Tabelle finden Sie im Knowledge Base-Artikel 139444: [Entfernen von doppelten Zeilen aus einer Tabelle in SQL Server](http://support.microsoft.com/kb/139444).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[CREATE INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/create-index-transact-sql.md)  
[Erstellen eindeutiger Indizes](~/relational-databases/indexes/create-unique-indexes.md)  
[Erstellen von Unique-Einschränkungen](~/relational-databases/tables/create-unique-constraints.md)  
  
