---
title: Überprüfen, ob die automatische Vergrößerung für alle Daten-und Protokolldateien während des Upgradevorgangs aktiviert ist | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], size
- data files [SQL Server], size
- tempdb [SQL Server], size
- autogrow [SQL Server]
ms.assetid: a5860904-e2be-4224-8a51-df18a10d3fb9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8ca12075598bce210a905cbdfba89f2d879cf09b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065191"
---
# <a name="verify-autogrow-is-turned-on-for-all-data-and-log-files-during-the-upgrade-process"></a>Überprüfen, ob für alle Daten- und Protokolldateien die automatische Vergrößerung während des Upgradeprozesses aktiviert ist
  Upgrade Advisor hat Daten- oder Protokolldateien erkannt, für die die automatische Vergrößerung nicht festgelegt ist. Neue und erweiterte Features erfordern zusätzlichen Speicherplatz für Benutzer Datenbanken und die **tempdb** -Systemdatenbank. Um sicherzustellen, dass Ressourcen während des Upgrades und bei nachfolgenden Produktions Vorgängen Größen Steigerungen berücksichtigen können, empfiehlt es sich, für alle Benutzerdaten-und-Protokolldateien und die **tempdb** -Daten-und-Protokolldateien vor dem Upgrade die automatische Vergrößerung  
  
 Nachdem Sie Ihre Arbeitsauslastungen aktualisiert und getestet haben, können Sie die automatische Vergrößerung auf OFF festlegen oder das FILEGROWTH-Inkrement für Benutzerdaten- und Protokolldateien entsprechend anpassen. Es wird empfohlen, die automatische Vergrößerung für die **tempdb** -Systemdatenbank auf on festhalten. Weitere Informationen finden Sie unter "Kapazitätsplanung für tempdb" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 **Datendateien**  
  
 In der folgenden Tabelle sind Änderungen an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen aufgelistet, die zusätzlichen Speicherplatz für benutzerdefinierte Datendateien erforderlich machen.  
  
|Funktion|In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeführte Änderungen|  
|-------------|-----------------------------------------------------|  
|Volltext|Die Zuordnung der Dokument-ID (DOCID) wird in der Datendatei statt im Volltextkatalog gespeichert.|  
|`text`-, `ntext`- und `image`-Spalten|LOB-Spalten (Large Object), die als Datentypen `text`, `ntext` oder `image` definiert sind, erfordern 40 Byte zusätzlichen Speicherplatz pro Spalte. Diese einmalige Speicherplatzerweiterung erfolgt beim ersten Update der jeweiligen LOB-Spalte.|  
|metadata|Für Datenbankobjekte und Benutzerberechtigungen werden zusätzliche Systemmetadaten in der PRIMARY-Dateigruppe der einzelnen Benutzerdatenbanken erstellt und verwaltet. In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden die Berechtigungen, die mit einem Berechtigenden (GRANTOR) oder einer Empfängerliste verknüpft sind, in einer einzigen Zeile als Bitmap gespeichert. Die Bitmap wird auf mehrere Zeilen ausgedehnt.<br /><br /> Während des Updateprozesses muss ausreichend Speicherplatz zur Verfügung stehen, um sowohl die alten als auch die neuen Metadaten zu speichern. Die alten Metadaten werden nach dem Upgrade gelöscht.|  
  
 **Transaktionsprotokolldateien**  
  
 In der folgenden Tabelle sind Änderungen an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen aufgelistet, die zusätzlichen Speicherplatz für Transaktionsprotokolldateien erforderlich machen.  
  
|Funktion|In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeführte Änderungen|  
|-------------|-----------------------------------------------------|  
|Wiederherstellung|Während der Rollbackphase einer Wiederherstellung nach einem Systemabsturz ermöglicht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] es Benutzern, auf die Datenbank zuzugreifen. Dies ist möglich, weil die Transaktionen, für die zum Zeitpunkt des Systemabsturzes noch kein Commit durchgeführt wurde, alle Sperren erneut abrufen, die sie vor dem Crash aufrechterhalten haben. Während für diese Transaktionen ein Rollback durchgeführt wird, schützen ihre Sperren sie vor Eingriffen seitens der Benutzer. Diese zusätzlichen Sperrinformationen müssen im Transaktionsprotokoll verwaltet werden.|  
  
 **tempdb-Daten- und Protokolldateien**  
  
 In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird die **tempdb** -Datenbank zum Speichern der folgenden Objekte verwendet:  
  
-   Temporäre Objekte, die explizit erstellt werden, z. B. Tabellen, gespeicherte Prozeduren, Tabellenvariablen oder Cursor  
  
-   Interne vom [!INCLUDE[ssDE](../../includes/ssde-md.md)] erstellte Arbeitstabellen  
  
-   Ergebnisse temporärer Sortierungen, wenn Sie Indizes erstellen oder neu erstellen, sofern SORT_IN_TEMPDB angegeben ist  
  
 Zusätzliche Objekte verwenden auch die **tempdb** -Datenbank. In der folgenden Tabelle sind Änderungen oder Erweiterungen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Features aufgeführt, die zu zusätzlichen Speicherplatzanforderungen für **tempdb** -Daten-und-Protokolldateien führen.  
  
|Funktion|In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeführte Änderungen|  
|-------------|-----------------------------------------------------|  
|Zeilenversionsverwaltung|Die Zeilenversionsverwaltung ist ein allgemeines Framework in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Es wird für folgende Aufgaben verwendet:<br /><br /> Unterstützungs Trigger: Erstellen Sie die eingefügten und gelöschten Tabellen in Triggern. Für alle durch den Trigger geänderten Zeilen wird die Versionsverwaltung verwendet. Das schließt die Zeilen ein, die durch die Anweisung geändert wurden, mit der der Start des Triggers erfolgte, sowie alle vom Trigger bewirkten Datenänderungen. AFTER-Trigger verwenden den Versionsspeicher von **tempdb** , um die before-Bilder der vom Trigger geänderten Zeilen zu speichern. Beim Massenladen von Daten mit aktivierten Triggern wird dem Versionsspeicher eine Kopie jeder Zeile hinzugefügt.<br /><br /> Unterstützen von Multiple Active Result Sets (MARS). Wenn eine MARS-Sitzung eine Datenänderungsanweisung (z. B. INSERT, UPDATE oder DELETE) ausgibt, während es ein aktives Resultset gibt, wird für die von der Änderungsanweisung betroffenen Zeilen die Versionsverwaltung verwendet.<br /><br /> Unterstützen von Indexvorgängen, die die ONLINE-Option angeben. Onlineindexvorgänge verwenden die Zeilenversionsverwaltung, um den Indexvorgang von den Auswirkungen der Änderungen zu isolieren, die von anderen Transaktionen vorgenommen wurden. Auf diese Weise ist es nicht erforderlich, freigegebene Sperren für Zeilen anzufordern, die gelesen wurden. Außerdem erfordern gleichzeitige benutzeraktualisierungs-und Löschvorgänge während Online Index Vorgängen Speicherplatz für Versionsdaten Sätze in **tempdb**.<br /><br /> Unterstützung von auf Zeilen Versionsverwaltung basierenden Transaktions Isolations Stufen: eine neue Implementierung der Isolationsstufe "Read Commit", die die Zeilen Versionsverwaltung verwendet, um Lese Konsistenz auf Anweisungs Ebene bereitzustellen Eine neue Isolationsstufe – Momentaufnahme, um die Lesekonsistenz auf der Transaktionsebene zu gewährleisten.<br /><br /> <br /><br /> Zeilen Versionen werden im **tempdb** -Versionsspeicher lange genug aufbewahrt, um den Anforderungen von Transaktionen gerecht zu werden, die unter auf Zeilen Versionsverwaltung basierenden Isolations Stufen ausgeführt werden.<br /><br /> Weitere Informationen über die Zeilenversionsverwaltung und den Versionsspeicher finden Sie im Thema "Grundlegendes zu zeilenversionsbasierten Isolationsstufen" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.|  
|Zwischenspeichern von Metadaten temporärer Tabellen und temporärer Variablen|Für alle Metadaten temporärer Tabellen und temporärer Variablen, die im Metadatencache von zwischengespeichert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden, werden zwei zusätzliche Seiten für **tempdb**zugeordnet.<br /><br /> Wenn eine gespeicherte Prozedur oder ein Trigger eine temporäre Tabelle oder eine temporäre Variable erstellt, wird das temporäre Objekt nach Ausführung der Prozedur bzw. des Triggers nicht gelöscht. Stattdessen wird das temporäre Objekt auf eine Seite gekürzt und wiederverwendet, wenn die Prozedur oder der Trigger das nächste Mal ausgeführt wird.|  
|Indizes für partitionierte Tabellen|Wenn das [!INCLUDE[ssDE](../../includes/ssde-md.md)] Sortieren zum Erstellen partitionierter Indizes durchführt, ist ausreichend Speicherplatz für die zwischen Sortier Läufe jeder Partition in **tempdb** erforderlich, wenn die SORT_IN_TEMPDB Index-Option angegeben wird.|  
|[!INCLUDE[ssSB](../../includes/sssb-md.md)]|[!INCLUDE[ssSB](../../includes/sssb-md.md)]verwendet **tempdb** explizit, wenn vorhandener Dialog Kontext beibehalten wird, der nicht im Speicher verbraucht werden kann (ungefähr 1 KB pro Dialogfeld).<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)]verwendet **tempdb** implizit durch das Zwischenspeichern von Objekten im Kontext der Abfrage Ausführung. Zum Beispiel Arbeitstabellen, die für Zeitgeberereignisse und im Hintergrund übermittelte Konversationen verwendet werden.<br /><br /> Die Funktionen DBMail, Ereignisbenachrichtigungen und Abfragebenachrichtigungen verwenden implizit [!INCLUDE[ssSB](../../includes/sssb-md.md)].|  
|LOB-Datentyp (Large Object)<br /><br /> LOB-Variablen und -Parameter|Die Datentypen `varchar(max)` , `nvarchar(max)` , **varbinary (max) Text**, `ntext` `image,` und `xml` sind große Objekttypen.<br /><br /> Wenn eine auf der Zeilen Versionsverwaltung basierende Transaktions Isolationsstufe in der Datenbank aktiviert ist und Änderungen an großen Objekten vorgenommen werden, wird das geänderte Fragment des LOB-Objekts in den Versionsspeicher in **tempdb**kopiert.<br /><br /> Als LOB-Datentyp definierte Parameter werden in **tempdb**gespeichert.|  
|Allgemeine Tabellenausdrücke|Temporäre Arbeits Tabellen für Spoolvorgänge werden in **tempdb** erstellt, wenn allgemeine Tabellen Ausdrucksabfragen ausgeführt werden.|  
  
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
|500 MB oder mehr|10 %|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
