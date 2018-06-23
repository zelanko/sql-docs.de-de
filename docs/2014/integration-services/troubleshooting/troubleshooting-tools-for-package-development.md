---
title: Tools zur Problembehandlung für die Paketentwicklung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Integration Services packages, troubleshooting
- SSIS packages, troubleshooting
- Integration Services, troubleshooting
- errors [Integration Services], troubleshooting
- packages [Integration Services], troubleshooting
ms.assetid: 41dd248c-dab3-4318-b8ba-789a42d5c00c
caps.latest.revision: 66
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: aae2fac11aab58193883c43e1062e12be837e065
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151155"
---
# <a name="troubleshooting-tools-for-package-development"></a>Tools zur Problembehandlung für die Paketentwicklung
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enthält Funktionen und Tools, mit denen Sie die Problembehandlung von Paketen vornehmen können, während Sie diese in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]entwickeln.  
  
## <a name="troubleshooting-design-time-validation-issues"></a>Behandlung von Problemen bei der Überprüfung zur Entwurfszeit  
 Wenn in der aktuellen Version von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]ein Paket geöffnet wird, werden vom System alle Verbindungen überprüft, bevor alle Datenflusskomponenten überprüft werden, sowie alle langsamen oder nicht verfügbaren Verbindungen auf den Offlinemodus festgelegt. So kann die Verzögerung beim Überprüfen des Paketdatenflusses reduziert werden.  
  
 Wenn ein Paket geöffnet wurde, können Sie eine Verbindung auch deaktivieren, indem Sie mit der rechten Maustaste im Bereich **Verbindungs-Manager** auf den Verbindungs-Manager und anschließend auf **Offline arbeiten**klicken. So können Vorgänge im SSIS-Designer beschleunigt werden.  
  
 Auf den Offlinemodus festgelegte Verbindungen bleiben offline, bis Sie eine der folgenden Aktionen ausführen:  
  
-   Testen Sie die Verbindung, indem Sie mit der rechten Maustaste im Bereich **Verbindungs-Manager** des SSIS-Designers auf den Verbindungs-Manager und anschließend auf **Verbindung testen**klicken.  
  
     Eine Verbindung ist beispielsweise anfänglich auf den Offlinemodus festgelegt, wenn das Paket geöffnet wird. Sie ändern die Verbindungszeichenfolge, um das Problem zu beheben, und klicken auf **Verbindung testen** , um die Verbindung zu testen.  
  
-   Öffnen Sie das Projekt erneut, oder öffnen Sie das Projekt mit dem Paket erneut. Die Überprüfung wird erneut für alle Verbindungen im Paket ausgeführt.  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] umfasst die folgenden, zusätzlichen Funktionen, um Ihnen das Vermeiden von Überprüfungsfehlern zu erleichtern:  
  
-   **Festlegen des gesamten Pakets und aller Verbindungen auf den Offlinemodus, wenn keine Datenquellen verfügbar sind**. Sie können **Offline arbeiten** im Menü **SSIS** aktivieren. Im Gegensatz zu den `DelayValidation` -Eigenschaft, die **Offline arbeiten** Option ist verfügbar, noch bevor Sie ein Paket zu öffnen. Sie können die Option **Offline arbeiten** auch aktivieren, um die Vorgänge im Designer zu beschleunigen, und sie lediglich zum Überprüfen des Pakets deaktivieren.  
  
-   **Konfiguration der DelayValidation-Eigenschaft für Paketelemente, die bis zur Laufzeit nicht gültig sind**. Zum Verhindern von Überprüfungsfehlern können Sie für Paketelemente, deren Konfigurationen zur Entwurfszeit ungültig sind, `DelayValidation` auf `True` festlegen. Ein Beispiel hierfür wäre ein Datenflusstask, der eine Zieltabelle verwendet, die erst zur Laufzeit durch einen Task 'SQL ausführen' erstellt wird. Die `DelayValidation` Eigenschaft kann aktiviert werden, auf Paketebene oder auf der Ebene der einzelnen Tasks und Container, die das Paket enthält. Normalerweise müssen Sie diese Eigenschaft auf festgelegt lassen `True` auf die betreffenden Paketelemente, wenn Sie das Paket aus, um zu verhindern, dass die gleichen Überprüfungsfehler zur Laufzeit bereitstellen.  
  
     Die `DelayValidation` Eigenschaft kann festgelegt werden auf einen Datenflusstask, jedoch nicht für einzelne Datenflusskomponenten verbunden. Sie erreichen für einzelne Datenflusskomponenten ein ähnliches Ergebnis, wenn Sie die <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A>-Eigenschaft der Datenflusskomponenten auf `false` festlegen. Wenn der Wert dieser Eigenschaft ist jedoch `false`, die Komponente ist nicht bekannt Änderungen an den Metadaten externer Datenquellen.  
  
 Wenn vom Paket verwendete Datenbankobjekte zum Zeitpunkt der Überprüfung gesperrt sind, reagiert der Überprüfungsvorgang möglicherweise nicht mehr. Unter diesen Umständen reagiert der [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer ebenfalls nicht mehr. Sie können die Überprüfung fortsetzen, indem Sie die zugehörigen Sitzung in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]schließen. Sie können dieses Problem auch mit den in diesem Abschnitt beschriebenen Einstellungen umgehen.  
  
## <a name="troubleshooting-control-flow"></a>Ablaufsteuerung (Problembehandlung)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enthält die folgenden Funktionen und Tools, mit denen Sie während der Paketentwicklung Probleme bei der Ablaufsteuerung in Paketen behandeln können:  
  
-   **Festlegen von Breakpoints für Tasks, Container sowie für das Paket**. Sie können dabei mithilfe der vom [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer bereitgestellten grafischen Tools Breakpoints festlegen. Breakpoints können auf Paketebene oder auf der Ebene der einzelnen, in den Paketen enthaltenen Tasks und Container aktiviert werden. Bestimmte Tasks und Container stellen zusätzliche Unterbrechungsbedingungen zum Festlegen von Breakpoints bereit. Beispielsweise können Sie eine Unterbrechungsbedingung für den For-Schleifencontainer aktivieren, welche die Ausführung zu Beginn jeder Iteration der Schleife anhält.  
  
-   **Verwenden der Debugfenster**. Beim Ausführen von Paketen mit Breakpoints ermöglichen die Debugfenster in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] Zugriff auf Variablenwerte und Statusmeldungen.  
  
-   **Überprüfen der Informationen auf der Registerkarte Status**. [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer werden zusätzliche Informationen zur Ablaufsteuerung beim Ausführen von Paketen in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Auf der Registerkarte Status werden Tasks und Container in der Ausführungsreihenfolge aufgeführt. Diese Registerkarte enthält außerdem die Start- und Beendigungszeiten, Warnungen und Fehlermeldungen für jeden Task, Container sowie das Paket selbst.  
  
 Weitere Informationen zu diesen Funktionen finden Sie unter [Debugging Control Flow](debugging-control-flow.md).  
  
## <a name="troubleshooting-data-flow"></a>Datenfluss (Problembehandlung)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enthält die folgenden Funktionen und Tools, mit denen Sie während der Paketentwicklung Probleme mit Datenflüssen in Paketen behandeln können.  
  
-   **Durchführen von Tests mit einer Untermenge der Daten**. Wenn Sie für die Problembehandlung des Datenflusses eines Pakets nur eine Stichprobe des Datasets verwenden wollen, können Sie eine Transformation für Prozentwert-Stichproben oder eine Transformation für Zeilenstichproben einschließen, um zur Laufzeit eine Inline-Datenstichprobe zu erstellen. Weitere Informationen finden Sie unter [Percentage Sampling Transformation](../data-flow/transformations/percentage-sampling-transformation.md) und [Row Sampling Transformation](../data-flow/transformations/row-sampling-transformation.md).  
  
-   **Verwenden von Daten-Viewern zum Überwachen des Datenflusses**. Die Daten-Viewer zeigen Datenwerte an, während die Daten zwischen Quellen, Transformationen und Zielen verschoben werden. Ein Daten-Viewer kann Daten in einem Raster anzeigen. Sie können die Daten von einem Daten-Viewer in die Zwischenablage kopieren und anschließend in eine Datei wie z. B. eine Excel-Kalkulationstabelle einfügen. Weitere Informationen finden Sie unter [Hinzufügen eines Daten-Viewers zu einem Datenfluss](../add-a-data-viewer-to-a-data-flow.md).  
  
-   **Konfigurieren von Fehlerausgaben für Datenflusskomponenten, die Fehlerausgaben unterstützen**. Viele Datenflussquellen, Transformationen und Ziele unterstützen Fehlerausgaben. Sie können die Fehlerausgabe einer Datenflusskomponente so konfigurieren, dass die Fehlerdaten an ein bestimmtes Ziel geleitet werden. Sie können die fehlerhaften oder abgeschnittenen Daten z. B. in einer separaten Textdatei aufzeichnen. Sie können darüber hinaus Fehlerausgaben Daten-Viewer anfügen, in denen Sie nur die fehlerhaften Daten überprüfen. Während der Entwurfszeit zeichnen die Fehlerausgaben fehlerhafte Datenwerte auf, um Sie beim Entwerfen von Paketen mit realistischen Daten zu unterstützen. Im Gegensatz zu anderen Tools und Funktionen zur Problembehandlung, die nur zur Entwurfszeit nützlich sind, bleibt die Nützlichkeit von Fehlerausgaben in der Produktionsumgebung erhalten. Weitere Informationen finden Sie unter [Fehlerbehandlung in Daten](../data-flow/error-handling-in-data.md).  
  
-   **Aufzeichnen der Anzahl der verarbeiteten Zeilen**. Wenn Sie ein Paket im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer ausführen, wird die Anzahl der Zeilen, die einen Pfad durchlaufen haben, im Datenfluss-Designer angezeigt. Dieser Wert wird regelmäßig aktualisiert, während die Daten den Pfad durchlaufen. Sie können dem Datenfluss auch eine Transformation für Zeilenanzahl hinzufügen, um die endgültige Zeilenanzahl in einer Variablen aufzuzeichnen. Weitere Informationen finden Sie unter [Row Count Transformation](../data-flow/transformations/row-count-transformation.md).  
  
-   **Überprüfen der Informationen auf der Registerkarte Status**. [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer werden zusätzliche Informationen zu Datenflüssen beim Ausführen von Paketen in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Auf der Registerkarte Status werden die Datenflusskomponenten in der Ausführungsreihenfolge aufgelistet sowie der Fortschritt der einzelnen Paketphasen in Prozent und die in das Ziel geschriebenen Zeilen.  
  
 Weitere Informationen zu diesen Funktionen finden Sie unter [Debugging Data Flow](debugging-data-flow.md).  
  
## <a name="troubleshooting-scripts"></a>Behandlung von Problemen mit Skripts  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Visual Studio-Tools für Anwendungen (VSTA) ist die Entwicklungsumgebung, in der Sie die vom Skripttask und der Skriptkomponente verwendeten Skripts schreiben. VSTA bietet die folgenden Funktionen und Tools, mit denen Sie während der Paketentwicklung Probleme mit Skripts behandeln können:  
  
-   **Festlegen von Breakpoints für Skripts in Skripttasks.** VSTA stellt ausschließlich Unterstützung für das Debuggen von Skripts in Skripttasks bereit. Die in Skripttasks festgelegten Breakpoints werden mit den Breakpoints in Paketen sowie mit den Breakpoints der in Paketen enthaltenen Tasks und Containern integriert. Auf diese Weise wird das nahtlose Debuggen aller Paketelemente sichergestellt.  
  
    > [!NOTE]  
    >  Wenn Sie ein Paket debuggen, das mehrere Skripttasks umfasst, erreicht der Debugger nur in einem Skripttask Breakpoints und ignoriert die Breakpoints in den anderen Skripttasks. Ist ein Skripttask Bestandteil einer Foreach-Schleife oder eines For-Schleifencontainers, dann ignoriert der Debugger nach der ersten Schleifeniteration Breakpoints im Skripttask.  
  
 Weitere Informationen finden Sie unter [Debugging Script](debugging-script.md). Vorschläge zum Debuggen der Skriptkomponente finden Sie unter [Coding and Debugging the Script Component] (.. / extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md.  
  
## <a name="troubleshooting-errors-without-a-description"></a>Behandlung von Fehlern ohne Beschreibung  
 Wenn Sie während der Paketentwicklung auf eine [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Fehlernummer ohne dazugehörige Beschreibung stoßen, finden Sie die entsprechende Beschreibung unter [Fehler- und Meldungsreferenz von Integration Services](../integration-services-error-and-message-reference.md). Die Liste enthält zurzeit keine Informationen zur Problembehandlung.  
  
## <a name="see-also"></a>Siehe auch  
 [Tools zur Problembehandlung für die Ausführung des Pakets](troubleshooting-tools-for-package-execution.md)   
 [Funktionen für die Datenflussleistung](../data-flow/data-flow-performance-features.md)  
  
  