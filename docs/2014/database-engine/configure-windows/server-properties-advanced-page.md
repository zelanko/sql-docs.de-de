---
title: Servereigenschaften (Seite „Erweitert)“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.advanced.f1
ms.assetid: cc5e65c2-448e-4f37-9ad4-2dfb1cc84ebe
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 998d42d262e3f980b4b35ed82b26904399d6b33c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62809381"
---
# <a name="server-properties-advanced-page"></a>Servereigenschaften (Seite Erweitert)
  Auf dieser Seite können Sie die erweiterten Servereinstellungen anzeigen und ändern.  
  
 **So zeigen Sie die Seite Servereigenschaften an**  
  
-   [Anzeigen oder Ändern von Servereigenschaften &#40;SQL Server&#41;](view-or-change-server-properties-sql-server.md)  
  
## <a name="containment"></a>Containment  
 Aktivieren enthaltener Datenbanken  
 Gibt an, ob diese Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eigenständige Datenbanken zulässt. Bei **True**kann eine eigenständige Datenbank erstellt, wiederhergestellt oder angefügt werden. Bei **False**kann keine eigenständige Datenbank erstellt, wiederhergestellt oder an diese Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]angefügt werden. Wenn die Einschlusseigenschaft geändert wird, kann sich dies auf die Sicherheit der Datenbank auswirken. Durch das Aktivieren eigenständiger Datenbanken gewährt der Datenbankbesitzer Zugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn eigenständige Datenbanken deaktiviert werden, können Benutzer u. U. keine Verbindung herstellen. Wie sich die Einschlusseigenschaft auswirken kann, erfahren Sie unter [Contained Databases](../../relational-databases/databases/contained-databases.md) und [Security Best Practices with Contained Databases](../../relational-databases/databases/security-best-practices-with-contained-databases.md).  
  
## <a name="filestream"></a>FILESTREAM  
 **FILESTREAM-Zugriffsebene**  
 Zeigt die aktuelle Ebene der FILESTREAM-Unterstützung auf der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]an. Um die Zugriffsebene zu ändern, wählen Sie einen der folgenden Werte aus:  
  
 **Disabled**  
 Binary Large Object-Daten (BLOB) können nicht auf dem Dateisystem gespeichert werden. Dies ist der Standardwert.  
  
 **Transact-SQL-Zugriff aktiviert**  
 Auf FILESTREAM-Daten kann mit [!INCLUDE[tsql](../../includes/tsql-md.md)]zugegriffen werden, aber nicht über das Dateisystem.  
  
 **Vollzugriff aktiviert**  
 Auf FILESTREAM-Daten kann mit [!INCLUDE[tsql](../../includes/tsql-md.md)] und über das Dateisystem zugegriffen werden.  
  
 Wenn Sie FILESTREAM zum ersten Mal aktivieren, müssen Sie den Computer möglicherweise neu starten, um Treiber zu konfigurieren.  
  
 **FILESTREAM-Freigabename**  
 Zeigt den schreibgeschützten Namen der FILESTREAM-Freigabe an, die während des Setups ausgewählt wurde. Weitere Informationen finden Sie unter [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md).  
  
## <a name="miscellaneous"></a>Sonstiges  
 **Triggern ermöglichen, weitere Trigger auszulösen**  
 Ermöglicht Triggern, weitere Trigger auszulösen. Trigger können maximal 32 Ebenen tief geschachtelt werden. Weitere Informationen finden Sie im Abschnitt „Geschachtelte Trigger“ unter [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).  
  
 **Schwellenwert für blockierte Prozesse**  
 Der Schwellenwert in Sekunden, bei dem blockierte Prozessberichte generiert werden. Der Schwellenwert kann auf einen Wert zwischen 0 und 86.400 festgelegt werden. Standardmäßig werden für blockierte Prozesse keine Berichte erstellt. Weitere Informationen finden Sie unter [Schwellenwert für blockierte Prozesse (Serverkonfigurationsoption)](blocked-process-threshold-server-configuration-option.md).  
  
 **Cursorschwellenwert**  
 Gibt die Anzahl der Zeilen im Cursorset an, bei der asynchron Cursor-Keysets generiert werden. Wenn Cursor ein Keyset für ein Resultset generieren, schätzt der Abfrageoptimierer die Anzahl der Zeilen, die für dieses Resultset zurückgegeben werden. Wenn der Abfrageoptimierer schätzt, dass die Anzahl der zurückgegebenen Zeilen über diesem Schwellenwert liegt, wird der Cursor asynchron generiert. Dadurch kann der Benutzer Zeilen aus dem Cursor abrufen, während der Cursor weiterhin aufgefüllt wird. Andernfalls wird der Cursor synchron generiert, und die Abfrage wartet, bis alle Zeilen zurückgegeben wurden.  
  
 Wenn als Wert -1 festgelegt ist, werden alle Keysets synchron generiert. Dies ist für kleine Cursorsets von Vorteil. Bei einem Wert von 0 werden alle Cursor-Keysets asynchron generiert. Bei anderen Werten vergleicht der Abfrageoptimierer die Anzahl der erwarteten Zeilen im Cursorset und erstellt das Keyset asynchron, wenn die Anzahl der als Cursorschwellenwert festgelegten Zeilen überschritten wird. Weitere Informationen finden Sie unter [Konfigurieren der Serverkonfigurationsoption Cursorschwellenwert](configure-the-cursor-threshold-server-configuration-option.md).  
  
 **Volltext-Standardsprache**  
 Gibt eine Standardsprache für Spalten mit Volltextindex an. Linguistische Analysen von Daten mit Volltextindex werden von der Sprache der Daten bestimmt. Der Standardwert für diese Option ist die Sprache des Servers. Informationen zu der Sprache, die der angezeigten Einstellung entspricht, finden Sie unter [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).  
  
 **Standardsprache**  
 Die Standardsprache für alle neuen Anmeldungen, sofern nicht anders angegeben.  
  
 **Volltextupgrade-Option**  
 Steuert, wie Volltextindizes migriert werden, wenn Sie für eine Datenbank ein Upgrade von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]ausführen. Diese Eigenschaft ist für die folgenden Aktionen gültig: Upgrade durch Anfügen einer Datenbank, Wiederherstellen einer Datenbanksicherung, Wiederherstellen einer Dateisicherung oder Kopieren der Datenbank mit dem Assistenten zum Kopieren von Datenbanken.  
  
 Die Alternativen lauten folgendermaßen:  
  
 **Importieren**  
 Volltextkataloge werden importiert. Dieser Vorgang ist bedeutend schneller als die Verwendung von **Neu erstellen**. Ein importierter Volltextkatalog verwendet jedoch nicht die neuen mit [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]eingeführten Wörtertrennungen. Aus diesem Grund sollten Sie die Volltextkataloge zu einem späteren Zeitpunkt neu erstellen.  
  
 Wenn ein Volltextkatalog nicht verfügbar ist, werden die zugehörigen Volltextindizes neu erstellt. Diese Option ist nur für [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Datenbanken verfügbar.  
  
 **Neuerstellen**  
 Volltextkataloge werden mithilfe der neuen und verbesserten Worttrennmodule neu erstellt. Das Neuerstellen von Indizes kann einige Zeit dauern, und nach dem Upgrade ist ggf. eine beträchtliche Menge an CPU-Leistung und Arbeitsspeicherkapazität erforderlich.  
  
 **Zurücksetzen**  
 Volltextkataloge werden zurückgesetzt. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Volltextkatalogdateien werden entfernt. Die Metadaten für die Volltextkataloge und die Volltextindizes bleiben jedoch erhalten. Nach der Upgrade wird die Änderungsnachverfolgung für alle Volltextindizes deaktiviert, und Durchforstungen werden nicht automatisch gestartet. Der Katalog bleibt leer, bis Sie ihn nach Beendigung des Upgrades manuell vollständig auffüllen.  
  
 Informationen zum Auswählen der Option für das Volltextupgrade finden Sie unter [Upgrade der Volltextsuche](../../relational-databases/search/upgrade-full-text-search.md).  
  
> [!NOTE]  
>  Die Option für das Volltextupgrade kann auch mit der [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)upgrade_option-Aktion festgelegt werden.  
  
 Nachdem Sie eine [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Datenbank in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]angehängt, wiederhergestellt oder kopiert haben, ist die Datenbank sofort verfügbar und wird automatisch aktualisiert. Wenn die Datenbank Volltextindizes aufweist, werden diese beim Upgrade entweder importiert, zurückgesetzt oder neu erstellt, je nach der Einstellung der Servereigenschaft **Volltextupgrade-Option** . Wenn die Upgradeoption auf **Importieren** oder **Neu erstellen**festgelegt ist, sind die Volltextindizes während des Upgrades nicht verfügbar. Je nach Menge der indizierten Daten kann der Importvorgang mehrere Stunden dauern; die Neuerstellung sogar bis zu zehnmal länger. Wenn die Upgradeoption auf **Importieren**festgelegt und kein Volltextkatalog verfügbar ist, werden die zugehörigen Volltextindizes neu erstellt. Informationen zum Anzeigen oder Ändern der Einstellung der Eigenschaft **Volltextupgrade-Option** finden Sie unter [Verwalten und Überwachen der Volltextsuche auf einer Serverinstanz](../../relational-databases/search/manage-and-monitor-full-text-search-for-a-server-instance.md).  
  
 **Max. Textgröße für Replikation**  
 Gibt die Maximalgröße (in Byte) der Daten vom Typ `text`, `ntext`, `varchar(max)`, `nvarchar(max)`, `xml` und `image`an, die einer replizierten oder aufgezeichneten Spalte in einer einzelnen Anweisung vom Typ INSERT, UPDATE, WRITETEXT oder UPDATETEXT hinzugefügt werden können. Die Änderung der Einstellung wird sofort wirksam. Weitere Informationen finden Sie unter [Konfigurieren der Serverkonfigurationsoption max text repl size](configure-the-max-text-repl-size-server-configuration-option.md).  
  
 **Startprozeduren suchen (Scan For Startup Procs)**  
 gibt an, dass von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beim Start nach der automatischen Ausführung gespeicherter Prozeduren gesucht wird. Bei **True**sucht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nach allen Prozeduren auf dem Server, für die eine automatische Ausführung definiert ist, und führt diese aus. Bei **False** (Standardeinstellung) wird keine Suche ausgeführt. Weitere Informationen finden Sie unter [Konfigurieren der Serverkonfigurationsoption Startprozeduren suchen](configure-the-scan-for-startup-procs-server-configuration-option.md).  
  
 **Umstellungsjahr für Angaben mit zwei Ziffern**  
 Gibt die höchste Zahl an, die als eine zweistellige Jahresangabe eingegeben werden kann. Das aufgeführte Jahr und die vorherigen 99 Jahre können als eine zweistellige Jahresangabe eingegeben werden. Alle anderen Jahre müssen als eine vierstellige Jahresangabe eingegeben werden.  
  
 Die Standardeinstellung 2049 zeigt beispielsweise an, dass ein als '3/14/49' eingegebenes Datum als 14. März 2049 und ein als '3/14/50' eingegebenes Datum als 14. März 1950 interpretiert wird. Weitere Informationen [Konfigurieren der Serverkonfigurationsoption Umstellungsjahr für Angaben mit zwei Ziffern](configure-the-two-digit-year-cutoff-server-configuration-option.md).  
  
## <a name="network"></a>Netzwerk  
 **Netzwerkpaketgröße**  
 Legt die im gesamten Netzwerk verwendete Paketgröße (in Bytes) fest. Der Standardwert ist 4096 Bytes. Wenn eine Anwendung Massenkopiervorgänge ausführt oder große Mengen an Daten vom Typ `text` oder `image` sendet bzw. empfängt, kann eine Paketgröße, die über der Standardgröße liegt, die Effizienz verbessern, da weniger Lese- und Schreibvorgänge im Netzwerk ausgeführt werden. Sendet und empfängt eine Anwendung kleine Mengen von Informationen, können Sie die Paketgröße auf 512 Bytes festlegen. Dies ist für die meisten Datenübertragungen ausreichend. Weitere Informationen finden Sie unter [Konfigurieren der Serverkonfigurationsoption Netzwerkpaketgröße](configure-the-network-packet-size-server-configuration-option.md).  
  
> [!NOTE]  
>  Sie sollten die Paketgröße nur dann ändern, wenn Sie sicher sind, dass die Leistung dadurch verbessert werden kann. Für die meisten Anwendungen empfiehlt sich die Standardpaketgröße.  
  
 **Timeout für Remoteanmeldung**  
 Gibt die Anzahl der Sekunden an, die bei einem fehlerhaften Remoteanmeldeversuch vergehen können, bis er von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als fehlerhaft abgebrochen wird. Diese Einstellung wirkt sich auf Verbindungen mit OLE DB-Anbietern aus, die für heterogene Abfragen hergestellt wurden. Der Standardwert ist 20 Sekunden. Bei einem Wert von 0 ist eine unbegrenzte Wartezeit zulässig. Weitere Informationen finden Sie unter [Konfigurieren der Serverkonfigurationsoption Timeout für Remoteanmeldungen](configure-the-remote-login-timeout-server-configuration-option.md).  
  
 Die Änderung der Einstellung wird sofort wirksam.  
  
## <a name="parallelism"></a>Parallelität:  
 **Kostenschwellenwert für Parallelität**  
 Gibt den Schwellenwert an, über dem von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] parallele Pläne für Abfragen erstellt und ausgeführt werden. Die Kosten beziehen sich auf eine geschätzte Zeit in Sekunden, die für das Ausführen des seriellen Plans bei einer bestimmten Hardwarekonfiguration benötigt wird. Aktivieren Sie diese Option nur bei symmetrischen Multiprozessorsystemen. Weitere Informationen finden Sie unter [Konfigurieren der Serverkonfigurationsoption Kostenschwellenwert für Parallelität](configure-the-cost-threshold-for-parallelism-server-configuration-option.md).  
  
 **Locks**  
 Legt die maximale Anzahl an verfügbaren Sperren fest. Gleichzeitig wird dadurch die Menge an Arbeitsspeicher begrenzt, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für diese Sperren verwendet wird. Die Standardeinstellung ist 0. Bei dieser Einstellung können von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] je nach Systemanforderungen Sperren dynamisch zugeordnet oder die Sperrenzuordnung aufgehoben werden.  
  
 Wenn Sperren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dynamisch verwendet werden dürfen, entspricht dies der empfohlenen Konfiguration. Weitere Informationen finden Sie unter [Konfigurieren der Serverkonfigurationsoption Sperren](configure-the-locks-server-configuration-option.md).  
  
 **Max. Grad an Parallelität**  
 Begrenzt die Anzahl der Prozessoren (auf maximal 64), die für die Ausführung paralleler Pläne verwendet werden können. Beim Standardwert von 0 werden alle verfügbaren Prozessoren verwendet. Bei einem Wert von 1 wird die Generierung paralleler Pläne unterdrückt. Bei einem Wert über 1 wird die maximale Anzahl der von einer Abfrageausführung verwendeten Prozessoren begrenzt. Wenn ein Wert angegeben wird, der über der Anzahl der verfügbaren Prozessoren liegt, wird die tatsächliche Anzahl der Prozessoren verwendet. Weitere Informationen finden Sie unter [Konfigurieren der Serverkonfigurationsoption Max. Grad an Parallelität](configure-the-max-degree-of-parallelism-server-configuration-option.md).  
  
 **Abfragewartezeit**  
 Gibt die Zeit in Sekunden an (von 0 bis 2147483647), die eine Abfrage auf Ressourcen wartet, bevor der Vorgang timeoutbedingt abgebrochen wird. Bei Verwendung des Standardwertes von –1 wird das Timeout als das 25-fache der geschätzten Abfragekosten berechnet. Weitere Informationen finden Sie unter [Konfigurieren der Serverkonfigurationsoption Abfragewartezeit.](configure-the-query-wait-server-configuration-option.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
