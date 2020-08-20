---
description: Testen von migrierten Datenbankobjekten (SybaseToSQL)
title: Testen von migrierten Datenbankobjekten (sybaseto SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4937f6b4-86bd-4070-88df-3d216306c33a
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: cfe57d436eac38052542eb2ed6c2133aab7ca07b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480396"
---
# <a name="testing-migrated-database-objects-sybasetosql"></a>Testen von migrierten Datenbankobjekten (SybaseToSQL)
Microsoft SQL Server Migration Assistant für Sybase Tester (SSMA Tester) testet automatisch die Datenbankobjekt Konvertierung und die von SSMA vorgenommene Daten Migration. Nachdem alle SSMA-Migrations Schritte abgeschlossen sind, überprüfen Sie mithilfe von SSMA Tester, ob konvertierte Objekte auf dieselbe Weise funktionieren und dass alle Daten ordnungsgemäß übertragen wurden.  
  
> [!NOTE]  
> Die Tester-Komponente ist im Fall von Azure-Konnektivität deaktiviert.  
  
Sie können die folgenden Objekttypen mit SSMA Tester testen:  
  
-   Tabellen  
  
-   Gespeicherte Prozeduren  
  
-   Ansichten.  
  
-   Eigenständige Anweisungen.  
  
SSMA Tester führt Objekte aus, die für das Testen auf Sybase und deren Entsprechungen in SQL Server ausgewählt wurden. Anschließend werden die Ergebnisse anhand der folgenden Kriterien verglichen:  
  
-   Sind die Änderungen in den Tabellendaten identisch?  
  
-   Sind die Werte der Ausgabeparameter für Prozeduren und Funktionen identisch?  
  
-   Gibt Functions dieselben Ergebnisse zurück?  
  
-   Sind die Resultsets identisch?  
  
> [!NOTE]  
> Achtung! Verwenden Sie SSMA Tester niemals auf Produktionssystemen. Während der Tester-Ausführung werden das Quell Schema und die Daten geändert. In der Zwischenzeit ist die Wiederherstellung des ursprünglichen Zustands für einige Typen von getestetem Code möglicherweise nicht möglich.  
  
## <a name="prerequisites"></a>Voraussetzungen  
Wenn Sie SSMA Tester verwenden möchten, installieren Sie SSMA Sybase Extension Pack mit aktivierter Option **Tester-Datenbank installieren** .  
  
Überprüfen Sie außerdem Folgendes:  
  
-   Sybase-OLE DB Anbieter wird auf dem Computer installiert, auf dem ausgeführt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Die CLR-Integration (Common Language Runtime) wurde auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Engine aktiviert.  
  
Beachten Sie, dass die aktuelle Version von SSMA Tester die parallele Ausführung durch andere Benutzer auf demselben Quell-oder Zielserver nicht unterstützt.  
  
## <a name="getting-started"></a>Erste Schritte  
[Erstellen von Test Fällen &#40;sybaseto SQL-&#41;](../../ssma/sybase/creating-test-cases-sybasetosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA-Komponenten auf SQL Server &#40;sybasedesql-&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Projekteinstellungen &#40;Konvertierung&#41; &#40;sybasedesql-&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
