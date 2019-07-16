---
title: Fehlermeldungen – Parallel Data Warehouse | Microsoft-Dokumentation
description: Parallel Data Warehouse (PDW)-Fehlermeldungen melden Fehler und Probleme auftreten, durch die PDW-Komponenten und können auch SQL Server-Fehler, die PDW zeigt enthalten. Diese Fehlermeldungen verwenden eine konsistente Syntax zur Darstellung von Informationen. Grundlegendes zu dieser Syntax können Sie zu identifizieren und Beheben von Problemen.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 78c5cd8dab37ac9cb32de794861c68e6c8085747
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960961"
---
# <a name="error-messages-in-parallel-data-warehouse"></a>Fehlermeldungen in Parallel Data Warehouse

Parallel Data Warehouse (PDW)-Fehlermeldungen melden Fehler und Probleme auftreten, durch die PDW-Komponenten und können auch SQL Server-Fehler, die PDW zeigt enthalten. Diese Fehlermeldungen verwenden eine konsistente Syntax zur Darstellung von Informationen. Grundlegendes zu dieser Syntax können Sie zu identifizieren und Beheben von Problemen auf SQL Server PDW.  
  
## <a name="Basics"></a>Grundlagen von Nachrichten Fehler  
Fehlermeldungen, die zurückgegeben werden, führen Sie die gleiche Syntax.  
  
`Error_Indicator [SQL_State_Code] [Driver_Details] [QueryID] Message_String`  
  
Dies sind die möglichen Werte für jedes Feld:  
  
|Feld|Beschreibung|Beispiel|  
|---------|---------------|-----------|  
|*Error_Indicator*|Das Wort "Fehler" oder anderer Text warnen der Benutzer auf ein Problem.|Fehler|  
|*SQL_State_Code*|Die SQL-Statuscode, gemäß ODBC-Spezifikation. Der Treiber generiert den entsprechenden Status des SQL-Code jedes Mal, wenn eine Meldung zu einer Anwendung zurückgegeben. Der Text "Microsoft" gibt die Quelle des Fehlers an.|42000|  
|*Driver_Details*|Treiberabhängig Details wie den Typ des verwendeten Treiber.|ODBC-SQL Server 2008 R2 Parallel Data Warehouse-Treiber|  
|*QueryID*|Der eindeutige Bezeichner für die Abfrage. Verwenden Sie diesen Wert zum Suchen zusätzlicher Informationen, die im Zusammenhang mit der Verarbeitung der Abfrage. Z. B. die Details der Ausführung der Abfrage in der Administratorkonsole finden Sie mithilfe der Abfrage-ID. Weitere Informationen finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole](monitor-the-appliance-by-using-the-admin-console.md).<br /><br />Ist eine "QueryId" nicht zutreffend, wird der Text "Intern" für den Benutzer zurückgegeben.|QID2377|  
|*Message_String*|Eine lesbare Beschreibung des Fehlers oder Problems. Beim SQL Server-Fehler zurückgeben, ist dies der Text der SQL Server-Nachricht.|Equal-Zuweisung kann in der festgelegten Liste einer UPDATE-Anweisung angezeigt werden.|  
  
Diese Beispielwerte würde dem Benutzer wie folgt angezeigt:  
  
`ERROR [42000] [Microsoft][ODBC SQL Server 2008 R2 Parallel Data Warehouse driver][QID2380]Only equal assignment can appear in the set list of an UPDATE statement.`  
  
## <a name="see-also"></a>Siehe auch  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Administratorkonsolenwarnungen](understanding-admin-console-alerts.md)  
  
