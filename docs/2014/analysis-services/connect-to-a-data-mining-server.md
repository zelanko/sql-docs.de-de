---
title: Herstellen einer Verbindung mit einem Data Mining-Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- connections
- getting started
ms.assetid: 85962ad6-d840-4bc6-905e-c667c3276944
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6e7fca367c72aaff5f02280829740942a36915ff
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527236"
---
# <a name="connect-to-a-data-mining-server"></a>Herstellen einer Verbindung mit einem Data Mining-Server
  ![Schaltfläche "Verbindungen"](media/misc-connection.gif "Schaltfläche "Verbindungen"")  
  
 Klicken Sie auf die Schaltfläche **Verbindung** , um eine vorhandene Verbindung auszuwählen oder eine neue Verbindung mit einer Instanz von zu erstellen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 **Weshalb muss eine Verbindung mit einem Server hergestellt werden?**  
  
 Wenn Sie eine Verbindung herstellen, können Sie auf diese Weise die Data Mining-Algorithmen verwenden, die vom [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server bereitgestellt werden, und Sie können die optimierte Verarbeitung des Servers nutzen.  
  
 Sie müssen Ihre Daten oder Ergebnisse nicht in einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank oder einer SQL Server-Datenbank speichern. Die Data Mining-Add-Ins für Excel können Daten verarbeiten, die nur in Excel gespeichert sind, sowie mit Daten, für die Sie eine Verbindung mit einer Excel-Datenquelle herstellen.  
  
## <a name="how-to-create-a-new-connection"></a>Vorgehensweise: Erstellen einer neuen Verbindung  
  
1.  Klicken Sie auf die Schaltfläche **Verbindung** .  
  
2.  Klicken Sie im Dialogfeld **Analysis Services Verbindungen** auf **neu**.  
  
3.  Geben Sie im Dialogfeld **Verbindung mit Analysis Services herstellen** einen Servernamen ein.  
  
4.  Geben Sie die Authentifizierungsmethode an.  
  
5.  Geben Sie den Katalog oder die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank an, in dem bzw. der Sie die Data Mining-Modelle speichern möchten.  
  
    > [!NOTE]  
    >  Wenn Sie bisher keine Datenbanken erstellt haben, können Sie (Standard) für das Erstellen verwenden und anschließend die Verbindung testen. Sie können der Standardverbindung jedoch keine Miningmodelle hinzufügen. Vor dem Erstellen von Miningmodellen müssen Sie eine Verbindung mit einer vorhandenen Datenbank herstellen.  
  
6.  Wenn Sie über einen Webdienst eine Verbindung mit dem Server herstellen, geben Sie den Benutzernamen und das Kennwort ein, der bzw. das für den Webdienst erforderlich ist.  
  
7.  Geben Sie einen Anzeigenamen für die neue Verbindung ein.  
  
8.  Klicken Sie auf **Verbindung testen** , um sicherzustellen, dass der Server verfügbar ist.  
  
## <a name="troubleshooting-connections"></a>Fehlerbehandlung von Verbindungen  
 Dieser Abschnitt bietet Antworten auf eine Reihe häufiger Fragen zu Verbindungen mit [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 **Ich erhalte eine Meldung, die besagt, dass keine Verbindung gefunden wurde.**  
  
 Wenn der Text im unteren Teil der Schaltfläche **keine Verbindung**besagt, bedeutet dies, dass Sie keine Verbindung mit einer-Datenbank hergestellt haben [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] oder dass die Verbindung nicht hergestellt werden konnte. Sie können die Arbeit mit den Daten aus Excel in Access oder anderen Quellen fortsetzen. Zum Erstellen eines Data Mining-Modells oder Ausführen einer Vorhersage benötigen Sie eine aktive Verbindung.  
  
 **Angenommen, ich verfüge nicht über die Berechtigung zum Verwenden des Servers?**  
  
 Wenn Sie über keine ausreichenden Berechtigungen verfügen, um Miningmodelle auf dem Server zu speichern, oder die Data Mining-Funktionen ausprobieren und die Arbeit nicht speichern möchten, können Sie die Tabellenanalysetools nutzen, durch die temporäre Datenstrukturen und Modelle erstellt werden. Sie müssen jedoch in der Lage sein, temporäre Modelle auf dem Server zu speichern. Bitten Sie den Administrator, die Verwendung von *Sitzungs Mining Modellen* auf dem Server zu aktivieren.  
  
 Wenn Sie sicherstellen möchten, dass die Modelle gespeichert werden, können Sie die Option zur Verwendung temporärer Modelle deaktivieren oder die Assistenten im Data Mining-Client verwenden. Diese Assistenten speichern alle Modelle auf dem Server. Da Sie Administratorzugriff auf die Datenbank benötigen, in der die Modelle gespeichert werden, empfiehlt es sich, dass der Administrator eine Datenbank speziell zum Erstellen von Miningmodellen mit den Add-Ins erstellt.  
  
 **Die Verbindung wurde unterbrochen, ist nun die gesamte Arbeit verloren gegangen?**  
  
 Wenn Sie die Verbindung zum Server beenden, gehen Ihre Ergebnisse und Daten nicht verloren, da sie in Excel gespeichert sind. Wenn Sie jedoch temporäre Modelle erstellt haben, werden diese nach kurzer Zeit vom Server gelöscht. Wenn Sie die Verbindung also vorübergehend verlieren, werden die Modelle noch nicht gelöscht.  
  
 Generierte Daten oder Ergebnisse gehen nicht verloren, da alle Berichte und Tabellen in Excel gespeichert werden.  
  
> [!NOTE]  
>  Trennen Sie nicht die Verbindung mit dem Server oder dem Netzwerk, während das Add-In mit dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server kommuniziert. Trennen Sie die Verbindung beispielsweise nicht, wenn ein Modell erstellt wird oder die Daten verarbeitet werden. In einigen Situationen können dadurch Daten beschädigt werden.  
  
 **Eine Verbindung mit dem Modell mithilfe der Visio-Tools kann nicht hergestellt werden.**  
  
 Von den Data Mining-Vorlagen für Visio können keine temporären Miningstrukturen und -modelle verwendet werden. Das Modell muss auf einem Server gespeichert sein, damit ein Diagramm eines Miningmodells erstellt werden kann.  
  
 **Wie kann die Nutzung der Verbindung überwacht werden?**  
  
 Das Tool [Trace &#40;Data Mining-Client für Excel&#41;](trace-data-mining-client-for-excel.md) erstellt ein Protokoll aller Aktivitäten zwischen den Add-Ins und dem angegebenen Server.  
  
 Um die Überwachung von Sitzungs Modellen zu aktivieren, wählen Sie die Option **Sitzungs Modelle verwenden** **im Dialogfeld** Überwachung aus.  
  
 In der Ablaufverfolgung können Sie die DMX- und XMLA-Befehle anzeigen, die beim Erstellen von Modellen und Strukturen generiert wurden. Zudem können Sie die Abfragen anzeigen, die vom Client gesendet wurden, um Ergebnisse und Berichte in Excel zu generieren.  
  
 **Was ist ein temporäres Modell? Wie kann ich ein temporäres Modell speichern?**  
  
 Mit den Tabellenanalysetools für Excel werden standardmäßig temporäre Datenstrukturen und Miningmodelle erstellt. Sie können temporäre Modelle weiterhin durchsuchen und abfragen, solange die Arbeitsmappe geöffnet ist und die Verbindung mit [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht getrennt wird.  
  
 Alle von Ihnen erstellten Strukturen und Modelle werden gelöscht, sobald Sie die Excel-Arbeitsmappe schließen oder wenn Sie die Verbindung mit [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ändern oder beenden.  
  
 Wenn Sie einen Assistenten im Data Mining-Client für Excel abschließen, werden Modelle standardmäßig auf dem Server gespeichert. Auf der letzten Seite jedes Assistenten wird jedoch die Option angeboten, ein temporäres Modell zu verwenden. Wenn Sie diese Option auswählen, werden sowohl die Data Mining-Struktur als auch das von Ihnen erstellte Modell in einer temporären Datei gespeichert. Sie können die Struktur und das Modell so lange durchsuchen, verwalten und ändern, wie Excel geöffnet ist. Beim Schließen von Excel werden die Struktur und alle damit verbundenen Modelle jedoch gelöscht.  
  
 Sie können auch explizit eine temporäre Struktur oder ein temporäres Modell erstellen, indem Sie den **erweiterten Data Mining-Abfrage-Editor** verwenden und eine der DMX-Vorlagen auswählen. Fügen Sie die `USE SESSION MODELS`-Klausel hinzu, um anzugeben, dass Objekte temporär sind.   
  
### <a name="creating-backups-of-mining-models-and-structures"></a>Erstellen von Sicherungen von Miningmodellen und -strukturen  
 Wenn Sie eine Sicherung eines Modells oder einer Struktur erstellen möchten, können Sie es mithilfe von [Verwalten von Modellen &#40;SQL Server Data Mining-Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md)im Data Mining-Client für Excel exportieren.  
  
 Wenn Sie ein temporäres Miningmodell erstellt haben, weist dieses i. d. R. einen schwer verständlichen Namen auf, beispielsweise Table5_593679_TS_62446. Sie können jedoch das Tool [Trace &#40;Data Mining-Client für Excel&#41;](trace-data-mining-client-for-excel.md) verwenden, um die Namen von temporären Strukturen und Modellen zu ermitteln, die von den Tabellenanalyse Tools erstellt wurden, und Sie dann mithilfe von **Modell verwalten**zu sichern.  
  
##### <a name="identify-and-export-a-temporary-model"></a>Identifizieren und Exportieren eines temporären Modells  
  
1.  Klicken Sie in der Gruppe **Verbindungen** des Data Mining-Clients für Excel auf Ablauf **Verfolgung**.  
  
2.  Sehen Sie das Verbindungsaktivitätsprotokoll ein, und suchen Sie nach dem Modell, indem Sie beispielsweise die Spalten und vorhersagbaren Ausgaben überprüfen.  
  
     Fortgeschrittene Benutzer: Wenn Sie mit DMX oder XMLA vertraut sind, können Sie die Anweisungen für die spätere Verwendung in eine Datei kopieren.  
  
3.  Wenn Sie den Namen des temporären Modells und der temporären Struktur gefunden haben, öffnen Sie **Modell verwalten** , und wählen Sie das Modell aus.  
  
4.  Klicken Sie auf Dieses Miningmodell exportieren, um eine Skriptdatei an einem von Ihnen angegebenen Speicherort zu generieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Herstellen einer Verbindung mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md)   
 [Server Konfigurations Hilfsprogramm &#40;Data Mining-Add-Ins für Excel&#41;](server-configuration-utility-data-mining-add-ins-for-excel.md)  
  
  
