---
title: Grundlegendes zu Cursortypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4f4d3db7-4f76-450d-ab63-141237a4f034
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b9ac737c528701baca47b8ffd592389cef3fad45
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52396334"
---
# <a name="understanding-cursor-types"></a>Grundlegendes zu Cursortypen
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Vorgänge in einer relationalen Datenbank beziehen sich immer auf eine vollständige Gruppe von Zeilen. Die von einer SELECT-Anweisung zurückgegebene Gruppe von Zeilen besteht aus allen Zeilen, die die Bedingungen der WHERE-Klausel der Anweisung erfüllen. Diese vollständige Gruppe von Zeilen, die von der Anweisung zurückgegeben wird, wird als Resultset bezeichnet. Anwendungen sind nicht immer effektiv, wenn das gesamte Resultset als eine Einheit bearbeitet wird. Diese Anwendungen benötigen einen Mechanismus, um jeweils eine Zeile oder einen kleinen Zeilenblock zu bearbeiten. Cursor sind eine Erweiterung zu Resultsets und stellen diesen Mechanismus bereit.  
  
 Cursor erweitern die Verarbeitung von Resultsets durch folgende Aktionen:  
  
-   Ermöglichen der Positionierung an bestimmten Zeilen des Resultsets.  
  
-   Abrufen einer Zeile oder eines ZeilenBlocks von der aktuellen Position im Resultset.  
  
-   Unterstützen von Datenänderungen in der Zeile an der aktuellen Position im Resultset.  
  
-   Unterstützen von unterschiedlichen Sichtbarkeitsebenen bei Änderungen, die von anderen Benutzern an den Datenbankdaten, die im Resultset dargestellt werden, ausgeführt wurden.  
  
> [!NOTE]  
>  Eine umfassende Beschreibung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Cursortypen finden Sie im Thema zu Cursortypen (Datenbank-Engine) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
 Die JDBC-Spezifikation stellt Unterstützung für Vorwärtscursor und scrollfähige Cursor bereit, die Änderungen durch andere Aufträge berücksichtigen oder nicht berücksichtigen können und schreibgeschützt oder aktualisierbar sein können. Diese Funktionalität wird von der [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] bereitgestellt.  
  
## <a name="remarks"></a>Remarks  
 Der JDBC-Treiber unterstützt die folgenden Cursortypen:  
  
|Resultset<br /><br /> (Cursor) Typ|SQL Server-Cursortyp|Merkmale|select<br /><br /> Methode|Antwort<br /><br /> Pufferung|und Beschreibung|  
|------------------------------------|----------------------------|---------------------|-----------------------|----------------------------|-----------------|  
|TYPE_FORWARD_ONLY (CONCUR_READ_ONLY)|–|Vorwärtscursor, schreibgeschützt|direct|Volle|Die Anwendung muss ein Pass-Through (vorwärts) für das Resultset ausführen. Dies ist das Standardverhalten und entspricht einem TYPE_SS_DIRECT_FORWARD_ONLY-Cursor. Der Treiber liest das gesamte Resultset während der Ausführung der Anweisung aus dem Server in einen Speicher.|  
|TYPE_FORWARD_ONLY (CONCUR_READ_ONLY)|–|Vorwärtscursor, schreibgeschützt|direct|adaptive|Die Anwendung muss ein Pass-Through (vorwärts) für das Resultset ausführen. Das Verhalten entspricht dem Verhalten eines TYPE_SS_DIRECT_FORWARD_ONLY-Cursors. Der Treiber liest Zeilen vom Server, wenn die Anwendung sie anfordert, und minimiert so die Speicherauslastung auf Clientseite.|  
|TYPE_FORWARD_ONLY (CONCUR_READ_ONLY)|Schneller Vorwärtscursor|Vorwärtscursor, schreibgeschützt|cursor|–|Die Anwendung muss mithilfe eines Servercursors ein Pass-Through (vorwärts) für das Resultset ausführen. Das Verhalten entspricht dem Verhalten eines TYPE_SS_SERVER_CURSOR_FORWARD_ONLY-Cursors.<br /><br /> Zeilen werden in durch die Abrufgröße angegebene Blöcke vom Server abgerufen.|  
|TYPE_FORWARD_ONLY (CONCUR_UPDATABLE)|Dynamisch (Vorwärtscursor)|Vorwärtscursor, aktualisierbar|–|–|Die Anwendung muss ein Pass-Through (vorwärts) für das Resultset ausführen, um eine oder mehrere Zeilen zu aktualisieren.<br /><br /> Zeilen werden in durch die Abrufgröße angegebene Blöcke vom Server abgerufen.<br /><br /> Die Abrufgröße ist standardmäßig festgelegt, wenn die Anwendung die [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md)-Methode des [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts aufruft.<br /><br /> **Hinweis:** Der JDBC-Treiber stellt ein Feature für die adaptive Pufferung bereit, mit dem Sie Ergebnisse der Anweisungsausführung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abrufen können, wenn sie in der Anwendung benötigt werden, statt alle Ergebnisse auf einmal abzurufen. Wenn die Anwendung beispielsweise eine große Datenmenge abrufen muss, für die der Anwendungsspeicher nicht ausreicht, kann die Clientanwendung den Wert mithilfe der adaptiven Pufferung als Datenstrom abrufen. Das Verhalten des Treibers ist standardmäßig auf **Adaptiv** festgelegt. Um jedoch die adaptive Pufferung für das aktualisierbare Resultset mit Vorwärtscursor zu aktivieren, muss die Anwendung die [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)-Methode des [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts explizit aufrufen, indem der **String-Wert** "**adaptive"** angegeben wird. Beispielcode finden Sie unter [Aktualisieren großer Datenbeispiel](../../connect/jdbc/updating-large-data-sample.md).|  
|TYPE_SCROLL_INSENSITIVE|STATIC-Cursor|Scrollfähig, nicht aktualisierbar<br /><br /> Externe Zeilenupdates, -einfügungen und -löschvorgänge sind nicht sichtbar.|N/V|–|Die Anwendung erfordert eine Datenbankmomentaufnahme. Das Resultset kann nicht aktualisiert werden. Nur CONCUR_READ_ONLY wird unterstützt.  Alle anderen Parallelitätstypen führen bei Verwendung mit diesem Cursortyp zu einer Ausnahme.<br /><br /> Zeilen werden in durch die Abrufgröße angegebene Blöcke vom Server abgerufen.|  
|TYPE_SCROLL_SENSITIVE<br /><br /> (CONCUR_READ_ONLY)|Keyset|Scrollfähig, schreibgeschützt. Externe Zeilenupdates sind sichtbar, und Löschvorgänge werden als fehlende Daten angezeigt.<br /><br /> Externe Zeileneinfügungen sind nicht sichtbar.|–|–|Die Anwendung muss geänderte Daten nur für vorhandene Zeilen anzeigen.<br /><br /> Zeilen werden in durch die Abrufgröße angegebene Blöcke vom Server abgerufen.|  
|TYPE_SCROLL_SENSITIVE<br /><br /> (CONCUR_UPDATABLE, CONCUR_SS_SCROLL_LOCKS, CONCUR_SS_OPTIMISTIC_CC, CONCUR_SS_OPTIMISTIC_CCVAL)|Keyset|Scrollfähig, aktualisierbar<br /><br /> Externe und interne Zeilenupdates sind sichtbar, Löschvorgänge werden als fehlende Daten angezeigt, und Einfügungen sind nicht sichtbar.|–|–|Die Anwendung kann Daten in vorhandenen Zeilen mit dem ResultSet-Objekt ändern. Auch Änderungen an Zeilen, die von anderen außerhalb des ResultSet-Objekts vorgenommen werden, müssen für die Anwendung sichtbar sein.<br /><br /> Zeilen werden in durch die Abrufgröße angegebene Blöcke vom Server abgerufen.|  
|TYPE_SS_DIRECT_FORWARD_ONLY|–|Vorwärtscursor, schreibgeschützt|–|"full" oder "adaptive"|Ganzzahliger Wert = 2003. Stellt einen schreibgeschützten clientseitigen Cursor bereit, der vollständig gepuffert wird. Es wird kein Servercursor erstellt.<br /><br /> Nur der Parallelitätstyp CONCUR_READ_ONLY wird unterstützt. Alle anderen Parallelitätstypen führen bei Verwendung mit diesem Cursortyp zu einer Ausnahme.|  
|TYPE_SS_SERVER_CURSOR_FORWARD_ONLY|Schneller Vorwärtscursor|Vorwärtscursor|–|–|Ganzzahliger Wert = 2004. Schnell, greift über einen Servercursor auf alle Daten zu. Bei Verwendung mit dem Parallelitätstyp CONCUR_UPDATABLE aktualisierbar.<br /><br /> Zeilen werden in durch die Abrufgröße angegebene Blöcke vom Server abgerufen.<br /><br /> In diesem Fall muss die Anwendung die Methode [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) des Objekts [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) durch Angabe des **String-Werts** "**adaptive"** explizit aufrufen, um die adaptive Pufferung abzurufen. Beispielcode finden Sie unter [Aktualisieren großer Datenbeispiel](../../connect/jdbc/updating-large-data-sample.md).|  
|TYPE_SS_SCROLL_STATIC|STATIC-Cursor|Die Updates von anderen Benutzern werden nicht reflektiert.|–|–|Ganzzahliger Wert = 1004. Die Anwendung erfordert einen Datenbanksnapshot. Dies ist das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifische Synonym für JDBC TYPE_SCROLL_INSENSITIVE und weist das gleiche Verhalten für die Festlegung der Parallelität auf.<br /><br /> Zeilen werden in durch die Abrufgröße angegebene Blöcke vom Server abgerufen.|  
|TYPE_SS_SCROLL_KEYSET<br /><br /> (CONCUR_READ_ONLY)|Keyset|Scrollfähig, schreibgeschützt Externe Zeilenupdates sind sichtbar, und Löschvorgänge werden als fehlende Daten angezeigt.<br /><br /> Externe Zeileneinfügungen sind nicht sichtbar.|–|–|Ganzzahliger Wert = 1005. Die Anwendung muss geänderte Daten nur für vorhandene Zeilen anzeigen. Dies ist das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifische Synonym für JDBC TYPE_SCROLL_SENSITIVE und weist das gleiche Verhalten für die Festlegung der Parallelität auf.<br /><br /> Zeilen werden in durch die Abrufgröße angegebene Blöcke vom Server abgerufen.|  
|TYPE_SS_SCROLL_KEYSET<br /><br /> (CONCUR_UPDATABLE, CONCUR_SS_SCROLL_LOCKS, CONCUR_SS_OPTIMISTIC_CC, CONCUR_SS_OPTIMISTIC_CCVAL)|Keyset|Scrollfähig, aktualisierbar<br /><br /> Externe und interne Zeilenupdates sind sichtbar, Löschvorgänge werden als fehlende Daten angezeigt, und Einfügungen sind nicht sichtbar.|–|–|Ganzzahliger Wert = 1005. Die Anwendung muss Daten ändern oder geänderte Daten für vorhandene Zeilen anzeigen. Dies ist das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifische Synonym für JDBC TYPE_SCROLL_SENSITIVE und weist das gleiche Verhalten für die Festlegung der Parallelität auf.<br /><br /> Zeilen werden in durch die Abrufgröße angegebene Blöcke vom Server abgerufen.|  
|TYPE_SS_SCROLL_DYNAMIC<br /><br /> (CONCUR_READ_ONLY)|Dynamic|Scrollfähig, schreibgeschützt.<br /><br /> Externe Zeilenupdates und -einfügungen werden angezeigt. Löschvorgänge werden als temporäre fehlende Daten im aktuellen Fetchpuffer angezeigt.|–|–|Ganzzahliger Wert = 1006. Die Anwendung muss geänderte Daten für vorhandene Zeilen anzeigen und eingefügte und gelöschte Zeilen während der Lebensdauer des Cursors anzeigen.<br /><br /> Zeilen werden in durch die Abrufgröße angegebene Blöcke vom Server abgerufen.|  
|TYPE_SS_SCROLL_DYNAMIC<br /><br /> (CONCUR_UPDATABLE, CONCUR_SS_SCROLL_LOCKS, CONCUR_SS_OPTIMISTIC_CC, CONCUR_SS_OPTIMISTIC_CCVAL)|Dynamic|Scrollfähig, aktualisierbar<br /><br /> Externe und interne Zeilenupdates und -einfügungen werden angezeigt. Löschvorgänge werden als temporäre fehlende Daten im aktuellen Fetchpuffer angezeigt.|–|–|Ganzzahliger Wert = 1006. Die Anwendung kann mit dem ResultSet-Objekt Daten für vorhandene Zeilen ändern, oder Zeilen einfügen bzw. entfernen. Auch Änderungen, Einfügungen und Löschvorgänge für Zeilen, die von anderen außerhalb des ResultSet-Objekts vorgenommen werden, müssen für die Anwendung sichtbar sein.<br /><br /> Zeilen werden in durch die Abrufgröße angegebene Blöcke vom Server abgerufen.|  
  
## <a name="cursor-positioning"></a>Cursorpositionierung  
 Die Cursor TYPE_FORWARD_ONLY, TYPE_SS_DIRECT_FORWARD_ONLY und TYPE_SS_SERVER_CURSOR_FORWARD_ONLY unterstützen nur die Positionierungsmethode [next](../../connect/jdbc/reference/next-method-sqlserverresultset.md).  
  
 Der TYPE_SS_SCROLL_DYNAMIC-Cursor unterstützt nicht die Methoden [absolute](../../connect/jdbc/reference/absolute-method-sqlserverresultset.md) und [getRow](../../connect/jdbc/reference/getrow-method-sqlserverresultset.md). Die absolute-Methode kann durch eine Kombination von Aufrufen der Methoden [first](../../connect/jdbc/reference/first-method-sqlserverresultset.md) und [relative](../../connect/jdbc/reference/relative-method-sqlserverresultset.md) für dynamische Cursor angeglichen werden.  
  
 Die getRow-Methode wird nur von den Cursors TYPE_FORWARD_ONLY, TYPE_SS_DIRECT_FORWARD_ONLY, TYPE_SS_SERVER_CURSOR_FORWARD_ONLY, TYPE_SS_SCROLL_KEYSET und TYPE_SS_SCROLL_STATIC unterstützt. Die getRow-Methode gibt mit allen Vorwärtscursortypen die Anzahl der bisher über den Cursor gelesenen Zeilen zurück.  
  
> [!NOTE]  
>  Wenn eine Anwendung einen nicht unterstützten Cursorpositionierungsaufruf oder einen nicht unterstützten Aufruf der getRow-Methode ausführt, wird eine Ausnahme mit der folgenden Meldung ausgelöst: „Der angeforderte Vorgang wird für diesen Cursortyp nicht unterstützt“.  
  
 Nur der TYPE_SS_SCROLL_KEYSET-Cursor und der entsprechende TYPE_SCROLL_SENSITIVE-Cursor machen gelöschte Zeilen verfügbar. Wenn der Cursor in einer gelöschten Zeile positioniert wird, sind die Spaltenwerte nicht verfügbar, und die [rowDeleted](../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md)-Methode gibt TRUE zurück. Aufrufe der get\<Type>-Methoden lösen eine Ausnahme mit der folgenden Meldung aus: „Cannot get value from a deleted row“ (Wert aus gelöschter Zeile kann nicht abgerufen werden). Gelöschte Zeilen können nicht aktualisiert werden. Wenn Sie versuchen, eine update\<Type>-Methode für eine gelöschte Zeile aufzurufen, wird eine Ausnahme mit der folgenden Meldung ausgelöst: „Eine gelöschte Zeile kann nicht aktualisiert werden“. Der TYPE_SS_SCROLL_DYNAMIC-Cursor weist dasselbe Verhalten auf, bis der Cursor aus dem aktuellen Fetchpuffer verschoben wird.  
  
 Vorwärtscursor und dynamische Cursor machen gelöschte Zeilen auf ähnliche Weise verfügbar, jedoch nur, wenn auf die Cursor weiterhin im Fetchpuffer zugegriffen werden kann. Für Vorwärtscursor ist dies relativ einfach. Bei dynamischen Cursorn ist dies komplexer, wenn die Fetchgröße größer als 1 ist. Eine Anwendung kann den Cursor in dem vom Fetchpuffer definierten Fenster vorwärts und rückwärts verschieben, die gelöschte Zeile wird jedoch nicht mehr angezeigt, wenn der ursprüngliche Fetchpuffer, in dem sie aktualisiert wurde, verlassen wird. Wenn eine Anwendung keine temporären gelöschten Zeilen mithilfe von dynamischen Cursorn anzeigen soll, sollte eine Fetchrelative (0) verwendet werden.  
  
 Wenn die Schlüsselwerte einer TYPE_SS_SCROLL_KEYSET-Cursorzeile oder einer TYPE_SCROLL_SENSITIVE-Cursorzeile mit dem Cursor aktualisiert werden, behält die Zeile die ursprüngliche Position im Resultset bei, unabhängig davon, ob die aktualisierte Zeile die Auswahlkriterien des Cursors erfüllt. Wenn die Zeile außerhalb des Cursors aktualisiert wurde, wird eine gelöschte Zeile an der ursprünglichen Position der Zeile angezeigt, die Zeile wird jedoch nur im Cursor angezeigt, wenn eine andere Zeile mit den neuen Schlüsselwerten im Cursor vorhanden war, aber anschließend gelöscht wurde.  
  
 Bei dynamischen Cursorn behalten aktualisierte Zeilen ihre Position im Fetchpuffer bei, bis das vom Fetchpuffer definierte Fenster verlassen wird. Aktualisierte Zeilen werden möglicherweise anschließend an anderen Positionen im Resultset erneut angezeigt oder überhaupt nicht mehr angezeigt. In Anwendungen, in denen temporäre Inkonsistenzen im Resultset vermieden werden sollen, sollte eine Fetchgröße von 1 verwendet werden. (Der Standardwert beträgt 8 Zeilen bei CONCUR_SS_SCROLL_LOCKS-Parallelität und 128 Zeilen bei anderen Parallelitäten.)  
  
## <a name="cursor-conversion"></a>Cursorkonvertierung  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird in einigen Fällen ein anderer Cursortyp als der angeforderte implementiert. Dies wird als implizite Cursorkonvertierung (oder Cursordegradierung) bezeichnet. Weitere Informationen zur impliziten Cursorkonvertierung finden Sie im Thema „Verwenden impliziter Cursorkonvertierungen“ in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
 Mit [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], bei der Aktualisierung der Daten durch das Ergebnis ResultSet.TYPE_SCROLL_SENSITIVE und ResultSet.CONCUR_UPDATABLE festgelegt, wird eine Ausnahme mit einer Meldung "der Cursor ist schreibgeschützt," ausgelöst. Diese Ausnahme tritt auf, weil [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] eine implizite Cursorkonvertierung für das Resultset ausgeführt und nicht den angeforderten aktualisierbaren Cursor zurückgegeben hat.  
  
 Um dieses Problem zu umgehen, können Sie eine der folgenden Lösungen auswählen:  
  
-   Stellen Sie sicher, dass die zugrunde liegende Tabelle einen Primärschlüssel aufweist.  
  
-   Verwendung [Type_ss_scroll_dynamic](../../connect/jdbc/reference/type-ss-scroll-dynamic-field-sqlserverresultset.md) statt ResultSet.TYPE_SCROLL_SENSITIVE beim Erstellen einer Anweisung.  
  
## <a name="cursor-updating"></a>Cursoraktualisierung  
 Ersetzungsupdates werden bei Cursorn unterstützt, bei denen Cursortyp und Parallelität Updates unterstützen. Wenn der Cursor nicht in einer aktualisierbaren Zeile im Resultset positioniert ist (es war kein get\<Type>-Methodenaufruf erfolgreich), löst ein Aufruf einer update\<Type>-Methode eine Ausnahme mit der folgenden Meldung aus: „Das Resultset verfügt über keine aktuelle Zeile“. Die JDBC-Spezifikation gibt an, dass eine Ausnahme ausgelöst wird, wenn eine Updatemethode für eine Spalte eines CONCUR_READ_ONLY-Cursors aufgerufen wird. Wenn die Zeile nicht aktualisiert werden kann, beispielsweise aufgrund eines Konflikts der vollständigen Parallelität durch einen konkurrierenden Aktualisierungs- oder Löschvorgang, wird die Ausnahme möglicherweise erst ausgelöst, wenn [insertRow](../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md), [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) oder [deleteRow](../../connect/jdbc/reference/deleterow-method-sqlserverresultset.md) aufgerufen wird.  
  
 Nach einem Aufruf von aktualisieren\<Type >, die betreffende Spalte kann nicht zugegriffen werden, indem Sie Get\<Typ > bis UpdateRow oder [CancelRowUpdates](../../connect/jdbc/reference/cancelrowupdates-method-sqlserverresultset.md) aufgerufen wurde. So werden Probleme vermieden, wenn eine Spalte durch einen anderen Typ als den vom Server zurückgegebenen Typ aktualisiert wird und folgende Abrufaufrufe clientseitige Typkonvertierungen aufrufen könnten, die ungenaue Ergebnisse liefern. Aufrufe von get\<Type> lösen eine Ausnahme mit der folgenden Meldung aus: „Der Zugriff auf aktualisierte Spalten kann erst nach dem Aufrufen von updateRow() oder cancelRowUpdates() erfolgen“.  
  
> [!NOTE]  
>  Wenn die updateRow-Methode aufgerufen wird und keine Spalten aktualisiert wurden, löst der JDBC-Treiber eine Ausnahme mit der folgenden Meldung aus: „updateRow() called when no columns have been updated“ (updateRow() wurde aufgerufen, obwohl keine Spalten aktualisiert wurden).  
  
 Nach dem Aufruf von [moveToInsertRow](../../connect/jdbc/reference/movetoinsertrow-method-sqlserverresultset.md) wird eine Ausnahme ausgelöst, wenn eine andere Methode als get\<Type>, update\<Type>, insertRow und Cursorpositionierungsmethoden (einschließlich [moveToCurrentRow](../../connect/jdbc/reference/movetocurrentrow-method-sqlserverresultset.md)) für das Resultset aufgerufen wird. Die moveToInsertRow-Methode versetzt das Resultset effektiv in den Einfügemodus, und Cursorpositionierungsmethoden beenden den Einfügemodus. Relative Cursorpositionierungsaufrufe verschieben den Cursor relativ zur Position, in der er sich vor dem Aufruf von moveToInsertRow befunden hat. Nach Cursorpositionierungsaufrufen wird die Zielcursorposition die neue Cursorposition.  
  
 Wenn der Cursorpositionierungsaufruf im Einfügemodus nicht erfolgreich ist, entspricht die Cursorposition nach dem fehlerhaften Aufruf der ursprünglichen Cursorposition vor dem Aufruf von moveToInsertRow. Wenn bei insertRow ein Fehler auftritt, bleibt der Cursor in der Einfügezeile, und der Cursor bleibt im Einfügemodus.  
  
 Spalten in der Einfügezeile befinden sich anfänglich in einem nicht initialisierten Status. Durch Aufrufe der update\<Type>-Methode wird der Spaltenstatus auf initialisiert festgelegt. Ein Aufruf der get\<Type>-Methode für eine nicht initialisierte Spalte löst eine Ausnahme aus. Ein Aufruf der insertRow-Methode gibt alle Spalten in der Einfügezeile in einem nicht initialisierten Status zurück.  
  
 Wenn Spalten beim Aufrufen der insertRow-Methode nicht initialisiert sind, wird der Standardwert für die Spalte eingefügt. Wenn kein Standardwert vorhanden ist, die Spalte jedoch auf NULL festgelegt werden kann, wird NULL eingefügt. Wenn kein Standardwert vorhanden ist und die Spalte nicht auf NULL festgelegt werden kann, gibt der Server einen Fehler zurück, und es wird eine Ausnahme ausgelöst.  
  
> [!NOTE]  
>  Aufrufe der getRow-Methode geben im Einfügemodus „0“ (null) zurück.  
>   
>  Der JDBC-Treiber unterstützt keine positionierten Updates oder Löschvorgänge. Entsprechend der JDBC-Spezifikation hat die [setCursorName](../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)-Methode keine Auswirkungen, und die [getCursorName](../../connect/jdbc/reference/getcursorname-method-sqlserverresultset.md)-Methode löst eine Ausnahme aus, wenn sie aufgerufen wird.  
>   
>  Schreibgeschützte und statische Cursor können nie aktualisiert werden.  
>   
>  SQL Server schränkt Servercursor auf ein einziges Resultset ein. Wenn ein Batch oder eine gespeicherte Prozedur mehrere Anweisungen enthält, muss ein schreibgeschützter Vorwärtsclientcursor verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verwalten von Resultsets mit dem JDBC-Treiber](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)  
  
  
