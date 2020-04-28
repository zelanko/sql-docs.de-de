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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ac454a8c57fe6e2f12724440dc37c3a1953e4c85
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302901"
---
# <a name="odbc-glossary"></a>ODBC-Glossar
## <a name="a"></a>Ein  
 **Zugriffs Plan**  
 Ein Plan, der von der Datenbank-Engine zum Ausführen einer SQL-Anweisung generiert wird. Entspricht dem ausführbaren Code, der aus einer Programmiersprache der dritten Generation wie C kompiliert wurde.  
  
 **Aggregatfunktion**  
 Eine Funktion, die einen einzelnen Wert aus einer Gruppe von Werten generiert, die häufig mit **Group by** **-und** with-Klauseln verwendet werden. Aggregatfunktionen umfassen **AVG**, **count**, **Max**, **Min**und **Sum**. Auch als *Set-Funktionen*bezeichnet. *Siehe auch* Skalarfunktion.  
  
 **ANSI**  
 American National Standards Institute. Die ODBC-API basiert auf der ANSI-Schnittstelle auf Aufrufebene.  
  
 **APD**  
 *Weitere Informationen finden* Sie unter Application Parameter Deskriptor (APD).  
  
 **API**  
 Anwendungsprogrammierschnittstelle. Eine Reihe von Routinen, die eine Anwendung verwendet, um Dienste auf niedrigerer Ebene anzufordern und auszuführen. Die ODBC-API besteht aus den ODBC-Funktionen.  
  
 **application**  
 Ein ausführbares Programm, das Funktionen in der ODBC-API aufruft.  
  
 **Anwendungsparameter Deskriptor (APD)**  
 Ein Deskriptor, der die dynamischen Parameter beschreibt, die in einer SQL-Anweisung vor allen von der Anwendung angegebenen Konvertierungen verwendet werden.  
  
 **Anwendungs Zeilen Deskriptor (ARD)**  
 Ein Deskriptor, der die Spalten Metadaten und Daten in den Puffer der Anwendung darstellt und eine Daten Zeile nach jeder von der Anwendung angegebenen Datenkonvertierung beschreibt.  
  
 **Mäuse**  
 *Weitere Informationen finden* Sie unter Anwendungs Zeilen Deskriptor (ARD).  
  
 **Autocommit-Modus**  
 Ein transaktionscommitmodus, in dem Transaktionen unmittelbar nach ihrer Ausführung committet werden.  
  
## <a name="b"></a>B  
 **Verhaltensänderung**  
 Eine Änderung in bestimmten Funktionen vom ODBC *3. x* -Verhalten zu ODBC *2. x* -Verhalten oder umgekehrt. Wird durch Ändern des SQL_ATTR_ODBC_VERSION Environment-Attributs verursacht.  
  
 **Binary Large Object (BLOB)**  
 Alle Binärdaten über eine bestimmte Anzahl von Bytes, z. b. 255. In der Regel viel länger. Diese Daten werden in der Regel an die Datenquelle gesendet und in Teilen aus der Datenquelle abgerufen. Wird auch als *Long Data*bezeichnet.  
  
 **lichere**  
 Als Verb wird das Verknüpfen einer Spalte in einem Resultset oder eines Parameters in einer SQL-Anweisung mit einer Anwendungsvariablen behandelt. Als Substantiv die Zuordnung.  
  
 **Bindungs Offset**  
 Ein Wert, der den Datenpuffer Adressen und Längen-/indikatorpufferadressen für alle gebundenen Spalten-oder Parameterdaten hinzugefügt wird und neue Adressen erzeugt.  
  
 **Blockcursor**  
 Ein Cursor, der mehrere Daten Zeilen gleichzeitig abrufen können soll.  
  
 **ert**  
 Ein Teil des Anwendungs Speichers, der verwendet wird, um Daten zwischen der Anwendung und dem Treiber zu übergeben. Puffer sind häufig paarweise enthalten: ein *Datenpuffer* und ein *Daten Längenpuffer*.  
  
 **byte**  
 8 Bits oder ein Oktett. *Siehe auch* Octett.  
  
## <a name="c"></a>C  
 **C-Datentyp**  
 Der Datentyp einer Variablen in einem C-Programm, in diesem Fall die Anwendung.  
  
 **sieren**  
 Der Satz von Systemtabellen in einer Datenbank, die die Form der Datenbank beschreiben. Wird auch als *Schema* oder *Datenwörterbuch*bezeichnet.  
  
 **Catalog-Funktion**  
 Eine ODBC-Funktion, die zum Abrufen von Informationen aus dem Katalog der Datenbank verwendet wird.  
  
 **BEFEHLSZEILENSCHNITTSTELLE (CLI)**  
 *Siehe* Found.  
  
 **Client/Server**  
 Eine Datenbankzugriffs Strategie, in der mindestens ein Client über einen Server auf Daten zugreift. Die Clients implementieren in der Regel die Benutzeroberfläche, während der Server den Datenbankzugriff steuert.  
  
 **Kolumne**  
 Der Container für ein einzelnes Element von Informationen in einer Zeile. Wird auch als " *Field*" bezeichnet.  
  
 **einzusetzen**  
 , Um die Änderungen in einer Transaktion permanent zu machen.  
  
 **concurrency**  
 Die Fähigkeit von mehr als einer Transaktion, gleichzeitig auf dieselben Daten zuzugreifen.  
  
 **Konformitätsstufe**  
 Eine diskrete Gruppe von Funktionen, die von einem Treiber oder einer Datenquelle unterstützt werden. ODBC definiert API-Konformitätsstufen und SQL-Konformitäts Ebenen.  
  
 **connection**  
 Eine bestimmte Instanz eines Treibers und einer Datenquelle.  
  
 **Durchsuchen von Verbindungen**  
 Suchen des Netzwerks nach Datenquellen, mit denen eine Verbindung hergestellt werden soll. Das Durchsuchen von Verbindungen kann mehrere Schritte umfassen. Beispielsweise kann der Benutzer das Netzwerk zuerst nach Servern durchsuchen und dann einen bestimmten Server nach einer Datenbank durchsuchen.  
  
 **Verbindungs Handle**  
 Ein Handle für eine Datenstruktur, die Informationen über eine Verbindung enthält.  
  
 **aktuelle Zeile**  
 Die Zeile, auf die der Cursor zurzeit zeigt. Positionierte Vorgänge agieren in der aktuellen Zeile.  
  
 **Cursor**  
 Ein Softwareelement, das Daten Zeilen an die Anwendung zurückgibt. Wird wahrscheinlich nach dem blinkende Cursor auf einem Computerterminal benannt. ebenso wie dieser Cursor die aktuelle Position auf dem Bildschirm anzeigt, gibt ein Cursor auf einem Resultset die aktuelle Position im Resultset an.  
  
## <a name="d"></a>D  
 **Datenpuffer**  
 Ein Puffer, der verwendet wird, um Daten zu übergeben. Einem Datenpuffer ist häufig ein *Daten Längenpuffer*zugeordnet.  
  
 **Datenwörterbuch**  
 *Siehe* catalog.  
  
 **Daten Längenpuffer**  
 Ein Puffer, der verwendet wird, um die Länge des Werts in einem entsprechenden *Datenpuffer*zu übergeben. Der Daten Längenpuffer wird auch zum Speichern von Indikatoren verwendet, z. b. ob der Datenwert NULL-terminiert ist.  
  
 **Datenquelle**  
 Die Daten, auf die der Benutzer zugreifen möchte, sowie das zugehörige Betriebssystem, DBMS und die Netzwerkplattform (sofern vorhanden).  
  
 **Datentyp**  
 Der Typ der Daten. ODBC definiert die C-und SQL-Datentypen. *Siehe auch* Typindikator.  
  
 **Data-at-Execution-Spalte**  
 Eine Spalte, für die Daten gesendet werden, nachdem **SQLSetPos** aufgerufen wurde. Das heißt, weil die Daten zur Ausführungszeit gesendet und nicht in einem rowsetpuffer abgelegt werden. Lange Daten werden in der Regel in Teilen zur Ausführungszeit gesendet.  
  
 **Data-at-Execution-Parameter**  
 Ein Parameter, für den Daten gesendet werden, nachdem **SQLExecute** oder **SQLExecDirect** aufgerufen wurde. Das heißt, weil die Daten gesendet werden, wenn die SQL-Anweisung ausgeführt wird, anstatt Sie in einem Parameter Puffer zu platzieren. Lange Daten werden in der Regel in Teilen zur Ausführungszeit gesendet.  
  
 **database**  
 Eine diskrete Auflistung von Daten in einem DBMS. Außerdem ein DBMS.  
  
 **Datenbank-Engine**  
 Die Software in einem DBMS, die SQL-Anweisungen analysiert und ausführt und auf die physischen Daten zugreift.  
  
 **DBMS**  
 Daten Bank Verwaltungs System. Eine Softwareebene zwischen der physischen Datenbank und dem Benutzer. Das DBMS dient zur Verwaltung des gesamten Zugriffs auf die Datenbank.  
  
 **DBMS-basierter Treiber**  
 Ein Treiber, der über eine eigenständige Datenbank-Engine auf physische Daten zugreift.  
  
 **DDL**  
 Datendefinitionssprache. Diese Anweisungen in SQL, die definieren, dass Daten nicht geändert werden. Beispielsweise **CREATE TABLE**, **Index erstellen**, **erteilen**und **widerrufen**.  
  
 **Begrenzungsbezeichner**  
 Ein Bezeichner, der in bezeichneranführungs Zeichen eingeschlossen ist, sodass er Sonderzeichen oder Vergleichs Schlüsselwörter enthalten kann (auch als Bezeichner in Anführungszeichen bezeichnet).  
  
 **Deskriptor**  
 Eine Datenstruktur, die Informationen zu Spaltendaten oder dynamischen Parametern enthält. Die physische Darstellung des Deskriptors ist nicht definiert. Anwendungen erhalten nur einen direkten Zugriff auf einen Deskriptor, indem Sie die zugehörigen Felder durch Aufrufen von ODBC-Funktionen mit dem Deskriptorhandle bearbeiten.  
  
 **Desktop Datenbank**  
 Ein DBMS, das auf einem persönlichen Computer ausgeführt werden soll. Im allgemeinen stellen diese DBMSs keine eigenständige Datenbank-Engine bereit und müssen über einen dateibasierten Treiber aufgerufen werden. Die Module in diesen Treibern haben in der Regel geringere Unterstützung für SQL und Transaktionen. Beispiel: dBASE, Paradox, Btrieve oder Microsoft® FoxPro®.  
  
 **Diagnostics**  
 Ein Datensatz, der Diagnoseinformationen über die letzte Funktion mit dem Namen enthält, die ein bestimmtes Handle verwendet haben. Diagnosedaten Sätze sind Umgebungs-, Verbindungs-, Anweisungs-und Deskriptorhandles zugeordnet.  
  
 **DML**  
 Daten Bearbeitungs Sprache. Diese Anweisungen in SQL, die bearbeiten, anstatt Daten zu definieren. Beispielsweise **Insert**, **Update**, **Delete**und **Select**.  
  
 **Trei**  
 Eine Routine Bibliothek, die die Funktionen in der ODBC-API verfügbar macht. Treiber sind für ein einzelnes DBMS spezifisch.  
  
 **Treiber-Manager**  
 Eine Routine Bibliothek, die den Zugriff auf Treiber für die Anwendung verwaltet. Der Treiber-Manager lädt und entlädt (bzw. stellt eine Verbindung mit dem Treiber her und trennt ihn) und übergibt Aufrufe an ODBC-Funktionen an den richtigen Treiber.  
  
 **Treiber-Setup-DLL**  
 Eine DLL, die Treiber spezifische Installations-und Konfigurationsfunktionen enthält.  
  
 **Dynamischer Cursor**  
 Ein Bild lauffähigen Cursor, der Zeilen erkennen kann, die im Resultset aktualisiert, gelöscht oder eingefügt wurden.  
  
 **Dynamisches SQL**  
 Ein eingebetteter SQL-Typ, in dem SQL-Anweisungen zur Laufzeit erstellt und kompiliert werden. *Siehe auch* statisches SQL.  
  
## <a name="e"></a>E  
 **eingebettetes SQL**  
 SQL-Anweisungen, die direkt in einem in einer anderen Sprache geschriebenen Programm enthalten sind, wie z. b. COBOL oder C. ODBC, verwenden Embedded SQL nicht. *Siehe auch* statisches SQL *und* dynamisches SQL.  
  
 **Umgebung**  
 Ein globaler Kontext, in dem auf Daten zugegriffen werden soll. der Umgebung zugeordnet sind alle Informationen, die Global sind, z. b. eine Liste aller Verbindungen in dieser Umgebung.  
  
 **Umgebungs Handle**  
 Ein Handle für eine Datenstruktur, die Informationen über die Umgebung enthält.  
  
 **Escape-Klausel**  
 Eine-Klausel in einer SQL-Anweisung.  
  
 **auszuführen**  
 Zum Ausführen einer SQL-Anweisung.  
  
## <a name="f"></a>F  
 **FAT-Cursor**  
 *Siehe* Block Cursor.  
  
 **Fetti**  
 , Wenn eine oder mehrere Zeilen aus einem Resultset abgerufen werden sollen.  
  
 **Flächen**  
 *Siehe* Spalte.  
  
 **Datei basierter Treiber**  
 Ein Treiber, der direkt auf physische Daten zugreift. In diesem Fall enthält der Treiber eine Datenbank-Engine und fungiert sowohl als Treiber als auch als Datenquelle.  
  
 **Datei Datenquelle**  
 Eine Datenquelle, für die Verbindungsinformationen in einer DSN-Datei gespeichert werden.  
  
 **Fremdschlüssel**  
 Eine Spalte oder Spalten in einer Tabelle, die mit dem Primärschlüssel in einer anderen Tabelle verglichen werden.  
  
 **Vorwärts Cursor**  
 Ein Cursor, der sich nur durch das Resultset vorwärts bewegen und in der Regel jeweils nur eine Zeile abruft. Die meisten relationalen Datenbanken unterstützen nur vorwärts Cursor.  
  
## <a name="h"></a>H  
 **bewältigen**  
 Ein Wert, der einen eindeutigen Wert angibt, z. b. eine Datei oder eine Datenstruktur. Handles sind nur für die Software von Bedeutung, die Sie erstellt und verwendet, aber von anderer Software zur Identifizierung von Informationen an Sie übermittelt wird. ODBC definiert Handles für Umgebungen, Verbindungen, Anweisungen und Deskriptoren.  
  
## <a name="i"></a>I  
 **Implementierungs Parameter Deskriptor (IPD)**  
 Ein Deskriptor, der die dynamischen Parameter beschreibt, die in einer SQL-Anweisung nach allen von der Anwendung angegebenen Konvertierungen verwendet werden.  
  
 **Implementierungs Zeilen Deskriptor (IRD)**  
 Ein Deskriptor, der eine Daten Zeile vor allen von der Anwendung angegebenen Konvertierungen beschreibt.  
  
 **Installer-dll**  
 Eine DLL, die ODBC-Komponenten installiert und Datenquellen konfiguriert.  
  
 **Integritäts Erweiterungs Funktion**  
 Eine Teilmenge von SQL, die zur Aufrechterhaltung der Integrität einer Datenbank entworfen wurde.  
  
 **Schnittstellen Konformitäts Ebene**  
 Die Ebene der von einem Treiber unterstützten ODBC 3,7-Schnittstelle. kann "Core", "Level 1" oder "Level 2" sein.  
  
 **interoper**  
 Die Fähigkeit einer Anwendung, beim Zugriff auf Daten in unterschiedlichen DBMSs denselben Code zu verwenden.  
  
 **IPD**  
 *Siehe* Implementierungs Parameter Deskriptor (IPD).  
  
 **IRD**  
 *Siehe* Implementierungs Zeilen Deskriptor (IRD).  
  
 **ISO/IEC**  
 International Standards Organization/Internationale Elektrotechnische Kommission. Die ODBC-API basiert auf der ISO/IEC-Schnittstelle auf der Telefon Ebene.  
  
## <a name="j"></a>J  
 **join**  
 Ein Vorgang in einer relationalen Datenbank, der die Zeilen in zwei oder mehr Tabellen durch übereinstimmende Werte in angegebenen Spalten verknüpft.  
  
## <a name="k"></a>K  
 **key**  
 Eine Spalte oder Spalten, deren Werte eine Zeile identifizieren. *Siehe auch* Fremdschlüssel *und* Primärschlüssel.  
  
 **Keyset**  
 Ein Satz von Schlüsseln, die von einem gemischten oder keysetgesteuerten Cursor zum erneuten Abrufen von Zeilen verwendet werden.  
  
 **Keysetgesteuerter Cursor**  
 Ein Bild lauffähigen Cursor, der aktualisierte und gelöschte Zeilen mithilfe eines Keysets erkennt.  
  
## <a name="l"></a>L  
 **wahrsten**  
 Eine Zeichen Darstellung eines tatsächlichen Datenwerts in einer SQL-Anweisung.  
  
 **gelungen**  
 Der Prozess, durch den ein DBMS den Zugriff auf eine Zeile in einer mehr Benutzerumgebung einschränkt. Das DBMS legt normalerweise ein Bit für eine Zeile oder die physische Seite mit einer Zeile fest, die angibt, dass die Zeile oder Seite gesperrt ist.  
  
 **lange Daten**  
 Alle Binär-oder Zeichendaten über eine bestimmte Länge, z. b. 255 Bytes oder Zeichen. In der Regel viel länger. Diese Daten werden in der Regel an die Datenquelle gesendet und in Teilen aus der Datenquelle abgerufen. Auch als *BLOB*s oder *CLOB*bezeichnet.  
  
## <a name="m"></a>M  
 **Computer Datenquelle**  
 Eine Datenquelle, für die Verbindungsinformationen auf dem System gespeichert werden (z. b. die Registrierung).  
  
 **manueller Commit-Modus**  
 Ein transaktionscommitmodus, in dem Transaktionen explizit durch Aufrufen von **SQLTransact**committet werden müssen.  
  
 **metadata**  
 Daten, die einen Parameter in einer SQL-Anweisung oder eine Spalte in einem Resultset beschreiben. Beispielsweise der Datentyp, die Byte Länge und die Genauigkeit eines Parameters.  
  
 **Treiber mit mehreren Ebenen**  
 *Siehe* DBMS-basierter Treiber.  
  
## <a name="n"></a>N  
 **NULL-Wert**  
 Es ist kein explizit zugewiesener Wert vorhanden. Ein NULL-Wert unterscheidet sich insbesondere von 0 (null) oder leer.  
  
## <a name="o"></a>O  
 **Oktett**  
 8 Bits oder ein Byte. *Siehe auch* Byte.  
  
 **Oktett-Länge**  
 Die Länge in Oktette eines Puffers oder der darin enthaltenen Daten.  
  
 **ODBC**  
 Open Database Connectivity. Eine Spezifikation für eine API, die einen Standardsatz von Routinen definiert, mit dem eine Anwendung auf Daten in einer Datenquelle zugreifen kann.  
  
 **ODBC-Administrator**  
 Ein ausführbares Programm, das die Installationsprogramm-dll zum Konfigurieren von Datenquellen aufruft.  
  
 Gruppe öffnen  
 Ein Unternehmen, das Standards veröffentlicht. Insbesondere werden die Standards der SQL-Zugriffs Gruppe ("-Dienst") veröffentlicht.  
  
 **optimistische Parallelität**  
 Eine Strategie zum Erhöhen der Parallelität, in der Zeilen nicht gesperrt sind. Stattdessen prüft ein Cursor vor der Aktualisierung oder Löschung, ob Sie seit dem letzten Lesen geändert wurden. Wenn dies der Fall ist, schlägt die Aktualisierung oder Löschung fehl. *Siehe auch* pessimistische Parallelität.  
  
 **Äußerer Join**  
 Ein Join, bei dem sowohl übereinstimmende als auch nicht passende Zeilen zurückgegeben werden. Die Werte aller Spalten aus der nicht übereinstimmenden Tabelle in nicht übereinstimmenden Zeilen werden auf NULL festgelegt.  
  
 **Eigentor**  
 Der Besitzer einer Tabelle.  
  
## <a name="p"></a>P  
 **Parame**  
 Eine Variable in einer SQL-Anweisung, die mit einer Parameter Markierung oder einem Fragezeichen (?) markiert ist. Parameter werden an Anwendungsvariablen und ihre Werte gebunden, die beim Ausführen der Anweisung abgerufen werden.  
  
 **Parameter Deskriptor**  
 Ein Deskriptor, der die in einer SQL-Anweisung verwendeten Lauf Zeitparameter beschreibt, entweder vor einer Konvertierung, die von der Anwendung (einem Anwendungsparameter Deskriptor oder einer APD) angegeben wird, oder nach einer von der Anwendung (einem Implementierungs Parameter Deskriptor oder IPD) angegebenen Konvertierung.  
  
 **Parameter Vorgangs Array**  
 Ein Array, das Werte enthält, die von einer Anwendung festgelegt werden können, um anzugeben, dass der entsprechende Parameter in einem **SQLExecDirect** -oder **SQLExecute** -Vorgang ignoriert werden soll.  
  
 **Parameter Status Array**  
 Ein Array, das nach einem-Befehl von **SQLExecDirect** oder **SQLExecute**den Status eines Parameters enthält.  
  
 **Eingeschränkte Parallelität**  
 Eine Strategie zum Implementieren der Serialisierbarkeit, bei der Zeilen gesperrt werden, sodass Sie von anderen Transaktionen nicht geändert werden können. *Siehe auch* vollständige Parallelität *und* Serialisierbarkeit.  
  
 **positionierter Vorgang**  
 Jeder Vorgang, der für die aktuelle Zeile fungiert. Beispielsweise positionierte UPDATE-und DELETE-Anweisungen, **SQLGetData**und **SQLSetPos**.  
  
 **positionierte UPDATE-Anweisung**  
 Eine SQL-Anweisung, die verwendet wird, um die Werte in der aktuellen Zeile zu aktualisieren.  
  
 **Positionierte DELETE-Anweisung**  
 Eine SQL-Anweisung, mit der die aktuelle Zeile gelöscht wird.  
  
 **erstellt**  
 So kompilieren Sie eine SQL-Anweisung Ein Zugriffs Plan wird erstellt, indem eine SQL-Anweisung vorbereitet wird.  
  
 **Primärschlüssel**  
 Eine Spalte oder Spalten, die eine Zeile in einer Tabelle eindeutig identifiziert.  
  
 **Dringlichkeit**  
 Eine Gruppe mit einer oder mehreren vorkompilierten SQL-Anweisungen, die als benanntes Objekt in einer Datenbank gespeichert werden.  
  
 **Spalte "Procedure"**  
 Ein Argument in einem Prozedur Befehl, der Wert, der von einer Prozedur zurückgegeben wird, oder eine Spalte in einem Resultset, das durch eine Prozedur erstellt wurde.  
  
## <a name="q"></a>Q  
 **Turnier**  
 Eine Datenbank, die eine oder mehrere Tabellen enthält.  
  
 **Frage**  
 Eine SQL-Anweisung. Wird manchmal verwendet, um eine **Select** -Anweisung zu verwenden.  
  
 **Bezeichner in Anführungszeichen**  
 Ein Bezeichner, der in bezeichneranführungs Zeichen eingeschlossen ist, sodass er Sonderzeichen oder Übereinstimmungs Schlüsselwörter (auch in SQL-92 als Begrenzungs Bezeichner bezeichnet) enthalten kann.  
  
## <a name="r"></a>R  
 **Basis**  
 Die Basis eines Zahlen Systems. Normalerweise 2 oder 10.  
  
 **Aufnahme**  
 *Siehe* Zeile.  
  
 **Resultset**  
 Der Satz von Zeilen, der durch Ausführen einer **Select** -Anweisung erstellt wird.  
  
 **Rückgabecode**  
 Der Wert, der von einer ODBC-Funktion zurückgegeben wird.  
  
 **Rollback**  
 , Um die von einer Transaktion geänderten Werte in ihren ursprünglichen Zustand zurückzusetzen.  
  
 **Zeile**  
 Ein Satz verwandter Spalten, die eine bestimmte Entität beschreiben. Wird auch als *Datensatz*bezeichnet.  
  
 **Zeilen Deskriptor**  
 Ein Deskriptor, der die Spalten eines Resultsets beschreibt, entweder vor allen von der Anwendung angegebenen Konvertierungen (einem Implementierungs Zeilen Deskriptor oder IRD) oder nach einer von der Anwendung (einem Anwendungs Zeilen Deskriptor oder einer ARD) angegebenen Konvertierung.  
  
 **Zeilen Vorgangs Array**  
 Ein Array, das Werte enthält, die von einer Anwendung festgelegt werden können, um anzugeben, dass die entsprechende Zeile bei einem **SQLSetPos** -Vorgang ignoriert werden soll.  
  
 **Zeilen Status Array**  
 Ein Array, das nach einem Aufrufen von **SQLFetch**, **SQLFetchScroll**oder **SQLSetPos**den Status einer Zeile enthält.  
  
 **Rowset**  
 Der Satz von Zeilen, die in einem einzelnen Abruf durch einen Block Cursor zurückgegeben werden.  
  
 **rowsetpuffer**  
 Die Puffer, die an die Spalten eines Resultsets gebunden sind und in denen die Daten für ein gesamtes Rowset zurückgegeben werden.  
  
## <a name="s"></a>E  
 **Sägen**  
 *Siehe* SQL Access Group (SAG).  
  
 **Skalarfunktion**  
 Eine Funktion, die einen einzelnen Wert aus einem einzelnen Wert generiert. Beispielsweise eine Funktion, mit der die Groß-/Kleinschreibung von Zeichendaten geändert wird.  
  
 **Chaos**  
 *Siehe* catalog.  
  
 **scrollfähigen Cursor**  
 Ein Cursor, der vorwärts oder rückwärts durch das Resultset verschoben werden kann.  
  
 **Serialisierbarkeit**  
 Gibt an, ob zwei Transaktionen, die gleichzeitig ausgeführt werden, ein Ergebnis erzeugt, das mit der seriellen (oder sequenziellen) Ausführung dieser Transaktionen identisch ist. Serialisierbare Transaktionen sind erforderlich, um die Datenbankintegrität beizubehalten.  
  
 **Server Datenbank**  
 Ein DBMS, das in einer Client-/Server-Umgebung ausgeführt werden soll. Diese DBMSs stellen ein eigenständiges Datenbankmodul bereit, das umfangreiche Unterstützung für SQL und Transaktionen bietet. Der Zugriff erfolgt über DBMS-basierte Treiber. Zum Beispiel Oracle, Informix, DB/2 oder Microsoft® SQL Server.  
  
 **Set-Funktion**  
 *Siehe* Aggregatfunktion.  
  
 **Setup-DLL**  
 *Weitere Informationen finden* Sie unter Treiber Setup *-dll und Setup-* dll  
  
 **Single-Tier-Treiber**  
 *Weitere Informationen finden* Sie unter Datei basierter Treiber.  
  
 **SQL**  
 strukturierte Abfragesprache. Eine Sprache, die von relationalen Datenbanken zum Abfragen, aktualisieren und Verwalten von Daten verwendet wird.  
  
 **SQL-Zugriffs Gruppe (SAG)**  
 Ein Branchen Konsortium von Unternehmen, die sich mit SQL DBMSs beschäftigen. Die Schnittstelle auf der Ebene der geöffneten Gruppe basiert auf der ursprünglich von der SQL-Zugriffs Gruppe ausgeführten Arbeit.  
  
 **SQL-Konformitätsstufe**  
 Die Ebene der SQL-92-Grammatik, die von einem Treiber unterstützt wird. kann "Entry", "fps Transition", "Intermediate" oder "Full" lauten  
  
 **SQL-Datentyp**  
 Der Datentyp einer Spalte oder eines Parameters, wie er in der Datenquelle gespeichert ist.  
  
 **SQLSTATE**  
 Ein-Wert mit fünf Zeichen, der einen bestimmten Fehler angibt.  
  
 **SQL-Anweisung**  
 Ein vollständiger Ausdruck in SQL, der mit einem Schlüsselwort beginnt und eine Aktion, die ausgeführt werden soll, vollständig beschreibt. Wählen Sie z. b. * from Orders aus. SQL-Anweisungen sollten nicht mit-Anweisungen verwechselt werden.  
  
 **state**  
 Eine klar definierte Bedingung eines Elements. Eine Verbindung besteht z. b. aus sieben Zuständen, einschließlich der nicht zugeordneten, zugeordneten, verbundenen und benötigten Daten. Bestimmte Vorgänge können nur ausgeführt werden, wenn sich ein Element in einem bestimmten Zustand befindet. Beispielsweise kann eine Verbindung nur freigegeben werden, wenn Sie sich in einem zugewiesenen Zustand befindet, nicht, wenn Sie sich z. b. in einem verbundenen Zustand befindet.  
  
 **Zustandsübergang**  
 Die Bewegung eines Elements von einem Zustand in einen anderen. ODBC definiert strenge Zustandsübergänge für Umgebungen, Verbindungen und Anweisungen.  
  
 **an**  
 Ein Container für alle Informationen im Zusammenhang mit einer SQL-Anweisung. -Anweisungen sollten nicht mit SQL-Anweisungen verwechselt werden.  
  
 **Anweisungs Handle**  
 Ein Handle für eine Datenstruktur, die Informationen über eine-Anweisung enthält.  
  
 **Statischer Cursor**  
 Ein Bild lauffähigen Cursor, der im Resultset keine Updates, Löschungen oder Einfügungen erkennen kann Wird normalerweise durch Erstellen einer Kopie des Resultsets implementiert.  
  
 **statisches SQL**  
 Ein Typ von eingebettetem SQL, bei dem SQL-Anweisungen hart codiert und kompiliert werden, wenn der Rest des Programms kompiliert wird. *Siehe auch* dynamisches SQL.  
  
 **gespeicherte Prozedur**  
 *Siehe* Procedure.  
  
## <a name="t"></a>T  
 **Tabelle**  
 Eine Auflistung von Zeilen.  
  
 **Thunking**  
 Die Konvertierung von 16-Bit-Adressen in 32-Bit-Adressen oder umgekehrt, wenn 16-Bit-Anwendungen mit 32-Bit-ODBC-Treibern verwendet werden.  
  
 **Geschäfte**  
 Unteilbare Arbeitseinheit. Die Arbeit in einer Transaktion muss als Ganzes abgeschlossen werden. Wenn bei einem Teil der Transaktion ein Fehler auftritt, misslingt die gesamte Transaktion.  
  
 **Transaktions Isolation**  
 Der Vorgang der Isolierung einer Transaktion von den Auswirkungen aller anderen Transaktionen.  
  
 **Transaktions Isolationsstufe**  
 Ein Measure, wie gut eine Transaktion isoliert ist. Es gibt fünf Transaktions Isolations Stufen: Read nicht Commit, Read Commit, Repeatable Read, serialisierbar und Versionierung.  
  
 **Konvertierungs-DLL**  
 Eine DLL, die verwendet wird, um Daten von einem Zeichensatz in einen anderen zu konvertieren.  
  
 **Setup-DLL für Translator**  
 Eine DLL, die Konvertierungs spezifische Installations-und Konfigurationsfunktionen enthält.  
  
 **Zweiphasencommit**  
 Der Prozess des Commits einer verteilten Transaktion in zwei Phasen. In der ersten Phase überprüft der Transaktionsprozessor, ob für alle Teile der Transaktion ein Commit ausgeführt werden kann. In der zweiten Phase werden für alle Teile der Transaktion ein Commit ausgeführt. Wenn ein Teil der Transaktion in der ersten Phase angibt, dass kein Commit ausgeführt werden kann, wird die zweite Phase nicht ausgeführt. ODBC unterstützt keine Zweiphasencommits.  
  
 **Typindikator**  
 Ein ganzzahliger Wert, der an eine ODBC-Funktion übergeben oder zurückgegeben wird, um den Datentyp einer Anwendungsvariablen, eines Parameters oder einer Spalte anzugeben. ODBC definiert Typindikatoren für C-und SQL-Datentypen.  
  
## <a name="v"></a>V  
 **Anschauung**  
 Eine alternative Methode, um die Daten in einer oder mehreren Tabellen zu betrachten. Eine Sicht wird in der Regel als Teilmenge der Spalten aus einer oder mehreren Tabellen erstellt. In ODBC entsprechen Sichten im Allgemeinen den Tabellen.
