---
title: Fehlermeldungen
description: Parallele Data Warehouse (PDW)-Fehlermeldungen melden Fehler und Probleme, die in den PDW-Komponenten aufgetreten sind, und können auch SQL Server Fehler enthalten, die über PDW ausgegeben werden. In diesen Fehlermeldungen wird eine konsistente Syntax zum Darstellen von Informationen verwendet. Wenn Sie diese Syntax verstanden haben, können Sie Probleme identifizieren und beheben.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 2d89e80a89df53e85ef8d2bf53c369d9e4dc0d49
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401166"
---
# <a name="error-messages-in-parallel-data-warehouse"></a>Fehlermeldungen parallel Data Warehouse

Parallele Data Warehouse (PDW)-Fehlermeldungen melden Fehler und Probleme, die in den PDW-Komponenten aufgetreten sind, und können auch SQL Server Fehler enthalten, die über PDW ausgegeben werden. In diesen Fehlermeldungen wird eine konsistente Syntax zum Darstellen von Informationen verwendet. Wenn Sie diese Syntax verstanden haben, können Sie Probleme auf SQL Server PDW identifizieren und beheben.  
  
## <a name="error-message-basics"></a><a name="Basics"></a>Grundlagen zu Fehlermeldungen  
Fehlermeldungen, die zurückgegeben werden, folgen derselben Syntax.  
  
`Error_Indicator [SQL_State_Code] [Driver_Details] [QueryID] Message_String`  
  
Dies sind die möglichen Werte für jedes Feld:  
  
|Feld|BESCHREIBUNG|Beispiel|  
|---------|---------------|-----------|  
|*Error_Indicator*|Das Wort "Error" oder ein anderer Text, der den Benutzer auf ein Problem hinweist.|ERROR|  
|*SQL_State_Code*|Der SQL-Statuscode gemäß der ODBC-Spezifikation. Der Treiber generiert den entsprechenden SQL-Statuscode jedes Mal, wenn er eine Nachricht an eine Anwendung zurückgibt. Der Text "Microsoft" gibt die Quelle des Fehlers an.|42000|  
|*Driver_Details*|Treiber abhängige Details, z. b. der Typ des verwendeten Treibers.|ODBC-SQL Server 2008 R2 parallel Data Warehouse-Treiber|  
|*QueryID*|Der eindeutige Bezeichner für die Abfrage. Verwenden Sie diesen Wert, um zusätzliche Informationen im Zusammenhang mit der Verarbeitung der Abfrage zu suchen. Beispielsweise können Sie die Details der Abfrage Ausführung in der-Verwaltungskonsole mithilfe der Abfrage-ID finden. Weitere Informationen finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole](monitor-the-appliance-by-using-the-admin-console.md).<br /><br />Wenn eine QueryId nicht anwendbar ist, wird der Text "Internal" an den Benutzer zurückgegeben.|QID2377|  
|*Message_String*|Eine lesbare Beschreibung des Fehlers oder Problems. Wenn SQL Server Fehler zurückgegeben werden, handelt es sich hierbei um den SQL Server Meldungs Text.|In der Set-Liste einer Update-Anweisung kann nur eine gleichmäßige Zuweisung enthalten sein.|  
  
Diese Beispiel Werte würden dem Benutzer wie folgt angezeigt werden:  
  
`ERROR [42000] [Microsoft][ODBC SQL Server 2008 R2 Parallel Data Warehouse driver][QID2380]Only equal assignment can appear in the set list of an UPDATE statement.`  
  
## <a name="see-also"></a>Weitere Informationen  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Grundlegendes zu Warnungen der Administrator Konsole](understanding-admin-console-alerts.md)  
  
