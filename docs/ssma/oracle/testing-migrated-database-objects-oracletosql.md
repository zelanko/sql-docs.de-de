---
title: Testen der Datenbankobjekte (OracleToSQL) migriert | Microsoft-Dokumentation
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
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266478"
---
# <a name="testing-migrated-database-objects-oracletosql"></a>Testen migrierter Datenbankobjekte (OracleToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant für Oracle-Tester (SSMA Tester) überprüft automatisch die Konvertierung der Datenbank-Objekt und die Datenmigration von SSMA vorgenommen. Können Sie SSMA-Tester, nachdem alle Schritte zur Datenmigration SSMA abgeschlossen sind, stellen Sie sicher, dass die konvertierten Objekte die gleiche Weise funktioniert und alle Daten ordnungsgemäß übertragen wurde.  
  
Sie können die folgenden Objekttypen mit SSMA-Tester testen:  
  
-   Tabellen  
  
-   Gespeicherte Prozeduren, einschließlich der verpackte Prozeduren.  
  
-   Benutzerdefinierte Funktionen, einschließlich Paketfunktionen.  
  
-   Ansichten.  
  
-   Eigenständige Anweisungen.  
  
SSMA-Tester ausgeführt wird, für Tests auf Oracle und ihren äquivalenten in ausgewählte Objekten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Danach werden sie die Ergebnisse nach folgenden Kriterien verglichen:  
  
-   Befinden sich die Änderungen in Tabelle identisch?  
  
-   Sind die Werte von Ausgabeparametern für Prozeduren und Funktionen identisch?  
  
-   Führen Sie Funktionen, die die gleichen Ergebnisse zurück?  
  
-   Sind Sie, dass die Resultsets identisch?  
  
> [!NOTE]  
> Achtung! Verwenden Sie niemals SSMA Tester auf die Produktionssysteme statt. Während der Ausführung der Tester werden dem Quellschema und die Daten geändert. In der Zwischenzeit kann das vollständige Wiederherstellen des ursprünglichen Zustands für einige Typen von getesteten Codes unmöglich sein.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
Wenn Sie SSMA Tester verwenden möchten, installieren Sie SSMA-Oracle-Erweiterungspaket mit der **Tester-Datenbank installieren** Option auf ON festgelegt.  
  
Um den Vergleich der resultierenden Tabellendaten zu ermöglichen, legen Sie die **generieren ROWID-Spalte** option **Ja** vor Beginn die schemakonvertierung. SSMA wird für alle Tabellen eine ROWID-Spalte hinzufügen, während der Ausführung der **Schema konvertieren** Befehl.  
  
Darüber hinaus überprüfen Sie Folgendes aus:  
  
-   Oracle-Clienttools auf dem Computer installiert sind, in denen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.  
  
-   Integration der Common Language Runtime (CLR) aktiviert wurde die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Engine.  
  
Beachten Sie, dass die aktuelle Version der SSMA-Tester die parallelen Ausführung von verschiedenen Benutzern auf der gleichen Quelle oder Ziel-Server nicht unterstützt.  
  
## <a name="getting-started"></a>Erste Schritte  
[Erstellen von Testfällen &#40;OracleToSQL&#41;](../../ssma/oracle/creating-test-cases-oracletosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA-Komponenten auf SQLServer &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[Projekteinstellungen &#40;Konvertierung&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md)  
  
