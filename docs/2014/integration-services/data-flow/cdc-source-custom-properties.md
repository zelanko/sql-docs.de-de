---
title: Benutzerdefinierte Eigenschaften der CDC-Quelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 744e9357-94a9-4202-abe8-1d3d202697e9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3c358e493a7e0c16207884754cd8008f60b17720
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163010"
---
# <a name="cdc-source-custom-properties"></a>Benutzerdefinierte Eigenschaften der CDC-Quelle
  In der folgenden Tabelle werden die benutzerdefinierten Eigenschaften der CDC-Quelle beschrieben. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|Description|  
|-------------------|---------------|-----------------|  
|Verbindung|ADO.NET-Verbindung|Eine ADO.NET-Verbindung zur [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -CDC-Datenbank für den Zugriff auf die Änderungstabellen.|  
|StateVariable|Zeichenfolge|Eine SSIS-Zeichenfolgenpaketvariable, mit der der CDC-Status der aktuellen CDC-Ausführung verwaltet wird.|  
|CdcProcessingMode|Ganze Zahl (Enumeration)|Dieser Modus bestimmt, wie die Verarbeitung behandelt wird. Die möglichen Optionen sind **All**, **All with old values**, **Net**, **Net with update mask**und **Net with merge**.<br /><br /> Für Modi, die mit All beginnen, werden alle Änderungen zurückgegeben, und für Modi, die mit Net beginnen, werden nur die Nettoänderungen zurückgegeben.<br /><br /> Tabellen ohne Primärschlüssel können nur ALL-Werte akzeptieren.<br /><br /> **Net with Update Mask** fügt boolesche Spalten mit dem Namensmuster **__$\<Spaltenname>\__Changed** hinzu, die auf geänderte Spalten in der aktuellen Änderungszeile hinweisen.<br /><br /> Weitere Informationen zu den Werten dieser Eigenschaft finden Sie unter [Quellen-Editor für CDC &#40;Seite Verbindungs-Manager&#41;](../cdc-source-editor-connection-manager-page.md).|  
|CaptureInstance|Zeichenfolge|Der Name der Aufzeichnungsinstanz mit der zu lesenden CDC-Tabelle. Eine aufgezeichnete Quelltabelle kann über eine oder zwei aufgezeichnete Instanzen zum Behandeln des nahtlosen Übergangs der Tabellendefinition mithilfe von Schemaänderungen verfügen. Wenn mehr als eine Aufzeichnungsinstanz für die aufzuzeichnende Quelltabelle definiert wird, müssen Sie hier die gewünschte Aufzeichnungsinstanz auswählen. Der Standardname einer Aufzeichnungsinstanz für eine Tabelle [Schema].[Tabelle] lautet \<Schema>_\<Tabelle>. Die tatsächlich verwendeten Namen der Aufzeichnungsinstanzen können jedoch abweichen. Die tatsächliche Tabelle, aus der gelesen wird, ist die CDC-Tabelle **cdc.\<Aufzeichnungsinstanz>_CT**.|  
|ReprocessingIndicator|Boolean|Ein Wert, der angibt, ob die Spalte **__$reprocessing** hinzugefügt werden soll. Beim Arbeiten am anfänglichen Verarbeitungsbereich können SSIS-Entwickler mithilfe dieser speziellen Ausgabespalte Konsistenzfehler auf alternative Weise behandeln.<br /><br /> Wenn **TRUE**gilt, wird die Spalte  **__$reprocessing** hinzugefügt.<br /><br /> Diese Spalte verfügt über den Wert **TRUE** , wenn sich der CDC-Verarbeitungsbereich mit dem ursprünglichen Verarbeitungsbereich überschneidet (der LSN-Bereich, der dem Zeitraum des erstmaligen Ladens entspricht) oder wenn ein CDC-Verarbeitungsbereich nach einem Fehler bei einer vorherigen Ausführung erneut verarbeitet wird. In dieser Indikatorspalte können SSIS-Entwickler Fehler unterschiedlich behandeln, wenn sie Änderungen erneut verarbeiten (z. B. können Aktionen, wie das Löschen einer nicht vorhandenen Zeile und ein fehlgeschlagener Einfügevorgang aufgrund eines doppelten Schlüssels, ignoriert werden).<br /><br /> Der Standardwert ist **false**.|  
|CommandTimeout|Integer|Dieser Wert gibt beim Kommunizieren mit der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Datenbank das Timeout (in Sekunden) an. Dieser Wert wird verwendet, wenn die Antwortzeit von der Datenbank sehr langsam ist und der Standardwert (30 Sekunden) nicht ausreicht.|  
  
 Weitere Informationen zur CDC-Quelle finden Sie unter [CDC Source](cdc-source.md).  
  
  
