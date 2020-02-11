---
title: Testen von migrierten Datenbankobjekten (oracleto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f03ef5e1-66e6-4c84-ada2-252dd5ada82f
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 858c564c965fe7105c86a3087923887097e4ddac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68266478"
---
# <a name="testing-migrated-database-objects-oracletosql"></a>Testen migrierter Datenbankobjekte (OracleToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant für Oracle Tester (SSMA Tester) testet automatisch die Datenbankobjekt Konvertierung und die von SSMA vorgenommene Datenmigration. Nachdem alle SSMA-Migrations Schritte abgeschlossen sind, überprüfen Sie mithilfe von SSMA Tester, ob konvertierte Objekte auf dieselbe Weise funktionieren und dass alle Daten ordnungsgemäß übertragen wurden.  
  
Sie können die folgenden Objekttypen mit SSMA Tester testen:  
  
-   Tabellen  
  
-   Gespeicherte Prozeduren, einschließlich paketierten Prozeduren.  
  
-   Benutzerdefinierte Funktionen, einschließlich paketierten Funktionen.  
  
-   Ansichten.  
  
-   Eigenständige Anweisungen.  
  
SSMA Tester führt Objekte aus, die für das Testen in Oracle und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]deren Entsprechungen in ausgewählt wurden. Anschließend werden die Ergebnisse anhand der folgenden Kriterien verglichen:  
  
-   Sind die Änderungen in den Tabellendaten identisch?  
  
-   Sind die Werte der Ausgabeparameter für Prozeduren und Funktionen identisch?  
  
-   Gibt Functions dieselben Ergebnisse zurück?  
  
-   Sind die Resultsets identisch?  
  
> [!NOTE]  
> Hingewiesen! Verwenden Sie SSMA Tester niemals auf Produktionssystemen. Während der Tester-Ausführung werden das Quell Schema und die Daten geändert. In der Zwischenzeit ist die Wiederherstellung des ursprünglichen Zustands für einige Typen von getestetem Code möglicherweise nicht möglich.  
  
## <a name="prerequisites"></a>Voraussetzungen  
Wenn Sie SSMA Tester verwenden möchten, installieren Sie SSMA Oracle Extension Pack mit aktivierter Option **Tester-Datenbank installieren** .  
  
Um den Vergleich der resultierenden Tabellendaten zu ermöglichen, legen Sie die Option **ROWID-Spalte generieren** vor dem Beginn der Schema Konvertierung auf **Yes** fest. SSMA fügt allen Tabellen während der Ausführung des Befehls " **Schema konvertieren** " eine ROWID-Spalte hinzu.  
  
Überprüfen Sie außerdem Folgendes:  
  
-   Oracle-Client Tools werden auf dem Computer installiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , auf dem ausgeführt wird.  
  
-   Die CLR-Integration (Common Language Runtime) wurde auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Engine aktiviert.  
  
Beachten Sie, dass die aktuelle Version von SSMA Tester die parallele Ausführung durch andere Benutzer auf demselben Quell-oder Zielserver nicht unterstützt.  
  
## <a name="getting-started"></a>Erste Schritte  
[Erstellen von Test Fällen &#40;oracleto SQL-&#41;](../../ssma/oracle/creating-test-cases-oracletosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA-Komponenten auf SQL Server &#40;oracledesql-&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[Projekteinstellungen &#40;Konvertierung&#41; &#40;oracleto SQL-&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md)  
  
