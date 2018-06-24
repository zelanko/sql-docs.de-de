---
title: Aktive Vorgänge (Dialogfeld) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.ssms.isoperations.executions.f1
- sql12.ssis.ssms.isoperations.general.f1
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: adf25cd2194e1a02877c38a15d81d8697427ad76
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048097"
---
# <a name="active-operations-dialog-box"></a>Aktive Vorgänge (Dialogfeld)
  Verwenden Sie das Dialogfeld **Aktive Vorgänge** , um den Status der derzeit ausgeführten [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Vorgänge auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server anzuzeigen, z. B. Bereitstellung, Überprüfung und Paketausführung. Diese Daten werden im SSISDB-Katalog gespeichert.  
  
 Weitere Informationen zu verwandten [!INCLUDE[tsql](../includes/tsql-md.md)]-Ansichten finden Sie unter [catalog.operations &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database), [catalog.validations &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-validations-ssisdb-database) und [catalog.executions &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database).  
  
 **Was möchten Sie tun?**  
  
1.  [Öffnet das Dialogfeld "aktive Vorgänge"](#open_dialog)  
  
2.  [Konfigurieren der Optionen](#options)  
  
##  <a name="open_dialog"></a> Dialogfeld "Aktive Vorgänge" öffnen  
  
1.  Open [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
2.  Stellen Sie eine Verbindung mit einer Microsoft SQL Server-Datenbank-Engine her.  
  
3.  Erweitern Sie im Objekt-Explorer den Knoten **Integration Services** , klicken Sie mit der rechten Maustaste auf den Knoten **SSISDB**, und klicken Sie dann auf **Aktive Vorgänge**.  
  
##  <a name="options"></a> Konfigurieren der Optionen  
  
### <a name="options"></a>Tastatur  
 **Typ**  
 Gibt den Vorgangstyp an. Im folgenden sind die möglichen Werte für die **Typ** Feld und die entsprechenden Werte in der Operations_type-Spalte der Transact-SQL `catalog.operations` anzeigen.  
  
|||  
|-|-|  
|Initialisierung der Integration Services|1|  
|Vorgangsbereinigung (SQL Agent-Auftrag)|2|  
|Projektversions-Cleanup (SQL Agent-Auftrag)|3|  
|Projekt bereitstellen|101|  
|Projekt wiederherstellen|106|  
|Paketausführung erstellen und starten|200|  
|Vorgang beenden (Beenden einer Überprüfung oder Ausführung)|202|  
|Projekt überprüfen|300|  
|Paket überprüfen|301|  
|Katalog konfigurieren|1000|  
  
 **Beenden**  
 Klicken Sie, um einen gerade ausgeführten Vorgang zu beenden.  
  
  
