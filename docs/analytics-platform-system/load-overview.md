---
title: Laden von Daten
description: Sie können Daten in SQL Server parallelen Data Warehouse (PDW) mithilfe Integration Services, bcp-Hilfsprogramms, dwloader oder der SQL INSERT-Anweisung laden oder einfügen.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: fd161820fd53d45642848697bce9589a98dec4ca
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401038"
---
# <a name="loading-data-into-parallel-data-warehouse"></a>Laden von Daten in parallele Data Warehouse
Sie können Daten mithilfe Integration Services, [bcp-Hilfsprogramms](../tools/bcp-utility.md), **"dwloader** -Befehlszeilen Lade Programm oder SQL INSERT-Anweisung in SQL Server parallele Data Warehouse (PDW) laden oder einfügen.  

## <a name="loading-environment"></a>Umgebung wird geladen  
Zum Laden von Daten benötigen Sie mindestens einen Lade Server. Sie können Ihre eigene vorhandene ETL-oder andere Server verwenden, oder Sie können neue Server erwerben. Weitere Informationen finden Sie unter [erwerben und Konfigurieren eines Lade Servers](acquire-and-configure-loading-server.md). Diese Anweisungen enthalten ein [Arbeitsblatt zum Planen der Server Kapazitätsplanung](loading-server-capacity-planning-worksheet.md) , mit dem Sie die richtige Lösung für das Laden planen können.  
  
## <a name="load-with-dwloader"></a>Mit "dwloader laden  
Die Verwendung des [Befehlszeilen Laders von "dwloader](dwloader.md) ist die schnellste Möglichkeit zum Laden von Daten in PDW.  
  
![Ladevorgang](media/loading-process.png "Ladevorgang")  
  
"dwloader lädt Daten direkt auf die Computeknoten, ohne die Daten über den Steuer Knoten zu übergeben. Zum Laden von Daten kommuniziert "dwloader zunächst mit dem Steuer Knoten, um Kontaktinformationen für die Computeknoten zu erhalten. "dwloader richtet einen Kommunikationskanal mit jedem Computeknoten ein und sendet dann mit einer Roundrobin-Methode 256 KB Datenblöcke an die Computeknoten.  
  
Auf jedem Computeknoten empfängt und verarbeitet der Daten Verschiebungs Dienst (Data Movement Service, DMS) die Datenblöcke. Die Verarbeitung der Daten umfasst das umrechnen der einzelnen Zeilen in SQL Server systemeigenen Format und das Berechnen des Verteilungs Hashwerts, um den Computeknoten zu ermitteln, zu dem die einzelnen Zeilen gehören.  
  
Nach der Verarbeitung der Zeilen verwendet DMS eine shuffle-Verschiebung, um jede Zeile auf den richtigen Computeknoten und die richtige Instanz von SQL Server zu übertragen. Wenn SQL Server die Zeilen empfängt, werden Sie gemäß dem in dwloader festgelegten Parameter für die Batch Größe **-b** Batches und dann Massen geladen.  

## <a name="load-with-prepared-statements"></a>Laden mit vorbereiteten Anweisungen

Sie können vorbereitete-Anweisungen verwenden, um Daten in verteilte und replizierte Tabellen zu laden. Wenn die Eingabedaten nicht mit dem Ziel Datentyp identisch sind, wird eine implizite Konvertierung durchgeführt. Die von PDW vorbereiteten Anweisungen unterstützten impliziten Konvertierungen sind eine Teilmenge der Konvertierungen, die von SQL Server unterstützt werden. Das heißt, es wird nur eine Teilmenge der Konvertierungen unterstützt, aber die unterstützten Konvertierungen Stimmen SQL Server impliziten Konvertierungen ab. Unabhängig davon, ob die zu ladende Ziel Tabelle als verteilte oder replizierte Tabelle definiert ist, werden implizite Konvertierungen (falls erforderlich) auf alle Spalten angewendet, die in der Ziel Tabelle vorhanden sind. 

<!-- MISSING LINK
For more information, see [Prepared statements](prepared-statements.md).
-->
  
## <a name="related-tasks"></a>Related Tasks  
  
|Aufgabe|BESCHREIBUNG|  
|--------|---------------|  
|Erstellen Sie die Stagingdatenbank.|[Erstellen der Stagingdatenbank](staging-database.md)|  
|Ladevorgang mit Integration Services.|[Laden mit Integration Services](load-with-ssis.md)|  
|Grundlegendes zu Typkonvertierungen für dwloader.|[Regeln für das Konvertieren von Datentypen für dwloader](dwloader-data-type-conversion-rules.md)|  
|Laden von Daten mit dwloader.|["dwloader-Befehlszeilen Lade Modul](dwloader.md)|  
|Grundlegendes zu Typkonvertierungen für INSERT.|[Laden von Daten mit SSIS](load-with-insert.md)|  
 
<!-- MISSING LINKS
## See Also  
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Common metadata query examles](metadata-query-examples.md)  
  
-->
