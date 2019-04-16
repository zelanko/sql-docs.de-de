---
title: Überprüfen Sie die automatische Vergrößerung ist für alle Daten und Protokolldateien auf aktiviert, während des Upgradevorgangs | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], size
- data files [SQL Server], size
- tempdb [SQL Server], size
- autogrow [SQL Server]
ms.assetid: a5860904-e2be-4224-8a51-df18a10d3fb9
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ab29cc94071b95f6ff8cffb95902851d1796ed80
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59583273"
---
# <a name="verify-autogrow-is-turned-on-for-all-data-and-log-files-during-the-upgrade-process"></a>Überprüfen, ob für alle Daten- und Protokolldateien die automatische Vergrößerung während des Upgradeprozesses aktiviert ist
  Upgrade Advisor hat Daten- oder Protokolldateien erkannt, für die die automatische Vergrößerung nicht festgelegt ist. Neue und verbesserte Funktionen erfordern zusätzlichen freien Speicherplatz für Benutzerdatenbanken und die **Tempdb** -Systemdatenbank. Um sicherzustellen, dass Ressourcen können Sie größenerweiterungen beim Upgrade und bei nachfolgenden Produktionsvorgängen, die durch die automatische Vergrößerung für alle Benutzer Daten und Protokolldateien auf empfohlen und **Tempdb** Daten- und Protokolldateien Dateien vor dem Upgrade.  
  
 Nachdem Sie Ihre Arbeitsauslastungen aktualisiert und getestet haben, können Sie die automatische Vergrößerung auf OFF festlegen oder das FILEGROWTH-Inkrement für Benutzerdaten- und Protokolldateien entsprechend anpassen. Es wird empfohlen, die automatische Vergrößerung auf für die **Tempdb** -Systemdatenbank. Weitere Informationen finden Sie unter "Kapazitätsplanung für tempdb" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 **Datendateien**  
  
 In der folgenden Tabelle sind Änderungen an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen aufgelistet, die zusätzlichen Speicherplatz für benutzerdefinierte Datendateien erforderlich machen.  
  
|Funktion|In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeführte Änderungen|  
|-------------|-----------------------------------------------------|  
|Volltext|Die Zuordnung der Dokument-ID (DOCID) wird in der Datendatei statt im Volltextkatalog gespeichert.|  
|`text`-, `ntext`- und `image`-Spalten|LOB-Spalten (Large Object), die als Datentypen `text`, `ntext` oder `image` definiert sind, erfordern 40 Byte zusätzlichen Speicherplatz pro Spalte. Diese einmalige Speicherplatzerweiterung erfolgt beim ersten Update der jeweiligen LOB-Spalte.|  
|Metadaten|Für Datenbankobjekte und Benutzerberechtigungen werden zusätzliche Systemmetadaten in der PRIMARY-Dateigruppe der einzelnen Benutzerdatenbanken erstellt und verwaltet. In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden die Berechtigungen, die mit einem Berechtigenden (GRANTOR) oder einer Empfängerliste verknüpft sind, in einer einzigen Zeile als Bitmap gespeichert. Die Bitmap wird auf mehrere Zeilen ausgedehnt.<br /><br /> Während des Updateprozesses muss ausreichend Speicherplatz zur Verfügung stehen, um sowohl die alten als auch die neuen Metadaten zu speichern. Die alten Metadaten werden nach dem Upgrade gelöscht.|  
  
 **Transaktionsprotokolldateien**  
  
 In der folgenden Tabelle sind Änderungen an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen aufgelistet, die zusätzlichen Speicherplatz für Transaktionsprotokolldateien erforderlich machen.  
  
|Funktion|In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeführte Änderungen|  
|-------------|-----------------------------------------------------|  
|Wiederherstellung|Während der Rollbackphase einer Wiederherstellung nach einem Systemabsturz ermöglicht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] es Benutzern, auf die Datenbank zuzugreifen. Dies ist möglich, weil die Transaktionen, für die zum Zeitpunkt des Systemabsturzes noch kein Commit durchgeführt wurde, alle Sperren erneut abrufen, die sie vor dem Crash aufrechterhalten haben. Während für diese Transaktionen ein Rollback durchgeführt wird, schützen ihre Sperren sie vor Eingriffen seitens der Benutzer. Diese zusätzlichen Sperrinformationen müssen im Transaktionsprotokoll verwaltet werden.|  
  
 **Daten- und Tempdb-Dateien**  
  
 In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **Tempdb** Datenbank dient zum Speichern der folgenden Objekte:  
  
-   Temporäre Objekte, die explizit erstellt werden, z. B. Tabellen, gespeicherte Prozeduren, Tabellenvariablen oder Cursor  
  
-   Interne vom [!INCLUDE[ssDE](../../includes/ssde-md.md)] erstellte Arbeitstabellen  
  
-   Ergebnisse temporärer Sortierungen, wenn Sie Indizes erstellen oder neu erstellen, sofern SORT_IN_TEMPDB angegeben ist  
  
 Verwenden auch zusätzliche Objekte die **Tempdb** Datenbank. Die folgende Tabelle enthält Änderungen und Ergänzungen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Features, die zusätzlichen Speicherplatz für **Tempdb** Daten-und Protokolldateien.  
  
|Funktion|In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeführte Änderungen|  
|-------------|-----------------------------------------------------|  
|Zeilenversionsverwaltung|Die Zeilenversionsverwaltung ist ein allgemeines Framework in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Es wird für folgende Aufgaben verwendet:<br /><br /> Unterstützung von Triggern: Erstellen der inserted- und deleted-Tabellen in Triggern. Für alle durch den Trigger geänderten Zeilen wird die Versionsverwaltung verwendet. Das schließt die Zeilen ein, die durch die Anweisung geändert wurden, mit der der Start des Triggers erfolgte, sowie alle vom Trigger bewirkten Datenänderungen. AFTER-Trigger den Versionsspeicher von **Tempdb** zum Speichern der vor der Images, der vom Trigger geänderten Zeilen. Beim Massenladen von Daten mit aktivierten Triggern wird dem Versionsspeicher eine Kopie jeder Zeile hinzugefügt.<br /><br /> Unterstützen von Multiple Active Result Sets (MARS). Wenn eine MARS-Sitzung eine Datenänderungsanweisung (z. B. INSERT, UPDATE oder DELETE) ausgibt, während es ein aktives Resultset gibt, wird für die von der Änderungsanweisung betroffenen Zeilen die Versionsverwaltung verwendet.<br /><br /> Unterstützen von Indexvorgängen, die die ONLINE-Option angeben. Onlineindexvorgänge verwenden die Zeilenversionsverwaltung, um den Indexvorgang von den Auswirkungen der Änderungen zu isolieren, die von anderen Transaktionen vorgenommen wurden. Auf diese Weise ist es nicht erforderlich, freigegebene Sperren für Zeilen anzufordern, die gelesen wurden. Darüber hinaus die gleichzeitige Update- und Löschvorgänge während Onlineindexvorgänge erfordern Speicherplatz für Versionsdatensätze in **Tempdb**.<br /><br /> Unterstützen von auf der Zeilenversionsverwaltung basierenden Transaktionsisolationsstufen: Eine neue Implementierung der Read Committed-Isolationsstufe, die die Zeilenversionsverwaltung verwendet, um die Lesekonsistenz auf Anweisungsebene zu gewährleisten. Eine neue Isolationsstufe – Momentaufnahme, um die Lesekonsistenz auf der Transaktionsebene zu gewährleisten.<br /><br /> <br /><br /> Zeilenversionen werden der **Tempdb** -Versionsspeicher lange genug aufbewahrt, um die Anforderungen von Transaktionen, die unter zeilenversionsbasierten Isolationsstufen erfüllen.<br /><br /> Weitere Informationen über die Zeilenversionsverwaltung und den Versionsspeicher finden Sie im Thema "Grundlegendes zu zeilenversionsbasierten Isolationsstufen" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.|  
|Zwischenspeichern von Metadaten temporärer Tabellen und temporärer Variablen|Für alle Metadaten temporärer Tabellen und temporärer Variablen, die im Metadatencache von zwischengespeicherten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], werden zwei extraseiten für zugeordnet **Tempdb**.<br /><br /> Wenn eine gespeicherte Prozedur oder ein Trigger eine temporäre Tabelle oder eine temporäre Variable erstellt, wird das temporäre Objekt nach Ausführung der Prozedur bzw. des Triggers nicht gelöscht. Stattdessen wird das temporäre Objekt auf eine Seite gekürzt und wiederverwendet, wenn die Prozedur oder der Trigger das nächste Mal ausgeführt wird.|  
|Indizes für partitionierte Tabellen|Wenn die [!INCLUDE[ssDE](../../includes/ssde-md.md)] Sortiervorgänge zum Erstellen von partitionierten Indizes, ausreichend Speicherplatz für die Zwischensortierläufe jeder Partition ist erforderlich, durchführt **Tempdb** , wenn die SORT_IN_TEMPDB-Indexoption angegeben ist.|  
|[!INCLUDE[ssSB](../../includes/sssb-md.md)]|[!INCLUDE[ssSB](../../includes/sssb-md.md)] explizit verwendet **Tempdb** bei vorhandenen dialogkontexts, der im Arbeitsspeicher (ca. 1 KB pro Dialogfeld) verbleiben kann.<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)] verwendet implizit **Tempdb** durch das Zwischenspeichern von Objekten im Kontext der abfrageausführung. Zum Beispiel Arbeitstabellen, die für Zeitgeberereignisse und im Hintergrund übermittelte Konversationen verwendet werden.<br /><br /> Die Funktionen DBMail, Ereignisbenachrichtigungen und Abfragebenachrichtigungen verwenden implizit [!INCLUDE[ssSB](../../includes/sssb-md.md)].|  
|LOB-Datentyp (Large Object)<br /><br /> LOB-Variablen und -Parameter|Die Datentypen `varchar(max)`, `nvarchar(max)`, **Varbinary (Max) Text**, `ntext`, `image,` und `xml` LOB-Typen sind.<br /><br /> Wenn eine Transaktion auf zeilenversionsverwaltung basierende Isolationsstufe für die Datenbank aktiviert ist, und Änderungen von großen Objekten vorgenommen werden, wird das geänderte Fragment des LOB-OBJEKTS in den Versionsspeicher in kopiert **Tempdb**.<br /><br /> Als LOB-Datentyp definierte Parameter befinden sich im **Tempdb**.|  
|Allgemeine Tabellenausdrücke|Temporäre Arbeitstabellen für spoolvorgänge werden in erstellt **Tempdb** wenn allgemeine tabellenausdrucksabfragen ausgeführt werden.|  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Um die automatische Vergrößerung für eine Daten- oder Protokolldatei festzulegen, ändern Sie die folgenden Anweisungen, um die Daten und das Protokoll für Ihre Datenbank anzugeben. Sie sollten das FILEGROWTH-Inkrement auf einen Wert einstellen, der für Ihr System geeignet ist.  
  
```  
ALTER DATABASE tempdb  
MODIFY FILE  
    (NAME = tempdev,  
    FILEGROWTH = 20MB);  
GO  
ALTER DATABASE tempdb  
MODIFY FILE  
    (NAME = templog,  
    FILEGROWTH = 10MB);  
```  
  
 Der Standardwert des Vergrößerungsinkrements für Datendateien beträgt 1 MB. Der Standardwert für Protokolldateien beträgt 10 %. Beim Festlegen des FILEGROWTH-Inkrements sollten die folgenden Richtlinien eingehalten werden:  
  
|Dateigröße|FILEGROWTH-Inkrement|  
|---------------|--------------------------|  
|0 - 50 MB|10 MB|  
|100 - 200 MB|20 MB|  
|500 MB oder mehr|10%|  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
