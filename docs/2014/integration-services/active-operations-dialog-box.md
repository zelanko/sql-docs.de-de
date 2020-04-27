---
title: Aktive Vorgänge (Dialog Feld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isoperations.executions.f1
- sql12.ssis.ssms.isoperations.general.f1
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f930a2e6f3ce84c330a4b7292ebaaba3b2ab871e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66062220"
---
# <a name="active-operations-dialog-box"></a>Aktive Vorgänge (Dialogfeld)
  Verwenden Sie das Dialogfeld **Aktive Vorgänge** , um den Status der derzeit ausgeführten [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Vorgänge auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server anzuzeigen, z. B. Bereitstellung, Überprüfung und Paketausführung. Diese Daten werden im SSISDB-Katalog gespeichert.  
  
 Weitere Informationen zu verwandten [!INCLUDE[tsql](../includes/tsql-md.md)]-Ansichten finden Sie unter [catalog.operations &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database), [catalog.validations &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-validations-ssisdb-database) und [catalog.executions &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database).  
  
 **Was möchten Sie tun?**  
  
1.  [Dialogfeld "Aktive Vorgänge" öffnen](#open_dialog)  
  
2.  [Konfigurieren der Optionen](#options)  
  
##  <a name="open-the-active-operations-dialog-box"></a><a name="open_dialog"></a>Dialog Feld "aktive Vorgänge" öffnen  
  
1.  Öffnen Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
2.  Stellen Sie eine Verbindung mit einer Microsoft SQL Server-Datenbank-Engine her.  
  
3.  Erweitern Sie im Objekt-Explorer den Knoten **Integration Services** , klicken Sie mit der rechten Maustaste auf den Knoten **SSISDB**, und klicken Sie dann auf **Aktive Vorgänge**.  
  
##  <a name="configure-the-options"></a><a name="options"></a>Konfigurieren der Optionen  
  
### <a name="options"></a>Optionen  
 **Typ**  
 Gibt den Vorgangstyp an. Im folgenden finden Sie die möglichen Werte für das **typanfeld** und die entsprechenden Werte in der operations_type-Spalte der Transact `catalog.operations` -SQL-Sicht.  
  
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
  
  
