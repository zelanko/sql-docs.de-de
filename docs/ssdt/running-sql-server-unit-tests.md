---
title: Ausführen von SQL Server-Komponententests
description: In diesem Artikel erhalten Sie Informationen zu Komponententests in SQL Server. Außerdem finden Sie hier Ressourcen zum Erstellen von Tests, zum Erstellen von benutzerdefinierten Testbedingungen, zum Ausführen von Tests und zum Interpretieren von Ergebnissen.
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
f1_keywords:
- sql.data.tools.unittesting.testconfig
ms.assetid: febcc87f-eb18-4c12-ba30-82ef0d49aaa3
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: d27d25d374d737cc51f7e0a5149556a4d5a92260
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85883464"
---
# <a name="running-sql-server-unit-tests"></a>Ausführen von SQL Server-Komponententests

Um eine beständige und optimale Codequalität zu gewährleisten, können Sie SQL Server-Komponententests erstellen und ausführen, durch die das Verhalten von Datenbankobjekten überprüft wird, und die Tests anschließend in die Versionskontrolle einchecken. Nachdem das Datenbankschema von Ihnen oder einem der Teammitglieder geändert wurde, führen Sie sowohl SQL Server-Komponententests als auch Softwarekomponententests aus, um sicherzustellen, dass bestehende Funktionen durch die Änderungen nicht außer Kraft gesetzt wurden. Sie können Einzeltests oder Testgruppen ausführen, die als "Testlisten" bezeichnet werden. Weitere Informationen finden Sie unter [Verwenden von Testlisten (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182461(VS.100).aspx).  
  
## <a name="ways-to-run-sql-server-unit-tests"></a>Methoden zum Ausführen von SQL Server-Komponententests  
Sie können SQL Server-Komponententests auf unterschiedliche Weisen wie folgt ausführen (je nach installierter Software):  
  
-   Ausführen von Tests mit dem Visual Studio 2010-Fenster **Testansicht**. Weitere Informationen finden Sie unter [Vorgehensweise: Ausführen von SQL Server-Komponententests](../ssdt/how-to-run-sql-server-unit-tests.md) und [Vorgehensweise: Ausführen von automatisierten Tests in Microsoft Visual Studio 2010](https://msdn.microsoft.com/library/ms182470(VS.100).aspx). Informationen zu Visual Studio 2012 finden Sie unter [Vorgehensweise: Ausführen von automatisierten Tests in Microsoft Visual Studio 2012](https://msdn.microsoft.com/library/ms182470.aspx).  
  
-   Ausführen von Tests mit dem Befehl "MSTest.exe" über eine Eingabeaufforderung. Weitere Informationen finden Sie unter [Gewusst wie: Ausführen von automatisierten Tests über die Befehlszeile mit MSTest (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182487(VS.100).aspx) oder [Gewusst wie: Ausführen von automatisierten Tests über die Befehlszeile mit MSTest (Visual Studio 2012)](https://msdn.microsoft.com/library/ms182487.aspx).  
  
-   Ausführen von Tests über den **Projektmappen-Explorer** mithilfe eines Testprojekts. Weitere Informationen finden Sie unter [Gewusst wie: Ausführen von automatisierten Tests von Microsoft Visual Studio 2010](https://msdn.microsoft.com/library/ms182470(VS.100).aspx) oder [Gewusst wie: Ausführen von automatisierten Tests von Microsoft Visual Studio 2012](https://msdn.microsoft.com/library/ms182470.aspx).  
  
-   Erneutes Ausführen von Tests über das Fenster **Testergebnisse**. Weitere Informationen finden Sie unter [Vorgehensweise: Erneutes Ausführen eines Tests (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182472(VS.100).aspx).  
  
-   Ausführen von Einzeltests oder Testlisten (Visual Studio 2010) über das Fenster **Testlisten-Editor**. Weitere Informationen finden Sie unter [Gewusst wie: Ausführen von automatisierten Tests von Microsoft Visual Studio 2010](https://msdn.microsoft.com/library/ms182470(VS.100).aspx) oder [Gewusst wie: Ausführen von automatisierten Tests von Microsoft Visual Studio 2012](https://msdn.microsoft.com/library/ms182470.aspx).  
  
-   Führen Sie Tests bei der Projekterstellung in Team Foundation Build aus. Weitere Informationen finden Sie unter [Gewusst wie: Konfigurieren und Ausführen planmäßiger Tests, nachdem die Anwendung erstellt wurde (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182465(VS.100).aspx) oder [Gewusst wie: Konfigurieren und Ausführen planmäßiger Tests, nachdem die Anwendung erstellt wurde (Visual Studio 2012)](https://msdn.microsoft.com/library/ms182465.aspx).  
  
Sie können die SQL Server-Komponententests in einer bestimmten Reihenfolge ausführen, indem Sie eine Testreihe verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer Testreihe (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182631(VS.100).aspx) oder [ Vorgehensweise: Erstellen einer Testreihe (Visual Studio 2012)](https://msdn.microsoft.com/library/ms182631.aspx).  
  
## <a name="interpreting-tests-results"></a>Interpretieren der Testergebnisse  
Nach Abschluss der Tests wird im Fenster **Testergebnisse** angezeigt, welche Tests erfolgreich bzw. fehlerhaft waren. Weitere Informationen finden Sie unter [Interpretieren der Ergebnisse von SQL Server-Komponententests](../ssdt/interpreting-sql-server-unit-test-results.md). Weitere Informationen zur Diagnose unerwarteter Fehler finden Sie unter [Vorgehensweise. Debuggen von Datenbankobjekten](../ssdt/how-to-debug-database-objects.md).  
  
## <a name="topics-in-this-section"></a>Themen in diesem Abschnitt  
Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Vorgehensweise: Debuggen von Datenbankobjekten](../ssdt/how-to-debug-database-objects.md)  
  
-   [Vorgehensweise: Ausführen von SQL Server-Komponententests aus Team Foundation Build](../ssdt/how-to-run-sql-server-unit-tests-from-team-foundation-build.md)  
  
-   [Vorgehensweise: Ausführen von SQL Server-Komponententests](../ssdt/how-to-run-sql-server-unit-tests.md)  
  
-   [Interpretieren der Ergebnisse von SQL Server-Komponententests](../ssdt/interpreting-sql-server-unit-test-results.md)  
  
## <a name="related-scenarios"></a>Verwandte Szenarien  
[Erstellen und Definieren von SQL Server-Komponententests](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
Sie können Komponententests definieren, um das Verhalten von Datenbankobjekten zu überprüfen, und jedem Testprojekt unterschiedliche Datengenerierungspläne, Bereitstellungskonfigurationen und Verbindungszeichenfolgen zuweisen.  
  
[Benutzerdefinierte Testbedingungen für SQL Server-Komponententests](../ssdt/custom-test-conditions-for-sql-server-unit-tests.md)  
Sie können eine benutzerdefinierte Testbedingung erstellen, um Komponenten auf Bedingungen zu testen, die mit den Standardtestbedingungen nicht überprüft werden können.  
  
## <a name="see-also"></a>Weitere Informationen  
[Überprüfen des Datenbankcodes mithilfe von SQL Server-Komponententests](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)  
  
