---
title: ODBC-Glossar | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], glossary
- glossary [ODBC]
ms.assetid: e8227000-1944-42e5-a881-1f549e1ff9d1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33116adaf74ed2d3fc52fec460859a7672ce2d0a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63057782"
---
# <a name="odbc-glossary"></a>ODBC-Glossar
## <a name="a"></a>A  
 **Access-plan**  
 Ein Plan generiert, die von der Datenbank-Engine zum Ausführen einer SQL-Anweisung. Äquivalent zu den ausführbaren Code kompiliert, die von einer dritten Generation Sprache wie z. B. c  
  
 **Aggregate-Funktion**  
 Eine Funktion, die einen einzelnen Wert aus einer Gruppe von Werten, die häufig zusammen mit generiert **GROUP BY** und **HAVING** Klauseln. Aggregatfunktionen **AVG**, **Anzahl**, **MAX**, **MIN**, und **Summe**. Auch bekannt als *Mengenfunktionen*. *Siehe auch* skalaren Funktion.  
  
 **ANSI**  
 American National Standards Institute. Der ODBC-API basiert auf der ANSI-Call-Level-Schnittstelle.  
  
 **APD**  
 *Finden Sie unter* anwendungsparameterdeskriptor (APD).  
  
 **API**  
 Application-Programmierschnittstelle. Ein Satz von Routinen, die eine Anwendung verwendet, um anzufordern, und führen Sie die Low-Level-Dienste. Der ODBC-API besteht aus der ODBC-Funktionen.  
  
 **application**  
 Ein ausführbares Programm, das Funktionen der ODBC-API aufruft.  
  
 **anwendungsparameterdeskriptor (APD)**  
 Ein Deskriptor, der beschreibt, die dynamischen Parameter in einer SQL-Anweisung vor der Konvertierung von der Anwendung angegebenes verwendet.  
  
 **Zeile anwendungsdeskriptor (ARD)**  
 Ein Deskriptor, der Metadaten und Daten in der Anwendung Puffern, beschreiben eine Zeile mit Daten, die nach der Datenkonvertierung von der Anwendung angegebenes darstellt.  
  
 **ARD**  
 *Finden Sie unter* Zeile anwendungsdeskriptor (ARD).  
  
 **Autocommit-Modus**  
 Eine Commit-Transaktionsmodus, in dem eine Transaktionen ein Commit ausgeführt werden, sofort nach der sie ausgeführt werden.  
  
## <a name="b"></a>B  
 **Unterschied im Verhalten**  
 Eine Änderung in bestimmte Funktionen von ODBC 3. *.x* Verhalten ODBC 2.. *X* Verhalten oder umgekehrt. Durch Ändern des umgebungsattributs SQL_ATTR_ODBC_VERSION verursacht.  
  
 **Binary large Object (BLOB)**  
 Beliebige binären Daten über eine bestimmte Anzahl von Bytes, beispielsweise 255. In der Regel viel länger. Diese Daten in der Regel an gesendet und abgerufen werden, aus der Datenquelle in Teilen. Auch bekannt als *long-Daten*.  
  
 **binding**  
 Als Verb, das Act eine Spalte in einem Resultset oder ein Parameter in einer SQL-Anweisung mit einer Anwendungsvariablen verknüpft. Als ein Nomen, die Zuordnung.  
  
 **Offset der Bindung**  
 Ein Wert, der die pufferadressen Daten und den Längenindikator/pufferadressen hinzugefügt, für alle neue Adressen für die Daten Abfragen, was von Spalte oder Parameter gebunden wird.  
  
 **Blockcursor**  
 Ein Cursor kann mehr als eine Zeile mit Daten zu einem Zeitpunkt abrufen.  
  
 **buffer**  
 Einen Speicherbereich Anwendung verwendet, um Daten zwischen der Anwendung und den Treiber übergeben. Puffer treten häufig paarweise: eine *Datenpuffer* und *Länge des Datenpuffers*.  
  
 **byte**  
 Acht Bits oder ein Oktett. *Siehe auch* Oktett.  
  
## <a name="c"></a>c  
 **C-Datentyp**  
 Der Datentyp einer Variablen in einem C-Programm in diesem Fall die Anwendung.  
  
 **catalog**  
 Der Satz von Systemtabellen in einer Datenbank, die die Form der Datenbank zu beschreiben. Auch bekannt als eine *Schema* oder *Datenwörterbuch*.  
  
 **Katalogfunktion**  
 Eine ODBC-Funktion zum Abrufen von Informationen aus der Datenbank-Katalog verwendet wird.  
  
 **CLI**  
 *Finden Sie unter* API.  
  
 **client/server**  
 Eine Zugriffsstrategie für die Datenbank in dem einen oder mehrere Clients Daten über einen Server zugreifen. Die Clients implementieren in der Regel die Benutzeroberfläche, während die Serversteuerelemente Access-Datenbank.  
  
 **column**  
 Der Container für ein einzelnes Element der Informationen in einer Zeile. Auch bekannt als *Feld*.  
  
 **commit**  
 Um die Änderungen in einer Transaktion permanent zu machen.  
  
 **concurrency**  
 Die Fähigkeit von mehr als eine Transaktion, die Zugriff auf die gleichen Daten zur gleichen Zeit.  
  
 **Übereinstimmungsebene**  
 Einen diskreten Satz von Funktionen, die durch einen Treiber oder eine Datenquelle unterstützt. ODBC definiert die API-Konformitätsgrad und SQL-Übereinstimmungsebenen.  
  
 **connection**  
 Eine bestimmte Instanz von einem Treiber und einer Datenquelle.  
  
 **Verbindung durchsuchen**  
 Suchen das Netzwerk für die Datenquellen für die Verbindung ein. Durchsuchen der Verbindung kann mehrere Schritte umfassen. Beispielsweise kann der Benutzer zunächst das Netzwerk nach Servern durchsuchen und navigieren Sie dann auf einen bestimmten Server für eine Datenbank.  
  
 **Verbindungshandles**  
 Ein Handle für eine Datenstruktur, die Informationen über eine Verbindung enthält.  
  
 **Aktuelle Zeile**  
 Die Zeile derzeit die Cursor verweist. Positionierte Operationen werden auf der aktuellen Zeile.  
  
 **Cursor**  
 Eine Softwarekomponente, die Zeilen von Daten an die Anwendung zurückgibt. Wahrscheinlich nach blinkenden Cursors auf dem Terminalserver die benannt werden. nur als Cursor zeigt die aktuelle Position auf dem Bildschirm, ein Cursor in einem Resultset gibt an, die aktuelle Position im Resultset.  
  
## <a name="d"></a>D  
 **Datenpuffer**  
 Ein Puffer wird verwendet, um Daten zu übergeben. Häufig in Verbindung mit einem Puffer ist eine *Länge des Datenpuffers*.  
  
 **Datenwörterbuch**  
 *Finden Sie unter* Katalog.  
  
 **Länge des Datenpuffers**  
 Ein Puffer verwendet, um die Länge des Werts in ein entsprechendes übergeben *Datenpuffer*. Der Datenpuffer für die Länge dient auch zum Speichern von Indikatoren, z. B., ob der Wert Null-terminiert ist.  
  
 **Datenquelle**  
 Die Daten, die der Benutzer den Zugriff und die zugehörigen Betriebssystem, DBMS und Network-Plattform (sofern vorhanden) möchte.  
  
 **Datentyp**  
 Der Typ der Daten. ODBC definiert C und SQL-Datentypen. *Siehe auch* "Typindikator".  
  
 **Data-at-Execution-Spalte**  
 Eine Spalte, die für die Daten, nach dem gesendet werden **SQLSetPos** aufgerufen wird. So genannt, da die Daten auf, die in einem Rowset Puffer platziert wird, statt Ausführungszeit gesendet werden. Long-Daten werden in der Regel in Teilen, die zum Zeitpunkt der Ausführung gesendet.  
  
 **Data-at-Execution-parameter**  
 Ein Parameter für die Daten, nach dem gesendet werden **SQLExecute** oder **SQLExecDirect** aufgerufen wird. So genannt, da die Daten gesendet werden, wenn die SQL-Anweisung ausgeführt wird, anstatt in einem Parameterpuffer platziert wird. Long-Daten werden in der Regel in Teilen, die zum Zeitpunkt der Ausführung gesendet.  
  
 **database**  
 Eine diskrete Sammlung von Daten in einem DBMS. Auch ein DBMS.  
  
 **Datenbank-engine**  
 Die Software in einem DBMS, die analysiert und SQL-Anweisungen ausgeführt und greift auf die physischen Daten.  
  
 **DBMS**  
 Datenbank-Managementsystem. Eine Softwareebene zwischen der physischen Datenbank und dem Benutzer. Das DBMS dient zur Verwaltung des gesamten Zugriffs auf die Datenbank.  
  
 **DBMS-basierten Treibers**  
 Ein Treiber, der physische Daten über eine eigenständige Datenbank-Engine zugreift.  
  
 **DDL**  
 Die Datendefinitionssprache. Diese Anweisungen in SQL, die nicht an, um zu bearbeiten, müssen Daten zu definieren. Z. B. **CREATE TABLE**, **CREATE INDEX**, **GRANT**, und **widerrufen**.  
  
 **delimited identifier**  
 Ein Bezeichner, der in Anführungszeichen für Bezeichner eingeschlossen ist, sodass Schlüsselwörter (auch bekannt als aus einem Bezeichner in Anführungszeichen entsprechen) oder Sonderzeichen enthalten kann.  
  
 **descriptor**  
 Eine Datenstruktur, die Informationen über die Spaltendaten oder dynamischen Parametern enthält. Die physikalische Darstellung des Deskriptors ist nicht definiert. Anwendungen erhalten direkten Zugriff auf den Deskriptor eines nur durch die Felder bearbeiten von Aufrufen von ODBC-Funktionen, mit dem Deskriptorhandle.  
  
 **Desktop-Datenbank**  
 Ein DBMS auf einem PC ausgeführt werden soll. Im Allgemeinen diese bieten einer eigenständige Datenbank-Engine keine DBMS und Zieltreiber müssen durch einen dateibasierten Treibers zugegriffen werden. Die Triebwerke in diese Treiber eingeschränkte Unterstützung für SQL und Transaktionen in der Regel. Z. B. dBASE, Paradox, Btrieve oder Microsoft® FoxPro®.  
  
 **diagnostic**  
 Ein Datensatz mit diagnostischen Angaben über die letzte Funktion, die aufgerufen wird, verwendet ein bestimmtes Handle. DiagnoseDatensätze sind Umgebung "," Verbindung "," Anweisung "und" Deskriptorhandles zugeordnet.  
  
 **DML**  
 Datenbearbeitungssprache. Diese Anweisungen in SQL, die nicht an, um zu definieren, Daten zu bearbeiten. Z. B. **einfügen**, **UPDATE**, **löschen**, und **wählen**.  
  
 **driver**  
 Eine routinemäßige-Bibliothek, die die Funktionen der ODBC-API verfügbar macht. Treiber sind spezifisch für eine einzelne DBMS.  
  
 **Treiber-Manager**  
 Eine routinemäßige-Bibliothek, die Zugriff auf Treiber für die Anwendung verwaltet. Der Treiber-Manager geladen und entladen wird (oder eine Verbindung mit her, und trennt die Verbindung) Aufrufe Treiber und übergibt an die ODBC-Funktionen, um den richtigen Treiber.  
  
 **Setup-DLL für Treiber**  
 Eine DLL, die treiberspezifische Funktionen für Installation und Konfiguration enthält.  
  
 **Dynamic-cursor**  
 Einen bildlauffähigen Cursor aktualisiert, gelöscht oder eingefügt werden, in das Resultset Zeilen erkennen kann.  
  
 **Dynamisches SQL**  
 Ein Typ von embedded SQL-Anweisungen sind in dem SQL erstellt und zur Laufzeit kompiliert werden soll. *Siehe auch* statische SQL-Anweisungen.  
  
## <a name="e"></a>E  
 **Embedded SQL**  
 SQL-Anweisungen, die direkt in einem Programm, das in einer anderen Sprache, z. B. COBOL oder C. ODBC enthalten sind embedded SQL nicht verwendet. *Siehe auch* statische SQL-Anweisungen *und* dynamischem SQL.  
  
 **environment**  
 Einem globalen Kontext in dem für den Datenzugriff der Umgebung zugeordnet ist, alle Informationen, die global in der Art, z. B. eine Liste aller Verbindungen in dieser Umgebung ist.  
  
 **Umgebungshandles**  
 Ein Handle für eine Datenstruktur, die Informationen über die Umgebung enthält.  
  
 **ESCAPE-Klausel**  
 Eine Klausel in einer SQL-Anweisung.  
  
 **execute**  
 Um eine SQL-Anweisung auszuführen.  
  
## <a name="f"></a>V  
 **FAT cursor**  
 *Finden Sie unter* Blockcursor.  
  
 **fetch**  
 Um eine oder mehrere Zeilen aus einem Resultset abgerufen werden.  
  
 **field**  
 *Finden Sie unter* Spalte.  
  
 **dateibasierte Treiber**  
 Ein Treiber, der physische Daten direkt zugreift. In diesem Fall wird der Treiber enthält eine Datenbank-Engine und fungiert gleichzeitig als Treiber und -Datenquelle.  
  
 **Datei als Datenquelle**  
 Eine Datenquelle, für welche, die Verbindung Informationen in einer DSN-Datei gespeichert werden.  
  
 **Fremdschlüssel**  
 Eine Spalte oder Spalten in einer Tabelle, die den Primärschlüssel in einer anderen Tabelle entsprechen.  
  
 **Vorwärtscursor**  
 Ein Cursor, der nur vorwärts durch die Ergebnisse und in der Regel verschieben kann ruft nur eine Zeile zu einem Zeitpunkt ab. Die meisten relationale Datenbanken unterstützen nur Vorwärtscursor.  
  
## <a name="h"></a>H  
 **handle**  
 Ein Wert, der eindeutig etwas wie eine Datei oder -Struktur identifiziert. Handles sind sinnvoll, nur für die Software, die erstellt und verwendet sie jedoch durch eine andere Software, die Elemente identifizieren übergeben werden. ODBC definiert Handles für Umgebungen, die Verbindungen, Anweisungen und Deskriptoren.  
  
## <a name="i"></a>I  
 **IPD (Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor)**  
 Ein Deskriptor, der beschreibt, die dynamischen Parameter in einer SQL-Anweisung nach der Konvertierung von der Anwendung angegebenes verwendet.  
  
 **implementierungszeilendeskriptors (IRD)**  
 Ein Deskriptor, der eine Zeile mit Daten vor der Konvertierung von der Anwendung angegebenes beschreibt.  
  
 **Installationsprogramm-DLL**  
 Eine DLL, die ODBC-Komponenten installiert und konfiguriert,-Datenquellen.  
  
 **Integritätserweiterungsfunktion**  
 Eine Teilmenge von SQL entwickelt, um die Integrität einer Datenbank zu gewährleisten.  
  
 **Interface-Konformitätsgrad**  
 Die Ebene der von einem Treiber unterstützten 3.7 der ODBC-Schnittstelle Hierbei kann es sich um Core, Level 1 und Ebene 2 sein.  
  
 **interoperability**  
 Die Fähigkeit einer Anwendung auf den gleichen Code verwenden, beim Zugriff auf Daten in anderen DBMS.  
  
 **IPD**  
 *Finden Sie unter* IPD (Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor).  
  
 **IRD**  
 *Finden Sie unter* Implementierung Zeile Deskriptor (IRD).  
  
 **ISO/IEC**  
 Internationale Standards Organisation/Internationalen Elektrotechnischen Kommission. Der ODBC-API basiert auf der ISO/IEC-Call-Level-Schnittstelle.  
  
## <a name="j"></a>J  
 **join**  
 Ein Vorgang in einer relationalen Datenbank, die die Zeilen in zwei oder mehr Tabellen verknüpft, indem Sie passende Werte in bestimmte Spalten dient.  
  
## <a name="k"></a>K  
 **key**  
 Eine Spalte oder Spalten, deren Werte eine Zeile zu identifizieren. *Siehe auch* Fremdschlüssel *und* Primärschlüssel.  
  
 **keyset**  
 Ein Satz von Schlüsseln, die von einem gemischten oder keysetgesteuerte Cursor verwendet, um die Zeilen erneut abzurufen.  
  
 **keysetgesteuerter cursor**  
 Welches einen bildlauffähigen Cursor, der aktualisierten und gelöschte Zeilen mit einem Keyset erkennt.  
  
## <a name="l"></a>L  
 **literal**  
 Eine breitzeichendarstellung eines Werts der tatsächlichen Daten in einer SQL­Anweisung.  
  
 **locking**  
 Der Prozess, mit dem ein DBMS den Zugriff auf eine Zeile in einer mehrbenutzerumgebung beschränkt. Das DBMS in der Regel legt ein bit auf eine Zeile oder die physische Seite mit je einer Zeile, die die Zeile gibt an, oder Seite ist gesperrt.  
  
 **long data**  
 Alle Binär- oder Zeichendatentypen Daten über eine bestimmte Länge, wie z. B. 255 Bytes oder Zeichen. In der Regel viel länger. Diese Daten in der Regel an gesendet und abgerufen werden, aus der Datenquelle in Teilen. Auch bekannt als *BLOB*s oder *CLOB*s.  
  
## <a name="m"></a>M  
 **Computer-Datenquelle**  
 Eine Datenquelle, für welche, die Verbindung Informationen, auf dem System (z. B. die Registrierung gespeichert werden).  
  
 **Manualcommit-Modus**  
 Eine Transaktion Commit-Modus in der Transaktionen werden explizit ein durch den Aufruf Commit müssen **SQLTransact**.  
  
 **metadata**  
 Daten, die einen Parameter in einer SQL-Anweisung oder eine Spalte in einem Resultset zu beschreiben. Z. B. den-Datentyp, Länge in Byte, und die Genauigkeit eines Parameters.  
  
 **Treiber mit mehreren Ebenen**  
 *Finden Sie unter* DBMS-basierten Treibers.  
  
## <a name="n"></a>N  
 **NULL-Wert**  
 Wenn kein Wert explizit zugewiesen. Ein NULL-Wert unterscheidet sich vor allem eine 0 (null) oder ein Leerzeichen.  
  
## <a name="o"></a>O  
 **octet**  
 Acht Bits oder ein Byte. *Siehe auch* Byte.  
  
 **Oktettlänge**  
 Die Länge in Oktetten einen Puffer oder die darin enthaltenen Daten.  
  
 **ODBC**  
 Öffnen Sie die Datenbankverbindung an. Eine Spezifikation für eine API, die einen standardmäßigen Satz von Routinen definiert, mit denen eine Anwendung Daten in einer Datenquelle zugreifen können.  
  
 **ODBC Administrator**  
 Ein ausführbares Programm, das das Installationsprogramm-DLL für die Konfiguration von Datenquellen aufruft.  
  
 Gruppe öffnen  
 Ein Unternehmen, die Standards veröffentlicht. Insbesondere veröffentlicht es SQL Access Group (SAG)-Standards.  
  
 **optimistic concurrency**  
 Eine Strategie zur Steigerung der Parallelität in dem Zeilen nicht gesperrt werden. Bevor sie aktualisiert oder gelöscht werden, überprüft ein Cursor stattdessen, um festzustellen, ob sie geändert wurden, seit sie zuletzt gelesen wurden. Wenn dies der Fall ist, schlägt fehl, die Update- oder Delete. *Siehe auch* pessimistische Parallelität.  
  
 **äußere Joins**  
 Ein join, bei die entsprechenden und nicht übereinstimmenden Zeilen zurückgegeben werden. Die Werte aller Spalten aus der nicht übereinstimmenden Tabelle in nicht übereinstimmenden Zeilen werden auf NULL festgelegt.  
  
 **owner**  
 Der Besitzer einer Tabelle.  
  
## <a name="p"></a>P  
 **parameter**  
 Eine Variable in einer SQL­Anweisung mit einer parametermarkierung oder ein Fragezeichen (?) markiert. Parameter sind gebunden, an Anwendungsvariablen und deren Werte abgerufen werden, wenn die Anweisung ausgeführt wird.  
  
 **parameter descriptor**  
 Ein Deskriptor, der beschreibt, die Laufzeit-Parameter, die in eine SQL-Anweisung entweder vor der Konvertierung von der Anwendung (einen Anwendungsdienst-Deskriptor-Parameter oder APD) oder nach der Konvertierung angegeben, die von der Anwendung (eine Implementierung angegeben verwendet Parameterdeskriptor oder Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor).  
  
 **Parameterarray-Vorgang**  
 Ein Array mit Werten, die eine Anwendung festlegen können, um anzugeben, dass der entsprechende Parameter sollen, in ignoriert werden eine **SQLExecDirect** oder **SQLExecute** Vorgang.  
  
 **Parameterarray-status**  
 Ein Array mit den Status eines Parameters, nach einem Aufruf von **SQLExecDirect** oder **SQLExecute**.  
  
 **die eingeschränkte Parallelität**  
 Eine Strategie für die Implementierung der Serialisierbarkeit, in dem Zeilen gesperrt werden, so dass andere Transaktionen, die sie ändern können. *Siehe auch* optimistische Parallelität *und* Serialisierbarkeit.  
  
 **positionierte operation**  
 Jeder Vorgang, der auf der aktuellen Zeile angewendet werden. Z. B. positioniert Update und delete-Anweisungen, **SQLGetData**, und **SQLSetPos**.  
  
 **positionierte Update-Anweisung**  
 Eine SQL-Anweisung verwendet, um die Werte in der aktuellen Zeile zu aktualisieren.  
  
 **positionierte Delete-Anweisung**  
 Eine SQL-Anweisung verwendet, um die aktuelle Zeile gelöscht wird.  
  
 **prepare**  
 Um eine SQL-Anweisung zu kompilieren. Ein Zugriffsplan wird durch die Vorbereitung einer SQL-Anweisung erstellt.  
  
 **Primärschlüssel**  
 Eine Spalte oder Spalten, die eine Zeile in einer Tabelle eindeutig identifiziert.  
  
 **procedure**  
 Eine Gruppe eine oder mehrere vorkompilierte SQL-Anweisungen, die als ein benanntes Objekt in einer Datenbank gespeichert sind.  
  
 **Prozedurspalte**  
 Ein Argument in einem Prozeduraufruf, der von einer Prozedur oder eine Spalte in einem Resultset, die von einer Prozedur erstellten zurückgegebene Wert.  
  
## <a name="q"></a>Q  
 **qualifier**  
 Eine Datenbank, die eine oder mehrere Tabellen enthält.  
  
 **query**  
 Eine SQL-Anweisung. Manchmal verwendet, um das bedeutet, dass eine **wählen** Anweisung.  
  
 **Bezeichner in Anführungszeichen**  
 Ein Bezeichner, der in Anführungszeichen für Bezeichner eingeschlossen ist, damit Schlüsselwörtern (die auch in SQL-92, als durch Trennzeichen getrennten Bezeichner bezeichnet werden) entsprechen oder Sonderzeichen enthalten kann.  
  
## <a name="r"></a>R  
 **radix**  
 Die Basis eines Systems Anzahl. In der Regel 2 "oder" 10 ".  
  
 **record**  
 *Finden Sie unter* Zeile.  
  
 **Resultset**  
 Der Satz von Zeilen, die Ausführung von erstellt eine **wählen** Anweisung.  
  
 **Rückgabecode**  
 Der Wert, der von einer ODBC-Funktion zurückgegeben wird.  
  
 **Zurücksetzen**  
 Um die Werte geändert, die von einer Transaktion an den ursprünglichen Zustand zurück.  
  
 **row**  
 Ein Satz von verknüpften Spalten, die eine bestimmte Entität zu beschreiben. Auch bekannt als eine *Datensatz*.  
  
 **Zeile Deskriptor**  
 Ein Deskriptor, der beschreibt, die Spalten eines Resultsets, die entweder vor der Konvertierung von der Anwendung (ein Implementierungszeilendeskriptor oder IRD) oder nach der Konvertierung angegeben, die von der Anwendung (einen Anwendungsdienst-Deskriptor Zeile oder ARD) angegeben.  
  
 **Zeile Operation-array**  
 Ein Array mit Werten, die eine Anwendung festlegen können, um anzugeben, dass die entsprechende Zeile soll, in ignoriert werden einem **SQLSetPos** Vorgang.  
  
 **zeilenstatusarray**  
 Ein Array mit den Status einer Zeile nach einem Aufruf von **SQLFetch**, **SQLFetchScroll**, oder **SQLSetPos**.  
  
 **rowset**  
 Der Satz von Zeilen, die in einen einzelnen Abruf von einem Blockcursor zurückgegeben.  
  
 **Rowset-Puffer**  
 Die Puffer gebunden an die Spalten eines Resultsets und bei der die Daten für eine gesamte Rowset zurückgegeben werden.  
  
## <a name="s"></a>S  
 **SAG**  
 *Finden Sie unter* SQL-Zugriffsgruppe (SAG).  
  
 **Skalarfunktion**  
 Eine Funktion, die einen einzelnen Wert aus einem einzelnen Wert generiert. Beispiel: eine Funktion, die die Groß-/Kleinschreibung von Zeichendaten geändert.  
  
 **schema**  
 *Finden Sie unter* Katalog.  
  
 **bildlauffähige cursor**  
 Ein Cursor, der über das Resultset vorwärts oder rückwärts bewegen kann.  
  
 **serializability**  
 Gibt an, ob zwei Transaktionen gleichzeitig ausgeführt werden zu einem Ergebnis, das gleiche wie die serielle (oder nacheinander) Ausführung dieser Transaktionen ist. Serializable-Transaktionen sind erforderlich, um die Datenbankintegrität zu verwalten.  
  
 **Server-Datenbank**  
 Ein DBMS in einer Client-/serverumgebung ausgeführt werden soll. Diese DBMS stellen ein eigenständiges Datenbankmodul, das bietet eine umfangreiche für SQL und Transaktionen Unterstützung bereit. Sie werden über die DBMS-basierten Treibern zugegriffen. Z.B. Oracle, Informix, DB/2 oder Microsoft® SQL Server.  
  
 **Set-Funktion**  
 *Finden Sie unter* Aggregatfunktion.  
  
 **Setup-DLL**  
 *Finden Sie unter* Setup-DLL für Treiber *und* Translator-Setup-DLL.  
  
 **ein-Ebenen-Treiber**  
 *Finden Sie unter* dateibasierten Treibers.  
  
 **SQL**  
 Strukturierte Abfragesprache. Eine Sprache, die von relationalen Datenbanken verwendet werden, zum Abfragen, aktualisieren und zu verwalten.  
  
 **SQL-Zugriffsgruppe (SAG)**  
 Ein Branchenkonsortium von Unternehmen, die mit SQL-Datenbank-Managementsysteme befassen. Die Open Group Call-Level-Interface basiert auf Arbeit, die ursprünglich von der SQL-Zugriffsgruppe.  
  
 **SQL-Konformitätsgrad**  
 Der Ebene der SQL-92-Grammatik, die vom Treiber unterstützt; Eintrag FIPS Transitional, zwischen- oder vollständige möglich.  
  
 **SQL-Datentyp**  
 Der Datentyp einer Spalte oder Parameter, wie er wird in der Datenquelle gespeichert.  
  
 **SQLSTATE**  
 Ein fünfstelligen-Wert, der einen bestimmten Fehler angibt.  
  
 **SQL-Anweisung**  
 Eine vollständige Ausdruck in SQL, beginnt mit einem Schlüsselwort und vollständig beschreibt eine Aktion an, die ausgeführt werden. Wählen Sie z. B. * FROM Orders. SQL-Anweisungen sollten nicht mit Anweisungen verwechselt werden.  
  
 **state**  
 Eine klar definierte Bedingung eines Elements. Beispielsweise muss eine Verbindung über sieben Zustände, einschließlich der verfügbare, zugewiesene, verbundene und daher Daten. Bestimmte Vorgänge möglich nur, wenn ein Element in einem bestimmten Zustand befindet. Beispielsweise kann eine Verbindung freigegeben werden, nur, wenn es in einem zugeordneten Zustand befindet und nicht der Fall, z. B. ist, wenn er verbunden ist.  
  
 **Zustandsübergang**  
 Das Verschieben eines Elements von einem Zustand in einen anderen. ODBC definiert strengen Statusübergänge für Umgebungen, Verbindungen und Anweisungen.  
  
 **statement**  
 Ein Container für alle Informationen im Zusammenhang mit einer SQL-Anweisung. -Anweisungen sollten mit SQL-Anweisungen nicht verwechselt werden.  
  
 **Anweisungshandle**  
 Ein Handle für eine Datenstruktur, die Informationen zu einer Anweisung enthält.  
  
 **static-cursor**  
 Welches ein bildlauffähiger Cursor, der Updates, die nicht erkannt, löschen oder Einfügen von im Resultset. In der Regel implementiert, indem eine Kopie des Resultsets.  
  
 **statische SQL-Anweisungen**  
 Ein Typ von embedded SQL-Anweisungen sind in dem SQL hartcodiert und kompiliert, wenn der Rest des Programms kompiliert wird. *Siehe auch* dynamischem SQL.  
  
 **gespeicherte Prozedur**  
 *Finden Sie unter* Verfahren.  
  
## <a name="t"></a>T  
 **table**  
 Eine Auflistung von Zeilen.  
  
 **thunking**  
 Die Konvertierung von 16-Bit-Adressen auf 32-Bit-Adressen (oder umgekehrt), wenn 16-Bit-Anwendungen mit 32-Bit-ODBC-Treiber verwendet werden.  
  
 **transaction**  
 Eine unteilbare Arbeitseinheit. Die Arbeit in einer Transaktion muss als Ganzes abgeschlossen werden; Wenn Sie einen beliebigen Teil der Transaktion ein Fehler auftritt, schlägt die gesamte Transaktion fehl.  
  
 **Transaktionsisolation**  
 Der Vorgang eine Transaktion vor den Auswirkungen von allen anderen Transaktionen isoliert.  
  
 **Transaktionsisolationsstufe**  
 Ein Maß, wie gut eine Transaktion isoliert ist. Es gibt fünf Isolationsstufen von Transaktionen: Read Uncommitted Committed, Repeatable Read, serialisierbar und Versionsverwaltung zu lesen.  
  
 **translator DLL**  
 Eine DLL verwendet, um Daten aus einem Zeichensatz in eine andere zu übersetzen.  
  
 **Translator-Setup-DLL**  
 Eine DLL, die Translator-spezifische Funktionen für Installation und Konfiguration enthält.  
  
 **Zweiphasen-commit**  
 Der Prozess der Commit einer verteilten Transaktions in zwei Phasen. In der ersten Phase überprüft der Prozessor für die Transaktion an, dass alle Teile der Transaktion ein Commit ausgeführt werden können. In der zweiten Phase werden alle Teile der Transaktion ein Commit ausgeführt. Wenn Sie einen beliebigen Teil der Transaktion in der ersten Phase angibt, dass sie ein Commit ausgeführt werden kann, tritt in der zweite Phase nicht. ODBC unterstützt zwei-Phasen-Commits nicht.  
  
 **Typindikator**  
 Ein ganzzahliger Wert übergeben oder von einer ODBC-Funktion an, dass der Datentyp von einer Anwendungsvariablen, Parameter oder einer Spalte zurückgegeben. ODBC definiert typindikatoren für C- und SQL-Datentypen.  
  
## <a name="v"></a>B  
 **view**  
 Eine alternative Möglichkeit der Blick auf die Daten in einer oder mehreren Tabellen. Eine Sicht ist in der Regel eine Teilmenge der Spalten aus einer oder mehreren Tabellen erstellt. In ODBC sind Ansichten in der Tabellen in der Regel entspricht.
