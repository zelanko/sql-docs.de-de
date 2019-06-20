---
title: Überprüfen einer Berichtsausführung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- auditing [Reporting Services]
- verifying report execution
- logs [Reporting Services], verifying report run
- report execution data [Reporting Services]
- status information [Reporting Services]
- report processing [Reporting Services], verifying execution
- checking report execution
ms.assetid: 18a98f2f-6b40-454e-9b37-568ed1a96458
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c11c57f7c5f67b2557f5637ad10658abc9f80606
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66103141"
---
# <a name="verifying-a-report-run"></a>Überprüfen einer Berichtsausführung
  Mit Protokolldateien oder den Statusinformationen, die zusammen mit einem Bericht im Berichts-Manager angezeigt werden, können Sie Informationen zum Status der Berichtsverarbeitung anzeigen.  
  
## <a name="sources-of-report-execution-data"></a>Quellen für Berichtausführungsdaten  
 Die Berichtsausführungsprotokolle stellen umfangreiche Informationen zur Berichtsausführung bereit. Hierzu zählen der Name des Berichts, der Name des Benutzers, der den Bericht ausgeführt hat, der Zeitpunkt der Berichtsausführung sowie die verwendete Übermittlungserweiterung für die Weitergabe des Berichts. Um diese Daten anzuzeigen und zu analysieren, kopieren Sie das Berichtsausführungsprotokoll in Datenbanktabellen, für die problemlos Abfragen ausgeführt und Berichte erstellt werden können.  
  
 Protokolldateien enthalten eine Vielzahl von Einträgen zur Berichtsausführung und zu anderen Serveraktivitäten. Da Protokolldateien so viele Daten enthalten, sollten Sie den Berichts-Manager verwenden, wenn Sie nur überprüfen möchten, wann der Bericht zuletzt ausgeführt wurde. Falls Sie zusätzliche Informationen benötigen, müssen Sie die Protokolldateien ansehen.  
  
> [!NOTE]  
>  Im Berichts-Manager werden die Verarbeitungszeiten von Berichten, die bei Bedarf ausgeführt wurden, nicht angezeigt.  
  
 In der folgenden Tabelle ist beschrieben, wie Sie das Datum und die Uhrzeit der Verarbeitung für verschiedene Berichtstypen anzeigen.  
  
|Berichtstyp|Datum und Uhrzeit ist hier zu finden|Vorgehensweise zum Anzeigen der Informationen|  
|-----------------------------|-----------------------------------------------|-----------------------------------------------|  
|Ein Bericht, der als Berichtsmomentaufnahme ausgeführt wird.|Auf der Seite Inhalt. Weitere Informationen finden Sie unter [Inhalt (Seite) (Berichts-Manager)](../contents-page-report-manager.md).|1) Suchen Sie den Ordner, in dem der Bericht gespeichert ist.<br />2) Wählen Sie für den Ordner die Sicht „Details“ aus.<br />(3) 3) Notieren Sie sich das Datum und die Uhrzeit in der **Ausführungszeitpunkt** Spalte.|  
|Eine Momentaufnahme im Berichtsverlauf.|Auf der Eigenschaftenseite Verlauf. Weitere Informationen finden Sie unter [Momentaufnahmeoptionen (Eigenschaftenseite) (Berichts-Manager)](../snapshot-options-properties-page-report-manager.md).|1) Öffnen Sie den Bericht.<br />2) Klicken Sie auf die Seite **Eigenschaften** .<br />3) Klicken Sie auf die Registerkarte **Verlauf** .<br />4) Notieren Sie sich das Datum und die Uhrzeit in der Spalte **Wann ausgeführt** .|  
|Ein zwischengespeicherter Bericht.|Im Zeitplan, der zum Erstellen und Aktualisieren des zwischengespeicherten Berichts verwendet wird.|1) Öffnen Sie den Bericht.<br />2) Klicken Sie auf die Seite **Eigenschaften** .<br />3) Klicken Sie auf die Registerkarte **Ausführung** .<br />4) Öffnen Sie den Zeitplan.|  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Protokolldateien und Quellen](../report-server/reporting-services-log-files-and-sources.md)   
 [Festlegen von Berichtsverarbeitungseigenschaften](set-report-processing-properties.md)   
 [Berichts-Manager (einheitlicher SSRS-Modus)](../report-manager-ssrs-native-mode.md)  
  
  
