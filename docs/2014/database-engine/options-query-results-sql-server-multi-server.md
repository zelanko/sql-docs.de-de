---
title: Optionen (Abfrageergebnisse – SQL Server-Multi-Abfrageserver) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqleditors.multiserverresultssettings
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLMultiServerResults
ms.assetid: d6768bd8-9cb5-4606-a726-a33a1df9e1bb
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 6019a328463d27b4495ae0db70e844eb4e05d747
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66089967"
---
# <a name="options-query-results-sql-server-multi-server"></a>Optionen (Abfrageergebnisse > SQL Server > Multiserver)
  Wenn Sie mehrere Server gleichzeitig abfragen, können Sie mit dieser Seite die Optionen für die Anzeige von Resultsets angeben. Die Option Ergebnisse zusammenführen kombiniert die Resultsets von allen Servern zu einem einzigen Resultset. Wenn Sie Ergebnisse zusammenführen, bestimmt der erste Server, der antwortet, das Schema für das Resultset. Um die Resultsets zusammenzuführen, muss die Abfrage dieselbe Anzahl von Spalten mit denselben Spaltennamen für jeden Server zurückgeben. Wenn Sie Ergebnisse zusammenführen, wird eine Meldung für jeden Server angezeigt, der dem durch den ersten antwortenden Server festgelegten Schema nicht entspricht (Spaltenanzahl und Spaltennamen).  
  
 Wenn Sie die Ergebnisse nicht zusammenführen, wird das Resultset von jedem Server in einem eigenen Raster mit einem eigenen Schema angezeigt.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Ergebnisse zusammenführen**  
 Aktivieren Sie dieses Kontrollkästchen, um die Resultsets von mehreren Servern im selben Raster zu kombinieren.  
  
 **Servername zu den Ergebnissen hinzufügen**  
 Aktivieren Sie dieses Kontrollkästchen, um eine zusätzliche Spalte einzuschließen, die den Namen des Servers bereitstellt, der jede Zeile erstellt hat.  
  
 **Anmeldename zu den Ergebnissen hinzufügen**  
 Aktivieren Sie dieses Kontrollkästchen, um eine zusätzliche Spalte einzuschließen, die den Benutzernamen enthält, der verwendet wurde, um die Verbindung zu dem Server herzustellen, der jede Zeile bereitgestellt hat.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen Sie einen zentralen Verwaltungsservers und einer Servergruppe &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)   
 [Gleichzeitiges Ausführen von Anweisungen für mehrere Server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/execute-statements-against-multiple-servers-simultaneously.md)  
  
  
