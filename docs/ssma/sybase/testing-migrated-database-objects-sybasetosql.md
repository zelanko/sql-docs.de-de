---
title: Testen von migrierten Datenbankobjekten (SybaseToSQL) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020916"
---
# <a name="testing-migrated-database-objects-sybasetosql"></a>Testen von migrierten Datenbankobjekten (SybaseToSQL)
Microsoft SQL Server Migration Assistant für Sybase-Tester (SSMA Tester) überprüft automatisch die Konvertierung der Datenbank-Objekt und die Datenmigration von SSMA vorgenommen. Können Sie SSMA-Tester, nachdem alle Schritte zur Datenmigration SSMA abgeschlossen sind, stellen Sie sicher, dass die konvertierten Objekte die gleiche Weise funktioniert und alle Daten ordnungsgemäß übertragen wurde.  
  
> [!NOTE]  
> Tester-Komponente ist im Fall von Azure-Verbindung deaktiviert.  
  
Sie können die folgenden Objekttypen mit SSMA-Tester testen:  
  
-   Tabellen  
  
-   Gespeicherte Prozeduren  
  
-   Ansichten.  
  
-   Eigenständige Anweisungen.  
  
SSMA-Tester führt Tests auf Sybase und ihren äquivalenten in SQL Server für den ausgewählten Objekte. Danach werden sie die Ergebnisse nach folgenden Kriterien verglichen:  
  
-   Befinden sich die Änderungen in Tabelle identisch?  
  
-   Sind die Werte von Ausgabeparametern für Prozeduren und Funktionen identisch?  
  
-   Führen Sie Funktionen, die die gleichen Ergebnisse zurück?  
  
-   Sind Sie, dass die Resultsets identisch?  
  
> [!NOTE]  
> Achtung! Verwenden Sie niemals SSMA Tester auf die Produktionssysteme statt. Während der Ausführung der Tester werden dem Quellschema und die Daten geändert. In der Zwischenzeit kann das vollständige Wiederherstellen des ursprünglichen Zustands für einige Typen von getesteten Codes unmöglich sein.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
Wenn Sie SSMA Tester verwenden möchten, installieren Sie SSMA Sybase-Erweiterungspaket mit der **Tester-Datenbank installieren** Option auf ON festgelegt.  
  
Darüber hinaus überprüfen Sie Folgendes aus:  
  
-   Sybase-OLE DB-Anbieter auf dem Computer installiert ist, in denen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.  
  
-   Integration der Common Language Runtime (CLR) aktiviert wurde die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Engine.  
  
Beachten Sie, dass die aktuelle Version der SSMA-Tester die parallelen Ausführung von verschiedenen Benutzern auf der gleichen Quelle oder Ziel-Server nicht unterstützt.  
  
## <a name="getting-started"></a>Erste Schritte  
[Erstellen von Testfällen &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-test-cases-sybasetosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA-Komponenten auf SQLServer &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Projekteinstellungen &#40;Konvertierung&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
