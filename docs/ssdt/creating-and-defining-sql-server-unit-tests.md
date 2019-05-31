---
title: Erstellen und Definieren von SQL Server-Komponententests | Microsoft-Dokumentation
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.unittesting.DatabaseMethodNameDialog
- sql.data.tools.unittesting.designer
ms.assetid: 3c082177-a2b1-4fde-8833-b49b2a351815
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ba48569633363dc7a1714bb036f40abcc0249160
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65099334"
---
# <a name="creating-and-defining-sql-server-unit-tests"></a>Erstellen und Definieren von SQL Server-Komponententests
Durch die Ausführung von SQL Server-Komponententests können Sie überprüfen, ob Änderungen an einem oder mehreren Datenbankobjekten in einem Schema dafür verantwortlich sind, dass vorhandene Funktionen einer Datenbankanwendung nicht mehr funktionieren. Diese Tests sind eine Ergänzung zu den Komponententests, die von den Softwareentwicklern erstellt werden. Um das Verhalten der Anwendung zu überprüfen, müssen Sie beide Arten von Tests ausführen.  
  
Sie können das Verhalten eines beliebigen Objekts im Schema überprüfen, indem Sie einen SQL Server-Komponententest sowie ein Transact\-SQL-Skript zum Testen dieses Objekts hinzufügen. Alternativ können Sie automatisch einen Stub eines Transact\-SQL-Skripts generieren, wenn Sie das Verhalten einer bestimmten Funktion oder gespeicherten Prozedur bzw. eines bestimmten Triggers überprüfen möchten. Nachdem Sie den Stub generiert haben, müssen Sie ihn anpassen, um aussagekräftige Ergebnisse zu erhalten.  
  
> [!NOTE]  
> Sie können einen leeren Test erstellen, diesem Code hinzufügen und den Test ausführen, ohne dass ein SQL Server-Datenbankprojekt geöffnet ist. Es ist jedoch nicht möglich, automatisch Transact\-SQL-Stubs zu generieren, durch die eine Funktion, ein Trigger oder eine gespeicherte Prozedur getestet wird, ohne dass das Projekt mit dem Testobjekt geöffnet ist.  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
Die folgende Tabelle enthält Beschreibungen allgemeiner Aufgaben, die dieses Szenario unterstützen. Außerdem finden Sie dort Links zu weiteren Informationen, wie Sie diese Aufgaben erfolgreich ausführen können.  
  
|Allgemeine Aufgaben|Hilfreiche Themen|  
|----------------|----------------------|  
|**Praktische Übungen:** Sie können eine allgemeine exemplarische Vorgehensweise durchlaufen, um sich mit der Erstellung und Ausführung eines einfachen SQL Server-Komponententests vertraut zu machen.|-   [Exemplarische Vorgehensweise: Erstellen und Ausführen eines SQL Server-Komponententests](../ssdt/walkthrough-creating-and-running-a-sql-server-unit-test.md)|  
|**Weitere Informationen zu SQL Server-Komponententests:** Weitere Informationen zu den Dateien und Skripts, aus denen ein SQL Server-Komponententest besteht. Sie erfahren außerdem mehr über die Verwendung von Testbedingungen und Transact\-SQL-Assertionen in Komponententests.|-   [Skripts in SQL Server-Komponententests](../ssdt/scripts-in-sql-server-unit-tests.md)<br />-   [SQL Server-Komponententestdateien](../ssdt/sql-server-unit-test-files.md)<br />-   [Verwenden von Testbedingungen in SQL Server-Komponententests](../ssdt/using-test-conditions-in-sql-server-unit-tests.md)<br />-   [Verwenden von Transact-SQL-Assertionen in SQL Server-Komponententests](../ssdt/using-transact-sql-assertions-in-sql-server-unit-tests.md)|  
|**Erstellen eines oder mehrerer Testprojekte:** Sie müssen SQL Server-Komponententests in einem Testprojekt erstellen. Wenn Sie einen SQL Server-Komponententest mit dem SQL Server-Objekt-Explorer erstellen, bevor Sie ein Testprojekt erstellen, wird automatisch ein Testprojekt für Sie erstellt. Sie können mehr als ein Testprojekt erstellen, z. B. wenn Sie in verschiedenen Testsätzen unterschiedliche Datengenerierungspläne oder Bereitstellungskonfigurationen verwenden möchten. Beim Erstellen des Testprojekts können Sie Testeinstellungen (z. B. die Verbindungszeichenfolge), Bereitstellungseinstellungen und einen Datengenerierungsplan für das Projekt konfigurieren.|-   [Vorgehensweise: Erstellen eines Testprojekts für SQL Server-Datenbankkomponententests](../ssdt/how-to-create-a-test-project-for-sql-server-database-unit-testing.md)<br />-|  
|**Konfigurieren, wie der Komponententest ausgeführt wird:** Sie können die Verbindungszeichenfolge für die Datenbank angeben, für die die Tests ausgeführt werden, sowie den Datengenerierungsplan und die Bereitstellungseinstellungen. Diese Einstellungen werden beim erstmaligen Hinzufügen eines SQL Server-Komponententests zum Projekt konfiguriert, können später jedoch auch geändert werden.|-   [Vorgehensweise: Konfigurieren der Ausführung von SQL Server-Komponententests](../ssdt/how-to-configure-sql-server-unit-test-execution.md)<br />-   [Übersicht über Verbindungszeichenfolgen und Berechtigungen](../ssdt/overview-of-connection-strings-and-permissions.md)|  
|**Erstellen eines SQL Server-Komponententests:** Sie können automatisch Transact\-SQL-Codestubs für SQL Server-Komponententests erstellen, durch die das Verhalten einer Funktion, eines Triggers oder einer gespeicherten Prozedur überprüft wird. Sie können auch einen leeren SQL Server-Komponententest erstellen und dann Transact\-SQL-Code hinzufügen, um weitere Typen von Datenbankobjekten zu testen.|-   [Vorgehensweise: Erstellen von SQL Server-Komponententests für Funktionen, Trigger und gespeicherte Prozeduren](../ssdt/how-to-create-unit-tests-for-functions-triggers-stored-procedures.md)<br />-   [Vorgehensweise: Erstellen eines leeren SQL Server-Komponententests](../ssdt/how-to-create-an-empty-sql-server-unit-test.md)|  
|**Schreiben von Code für einen SQL Server-Komponententest:** Nachdem Sie einen Komponententest erstellt haben, ändern oder schreiben Sie Transact\-SQL-Code zum Testen eines Datenbankobjekts. Für jeden Test definieren Sie mindestens eine Testbedingung, durch die ermittelt wird, ob der Test erfolgreich ist oder fehlschlägt. Bei komplexeren Tests können Sie den Visual Basic- oder Visual C\#-Code im Datenbankprojekt ändern. Beispielsweise können Sie einen Komponententest schreiben, der im Gültigkeitsbereich einer einzelnen Transaktion ausgeführt wird.|-   [Vorgehensweise: Öffnen eines SQL Server-Komponententests zur Bearbeitung](../ssdt/how-to-open-a-sql-server-unit-test-to-edit.md)<br />-   [Vorgehensweise: Hinzufügen von Testbedingungen zu SQL Server-Komponententests](../ssdt/how-to-add-test-conditions-to-sql-server-unit-tests.md)<br />-   [Vorgehensweise: Schreiben eines SQL Server-Komponententests, der im Gültigkeitsbereich einer einzelnen Transaktion ausgeführt wird](../ssdt/how-to-write-sql-server-unit-test-that-runs-in-single-transaction-scope.md)<br />-   [Tastenkombinationen für den SQL Server-Komponententest-Designer](../ssdt/keyboard-shortcuts-for-sql-server-unit-test-designer.md)|  
|**Behandeln von Problemen:** Erhalten Sie weitere Informationen darüber, wie allgemeine Probleme mit SQL Server behandelt werden.|-   [Behandeln von Problemen bei SQL Server-Datenbankkomponententests](../ssdt/troubleshooting-sql-server-database-unit-testing-issues.md)|  
  
## <a name="related-scenarios"></a>Verwandte Szenarien  
[Ausführen von SQL Server-Komponententests](../ssdt/running-sql-server-unit-tests.md)  
Nachdem Sie SQL Server-Komponententests erstellt haben, können Sie sie im Fenster „Testansicht“, im SQL Server-Komponententest-Designer oder über Team Foundation Build ausführen.  
  
[Szenario: Definieren benutzerdefinierter Testbedingungen für Datenbankkomponententests](https://msdn.microsoft.com/library/dd193282(VS.100).aspx)  
Sie können eine benutzerdefinierte Testbedingung erstellen, wenn Sie ein bestimmtes Verhalten testen möchten, das anhand von Standardtestbedingungen nicht überprüft werden kann.  
  
## <a name="see-also"></a>Weitere Informationen  
[Überprüfen des Datenbankcodes mithilfe von SQL Server-Komponententests](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)  
  
