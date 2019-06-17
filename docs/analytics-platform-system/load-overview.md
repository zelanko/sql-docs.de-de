---
title: Laden von Daten in Parallel Data Warehouse | Microsoft-Dokumentation
description: Laden oder Einfügen von Daten in SQL Server Parallel Data Warehouse (PDW) mit Integration Services "," Hilfsprogramm "Bcp" "," Dwloader "oder" SQL INSERT-Anweisung.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f4551f77b1348ece34dc87dc8abeb91e27290d00
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63183482"
---
# <a name="loading-data-into-parallel-data-warehouse"></a>Laden von Daten in Parallel Data Warehouse
Laden oder Einfügen von Daten in SQL Server Parallel Data Warehouse (PDW) mit Integration Services, [Hilfsprogramm "Bcp"](../tools/bcp-utility.md), **Dwloader** Command-Line-Loader oder die SQL-INSERT-Anweisung.  

## <a name="loading-environment"></a>Umgebung wird geladen  
Um Daten zu laden, benötigen Sie eine oder mehrere beim Laden von Servern. Können Sie Ihre eigenen vorhandenen ETL- oder anderen Servern, oder Sie können neue Server erwerben. Weitere Informationen finden Sie unter [abrufen und Konfigurieren eines Servers geladen](acquire-and-configure-loading-server.md). Diese Anweisungen beinhalten eine [Laden von Server-Kapazität Planungsarbeitsblatt](loading-server-capacity-planning-worksheet.md) helfen Ihnen beim Planen der richtigen Lösung für das Laden.  
  
## <a name="load-with-dwloader"></a>Laden mit dwloader  
Mithilfe der [Dwloader Command-Line-Ladeprogramm](dwloader.md) ist die schnellste Möglichkeit zum Laden von Daten in PDW.  
  
![Prozess des Ladens](media/loading-process.png "Prozess des Ladens")  
  
Dwloader lädt die Daten direkt an den Compute-Knoten ohne Weiterleitung der Daten durch den Steuerelementknoten aus. Zum Laden von Daten kommuniziert die Dwloader zunächst mit den Steuerelementknoten aus, um Kontaktinformationen für den Compute-Knoten zu erhalten. Dwloader richtet einen Kommunikationskanal mit jeder Compute-Knoten und sendet dann die 256-KB-Segmenten der Daten, auf den Computeknoten, auf eine Roundrobin-Weise.  
  
Auf jedem Computeknoten (Data Movement Service, DMS) empfängt und verarbeitet die Datenblöcke. Verarbeitung der Daten enthält jede Zeile in der systemeigenen SQL Server-Format konvertieren und Errechnen des Hashs Verteilung, um den Compute-Knoten zu ermitteln, zu dem jede Zeile gehört.  
  
Nach der Verarbeitung von Zeilen, verwendet DMS eine Verschiebung mit Vermischung, um jede Zeile in den richtigen Compute-Knoten und die Instanz von SQL Server zu übertragen. Wie SQL Server die Zeilen empfängt, als batches werden gemäß der **-b** batchgrößenparameter Dwloader setzen und Bulk lädt dann den Batch.  

## <a name="load-with-prepared-statements"></a>Laden mit vorbereiteten Anweisungen

Vorbereitete Anweisungen können zum Laden von Daten in verteilten und replizierten Tabellen. Wenn die Eingabedaten nicht den Zieldatentyp übereinstimmt, wird eine implizite Konvertierung ausgeführt. Die impliziten Konvertierungen von vorbereiteten Anweisungen PDW unterstützt sind eine Teilmenge von Konvertierungen, die von SQL Server unterstützt. D. h. nur eine Teilmenge der Konvertierungen werden unterstützt, aber die unterstützten Konvertierungen entsprechen der implizite Konvertierungen von SQL Server. Unabhängig davon, ob die Zieltabelle geladen werden als verteilte oder replizierte Tabelle definiert ist sind implizite Konvertierungen (falls erforderlich) auf alle Spalten angewendet, die in der Zieltabelle vorhanden sind. 

<!-- MISSING LINK
For more information, see [Prepared statements](prepared-statements.md).
-->
  
## <a name="related-tasks"></a>Related Tasks  
  
|Aufgabe|Beschreibung|  
|--------|---------------|  
|Erstellen Sie die staging-Datenbank.|[Erstellen der Stagingdatenbank](staging-database.md)|  
|Laden Sie mit Integrationsservices.|[Laden mit Integration Services](load-with-ssis.md)|  
|Erfahren Sie, die typkonvertierungen für Dwloader.|[Regeln für das Konvertieren von Datentypen für dwloader](dwloader-data-type-conversion-rules.md)|  
|Laden von Daten mit Dwloader.|[Dwloader Command-Line-Ladeprogramm](dwloader.md)|  
|Erfahren Sie, die typkonvertierungen für das Einfügen.|[Laden von Daten mit SSIS](load-with-insert.md)|  
 
<!-- MISSING LINKS
## See Also  
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Common metadata query examles](metadata-query-examples.md)  
  
-->
