---
title: 'Aufgabe 17: Überprüfung des DQS-Bereinigung erstellt wurde vom SSIS-Paket | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fc6cc258-72f5-4593-8edb-9f5bc66de9db
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 4653ce040e19b82b9e70daa7ebfc02047d71b194
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63057846"
---
# <a name="task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package"></a>Aufgabe 17: Überprüfung des vom SSIS-Paket erstellten DQS-Bereinigungsprojekts
  In dieser Aufgabe öffnen Sie das DQS-Projekt, das durch das SSIS-Paket in DQS-Client erstellt wurde, prüfen die Ergebnisse des Bereinigungsprozesses, führen optional eine interaktive Bereinigung aus und exportieren die Ergebnisse.  
  
1.  Starten Sie **Data Quality-Client**.  
  
2.  Klicken Sie auf **Aktivitätsüberwachung** in die **Verwaltung** Bereich.  
  
3.  Sortieren Sie die Liste basierend auf **Startzeit der Aktivität** auf den letzten Datensatz anzuzeigen.  
  
4.  Beachten Sie, dass Sie einen Namen des Projekts im folgenden Format angezeigt: **CleanseAndCurate.Cleanse Supplier Data.GUID**.  
  
     ![SSIS-Paket erstellt DQS-Bereinigungsprojekts](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "DQS-Bereinigungsprojekts erstellt SSIS-Paket")  
  
5.  Beachten Sie, dass der Wert in der **ist aktiv** Feld **Active**.  
  
6.  Klicken Sie auf **Profiler** Registerkarte im unteren Bereich, um die profilerstatistiken für die bereinigungsaktivität finden Sie unter, der das SSIS-Paket ausgeführt.  
  
7.  Klicken Sie auf **schließen** schließen die **Verwaltung** Bildschirm.  
  
8.  Auf der Hauptseite des **DQS-Client**, klicken Sie auf **Open Data Quality-Projekt** in die **Data Quality-Projekte** Bereich.  
  
9. Wählen Sie in der Liste der Projekte das Projekt aus, das von der SSIS-DQS-Bereinigungskomponente erstellt wird. Der Name des Projekts sollte im Format aufweisen:  **CleanseAndCurate.Cleanse Supplier Data.GUID (in Rot)**. Möglicherweise müssen Sie die Liste basierend auf sortieren **Erstellungsdatum** Spalte und suchen Sie nach der neueste Datensatz.  
  
10. Klicken Sie auf **Weiter**.  
  
11. Die **verwalten und Anzeigen der Ergebnisse** Seite sollten Sie von der interaktiven Bereinigung weiter oben in diesem Tutorial Sie haben damit vertraut sein.  
  
12. Überprüfen Sie die Bereinigungsergebnisse. Sie können auf der nächsten Seite auch interaktive Bereinigungen ausführen und Ergebnisse in eine Excel-Datei oder eine Datenbank exportieren.  
  
13. Klicken Sie auf **Weiter**. In diesem **exportieren** Seite können Sie Ergebnisse in eine Excel-Datei, CSV-Datei oder eine SQL-Datenbank exportieren.  
  
14. Klicken Sie auf **Fertig stellen** auf die Aktivität fertig zu stellen.  
  
15. Auf der Hauptseite des **DQS-Client**, klicken Sie auf **Aktivitätsüberwachung** in die **Verwaltung** Bereich.  
  
16. Beachten Sie, dass der Wert des **IsActive** Feld für das Projekt **beendet** jetzt.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Fazit](../../2014/tutorials/conclusion.md)  
  
  
