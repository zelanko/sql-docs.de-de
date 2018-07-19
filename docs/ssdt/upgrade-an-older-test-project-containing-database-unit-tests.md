---
title: Durchführen eines Upgrades für ein älteres Testprojekt mit Datenbankkomponententests | Microsoft-Dokumentation
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42782ff3-e8cf-4c9d-8dac-a95b236edfc4
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7cfc482daed9c150079a8a5b29d32ee319f54745
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094201"
---
# <a name="upgrade-an-older-test-project-containing-database-unit-tests"></a>Upgrade eines älteren Testprojekts, das Datenbankkomponententests enthält
Sie können ein Upgrade für ein älteres Testprojekt, das in Visual Studio 2010 erstellt wurde und Datenbankkomponententests enthält, für die Verwendung der neuen Laufzeit und Tools für SQL Server Data Tools-Datenbankkomponententests durchführen. Nachdem Sie ein Upgrade für ein älteres Projekt durchgeführt haben, können Sie dem Projekt SQL Server-Komponententests hinzufügen (weitere Informationen finden Sie unter [Erstellen und Definieren von SQL Server-Komponententests](../ssdt/creating-and-defining-sql-server-unit-tests.md)).  
  
> [!TIP]  
> Bei Verwendung von Visual Studio 2010 sollten Sie keine Komponententests mithilfe der älteren Vorlage für Datenbankkomponententests hinzufügen, nachdem Sie einem Testprojekt SQL Server-Komponententests hinzugefügt haben. Andernfalls müssen Sie das Projekt erneut konvertieren, damit die Tests ordnungsgemäß ausgeführt werden.  
  
Bei einem Testdatenbankprojekt, das in einem Release vor Visual Studio 2010 erstellt wurde, informieren Sie sich unter [Gewusst wie: Durchführen eines Upgrades für Datenbankkomponententests früherer Visual Studio-Releases](http://msdn.microsoft.com/library/dd193412(VS.100).aspx) über die Durchführung eines Upgrade für das Datenbankprojekt auf Visual Studio 2010, bevor Sie ein Upgrade für das Projekt auf SQL Server Data Tools durchführen.  
  
### <a name="initiating-an-upgrade"></a>Initiieren eines Upgrades  
  
-   Sie können ein Projektupgrade über das Kontextmenü eines Testprojekts starten.  
  
    In einigen Fällen wird in SQL Server Data Tools ein Dialogfeld angezeigt, in dem Sie ein Upgrade für ein Testprojekt initiieren können.  
  
-   Durch das Projektupgrade wird der Assemblyverweis auf das ältere Datenbanktestframework entfernt und ein Verweis auf das neue Framework und eine Adapterassembly hinzugefügt. Die Datei app.config wird ebenfalls aktualisiert.  
  
    > [!NOTE]  
    > Wenn das Testprojekt sowohl über die Codedatei „DatabaseSetup“ als auch über die Codedatei „SQLDatabaseSetup“ verfügt, wird die Datei „DatabaseSetup“ durch die Durchführung eines Upgrades für das Projekt auf SQL Server Data Tools aus dem Build ausgeschlossen. Sie können die Datei DatabaseSetup entfernen, wenn sie aus dem Build ausgeschlossen wird.  
  
-   Nach der Konvertierung verwenden vorhandene Datenbankkomponententests, die mit der älteren Vorlage erstellt wurden, Typen in der Adapterassembly, um auf das neue Framework zuzugreifen. Die Verwendung einer Adapterassembly deutet darauf hin, dass die Testskripts und der Code durch den Upgradevorgang nicht geändert wurden. Wenn Sie dem Projekt einen SQL Server-Komponententest hinzufügen, verweist der neue Test direkt und nicht über einen Adapter auf das neue Framework. Sie können vorhandenen Code manuell für die Verwendung des neuen Frameworks aktualisieren, um Konsistenz mit neuen Tests zu gewährleisten. Dies ist jedoch nicht zwingend erforderlich.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Überprüfen des Datenbankcodes mithilfe von SQL Server-Komponententests](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)  
  
