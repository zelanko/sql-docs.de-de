---
title: ODBC Glossar | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302901"
---
# <a name="odbc-glossary"></a>ODBC-Glossar
## <a name="a"></a>Ein  
 **Zugangsplan**  
 Ein Plan, der vom Datenbankmodul generiert wird, um eine SQL-Anweisung auszuführen. Entspricht ausführbarem Code, der aus einer Sprache der dritten Generation wie C kompiliert wird.  
  
 **Aggregatfunktion**  
 Eine Funktion, die einen einzelnen Wert aus einer Gruppe von Werten generiert, die häufig mit **GROUP BY-** und **HAVING-Klauseln** verwendet werden. Zu den Aggregatfunktionen gehören **AVG**, **COUNT**, **MAX**, **MIN**und **SUM**. Auch als *Set-Funktionen*bekannt . *Siehe auch* skalarfunktionär.  
  
 **Ansi**  
 American National Standards Institute. Die ODBC-API basiert auf der ANSI Call-Level-Schnittstelle.  
  
 **APD**  
 *Siehe* Anwendungsparameterdeskriptor (APD).  
  
 **API**  
 Anwendungsprogrammierschnittstelle. Eine Reihe von Routinen, die eine Anwendung verwendet, um Dienste auf niedrigerer Ebene anzufordern und auszuführen. Die ODBC-API besteht aus den ODBC-Funktionen.  
  
 **application**  
 Ein ausführbares Programm, das Funktionen in der ODBC-API aufruft.  
  
 **Anwendungsparameterdeskriptor (APD)**  
 Ein Deskriptor, der die dynamischen Parameter beschreibt, die in einer SQL-Anweisung vor jeder von der Anwendung angegebenen Konvertierung verwendet werden.  
  
 **Anwendungszeilendeskriptor (ARD)**  
 Ein Deskriptor, der die Spaltenmetadaten und -daten in den Puffern der Anwendung darstellt und eine Datenzeile nach einer von der Anwendung angegebenen Datenkonvertierung beschreibt.  
  
 **Ard**  
 *Siehe* Anwendungszeilendeskriptor (ARD).  
  
 **Auto-Commit-Modus**  
 Ein Transaktionscommitmodus, in dem Transaktionen unmittelbar nach der Ausführung festgeschrieben werden.  
  
## <a name="b"></a>B  
 **Verhaltensänderung**  
 Eine Änderung bestimmter Funktionen von ODBC *3.x-Verhalten* zu ODBC *2.x-Verhalten* oder umgekehrt. Verursacht durch Ändern des SQL_ATTR_ODBC_VERSION Umgebungsattributs.  
  
 **Binäres großes Objekt (BLOB)**  
 Alle Binärdaten über eine bestimmte Anzahl von Bytes, z. B. 255. In der Regel viel länger. Solche Daten werden in der Regel in Teilen an die Datenquelle gesendet und von ihr abgerufen. Auch als *Long Data*bekannt .  
  
 **Bindung**  
 Als Verb, der Akt der Zuordnung einer Spalte in einer Ergebnismenge oder eines Parameters in einer SQL-Anweisung mit einer Anwendungsvariablen. Als ein Nostantiv, der Verein.  
  
 **Bindungsversatz**  
 Ein Mehrwert zu den Datenpufferadressen und Längen-/Indikatorpufferadressen für alle gebundenen Spalten- oder Parameterdaten, wodurch neue Adressen erzeugt werden.  
  
 **Blockcursor**  
 Ein Cursor, der mehr als eine Datenzeile gleichzeitig abrufen kann.  
  
 **Puffer**  
 Ein Stück Anwendungsspeicher, der zum Übergeben von Daten zwischen der Anwendung und dem Treiber verwendet wird. Puffer kommen oft paarweise vor: ein *Datenpuffer* und ein *Datenlängenpuffer*.  
  
 **Byte**  
 Acht Bits oder ein Oktett. *Siehe auch* Oktett.  
  
## <a name="c"></a>C  
 **C-Datentyp**  
 Der Datentyp einer Variablen in einem C-Programm, in diesem Fall die Anwendung.  
  
 **Katalog**  
 Der Satz von Systemtabellen in einer Datenbank, die die Form der Datenbank beschreiben. Wird auch als *Schema* oder *Datenwörterbuch*bezeichnet.  
  
 **Katalogfunktion**  
 Eine ODBC-Funktion, die zum Abrufen von Informationen aus dem Datenbankkatalog verwendet wird.  
  
 **Befehlszeilenschnittstelle (CLI)**  
 *Siehe* Api.  
  
 **Client/Server**  
 Eine Datenbankzugriffsstrategie, bei der ein oder mehrere Clients über einen Server auf Daten zugreifen. Die Clients implementieren in der Regel die Benutzeroberfläche, während der Server den Datenbankzugriff steuert.  
  
 **Spalte**  
 Der Container für ein einzelnes Informationselement in einer Zeile. Auch bekannt als *Feld*.  
  
 **begehen**  
 So machen Sie die Änderungen in einer Transaktion dauerhaft.  
  
 **concurrency**  
 Die Möglichkeit von mehr als einer Transaktion, gleichzeitig auf dieselben Daten zuzugreifen.  
  
 **Konformitätsstufe**  
 Ein diskreter Satz von Funktionen, die von einem Treiber oder einer Datenquelle unterstützt werden. ODBC definiert API-Konformitätsstufen und SQL-Konformitätsebenen.  
  
 **connection**  
 Eine bestimmte Instanz eines Treibers und einer Datenquelle.  
  
 **Verbindungs-Browsing**  
 Durchsuchen des Netzwerks nach Datenquellen, mit der eine Verbindung hergestellt werden soll. Das Durchsuchen der Verbindung kann mehrere Schritte umfassen. Der Benutzer kann z. B. zuerst das Netzwerk nach Servern durchsuchen und dann einen bestimmten Server nach einer Datenbank durchsuchen.  
  
 **Verbindungshandle**  
 Ein Handle für eine Datenstruktur, die Informationen zu einer Verbindung enthält.  
  
 **aktuelle Zeile**  
 Die Zeile, auf die der Cursor derzeit zeigt. Positionierte Vorgänge wirken auf die aktuelle Zeile.  
  
 **Cursor**  
 Eine Software, die Datenzeilen an die Anwendung zurückgibt. Wahrscheinlich nach dem blinkenden Cursor auf einem Computerterminal benannt; genau wie dieser Cursor die aktuelle Position auf dem Bildschirm angibt, zeigt ein Cursor in einem Resultset die aktuelle Position im Resultset an.  
  
## <a name="d"></a>D  
 **Datenpuffer**  
 Ein Puffer, der zum Übergeben von Daten verwendet wird. Häufig ist ein *Datenlängenpuffer*mit einem Datenpuffer verknüpft.  
  
 **Datenwörterbuch**  
 *Siehe* Katalog.  
  
 **Datenlängenpuffer**  
 Ein Puffer, der verwendet wird, um die Länge des Werts in einem entsprechenden *Datenpuffer*zu übergeben. Der Datenlängenpuffer wird auch zum Speichern von Indikatoren verwendet, z. B. ob der Datenwert null-terminiert ist.  
  
 **Datenquelle**  
 Die Daten, auf die der Benutzer zugreifen möchte, und das zugehörige Betriebssystem, DBMS und Netzwerkplattform (falls vorhanden).  
  
 **Datentyp**  
 Der Typ eines Datenstücks. ODBC definiert C- und SQL-Datentypen. *Siehe auch* Typanzeige.  
  
 **Data-at-Execution-Spalte**  
 Eine Spalte, für die Daten gesendet werden, nachdem **SQLSetPos** aufgerufen wurde. Benannt also, da die Daten zur Ausführungszeit gesendet werden, anstatt in einem Rowset-Puffer platziert zu werden. Lange Daten werden in der Regel in Teilen zur Ausführungszeit gesendet.  
  
 **Data-at-Execution-Parameter**  
 Ein Parameter, für den Daten nach **SQLExecute** oder **SQLExecDirect** gesendet werden, wird aufgerufen. Benannt also, weil die Daten gesendet werden, wenn die SQL-Anweisung ausgeführt wird, anstatt in einem Parameterpuffer platziert zu werden. Lange Daten werden in der Regel in Teilen zur Ausführungszeit gesendet.  
  
 **Datenbank**  
 Eine diskrete Datensammlung in einem DBMS. Auch ein DBMS.  
  
 **Datenbankmodul**  
 Die Software in einem DBMS, die SQL-Anweisungen analysiert und ausführt und auf die physischen Daten zugreift.  
  
 **Dbms**  
 Datenbankverwaltungssystem. Eine Softwareebene zwischen der physischen Datenbank und dem Benutzer. Das DBMS dient zur Verwaltung des gesamten Zugriffs auf die Datenbank.  
  
 **DBMS-basierter Treiber**  
 Ein Treiber, der über ein eigenständiges Datenbankmodul auf physische Daten zugreift.  
  
 **DDL**  
 Datendefinitionssprache. Die Anweisungen in SQL, die Daten definieren, anstatt sie zu manipulieren. Beispiel: **CREATE TABLE**, **CREATE INDEX**, **GRANT**und **REVOKE**.  
  
 **Begrenzungsbezeichner**  
 Ein Bezeichner, der in Bezeichner-Anführungszeichen eingeschlossen ist, sodass er Sonderzeichen oder Übereinstimmungsschlüsselwörter enthalten kann (auch als Anführungszeichen bezeichnet).  
  
 **Deskriptor**  
 Eine Datenstruktur, die Informationen zu Spaltendaten oder dynamischen Parametern enthält. Die physische Darstellung des Deskriptors ist nicht definiert. Anwendungen erhalten direkten Zugriff auf einen Deskriptor nur, indem sie seine Felder bearbeiten, indem odBC-Funktionen mit dem Deskriptor-Handle aufgerufen werden.  
  
 **Desktop-Datenbank**  
 Ein DBMS, das für die Ausführung auf einem PC entwickelt wurde. Im Allgemeinen stellen diese DBMS kein eigenständiges Datenbankmodul bereit und müssen über einen dateibasierten Treiber aufgerufen werden. Die Engines in diesen Treibern haben in der Regel die Unterstützung für SQL und Transaktionen reduziert. Beispiel: dBASE, Paradox, Btrieve oder Microsoft® FoxPro®.  
  
 **Diagnose**  
 Ein Datensatz, der Diagnoseinformationen über die letzte Funktion enthält, die aufgerufen wurde, die ein bestimmtes Handle verwendet hat. Diagnosedatensätze sind Umgebungs-, Verbindungs-, Anweisungs- und Deskriptorhandles zugeordnet.  
  
 **DML**  
 Datenmanipulationssprache. Die Anweisungen in SQL, die Daten manipulieren, anstatt sie zu definieren. Beispiel: **INSERT**, **UPDATE**, **DELETE**und **SELECT**.  
  
 **Treiber**  
 Eine Routinebibliothek, die die Funktionen in der ODBC-API verfügbar macht. Treiber sind spezifisch für ein einzelnes DBMS.  
  
 **Treiber-Manager**  
 Eine Routinebibliothek, die den Zugriff auf Treiber für die Anwendung verwaltet. Der Treiber-Manager lädt und entlädt Treiber (oder verbindet sie mit ihnen und trennt diese von ihnen) und übergibt Anrufe an ODBC-Funktionen an den richtigen Treiber.  
  
 **Treiber-Setup-DLL**  
 Eine DLL, die treiberspezifische Installations- und Konfigurationsfunktionen enthält.  
  
 **Dynamischer Cursor**  
 Ein scrollbarer Cursor, der zeilenaktualisierte, gelöschte oder in das Resultset eingefügte Zeilen erkennen kann.  
  
 **Dynamisches SQL**  
 Ein Typ eingebetteter SQL, in dem SQL-Anweisungen zur Laufzeit erstellt und kompiliert werden. *Siehe auch* statischeSQL.  
  
## <a name="e"></a>E  
 **Eingebettete SQL**  
 SQL-Anweisungen, die direkt in einem Programm enthalten sind, das in einer anderen Sprache geschrieben wurde, z. B. COBOL oder C. ODBC verwendet keine eingebettete SQL. *Siehe auch* statisches SQL *und* dynamisches SQL.  
  
 **Umgebung**  
 Ein globaler Kontext für den Zugriff auf Daten; Der Umgebung zugeordnet sind alle Informationen, die globaler Natur sind, z. B. eine Liste aller Verbindungen in dieser Umgebung.  
  
 **Umgebungshandle**  
 Ein Handle für eine Datenstruktur, die Informationen über die Umgebung enthält.  
  
 **Fluchtklausel**  
 Eine Klausel in einer SQL-Anweisung.  
  
 **Ausführen**  
 So führen Sie eine SQL-Anweisung aus.  
  
## <a name="f"></a>F  
 **Fettcursor**  
 *Siehe* Blockcursor.  
  
 **Holen**  
 So rufen Sie eine oder mehrere Zeilen aus einem Resultset ab.  
  
 **Feld**  
 *Siehe* Spalte.  
  
 **Dateibasierter Treiber**  
 Ein Treiber, der direkt auf physische Daten zugreift. In diesem Fall enthält der Treiber ein Datenbankmodul und fungiert sowohl als Treiber als auch als Datenquelle.  
  
 **Dateidatenquelle**  
 Eine Datenquelle, für die Verbindungsinformationen in einer DSN-Datei gespeichert werden.  
  
 **Fremdschlüssel**  
 Eine Spalte oder Spalten in einer Tabelle, die mit dem Primärschlüssel in einer anderen Tabelle übereinstimmen.  
  
 **Vorwärts-Cursor**  
 Ein Cursor, der sich nur durch das Resultset vorwärts bewegen kann und in der Regel nur eine Zeile nach einander abruft. Die meisten relationalen Datenbanken unterstützen nur Vorwärtscursor.  
  
## <a name="h"></a>H  
 **Behandeln**  
 Ein Wert, der eindeutig etwas wie eine Datei oder Datenstruktur identifiziert. Griffe sind nur für die Software sinnvoll, die sie erstellt und verwendet, aber von anderer Software übergeben werden, um Dinge zu identifizieren. ODBC definiert Handles für Umgebungen, Verbindungen, Anweisungen und Deskriptoren.  
  
## <a name="i"></a>I  
 **Implementierungsparameterdeskriptor (IPD)**  
 Ein Deskriptor, der die dynamischen Parameter beschreibt, die in einer SQL-Anweisung nach jeder von der Anwendung angegebenen Konvertierung verwendet werden.  
  
 **Implementierungszeilendeskriptor (IRD)**  
 Ein Deskriptor, der eine Datenzeile vor jeder von der Anwendung angegebenen Konvertierung beschreibt.  
  
 **Installations-DLL**  
 Eine DLL, die ODBC-Komponenten installiert und Datenquellen konfiguriert.  
  
 **Fazilität zur Verbesserung der Integrität**  
 Eine Teilmenge von SQL, die die Integrität einer Datenbank aufrechtzuerhalten.  
  
 **Schnittstellenkonformitätsebene**  
 Die Ebene der ODBC 3.7-Schnittstelle, die von einem Treiber unterstützt wird; kann Core, Level 1 oder Level 2 sein.  
  
 **Interoperabilität**  
 Die Möglichkeit einer Anwendung, denselben Code beim Zugriff auf Daten in verschiedenen DBMS zu verwenden.  
  
 **IPD**  
 *Siehe* Implementierungsparameterdeskriptor (IPD).  
  
 **Ird**  
 *Siehe* Implementierungszeilendeskriptor (IRD).  
  
 **ISO/IEC**  
 International Standards Organization/International Electrotechnical Commission. Die ODBC-API basiert auf der ISO/IEC Call-Level-Schnittstelle.  
  
## <a name="j"></a>J  
 **join**  
 Ein Vorgang in einer relationalen Datenbank, der die Zeilen in zwei oder mehr Tabellen verknüpft, indem Werte in angegebenen Spalten übereinstimmen.  
  
## <a name="k"></a>K  
 **key**  
 Eine Spalte oder Spalten, deren Werte eine Zeile identifizieren. *Siehe auch* Fremdschlüssel *und* Primärschlüssel.  
  
 **Keyset**  
 Eine Reihe von Schlüsseln, die von einem gemischten oder keysetgesteuerten Cursor zum erneuten Abrufen von Zeilen verwendet werden.  
  
 **Keysetgesteuerter Cursor**  
 Ein scrollbarer Cursor, der aktualisierte und gelöschte Zeilen mithilfe eines Keysets erkennt.  
  
## <a name="l"></a>L  
 **literal**  
 Eine Zeichendarstellung eines tatsächlichen Datenwerts in einer SQL-Anweisung.  
  
 **Sperren**  
 Der Prozess, mit dem ein DBMS den Zugriff auf eine Zeile in einer Mehrbenutzerumgebung einschränkt. Das DBMS legt normalerweise ein Bit für eine Zeile oder die physische Seite fest, die eine Zeile enthält, die angibt, dass die Zeile oder Seite gesperrt ist.  
  
 **lange Daten**  
 Binär- oder Zeichendaten über eine bestimmte Länge, z. B. 255 Bytes oder Zeichen. In der Regel viel länger. Solche Daten werden in der Regel in Teilen an die Datenquelle gesendet und von ihr abgerufen. Wird auch als *BLOB*s oder *CLOB*s bezeichnet.  
  
## <a name="m"></a>M  
 **Maschinendatenquelle**  
 Eine Datenquelle, für die Verbindungsinformationen auf dem System gespeichert werden (z. B. die Registrierung).  
  
 **manueller Commit-Modus**  
 Ein Transaktionscommitmodus, in dem Transaktionen explizit durch Aufrufen von **SQLTransact**festgeschrieben werden müssen.  
  
 **metadata**  
 Daten, die einen Parameter in einer SQL-Anweisung oder eine Spalte in einem Resultset beschreiben. Beispielsweise der Datentyp, die Bytelänge und die Genauigkeit eines Parameters.  
  
 **Mehrstufiger Treiber**  
 *Siehe* DBMS-basierten Treiber.  
  
## <a name="n"></a>N  
 **NULL-Wert**  
 Kein explizit zugewiesener Wert. Insbesondere unterscheidet sich ein NULL-Wert von einer Null oder einem Leerzeichen.  
  
## <a name="o"></a>O  
 **Oktett**  
 Acht Bits oder ein Byte. *Siehe auch* Byte.  
  
 **Oktettlänge**  
 Die Länge in den Oktetten eines Puffers oder die darin enthaltenen Daten.  
  
 **ODBC**  
 Öffnen Sie die Datenbankkonnektivität. Eine Spezifikation für eine API, die einen Standardsatz von Routinen definiert, mit denen eine Anwendung auf Daten in einer Datenquelle zugreifen kann.  
  
 **ODBC-Administrator**  
 Ein ausführbares Programm, das die Installations-DLL aufruft, um Datenquellen zu konfigurieren.  
  
 Gruppe öffnen  
 Ein Unternehmen, das Standards veröffentlicht. Insbesondere werden SQL Access Group (SAG)-Standards veröffentlicht.  
  
 **optimistische Parallelität**  
 Eine Strategie zum Erhöhen der Parallelität, bei der Zeilen nicht gesperrt sind. Bevor sie aktualisiert oder gelöscht werden, überprüft ein Cursor, ob sie seit dem letzten Lesen geändert wurden. Wenn dies der Vorgang der Option ist, schlägt die Aktualisierung oder das Löschen fehl. *Siehe auch* pessimistische Parallelität.  
  
 **Äußerer Join**  
 Eine Verknüpfung, in der sowohl übereinstimmende als auch nicht übereinstimmende Zeilen zurückgegeben werden. Die Werte aller Spalten aus der nicht übereinstimmenden Tabelle in nicht übereinstimmenden Zeilen werden auf NULL festgelegt.  
  
 **Besitzer**  
 Der Besitzer einer Tabelle.  
  
## <a name="p"></a>P  
 **Parameter**  
 Eine Variable in einer SQL-Anweisung, die mit einer Parametermarkierung oder einem Fragezeichen (?) gekennzeichnet ist. Parameter sind an Anwendungsvariablen gebunden und ihre Werte werden abgerufen, wenn die Anweisung ausgeführt wird.  
  
 **Parameterdeskriptor**  
 Ein Deskriptor, der die in einer SQL-Anweisung verwendeten Laufzeitparameter beschreibt, entweder vor jeder von der Anwendung angegebenen Konvertierung (ein Anwendungsparameterdeskriptor oder APD) oder nach einer von der Anwendung angegebenen Konvertierung (Implementierungsparameterdeskriptor oder IPD).  
  
 **Parameteroperation Array**  
 Ein Array, das Werte enthält, die eine Anwendung festlegen kann, um anzugeben, dass der entsprechende Parameter in einem **SQLExecDirect-** oder **SQLExecute-Vorgang** ignoriert werden soll.  
  
 **Parameterstatus-Array**  
 Ein Array, das den Status eines Parameters nach einem Aufruf von **SQLExecDirect** oder **SQLExecute**enthält.  
  
 **Eingeschränkte Parallelität**  
 Eine Strategie zum Implementieren der Serialisierbarkeit, bei der Zeilen gesperrt sind, damit sie von anderen Transaktionen nicht geändert werden können. *Siehe auch* optimistische Parallelität *und* Serialisierbarkeit.  
  
 **positionierter Betrieb**  
 Alle Operationen, die auf die aktuelle Zeile wirken. Beispielsweise positionierte Update- und Löschanweisungen, **SQLGetData**und **SQLSetPos**.  
  
 **Positionierte Update-Anweisung**  
 Eine SQL-Anweisung, die zum Aktualisieren der Werte in der aktuellen Zeile verwendet wird.  
  
 **Positionierte Löschanweisung**  
 Eine SQL-Anweisung, die zum Löschen der aktuellen Zeile verwendet wird.  
  
 **Zubereiten**  
 So kompilieren Sie eine SQL-Anweisung. Ein Zugriffsplan wird erstellt, indem eine SQL-Anweisung vorbereitet wird.  
  
 **Primärschlüssel**  
 Eine Spalte oder Spalten, die eine Zeile in einer Tabelle eindeutig identifiziert.  
  
 **Verfahren**  
 Eine Gruppe von einer oder mehreren vorkompilierten SQL-Anweisungen, die als benanntes Objekt in einer Datenbank gespeichert werden.  
  
 **Prozedurspalte**  
 Ein Argument in einem Prozeduraufruf, der von einer Prozedur zurückgegebene Wert oder eine Spalte in einer Resultset, die von einer Prozedur erstellt wurde.  
  
## <a name="q"></a>Q  
 **Qualifizierer**  
 Eine Datenbank, die eine oder mehrere Tabellen enthält.  
  
 **Abfrage**  
 Eine SQL-Anweisung. Manchmal wird eine **SELECT-Anweisung** bezeichnet.  
  
 **Bezeichner in Anführungszeichen**  
 Ein Bezeichner, der in Bezeichner-Anführungszeichen eingeschlossen ist, sodass er Sonderzeichen oder Übereinstimmungsschlüsselwörter enthalten kann (auch in SQL-92 als Trennbezeichner bezeichnet).  
  
## <a name="r"></a>R  
 **Radix**  
 Die Basis eines Zahlensystems. Normalerweise 2 oder 10.  
  
 **Aufzeichnung**  
 *Siehe* Zeile.  
  
 **Resultset**  
 Der Satz von Zeilen, die durch Ausführen einer **SELECT-Anweisung** erstellt wurden.  
  
 **Rückgabecode**  
 Der von einer ODBC-Funktion zurückgegebene Wert.  
  
 **Rollback**  
 So geben Sie die durch eine Transaktion geänderten Werte in ihren ursprünglichen Zustand zurück.  
  
 **Zeile**  
 Ein Satz verwandter Spalten, die eine bestimmte Entität beschreiben. Auch bekannt als *Datensatz*.  
  
 **Zeilendeskriptor**  
 Ein Deskriptor, der die Spalten eines Resultsets beschreibt, entweder vor jeder von der Anwendung angegebenen Konvertierung (implementierungszeilendeskriptor oder IRD) oder nach einer von der Anwendung angegebenen Konvertierung (ein Anwendungszeilendeskriptor oder ARD).  
  
 **Zeilenoperation-Array**  
 Ein Array, das Werte enthält, die eine Anwendung festlegen kann, um anzugeben, dass die entsprechende Zeile in einem **SQLSetPos-Vorgang** ignoriert werden soll.  
  
 **Zeilenstatus-Array**  
 Ein Array, das den Status einer Zeile nach einem Aufruf von **SQLFetch**, **SQLFetchScroll**oder **SQLSetPos**enthält.  
  
 **Rowset**  
 Der Satz von Zeilen, die in einem einzelnen Abruf von einem Blockcursor zurückgegeben werden.  
  
 **Rowset-Puffer**  
 Die Puffer, die an die Spalten eines Resultsets gebunden sind und in denen die Daten für ein gesamtes Rowset zurückgegeben werden.  
  
## <a name="s"></a>E  
 **SAG**  
 *Siehe* SQL Access Group (SAG).  
  
 **Skalarfunktion**  
 Eine Funktion, die einen einzelnen Wert aus einem einzelnen Wert generiert. Zum Beispiel eine Funktion, die die Groß-/Kleinschreibung von Zeichendaten ändert.  
  
 **Schema**  
 *Siehe* Katalog.  
  
 **scrollbarer Cursor**  
 Ein Cursor, der sich vorwärts oder rückwärts durch das Resultset bewegen kann.  
  
 **Serialisierbarkeit**  
 Gibt an, ob zwei gleichzeitig ausgeführte Transaktionen zu einem Ergebnis führen, das mit der seriellen (oder sequenziellen) Ausführung dieser Transaktionen identisch ist. Serialisierbare Transaktionen sind erforderlich, um die Datenbankintegrität aufrechtzuerhalten.  
  
 **Serverdatenbank**  
 Ein DBMS, das für die Ausführung in einer Client/Server-Umgebung entwickelt wurde. Diese DBMS bieten eine eigenständige Datenbank-Engine, die umfassende Unterstützung für SQL und Transaktionen bietet. Auf sie wird über DBMS-basierte Treiber zugegriffen. Beispiel: Oracle, Informix, DB/2 oder Microsoft® SQL Server.  
  
 **Set-Funktion**  
 *Siehe* Aggregatfunktion.  
  
 **Einrichten der DLL**  
 *Siehe* Treibereinrichtung DLL *und* Übersetzer-Setup-DLL.  
  
 **Einstufiger Treiber**  
 *Siehe* dateibasierter Treiber.  
  
 **SQL**  
 Strukturierte Abfragesprache. Eine Sprache, die von relationalen Datenbanken zum Abfragen, Aktualisieren und Verwalten von Daten verwendet wird.  
  
 **SQL Access Group (SAG)**  
 Ein Branchenkonsortium von Unternehmen, die sich mit SQL DBMS befassen. Die Call-Level-Schnittstelle der Open Group basiert auf der Arbeit, die ursprünglich von der SQL Access Group ausgeführt wurde.  
  
 **SQL-Konformitätsebene**  
 Die Ebene der SQL-92-Grammatik, die von einem Treiber unterstützt wird; kann Entry, FIPS Transitional, Intermediate oder Full sein.  
  
 **SQL-Datentyp**  
 Der Datentyp einer Spalte oder eines Parameters, wie er in der Datenquelle gespeichert wird.  
  
 **SQLSTATE**  
 Ein fünfstelliger Wert, der auf einen bestimmten Fehler hinweist.  
  
 **SQL-Anweisung**  
 Ein vollständiger Ausdruck in SQL, der mit einem Schlüsselwort beginnt und eine zu ergreifende Aktion vollständig beschreibt. Beispiel: SELECT * FROM Orders. SQL-Anweisungen sollten nicht mit Anweisungen verwechselt werden.  
  
 **Staat**  
 Eine klar definierte Bedingung eines Artikels. Eine Verbindung hat z. B. sieben Zustände, einschließlich nicht zugewiesener, zugewiesener, verbundener und benötigter Daten. Bestimmte Vorgänge können nur ausgeführt werden, wenn sich ein Element in einem bestimmten Zustand befindet. Eine Verbindung kann z. B. nur freigegeben werden, wenn sie sich in einem zugewiesenen Zustand befindet, und nicht z. B. nicht, wenn sie sich in einem verbundenen Zustand befindet.  
  
 **Zustandsübergang**  
 Die Bewegung eines Elements von einem Zustand in einen anderen. ODBC definiert strenge Zustandsübergänge für Umgebungen, Verbindungen und Anweisungen.  
  
 **Anweisung**  
 Ein Container für alle Informationen, die sich auf eine SQL-Anweisung beziehen. Anweisungen sollten nicht mit SQL-Anweisungen verwechselt werden.  
  
 **Anweisungshandle**  
 Ein Handle für eine Datenstruktur, die Informationen zu einer Anweisung enthält.  
  
 **Statischer Cursor**  
 Ein scrollbarer Cursor, der Keine Aktualisierungen erkennen, löschen oder in das Resultset einfügen kann. In der Regel implementiert, indem sie eine Kopie des Resultsets erstellen.  
  
 **Statische SQL**  
 Ein Typ eingebetteter SQL, bei dem SQL-Anweisungen hartcodiert und kompiliert werden, wenn der Rest des Programms kompiliert wird. *Siehe auch* dynamisches SQL.  
  
 **gespeicherte Prozedur**  
 *Siehe* Verfahren.  
  
## <a name="t"></a>T  
 **Tabelle**  
 Eine Auflistung von Zeilen.  
  
 **Thunking**  
 Die Konvertierung von 16-Bit-Adressen in 32-Bit-Adressen oder umgekehrt, wenn 16-Bit-Anwendungen mit 32-Bit-ODBC-Treibern verwendet werden.  
  
 **Transaktion**  
 Unteilbare Arbeitseinheit. Die Arbeit in einer Transaktion muss als Ganzes abgeschlossen werden. Wenn bei einem Teil der Transaktion ein Fehler auftritt, misslingt die gesamte Transaktion.  
  
 **Transaktionsisolation**  
 Der Akt der Isolierung einer Transaktion von den Auswirkungen aller anderen Transaktionen.  
  
 **Transaktionsisolationsstufe**  
 Ein Maß dafür, wie gut eine Transaktion isoliert ist. Es gibt fünf Transaktionsisolationsstufen: Nicht festschreiben, "Zugeschrieben", "Wiederholbares Lesen", "Serialisierbares" und "Versionierung" ablesen.  
  
 **Übersetzer DLL**  
 Eine DLL, die verwendet wird, um Daten von einem Zeichensatz in einen anderen zu übersetzen.  
  
 **Übersetzer-Setup-DLL**  
 Eine DLL, die übersetzerspezifische Installations- und Konfigurationsfunktionen enthält.  
  
 **Zwei-Phasen-Commit**  
 Der Prozess des Commits einer verteilten Transaktion in zwei Phasen. In der ersten Phase prüft der Transaktionsprozessor, ob alle Teile der Transaktion festgeschrieben werden können. In der zweiten Phase werden alle Teile der Transaktion festgeschrieben. Wenn ein Teil der Transaktion in der ersten Phase angibt, dass er nicht festgeschrieben werden kann, tritt die zweite Phase nicht ein. ODBC unterstützt keine zweiphasigen Commits.  
  
 **Typanzeige**  
 Ein Ganzzahlwert, der an eine ODBC-Funktion übergeben oder von dieser zurückgegeben wird, um den Datentyp einer Anwendungsvariablen, eines Parameters oder einer Spalte anzugeben. ODBC definiert Typindikatoren für C- und SQL-Datentypen.  
  
## <a name="v"></a>V  
 **ansehen**  
 Eine alternative Möglichkeit, die Daten in einer oder mehreren Tabellen zu betrachten. Eine Ansicht wird in der Regel als Teilmenge der Spalten aus einer oder mehreren Tabellen erstellt. In ODBC sind Ansichten im Allgemeinen Tabellen gleichwertig.
