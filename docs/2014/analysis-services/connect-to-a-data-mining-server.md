---
title: Herstellen einer Verbindung eine Datamining-Server mit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- connections
- getting started
ms.assetid: 85962ad6-d840-4bc6-905e-c667c3276944
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f9ca50a030fef65c9de02bc93dcd970df2686b0a
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52420391"
---
# <a name="connect-to-a-data-mining-server"></a>Herstellen einer Verbindung mit einem Data Mining-Server
  ![Schaltfläche "Verbindungen"](media/misc-connection.gif "Schaltfläche \"Verbindungen\"")  
  
 Klicken Sie auf die **Verbindung** Schaltfläche, um eine vorhandene Verbindung auswählen oder erstellen Sie eine neue Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 **Warum muss ich mit einem Server herstellen?**  
  
 Wenn Sie eine Verbindung herstellen, können Sie auf diese Weise die Data Mining-Algorithmen verwenden, die vom [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server bereitgestellt werden, und Sie können die optimierte Verarbeitung des Servers nutzen.  
  
 Sie müssen Ihre Daten oder Ergebnisse nicht in einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank oder einer SQL Server-Datenbank speichern. Die Data Mining-Add-Ins für Excel können Daten verarbeiten, die nur in Excel gespeichert sind, sowie mit Daten, für die Sie eine Verbindung mit einer Excel-Datenquelle herstellen.  
  
## <a name="how-to-create-a-new-connection"></a>Vorgehensweise: Erstellen einer neuen Verbindung  
  
1.  Klicken Sie auf die **Verbindung** Schaltfläche.  
  
2.  In der **Analysis Services-Verbindungen** Dialogfeld klicken Sie auf **neu**.  
  
3.  In der **Herstellen einer Verbindung mit Analysis Services** Dialogfeld geben einen Servernamen ein.  
  
4.  Geben Sie die Authentifizierungsmethode an.  
  
5.  Geben Sie den Katalog oder die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank an, in dem bzw. der Sie die Data Mining-Modelle speichern möchten.  
  
    > [!NOTE]  
    >  Wenn Sie bisher keine Datenbanken erstellt haben, können Sie (Standard) für das Erstellen verwenden und anschließend die Verbindung testen. Sie können der Standardverbindung jedoch keine Miningmodelle hinzufügen. Vor dem Erstellen von Miningmodellen müssen Sie eine Verbindung mit einer vorhandenen Datenbank herstellen.  
  
6.  Wenn Sie über einen Webdienst eine Verbindung mit dem Server herstellen, geben Sie den Benutzernamen und das Kennwort ein, der bzw. das für den Webdienst erforderlich ist.  
  
7.  Geben Sie einen Anzeigenamen für die neue Verbindung ein.  
  
8.  Klicken Sie auf **Testverbindung** um sicherzustellen, dass der Server verfügbar ist.  
  
## <a name="troubleshooting-connections"></a>Fehlerbehandlung von Verbindungen  
 Dieser Abschnitt bietet Antworten auf eine Reihe häufiger Fragen zu Verbindungen mit [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 **Ich erhalte die Meldung "Keine Verbindung gefunden."**  
  
 Wenn der Text im unteren Teil der Schaltfläche anzeigt **keine Verbindung**, dies bedeutet, dass Sie eine Verbindung mit nicht erstellt haben eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Datenbank oder, dass Fehler bei der Verbindung. Sie können die Arbeit mit den Daten aus Excel in Access oder anderen Quellen fortsetzen. Zum Erstellen eines Data Mining-Modells oder Ausführen einer Vorhersage benötigen Sie eine aktive Verbindung.  
  
 **Angenommen, ich besitzen nicht die Berechtigung, um den Server verwenden?**  
  
 Wenn Sie über keine ausreichenden Berechtigungen verfügen, um Miningmodelle auf dem Server zu speichern, oder die Data Mining-Funktionen ausprobieren und die Arbeit nicht speichern möchten, können Sie die Tabellenanalysetools nutzen, durch die temporäre Datenstrukturen und Modelle erstellt werden. Sie müssen jedoch in der Lage sein, temporäre Modelle auf dem Server zu speichern. Bitten Sie Ihren Administrator, aktivieren Sie die Verwendung von *sitzungsminingmodelle* auf dem Server.  
  
 Wenn Sie sicherstellen möchten, dass die Modelle gespeichert werden, können Sie die Option zur Verwendung temporärer Modelle deaktivieren oder die Assistenten im Data Mining-Client verwenden. Diese Assistenten speichern alle Modelle auf dem Server. Da Sie Administratorzugriff auf die Datenbank benötigen, in der die Modelle gespeichert werden, empfiehlt es sich, dass der Administrator eine Datenbank speziell zum Erstellen von Miningmodellen mit den Add-Ins erstellt.  
  
 **Ich verloren Meine Verbindung; Gehen meine gesamte Arbeit verloren?**  
  
 Wenn Sie die Verbindung zum Server beenden, gehen Ihre Ergebnisse und Daten nicht verloren, da sie in Excel gespeichert sind. Wenn Sie jedoch temporäre Modelle erstellt haben, werden diese nach kurzer Zeit vom Server gelöscht. Also, wenn die Verbindung vorübergehend unterbrochen wird, wird nicht noch Mal die Modelle noch gelöscht werden.  
  
 Generierte Daten oder Ergebnisse gehen nicht verloren, da alle Berichte und Tabellen in Excel gespeichert werden.  
  
> [!NOTE]  
>  Trennen Sie nicht die Verbindung mit dem Server oder dem Netzwerk, während das Add-In mit dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server kommuniziert. Trennen Sie die Verbindung beispielsweise nicht, wenn ein Modell erstellt wird oder die Daten verarbeitet werden. In einigen Situationen können dadurch Daten beschädigt werden.  
  
 **Ich kann nicht mit dem Modell, mit dem Visio-Tools herzustellen.**  
  
 Von den Data Mining-Vorlagen für Visio können keine temporären Miningstrukturen und -modelle verwendet werden. Das Modell muss auf einem Server gespeichert sein, damit ein Diagramm eines Miningmodells erstellt werden kann.  
  
 **Wie kann ich die Nutzung der Verbindung überwachen?**  
  
 Die [Ablaufverfolgung &#40;Data Mining-Client für Excel&#41; ](trace-data-mining-client-for-excel.md) Tool erstellt ein Protokoll sämtlicher Aktivitäten zwischen den Add-ins und dem angegebenen Server.  
  
 Zum Aktivieren der Überwachung von sitzungsmodellen wählen die **sitzungsmodelle verwenden** option die **Überwachungstoken** Dialogfeld.  
  
 In der Ablaufverfolgung können Sie die DMX- und XMLA-Befehle anzeigen, die beim Erstellen von Modellen und Strukturen generiert wurden. Zudem können Sie die Abfragen anzeigen, die vom Client gesendet wurden, um Ergebnisse und Berichte in Excel zu generieren.  
  
 **Was ist ein temporäres Modell? Wie kann ich ein temporäres Modell werden gespeichert?**  
  
 Mit den Tabellenanalysetools für Excel werden standardmäßig temporäre Datenstrukturen und Miningmodelle erstellt. Sie können temporäre Modelle weiterhin durchsuchen und abfragen, solange die Arbeitsmappe geöffnet ist und die Verbindung mit [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht getrennt wird.  
  
 Alle von Ihnen erstellten Strukturen und Modelle werden gelöscht, sobald Sie die Excel-Arbeitsmappe schließen oder wenn Sie die Verbindung mit [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ändern oder beenden.  
  
 Wenn Sie einen Assistenten im Data Mining-Client für Excel abschließen, werden Modelle standardmäßig auf dem Server gespeichert. Auf der letzten Seite jedes Assistenten wird jedoch die Option angeboten, ein temporäres Modell zu verwenden. Wenn Sie diese Option auswählen, werden sowohl die Data Mining-Struktur als auch das von Ihnen erstellte Modell in einer temporären Datei gespeichert. Sie können die Struktur und das Modell so lange durchsuchen, verwalten und ändern, wie Excel geöffnet ist. Beim Schließen von Excel werden die Struktur und alle damit verbundenen Modelle jedoch gelöscht.  
  
 Sie können eine temporäre Struktur oder Modell auch explizit erstellen, mit der **erweiterten Data Mining Query Editor** und eine der DMX-Vorlagen auswählen. Fügen Sie die `USE SESSION MODELS`-Klausel hinzu, um anzugeben, dass Objekte temporär sind.   
  
### <a name="creating-backups-of-mining-models-and-structures"></a>Erstellen von Sicherungen von Miningmodellen und -strukturen  
 Sie können es zum Erstellen einer Sicherung eines Modells oder einer Struktur mit exportieren [Modelle verwalten &#40;SQL Server Data Mining-Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md), im Data Mining-Client für Excel.  
  
 Wenn Sie ein temporäres Miningmodell erstellt haben, weist dieses i. d. R. einen schwer verständlichen Namen auf, beispielsweise Table5_593679_TS_62446. Sie können jedoch die [Ablaufverfolgung &#40;Data Mining-Client für Excel&#41; ](trace-data-mining-client-for-excel.md) Tool zum Ermitteln der Namen von temporären Strukturen und Modelle, die von den Tabellenanalysetools erstellt wurden, und Sichern sie Sie mithilfe von  **Verwalten von Modellen**.  
  
##### <a name="identify-and-export-a-temporary-model"></a>Identifizieren und Exportieren eines temporären Modells  
  
1.  In der **Verbindungen** Gruppe von Data Mining-Client für Excel, klicken Sie auf **Ablaufverfolgung**.  
  
2.  Sehen Sie das Verbindungsaktivitätsprotokoll ein, und suchen Sie nach dem Modell, indem Sie beispielsweise die Spalten und vorhersagbaren Ausgaben überprüfen.  
  
     Erfahrene Benutzer: Wenn Sie mit DMX oder XMLA vertraut sind, können Sie die Anweisungen in einer Datei für die spätere Verwendung kopieren.  
  
3.  Wenn Sie den Namen des temporären Modells und der Struktur gefunden haben, öffnen Sie **Modell verwalten** , und wählen Sie das Modell.  
  
4.  Klicken Sie auf Dieses Miningmodell exportieren, um eine Skriptdatei an einem von Ihnen angegebenen Speicherort zu generieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Verbinden mit Quelldaten &#40;Datamining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md)   
 [Serverkonfigurations-Hilfsprogramm &#40;Data Mining-Add-ins für Excel&#41;](server-configuration-utility-data-mining-add-ins-for-excel.md)  
  
  
