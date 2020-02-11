---
title: Testen von migrierten Datenbankobjekten (sybaseto SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4937f6b4-86bd-4070-88df-3d216306c33a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 6fb469dfcaaec33a03681bfb64f411851df0400e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020916"
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
> Hingewiesen! Verwenden Sie SSMA Tester niemals auf Produktionssystemen. Während der Tester-Ausführung werden das Quell Schema und die Daten geändert. In der Zwischenzeit ist die Wiederherstellung des ursprünglichen Zustands für einige Typen von getestetem Code möglicherweise nicht möglich.  
  
## <a name="prerequisites"></a>Voraussetzungen  
Wenn Sie SSMA Tester verwenden möchten, installieren Sie SSMA Sybase Extension Pack mit aktivierter Option **Tester-Datenbank installieren** .  
  
Überprüfen Sie außerdem Folgendes:  
  
-   Sybase-OLE DB Anbieter wird auf dem Computer installiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , auf dem ausgeführt wird.  
  
-   Die CLR-Integration (Common Language Runtime) wurde auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Engine aktiviert.  
  
Beachten Sie, dass die aktuelle Version von SSMA Tester die parallele Ausführung durch andere Benutzer auf demselben Quell-oder Zielserver nicht unterstützt.  
  
## <a name="getting-started"></a>Erste Schritte  
[Erstellen von Test Fällen &#40;sybaseto SQL-&#41;](../../ssma/sybase/creating-test-cases-sybasetosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA-Komponenten auf SQL Server &#40;sybasedesql-&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Projekteinstellungen &#40;Konvertierung&#41; &#40;sybasedesql-&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
