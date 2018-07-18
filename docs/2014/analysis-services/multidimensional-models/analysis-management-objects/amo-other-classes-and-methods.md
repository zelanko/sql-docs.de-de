---
title: AMO andere Klassen und Methoden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- restores [AMO]
- AMO, backup and restore
- capture logs [AMO]
- AmoException class [AMO]
- Analysis Management Objects, backup and restore
- assembly objects [AMO]
- traces [AMO]
- backups [AMO]
ms.assetid: 60ed5cfa-3a03-4161-8271-0a71a3ae363b
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6ff888c133491bfca9569daf08dc76e54e14d6d1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180877"
---
# <a name="amo-other-classes-and-methods"></a>Andere AMO-Klassen und Methoden
  Dieser Abschnitt enthält gängige Klassen, die nicht OLAP-oder Datamining spezifisch sind und, sind hilfreich bei der Verwaltung Verwalten von Objekten in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Diese Klassen decken Funktionen wie gespeicherte Prozeduren, Ablaufverfolgung, Ausnahmen sowie Sicherung und Wiederherstellung ab.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
-   [Assemblyobjekte](#Assembly)  
  
-   [Backup- und Restore-Methoden](#Backup)  
  
-   [Trace-Objekte](#Traces)  
  
-   [CaptureLog-Klasse und CaptureXML-Attribut](#CaptureLog)  
  
-   [AMOException-Ausnahmeklasse](#AMO)  
  
 Die folgende Abbildung zeigt die Beziehung der in diesem Thema erläuterten Klassen.  
  
 ![Andere Klassen in AMO](../../../analysis-services/dev-guide/media/amo-otherclasses.gif "andere Klassen in AMO")  
  
##  <a name="Assembly"></a> Assemblyobjekte  
 Ein <xref:Microsoft.AnalysisServices.Assembly>-Objekt wird erstellt, indem es der Auflistung der Assemblys auf dem Server hinzugefügt und anschließend das <xref:Microsoft.AnalysisServices.Assembly>-Objekt auf dem Server mithilfe der Update-Methode aktualisiert wird.  
  
 So entfernen Sie eine <xref:Microsoft.AnalysisServices.Assembly> Objekt muss gelöscht werden, indem Sie mit der Drop-Methode, der die <xref:Microsoft.AnalysisServices.Assembly> Objekt. Durch das Entfernen eines <xref:Microsoft.AnalysisServices.Assembly>-Objekts aus der Auflistung der Assemblys der Datenbank wird die Assembly nicht gelöscht. Allerdings können Sie die Assembly erst wieder in Ihrer Anwendung anzeigen, wenn Sie diese das nächste Mal ausführen.  
  
 Weitere Informationen zu den Methoden und Eigenschaften zur Verfügung stehen, finden Sie unter <xref:Microsoft.AnalysisServices.Assembly> in <xref:Microsoft.AnalysisServices> .  
  
> [!IMPORTANT]  
>  COM-Assemblys können ein Sicherheitsrisiko darstellen. Aufgrund dieses Risikos und anderer Überlegungen wurden COM-Assemblys in [!INCLUDE[ssASversion10](../../../includes/ssasversion10-md.md)]als veraltet markiert. COM-Assemblys werden in zukünftigen Versionen möglicherweise nicht mehr unterstützt.  
  
##  <a name="Backup"></a> Backup- und Restore-Methoden  
 Die Methoden Backup und Restore sind Methoden, mit denen Sie Kopien einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Datenbank erstellen können, mit deren Hilfe diese Datenbank wiederhergestellt werden kann. Die Backup-Methode gehört zum <xref:Microsoft.AnalysisServices.Database>-Objekt, und die Restore-Methode gehört zum <xref:Microsoft.AnalysisServices.Server>-Objekt.  
  
 Nur Server- und Datenbankadministratoren ist es gestattet, eine Datenbank zu sichern. Nur Serveradministratoren können eine Datenbank auf einem anderen Server als dem, auf dem die Sicherung ausgeführt wurde, wiederherstellen. Datenbankadministratoren können eine Datenbank durch Überschreiben der vorhandenen Datenbank wiederherstellen, jedoch nur, wenn sie die zu überschreibende Datenbank besitzen. Nach der Wiederherstellung verliert der Datenbankadministrator möglicherweise die Zugriffsberechtigung für die wiederhergestellte Datenbank, wenn diese mit den ursprünglichen Sicherheitsdefinitionen wiederhergestellt wurde.  
  
 Datenbanksicherungsdateien müssen eine .abf-Erweiterung aufweisen.  
  
### <a name="backup-method"></a>Backup-Methode  
 Verwenden Sie zum Sichern einer Datenbank die Backup-Methode des Datenbankobjekts zusammen mit dem Namen der Sicherungsdatei als Parameter.  
  
##### <a name="default-values"></a>Standardwerte:  
 AllowOverwrite=`false`  
  
 BackupRemotePartitions=`false`  
  
 Security=`CopyAll`  
  
 ApplyCompression=`true`  
  
### <a name="restore-method"></a>Restore-Methode  
 Verwenden Sie zum Wiederherstellen einer Datenbank auf einem Server die Restore-Methode des Servers zusammen mit dem Namen der Sicherungsdatei als Parameter.  
  
##### <a name="default-values"></a>Standardwerte:  
 AllowOverwrite=`false`  
  
 DataSourceType=`Remote`  
  
 Security=`CopyAll`  
  
##### <a name="restrictions"></a>Restrictions  
  
1.  Eine lokale Partition kann nicht als Remotepartition wiederhergestellt werden.  
  
2.  Eine Remotepartition kann nicht als lokale Partition wiederhergestellt werden, jedoch kann eine Remotepartition auf einem anderen Server wiederhergestellt werden als auf dem Server, auf dem die Sicherung vorgenommen wurde.  
  
### <a name="common-parameters-and-properties-for-backup-and-restore-methods"></a>Allgemeine Parameter und Eigenschaften für die Backup- und Restore-Methoden  
  
-   `File` ist der Name der Datei (UNC-Name), in die/aus der die Sicherung vorgenommen werden soll.  
  
-   `Location` gibt serverspezifische Sicherungsinformationen wie `BackupFile` an. Das gestattet Ihnen, eine separate Sicherungsdatei für eine Remotedatenbank anzugeben.  
  
-   `DatasourceID` gibt die ID der untergeordneten Datenbank auf einem Remoteserver an.  
  
-   Mit `ConnectionString` können Sie die Remotedatenquelle anpassen, falls sich der Remoteserver geändert hat. DatasourceID muss immer angegeben werden, wenn ConnectionString vorhanden ist.  
  
-   `Folder` ermöglicht die Neuzuordnung der Ordner für Partitionen auf der lokalen Festplatte.  
  
-   `Original` ist der ursprüngliche Ordner für lokale Partitionen.  
  
-   `New` ist der neue Speicherort für lokale Partitionen, die sich zuvor im entsprechenden Ordner Original befanden.  
  
-   `Password` gibt an, dass der Server die Sicherungsdatei verschlüsselt (sofern ein bestimmter Wert festgelegt ist).  
  
##  <a name="Traces"></a> Trace-Objekte  
 Die Ablaufverfolgung ist ein für die Überwachung, Wiedergabe und Verwaltung einer Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verwendetes Framework. Eine Clientanwendung wie [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] abonniert eine Ablaufverfolgung, und der Server sendet Ablaufverfolgungsereignisse gemäß Ablaufverfolgungsdefinition zurück.  
  
 Jedes Ereignis wird von einer Ereignisklasse beschrieben. Die Ereignisklasse beschreibt den Typ des generierten Ereignisses. Innerhalb einer Ereignisklasse beschreiben Ereignisunterklassen eine stärker differenzierte Kategorisierung. Jedes Ereignis wird von einer Anzahl an Spalten beschrieben. Die Spalten, die ein Ablaufverfolgungsereignis beschreiben, sind für alle Ereignisse konsistent und entsprechen der SQL-Ablaufverfolgungsstruktur. Die in den einzelnen Spalten enthaltenen Informationen können je nach Ereignisklasse variieren. Ein vordefinierter Satz Spalten ist also für jede Ablaufverfolgung definiert, die Bedeutung der Spalten kann sich jedoch abhängig von der Ereignisklasse ändern. Beispielsweise wird die TextData-Spalte dazu verwendet, die ursprüngliche ASSL für alle Anweisungsereignisse aufzuzeichnen.  
  
 Eine Ablaufverfolgungsdefinition kann eine oder mehrere Ereignisklassen enthalten, die gleichzeitig verfolgt werden sollen. Für jede Ereignisklasse kann mindestens eine Datenspalte zur Ablaufverfolgungsdefinition hinzugefügt werden. Jedoch müssen nicht alle Ablaufverfolgungsspalten verwendet werden. Der Datenbankadministrator kann entscheiden, welche der verfügbaren Spalten in eine Ablaufverfolgung einbezogen werden soll. Weiterhin können Ereignisklassen auf Grundlage von Filterkriterien in einer beliebigen Spalte in der Ablaufverfolgung selektiv verfolgt werden.  
  
 Ablaufverfolgungen können gestartet und gelöscht werden. Mehrere Ablaufverfolgungen können gleichzeitig ausgeführt werden. Ablaufverfolgungsereignisse können live aufgezeichnet oder an eine Datei weitergeleitet und später analysiert und wiedergegeben werden. [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]-Ablaufverfolgungsereignisse werden mit dem Tool [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] analysiert und wiedergegeben. Mehrere Verbindungen sind zulässig, um Ereignisse aus derselben Ablaufverfolgung erhalten.  
  
 Ablaufverfolgungen können in zwei Gruppen unterteilt werden: Serverablaufverfolgungen und Sitzungsablaufverfolgungen. Serverablaufverfolgungen bieten Informationen zu allen Ereignissen auf dem Server; Sitzungsablaufverfolgungen bieten nur Informationen zu Ereignissen in der aktuellen Sitzung.  
  
 Ablaufverfolgungen über die Auflistung der Ablaufverfolgungen auf dem Server werden folgendermaßen definiert:  
  
1.  Erstellen Sie ein <xref:Microsoft.AnalysisServices.Trace>-Objekt, und füllen Sie seine grundlegenden Daten aus, einschließlich Ablaufverfolgungs-ID, Name, Name der Protokolldatei, Anfügen/Überschreiben und andere.  
  
2.  Fügen Sie der Events-Auflistung des Ablaufverfolgungsobjekts Ereignisse hinzu, die überwacht werden sollen. Für jedes Ereignis werden Datenspalten hinzugefügt.  
  
3.  Legen Sie Filter fest, um unnötige Zeilen mit Daten auszuschließen, indem Sie diese zur Filterauflistung hinzufügen.  
  
4.  Starten Sie die Ablaufverfolgung; durch das Erstellen der Ablaufverfolgung wird die Datensammlung nicht gestartet.  
  
5.  Beenden Sie die Ablaufverfolgung.  
  
6.  Überprüfen Sie die Ablaufverfolgungsdatei mit [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)].  
  
 Ablaufverfolgungen über das Sitzungsobjekt werden folgendermaßen abgerufen:  
  
1.  Definieren Sie Funktionen, um die in der Anwendung mithilfe von SessionTrace generierten Ablaufverfolgungsereignisse zu handhaben. Mögliche Ereignisse sind OnEvent und Stopped.  
  
2.  Fügen Sie dem Ereignishandler Ihre definierten Funktionen hinzu.  
  
3.  Starten Sie die Ablaufverfolgung der Sitzung.  
  
4.  Führen Sie Ihren Prozess aus, und lassen Sie die Funktionshandler die Ereignisse aufzeichnen.  
  
5.  Beenden Sie die Ablaufverfolgung der Sitzung.  
  
6.  Fahren Sie mit der Anwendung fort.  
  
##  <a name="CaptureLog"></a> CaptureLog-Klasse und CaptureXML-Attribut  
 Alle Aktionen, die von AMO ausgeführt werden sollen, werden als XMLA-Nachrichten an den Server gesendet. AMO stellt die Mittel bereit, alle diese Nachrichten ohne die SOAP-Header aufzuzeichnen. Weitere Informationen finden Sie unter [Einführung in AMO-Klassen](amo-classes-introduction.md). CaptureLog ist der Mechanismus in AMO, der für das Ausgeben von Objekten und Vorgängen verwendet wird. Für die Objekte und Vorgänge werden in XMLA Skripts erstellt.  
  
 Damit Sie mit dem Aufzeichnen der XML-Elemente beginnen können, muss die CaptureXML-Serverobjekteigenschaft auf `true` festgelegt werden. Anschließend werden alle Aktionen, die an den Server gesendet werden sollen, in der CaptureLog-Klasse aufgezeichnet, ohne dass die Aktionen an den Server gesendet werden. CaptureLog kann als Klasse betrachtet werden, da es eine Methode (Clear) aufweist, die zum Löschen des Aufzeichnungsprotokolls dient.  
  
 Um das Protokoll zu lesen, rufen Sie die Zeichenfolgenauflistung ab, und beginnen Sie mit dem Durchlaufen der Zeichenfolgen. Sie können auch alle Protokolle in einer Zeichenfolge verketten, indem Sie die Serverobjektmethode ConcatenateCaptureLog verwenden. ConcatenateCaptureLog weist drei Parameter auf, von denen zwei erforderlich sind. Die erforderlichen Parameter *transaktionale*, des booleschen Typs und *parallele*, des booleschen Typs. Wenn *transaktionale* nastaven NA hodnotu `true`, bedeutet dies, dass die XML-Batchdatei erstellt wird, wie eine einzelne Transaktion nicht jeder Befehl als separate Transaktion behandelt. Wenn *parallele* nastaven NA hodnotu `true`, bedeutet dies, dass alle Befehle in der Batchdatei für die gleichzeitige Ausführung nicht sequenziell aufgezeichnet werden werden, wie sie aufgezeichnet wurden.  
  
##  <a name="AMO"></a> AMOException-Ausnahmeklasse  
 Sie können die AMOException-Ausnahmeklasse verwenden, um Ausnahmen in Ihrer Anwendung, die von AMO ausgegeben werden, einfach abzufangen.  
  
 AMO löst bei verschiedenen Problemen Ausnahmen aus. In der folgenden Tabelle wird die Art von Ausnahmen, die von AMO behandelt werden, aufgelistet. Ausnahmen werden von <xref:Microsoft.AnalysisServices.AmoException> abgeleitet.  
  
|Exception|Ursprung|Description|  
|---------------|------------|-----------------|  
|<xref:Microsoft.AnalysisServices.AmoException>|Basisklasse|Die Anwendung empfängt diese Ausnahme, wenn ein erforderliches übergeordnetes Objekt fehlt oder wenn ein erforderliches Element nicht in einer Auflistung auffindbar ist.|  
|<xref:Microsoft.AnalysisServices.OutOfSyncException>|Abgeleitet von AMOException|Die Anwendung empfängt diese Ausnahme, wenn AMO nicht mit der Engine synchronisiert ist und die Engine einen Objektverweis zurückgibt, der AMO unbekannt ist.|  
|<xref:Microsoft.AnalysisServices.OperationException>|Abgeleitet von AMOException|Dies ist eine wichtige Ausnahme, die häufig von Anwendungen empfangen wird. Diese Ausnahme enthält die Details eines Fehlers, der vom Server stammt. Die Ursache ist wahrscheinlich ein fehlerhafter AMO-Vorgang wie Update oder Process oder Drop.|  
|<xref:Microsoft.AnalysisServices.ResponseFormatException>|Abgeleitet von AMOException|Diese Ausnahme tritt auf, wenn die Engine eine Meldung in einem Format zurückgibt, das AMO nicht versteht.|  
|<xref:Microsoft.AnalysisServices.ConnectionException>|Abgeleitet von AMOException|Diese Ausnahme tritt auf, wenn eine Verbindung nicht hergestellt werden kann (mit Server Connect) oder wenn die Verbindung getrennt wird, während AMO Daten mit der Engine austauscht (beispielsweise während eines Update-, Process- oder Drop-Vorgangs).|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.AnalysisServices>   
 [Einführung in AMO-Klassen](amo-classes-introduction.md)   
 [Logische Architektur &#40;Analysis Services – mehrdimensionale Daten&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Datenbankobjekte &#40;Analysis Services – mehrdimensionale Daten&#41;](../olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
