---
title: 'Aufgabe 17: Überprüfung des DQS-Bereinigung erstellt vom SSIS-Paket | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc6cc258-72f5-4593-8edb-9f5bc66de9db
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4226fd9a8e8eb8aa2851eed8eb318b8535010c8a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151480"
---
# <a name="task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package"></a>Aufgabe 17: Überprüfung des DQS-Bereinigungsprojekts, das vom SSIS-Paket erstellt wurde
  In dieser Aufgabe öffnen Sie das DQS-Projekt, das durch das SSIS-Paket in DQS-Client erstellt wurde, prüfen die Ergebnisse des Bereinigungsprozesses, führen optional eine interaktive Bereinigung aus und exportieren die Ergebnisse.  
  
1.  Starten Sie **Data Quality-Client**.  
  
2.  Klicken Sie auf **Aktivitätsüberwachung** in der **Verwaltung** Bereich.  
  
3.  Sortieren Sie die Liste basierend auf **Startzeit der Aktivität** auf den letzten Datensatz anzuzeigen.  
  
4.  Beachten Sie, dass Sie einen Namen für das Projekt in folgendem Format finden Sie unter: **CleanseAndCurate.Cleanse Supplier Data.GUID**.  
  
     ![DQS-Bereinigungsprojekts, das vom SSIS-Paket erstellt](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "DQS-Bereinigungsprojekts, das vom SSIS-Paket erstellt")  
  
5.  Beachten Sie, dass der Wert in der **ist aktiv** Feld **Active**.  
  
6.  Klicken Sie auf **Profiler** Registerkarte im unteren Bereich, um die profilerstatistiken für die bereinigungsaktivität anzuzeigen, die das SSIS-Paket ausgeführt.  
  
7.  Klicken Sie auf **schließen** schließen die **Verwaltung** Bildschirm.  
  
8.  Auf der Hauptseite des **DQS-Client**, klicken Sie auf **Data Quality-Projekt öffnen** in der **Data Quality-Projekte** Bereich.  
  
9. Wählen Sie in der Liste der Projekte das Projekt aus, das von der SSIS-DQS-Bereinigungskomponente erstellt wird. Der Name des Projekts sollte im Format sein: **CleanseAndCurate.Cleanse Supplier Data.GUID (in Rot)**. Möglicherweise müssen Sie die Liste basierend auf sortieren **Erstellungsdatum** Spalte und suchen Sie nach dem letzten Datensatz.  
  
10. Klicken Sie auf **Weiter**.  
  
11. Die **verwalten und Anzeigen der Ergebnisse** Seite sollte von der interaktiven Bereinigung Sie weiter oben in diesem Lernprogramm haben Sie vertraut sein.  
  
12. Überprüfen Sie die Bereinigungsergebnisse. Sie können auf der nächsten Seite auch interaktive Bereinigungen ausführen und Ergebnisse in eine Excel-Datei oder eine Datenbank exportieren.  
  
13. Klicken Sie auf **Weiter**. In diesem **exportieren** Seite können Sie Ergebnisse in eine Exceldatei, CSV-Datei oder einer SQL-Datenbank exportieren.  
  
14. Klicken Sie auf **Fertig stellen** auf die Aktivität fertig zu stellen.  
  
15. Auf der Hauptseite des **DQS-Client**, klicken Sie auf **Aktivitätsüberwachung** in der **Verwaltung** Bereich.  
  
16. Beachten Sie, dass der Wert der **IsActive** Feld für das Projekt **beendet** jetzt.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Fazit](../../2014/tutorials/conclusion.md)  
  
  