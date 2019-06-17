---
title: Interpretieren der Ergebnisse von SQL Server-Komponententests | Microsoft-Dokumentation
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: fde3c95b-2f68-483d-a197-0f7161b72fa3
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1c68ace0ccbd49b63404aaf52419a06dda297f8d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65088713"
---
# <a name="interpreting-sql-server-unit-test-results"></a>Interpretieren der Ergebnisse von SQL Server-Komponententests
Wenn Sie einen SQL Server-Komponententest ausführen, werden die Testergebnisse automatisch erzeugt, auf dem Datenträger gespeichert und im Fenster **Testergebnisse** zusammengefasst. Sobald Sie einen Testlauf starten, wird das Fenster **Testergebnisse** mit dem Status des Testlaufs angezeigt. In diesem Fenster sind sowohl die aktiven als auch die abgeschlossenen Tests enthalten.  
  
Sie können ausführliche Informationen zu einem Testergebnis anzeigen, indem Sie im Fenster **Testergebnisse** darauf doppelklicken, um die Seite **Testergebnisdetails** zu öffnen. Um weitere Informationen zu einem Testergebnis zu erhalten, doppelklicken Sie auf das Ergebnis.  
  
Weitere Informationen zur Vorgehensweise beim Ändern der Anzeige des Fensters **Testergebnisse** finden Sie unter [Vorgehensweise: Hinzufügen oder Entfernen von Spalten in Testfenstern (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182508(VS.100).aspx) oder [Vorgehensweise: Hinzufügen oder Entfernen von Spalten in Testfenstern (Visual Studio 2012)](https://msdn.microsoft.com/library/ms182508.aspx).  
  
## <a name="storing-test-results"></a>Speichern von Testergebnissen  
Die Ergebnisse der Komponententests werden in einer Datei mit der Erweiterung TRX automatisch auf der Festplatte gespeichert. Eine TRX-Datei ist eine XML-Datei, die die Details eines Testlaufs enthält. Sie können TRX-Dateien vorheriger Testläufe laden, um die Ergebnisse dieser Testläufe zu überprüfen oder um frühere Tests erneut auszuführen. Weitere Informationen finden Sie unter [Vorgehensweise: Erneutes Ausführen eines Tests (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182472(VS.100).aspx).  
  
> [!NOTE]  
> Komponententests können nicht remote ausgeführt werden.  
  
Wenn Ihr Team die Arbeit mithilfe eines Visual Studio Team Foundation Server-Teamprojekts verwaltet, können Sie die Testdaten auch in einer SQL Server-Datenbank veröffentlichen, die als Betriebsspeicher bezeichnet wird.  
  
Weitere Informationen zum Speichern, erneuten Verwenden und Teilen von Testergebnissen mit Ihrem Team finden Sie unter [Vorgehensweise: Speichern und Öffnen von Testergebnissen in Visual Studio 2010](https://msdn.microsoft.com/library/ms404662(VS.100).aspx) oder [Vorgehensweise: Speichern und Öffnen von Testergebnissen in Visual Studio 2012](https://msdn.microsoft.com/library/ms404662.aspx).  
  
## <a name="see-also"></a>Weitere Informationen  
[Ausführen von SQL Server-Komponententests](../ssdt/running-sql-server-unit-tests.md)  
  
