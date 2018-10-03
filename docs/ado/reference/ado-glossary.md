---
title: ADO-Glossar | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ADO, glossary
ms.assetid: b0478836-4123-4357-969a-c5784fc28be5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e60c8f979b52293e2320a1a84cecd17c83caaad4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47681728"
---
# <a name="ado-glossary"></a>ADO-Glossar
In diesem Thema werden die Begriffe, die relevant für ADO definiert.  
  
## <a name="a"></a>A  
 absolute URL  
 Eine vollqualifizierte URL, der angibt, den Speicherort einer Ressource, die befindet sich im Internet oder Intranet. Siehe auch *URL* und *relativen URL*.  
  
 ActiveX-Steuerelement  
 Selbst registrieren von in-Process-COM-Komponente, die häufig ein visuelles Element entweder zur Entwurfszeit oder zur Laufzeit. ActiveX-Steuerelemente können auch für die Kommunikation mit Active Document-Container, z. B. Microsoft Internet Explorer.  
  
 ADISAPI (erweiterte Daten Internet Server Application Programming Interface)  
 Eine ISAPI-DLL, die Analyse bietet, Automation-Steuerelement, Recordset Marshalling und MIME-Paket. Die ADISAPI-Komponente wird über die API von IIS (Internetinformationsdienste) bereitgestellt. Siehe auch *ISAPI*.  
  
 Aggregatfunktion  
 In einer Abfrage, einer Funktion wie COUNT, AVG und STDEV, die einen Wert mit der alle Zeilen in einer Spalte einer Tabelle berechnet. Schreiben von Ausdrücken und beim Programmieren können Sie SQL-Aggregatfunktionen (einschließlich der drei oben aufgeführten) und Domain-Aggregatfunktionen, um verschiedene Statistiken zu ermitteln können.  
  
 alias  
 Ein alternativer Name, den Sie eine Spalte oder einen Ausdruck in einer SQL-SELECT-Anweisung, häufig kürzere oder aussagekräftigere gewähren. ///BobSales ist z. B. den Alias in der folgenden SELECT-Anweisung: "Select Wr-Sales als ///BobSales from SalesDB". Ein Alias kann verwendet werden, um dynamische Zuweisung von Spalten zu Bindungen für das DataControl-Objekt.  
  
 Apartmentthreading  
 Eine COM-Threadingmodell, in dem alle Aufrufe an ein Objekt in einem einzelnen Thread ausgeführt. Apartmentthreading COM synchronisiert und marshallt Aufrufe. Siehe auch *COMmddefcom*.  
  
 asynchroner Vorgang  
 Ein Vorgang, der ohne warten auf Abschluss des Vorgangs die Steuerung an das aufrufende Programm zurückgibt. Bevor der Vorgang abgeschlossen ist, wird die codeausführung fortgesetzt. Siehe auch *synchronen Vorgang*.  
  
## <a name="b"></a>B  
 Bindungseintrags  
 Eine Zuordnung zwischen einem Feld in einer Tabelle und einer Variablen. In den Visual C++ für ADO-Erweiterungen **Recordset** Felder C/C++-Variablen zugeordnet werden.  
  
 Bitmaske  
 Ein numerischer Wert für vorgesehen ein Bit für Bit Wertvergleich mit anderen numerischen Werten in der Regel um Optionen für in-Parameter oder Rückgabewerte zu kennzeichnen. Dieser Vergleich erfolgt normalerweise für bitweise logische Operatoren wie z. B. **und** und **oder** in Visual Basic **&** und **&#124;** in C++.  
  
 Zum Beispiel das ADO- **FieldAttributeEnum** Werte können als Bitmasken verwendet werden, um die Attribute eines Felds zu bestimmen. Angenommen Sie, Sie möchten, um festzustellen, ob ein Feld aktualisiert wurde. Sie können mit dem folgenden Ausdruck in Visual Basic für diesen testen:`Field.Attributes AND adFldUpdatable`  
  
 Wenn das Ergebnis "true", und klicken Sie dann das Feld aktualisierbar ist.  
  
 Lesezeichen (bookmark)  
 Ein Marker, der eine Zeile in einer Gruppe von Zeilen eindeutig zu machen, sodass Benutzer schnell dorthin navigieren kann.  
  
 Geschäftsobjekt  
 Ein Objekt, das einen definierten Satz von Vorgängen, z. B. Daten Überprüfung oder die Regel Geschäftslogik ausführt. Geschäftsobjekte befinden sich normalerweise auf der mittleren Ebene.  
  
 Geschäftsregel  
 Die Kombination der Validierung Bearbeitungen Anmeldung zur Überprüfung, DatenbankSuchen, Richtlinien und algorithmische Transformationen, die Möglichkeit, eines Unternehmens Geschäftsaktivitäten zu bilden. Auch bekannt als *Geschäftslogik*.  
  
## <a name="c"></a>c  
 berechneter Ausdruck  
 Ein Ausdruck, die sich nicht konstant, aber, dessen Wert hängt von anderen Werten. Um ausgewertet werden, muss ein berechneter Ausdruck zu erhalten und berechnet Werte aus anderen Quellen, in der Regel in anderen Feldern oder Zeilen.  
  
 Kapitel  
 Ein Verweis auf einen Bereich von Zeilen aus einer Datenquelle. In ADO ist ein Kapitel in der Regel ein Verweis auf einen anderen **Recordset**.  
  
 Kapitelspalten ermöglichen das Definieren einer *über-und untergeordneten* Beziehung, in denen die *übergeordneten* ist die **Recordset** mit der Kapitelspalte im und die  *untergeordnete* ist die **Recordset** durch das Kapitel dargestellt wird.  
  
 Kapitel-alias  
 Ein Alias, der auf die Spalte aus, das dem übergeordneten angefügt verweist.  
  
 Zeichensatz  
 Eine Zuordnung eines Satzes von Zeichen, die numerische Werte. Unicode ist z. B. eine 16-Bit-Zeichensatz kann alle bekannten Zeichen codiert und als einen weltweiten Standard für zeichencodierung verwendet.  
  
 Untergeordnetes Element  
 Die abhängige Seite einer hierarchischen Beziehung. Ein untergeordnetes Element ist ein Knoten in einer hierarchischen Struktur, die einem anderen übergeordneten Knoten (näher am Stamm). Siehe auch *untergeordnete-Alias*, *über-/ unterordnungsbeziehung*, *übergeordneten*.  
  
 untergeordnete-alias  
 Ein Alias, der auf das untergeordnete Element verweist. Siehe auch *Alias*, *untergeordneten*.  
  
 Die CLSID (Klassen-ID)  
 Einen universally unique Identifier (UUID), der eine COM-Komponente identifiziert. Jede COM-Komponente hat seines CLSID in der Windows-Registrierung, sodass sie von anderen Anwendungen geladen werden können. Siehe auch *ProgID*, *COM*.  
  
 Clientebene  
 Eine logische Ebene eines verteilten Systems, der in der Regel zu Daten und Prozesse, die Eingabe des Benutzers, enthält auch bezeichnet als die *Front-End*. In der Regel die Clientebene fordert Daten von einem Server, auf Grundlage von Eingaben, formatiert und das Ergebnis wird angezeigt. Siehe auch *mittleren Ebene*, *Daten Quellebene*, *verteilte Anwendung*.  
  
 COM (Component Object Model)  
 Eine binäre Standard, der ermöglicht Objekte für die Zusammenarbeit in einer vernetzten Umgebung unabhängig von der Sprache, in der sie entwickelt wurden, oder auf welche Computer sie sich befinden. COM-basierte Technologien zählen ActiveX-Steuerelemente, Automatisierung und Objekt verlinken und einbetten (OLE). COM ermöglicht ein Objekt, dessen Funktionalität mit anderen Komponenten und hostanwendungen verfügbar zu machen. Sie definiert sowohl wie das Objekt selbst verfügbar macht und wie dieses Offenlegen über Prozesse und über Netzwerke hinweg funktioniert. COM definiert auch die Lebensdauer des Objekts.  
  
 COM-Komponente  
 Binäre Datei – z. B. .dll, .ocx und einige .exe-Dateien –, die die COM-Standard für die Bereitstellung von Objekten unterstützt. Eine solche Datei enthält Code für eine oder mehrere Klassenfactorys, COM-Klassen, Mechanismen für Registrierungseinträge, Code zum Laden und So weiter.  
  
 Vergleichsoperator  
 Ein Operator, der vergleicht zwei Ausdrücke und gibt einen booleschen Wert zurück.  
  
 Ein Kriterienparameter, der als ausgedrückt werden kann ">" (größer als), "\<" (kleiner als), "=" (gleich), "> =" (größer als oder gleich), "< =" (kleiner als oder gleich), "<>" (ungleich), oder "like" (Mustervergleich).  
  
 Komponente  
 Ein Objekt, das kapselt sowohl Code als auch Daten und eine wohldefinierte öffentlich zugängliche Dienste bereitstellt.  
  
 Verbunddatei  
 Eine Implementierung von COM strukturiertem Speicher für Dateien. Eine Verbunddatei speichert separate Objekte in einer einzelnen, strukturierte-Datei, die aus zwei Hauptelementen: Storage-Objekte und Streamobjekten. Zusammen können sie wie ein Dateisystem in einer Datei.  
  
 Eine Anzahl von einzelnen Dateien, die zusammen in einer physischen Datei gebunden. Jede einzelne Datei in einer Verbunddatei kann zugegriffen werden, als handele es sich um eine einzelne physische Datei.  
  
 Konstante  
 Ein numerisch oder String-Wert, der nicht geändert wird. Benannte ADO-Enumerationen (Enumerationskonstanten) dienen in Ihrem Code anstelle von tatsächlichen Werten, z. B. **AdUseClient** ist eine Konstante, deren Wert 3 ist. (Const AdUseClient = 3). Siehe auch *Enumeration*.  
  
 cursor  
 Ein Datenbankelement, das Datensatznavigation, aktualisierbarkeit der Daten und die Sichtbarkeit der Änderungen, die von anderen Benutzern in der Datenbank steuert.  
  
## <a name="d"></a>D  
 Datenbindung  
 Der Prozess der Zuordnung, die Objekte oder Steuerelemente von einer Anwendung mit einer Datenquelle. Ein Steuerelement einer Datenquelle zugeordnet wird aufgerufen, eine *vom datengebundenen Steuerelement*.  
  
 Der Inhalt eines datengebundenen Steuerelements werden Werte aus einer Datenbank zugeordnet. Z. B. ein Rastersteuerelement gebunden ist, die eine **Recordset** Objekt kann es sich aktualisiert, wenn die Zeilen in der **Recordset** werden aktualisiert. Neue Werte werden bei abgerufen, indem die **Recordset**, neue Werte werden im Raster angezeigt.  
  
 Datenanbieter  
 Software, die Daten in eine ADO-Anwendung verfügbar macht entweder direkt oder über einen Dienstanbieter. Siehe auch "Dienstanbieter".  
  
 Strukturieren von Daten  
 Eine Technik, die mit der eine formalisierte Syntax (aufgerufen **Form Sprache**) ein spezieller definieren **Recordset** Objekt (Namens eine *Recordset strukturiert*), enthält nicht nur Daten, sondern auch Verweise auf andere **Recordset** Objekten und/oder berechnete Werte basierend auf den anderen **Recordset** Objekte.  
  
 Datenebenen-Quelle  
 Eine logische Ebene eines verteilten Systems, das einen Computer mit einem DBMS, wie z. B. eine SQL Server-Datenbank darstellt. Siehe auch *Clientebene*, *mittleren Ebene*, *verteilte Anwendung*.  
  
 DCOM  
 Ein Wire-Protokoll, das COM-Komponenten in einem Netzwerk direkt miteinander kommunizieren kann. Siehe auch *COM*, *Komponente*.  
  
 DDL (Data Definition Language)  
 Diese Anweisungen in SQL, die nicht an, um zu bearbeiten, müssen Daten zu definieren. Das Schema einer Datenbank erstellt oder geändert werden, mit der DDL. Z. B. **CREATE TABLE**, **CREATE INDEX**, **GRANT**, und **widerrufen** SQL-DDL-Anweisungen sind.  
  
 Standarddatenstrom  
 Einen Text- oder Binärdaten-Datenstrom (dargestellt durch eine **Stream** Objekt) zugeordneten **Datensatz** oder **Recordset** Objekte bei bestimmten OLE DB-Anbieter, wie die Microsoft OLE DB-Anbieter für Internet Publishing. Der Standarddatenstrom enthält normalerweise den Inhalt einer Datei wie z. B. der HTML-Code für das Stammverzeichnis der Website.  
  
 verteilte Anwendung  
 Ein Programm geschrieben, sodass die Verarbeitung auf mehreren Computern über ein Netzwerk geteilt werden kann. In der Regel eine verteilte Anwendung wird in unterteilt Präsentation, Geschäftslogik und Daten Store Ebenen oder *Ebenen*. Siehe auch Client-Ebene, die mittlere Ebene und die Datenebene für die Quelle.  
  
 getrenntes Recordset  
 Ein **Recordset** Objekt im Cache des Clients, die über eine liveverbindung mit dem Server nicht mehr verfügt. Wenn die ursprüngliche Datenquelle für einige Grund – z. B. Aktualisieren von Daten, zugegriffen werden muss muss die Verbindung erneut hergestellt werden. Allerdings die Auflistungen, Eigenschaften und Methoden von einem nicht verbundenen **Recordset** kann weiterhin zugegriffen werden.  
  
 DML (Data Manipulation Language)  
 Diese Anweisungen in SQL, die nicht an, um zu definieren, Daten zu bearbeiten. Die Werte in einer Datenbank ausgewählt und mit DML geändert. Z. B. **einfügen**, **UPDATE**, **löschen**, und **wählen** SQL-DML-Anweisungen sind.  
  
 Ein Anbieter  
 Eine besondere Klasse von Anbietern, die Ordner und Dokumente zu verwalten. Wenn ein Dokument durch dargestellt wird ein **Datensatz** Objekt oder einen Ordner von Dokumenten wird dargestellt, durch eine **Recordset** Objekts, die ein Anbieter füllt diese Objekte mit einem eindeutigen Satz von Feldern, die Beschreiben Sie die Eigenschaften des Dokuments, anstatt das Dokument selbst. Siehe auch-Ressourceneintrag.  
  
 DSN (Data Source Name)  
 Die Auflistung der Informationen, mit denen Ihre Anwendung mit einer bestimmten ODBC-Datenbank verbinden. Der ODBC-Treiber-Manager verwendet diese Informationen, um eine Verbindung mit der Datenbank zu erstellen. Ein DSN kann in einer Datei (Datei-DSN) oder in der Windows-Registrierung (Computer-DSN) gespeichert werden.  
  
 dynamische Eigenschaft  
 Eine Eigenschaft, die spezifisch für einen Datenanbieter oder die Cursor-Dienst. Die **Eigenschaften** Auflistung eines Objekts wird automatisch mit diesen aufgefüllt ("dynamisch"). Ein Objekt hat keine dynamischen Eigenschaften, bis er mit einer Datenquelle über einen bestimmten Datenanbieter verbunden ist. Siehe auch Daten-Anbieter, den Cursor.  
  
## <a name="e"></a>E  
 Enumeration  
 Eine Liste benannter Konstanten. Aufgezählte Werte müssen nicht eindeutig sein. Jedoch muss der Name der einzelnen Werte innerhalb des Bereichs eindeutig sein, in dem die Enumeration definiert ist. In ADO Enumerationen werden verwendet, für numerische Parameter und Rückgabewerte, zum Hinzufügen von Bedeutungen zu ADO-Code und den Entwickler die numerischen Werte (die sich von Version zu Version ändern kann) zu schützen. Um beispielsweise eine statische öffnen **Recordset**, verwenden die **"adOpenStatic"** Enumerationswert: `Recordset.Open ,,adOpenStatic`  
  
 Auch bezeichnet als *Enumerationskonstante*. Siehe auch *Konstanten*.  
  
 Ereignis  
 Eine Aktion, die von einem Objekt, für die Sie Code aus, um Antworten schreiben können erkannt wird. Ereignisse können durch Ausführung des Befehls, Transaktionsabschlusses, Recordsetnavigation und Daten aktualisiert werden, unter anderem generiert werden. Siehe auch *Ereignishandler*.  
  
 Ereignishandler  
 Ein Ereignishandler ist der Code, der ausgeführt wird, wenn ein Ereignis auftritt. Siehe auch: Ereignis.  
  
## <a name="h"></a>H  
 Ereignishandler  
 Eine Routine, die eine häufige und relativ einfache Bedingung oder ein Vorgang wie die fehlerverwaltung Wiederherstellungs- oder verwaltet.  
  
 hierarchische Recordsets  
 Ein **Recordset** , enthält eine andere **Recordset**. Siehe auch Daten strukturieren, Kapitel.  
  
 Weitere Informationen finden Sie unter [den Zugriff auf Zeilen in einem hierarchischen Recordset](../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md).  
  
 Hierarchie (hierarchy)  
 Im Allgemeinen eine Hierarchie ist eine geordneten Struktur mit einer oberen Ebene und untergeordneten Ebenen. In ADO hierarchische **Recordsets** werden verwendet, um die über-/ unterordnungsbeziehung zwischen einem Datensatz und ein Kapitel darstellen. Auch in ADO **Datensatz** und **Stream** Objekte können verwendet werden, z. B. einen Ordner und Dokumente der hierarchischen Struktur auf. ADO MD enthält auch **Hierarchie** -Objekten zur Darstellung einer Beziehung zwischen den Ebenen einer Dimension in einem OLAP-Cube. Siehe auch hierarchische Recordsets, die über-/ unterordnungsbeziehung, die im Kapitel, die Struktur.  
  
## <a name="i-l"></a>I-L  
 ISAPI (Internet Server Application Programming Interface)  
 Ein Satz von Funktionen für Internetserver, z. B. eine Windows NT® Server/Windows 2000 Server, die Microsoft® Internet Information Services (IIS) ausgeführt werden soll.  
  
 Key  
 Eine Spalte oder Spalten in einer Tabelle, die eine Zeile eindeutig zu identifizieren; häufig verwendet, um eine Tabelle zu indizieren.  
  
## <a name="m"></a>M  
 Marshalling  
 Der Prozess der paketerstellung, senden und Entpackens Schnittstellenmethodenparameter Prozess oder Thread hinweg.  
  
 Mittlere Ebene  
 Die logische Ebene in einem verteilten System zwischen einer Benutzeroberfläche "oder" Webclient "und" der Datenbank. Dies ist in der Regel an, an dem Geschäftsobjekte instanziiert werden. Die mittlere Ebene ist eine Sammlung von Geschäftsregeln und Funktionen, die beim Abrufen von Daten ausgeführt werden. Sie erreichen dies anhand von Geschäftsregeln, die sich häufig ändern können und werden daher gekapselt, die in Komponenten, die von der Anwendungslogik selbst physisch getrennt sind. Auch bekannt als *Anwendungsserverebene*. Siehe auch verteilte Anwendung, die Clientebene, datenebenenanwendungs-Quelle.  
  
 MIME (Multi-Purpose Internet Mail Extension)  
 Ein Internetprotokoll entwickelt sich ursprünglich auf um Exchange von e-Mail-Nachrichten mit umfassenden Inhalten über heterogene Netzwerk-, Computer- und e-Mail-Umgebungen zu erlauben. In der Praxis wurde MIME auch übernommen und erweitert, indem nicht-e-Mail-Anwendungen.  
  
 MIME ist ein Standard, der binäre Daten zu veröffentlichen und Lesen Sie auf das Internet ermöglicht. Der Header einer Datei mit Binärdaten enthält den MIME-Typ der Daten. Dieser informiert Clientprogramme (-Web-Browser und e-Mail-Pakete, z. B.), müssen sie die Daten auf andere Weise zu behandeln, als einfachen Text. Beispielsweise enthält der Header eines Webdokuments eine JPEG-Grafik mit den MIME-Typ für das JPEG-Datei-Format. Dies ermöglicht einen Browser zum Anzeigen der Datei mit der JPEG-Viewer, wenn ein solcher vorhanden ist.  
  
## <a name="n-o"></a>N-O  
 Knoten  
 Ein Element in einer hierarchischen Baumstruktur. Ein Knoten kann der Stamm oder das untergeordnete Element eines anderen Knotens sein. Ein Knoten kann auch das übergeordnete Element des mehrere untergeordnete Elemente sein. Siehe auch "Hierarchie", "Struktur", "Root", "untergeordneten", "übergeordneten".  
  
 Objektvariable  
 Eine Variable, die einen Verweis auf ein Objekt enthält. Z. B. `objCustomObject` ist eine Variable, die auf ein Objekt des Typs Benutzerobjekt verweist:`Set objCustomObject = CreateObject(adodb.Recordset)`  
  
 ODBC (Open Database Connectivity)  
 Eine standardmäßige Sprache Programmierschnittstelle für die Verbindung mit einer Vielzahl von Datenquellen verwendet. Dies wird in der Regel über die Systemsteuerung, zugegriffen, in dem-Datenquellennamen (DSNs) zugewiesen werden kann, zu bestimmten ODBC-Treiber verwenden.  
  
 OLE DB  
 Ein Satz von Schnittstellen, die Daten aus einer Vielzahl von Quellen mithilfe von COM verfügbar machen. OLE DB-Schnittstellen bieten Anwendungen mit einheitlichen Zugriff auf Daten in verschiedenen Datenquellen. Diese Schnittstellen unterstützen die Menge der DBMS-Funktionen, die für die Datenquelle, sodass die Daten gemeinsam nutzen. Siehe auch COM.  
  
 eingeschränktes Sperren  
 Eine Art von Sperre in dem die Datenseite mit einem oder mehreren Datensätzen, inklusive dem Datensatz, der bearbeitet wird, nicht verfügbar ist, anderen Benutzern ist nur verwendet werden, während der Aktualisierung des Datensatzes durch die **Update** -Methode, jedoch steht vor und nach der aufrufen, um **Update**.  
  
 Optimistische Sperre verwendet wird bei der **Recordset** Objekt wird geöffnet, mit der **LockType** Parameter oder die Eigenschaft auf festgelegt **AdLockOptimistic** oder  **AdLockBatchOptimistic**. Siehe auch pessimistische Sperren.  
  
 Ordinalwert  
 Die numerische Position eines Elements innerhalb einer Bestellung. In einer ADO-Sammlung ist der Ordinalwert des ersten Elements 0 (null). Das nächste Element ist eins (1), und So weiter.  
  
## <a name="p"></a>P  
 parametrisierte Befehle  
 Eine Abfrage oder den Befehl, mit dem Sie Parameterwerte festlegen, bevor der Befehl ausgeführt wird. Z. B. eine SQL-Zeichenfolge durch Einbetten von parametermarkierungen in der SQL-Zeichenfolge parametrisiert werden kann (festgelegt durch die "?" Zeichen). Die Anwendung dann gibt Werte für jeden Parameter und führt den Befehl.  
  
 parent (parent)  
 Die steuernde Seite einer hierarchischen Beziehung. In einer hierarchischen Struktur hat ein übergeordnetes Element ein oder mehrere untergeordnete Knoten direkt darunter liegenden in der Hierarchie. Siehe auch Alias des übergeordneten Elements, die über-/ unterordnungsbeziehung, die untergeordnete.  
  
 übergeordnete-alias  
 Ein Alias, der auf das übergeordnete Element verweist. Siehe auch alias übergeordneten.  
  
 über-/ unterordnungsbeziehung  
 Eine Beziehung in einer hierarchischen Struktur, in der das übergeordnete Element eine Ebene höher und direkt mit einem oder mehreren untergeordneten verknüpft ist. Ein untergeordnetes Element ist eine Ebene unter, und es muss ein übergeordnetes Element aufweisen. Siehe auch übergeordnete, untergeordnete.  
  
 Pessimistische Sperrung  
 Eine Art von Sperre in dem die Seite enthält ein oder mehrere Datensätze, einschließlich des Datensatzes, der bearbeitet wird, ist nicht verfügbar ist, anderen Benutzern, um sicherzustellen, dass eine Aktualisierung vorgenommen werden. Pessimistische Sperren Verhalten wird vom OLE DB-Anbieter definiert. In der Regel Datensätze werden nach dem Bearbeiten gesperrt, und bleiben nicht verfügbar, bis die **Update** -Methode abgeschlossen wurde.  
  
 Pessimistische Sperrung ist aktiviert. wenn die **Recordset** Objekt wird geöffnet, mit der **LockType** Parameter oder die Eigenschaft auf festgelegt **AdLockPessimistic**. Finden Sie ebenfalls optimistische Sperren.  
  
 Verbindungspooling  
 Zur Optimierung der Leistung basierend auf Sammlungen von vorab zugeordneten Ressourcen, z. B. Objekte oder Datenbankverbindungen verwenden. Es ist sehr viel effizienter, eine vorhandene Ressource aus dem Pool als zum Erstellen einer neuen Ressource zu zeichnen.  
  
 ProgID (Programmbezeichner)  
 Ein eindeutiger Name, der die Windows-Registrierung einer COM-Anwendung zugeordnet ist. Die ProgID für eine ADO-Verbindung ist "ADODB. Verbindung". Siehe auch CLSID, COM.  
  
 Proxy  
 Ein Schnittstellenspezifische-Objekt, das Parameter-Marshalling bereitstellt, und die Kommunikation erforderlich, damit ein Client ein Anwendungsobjekt aufrufen, die in einer anderen ausführungsumgebung, z. B. in einem anderen Thread oder in einem anderen Prozess ausgeführt wird. Der Proxy befindet, mit dem Client und kommuniziert mit einem entsprechenden Stub, der sich auf das Anwendungsobjekt ist, die aufgerufen wird. Siehe auch Stub.  
  
## <a name="r"></a>R  
 relative URL.  
 Eine teilweise qualifizierte URL, der angibt, eine Ressource im Internet oder ein Intranet, deren Speicherort relativ zum Ausgangspunkt durch einen absoluten URL oder einen gleichwertigen Objekte von ADO-Verbindung angegeben ist. Gültig, die verketteten absolute und relative URLs bilden eine vollständige URL ein. Siehe auch URL und die absolute URL.  
  
 Remote-Datenquelle  
 Eine Datenquelle, die vorhanden ist, auf einen anderen Computer, und nicht auf dem lokalen System (, in dem die Clientanwendung ausgeführt wird).  
  
 -Ressourceneintrag  
 Ein Datensatz aus der ein Anbieter, der Felder für die Definition und die Beschreibung eines Ordners oder Dokuments enthält. Das Dokument selbst befindet sich nicht im Ressourcendatensatz jedoch in der Regel von der Standard-Stream oder ein Feld in den Ressourceneintrag, die mit einer URL zugegriffen werden kann. Siehe auch Quellanbieter "Dokument", "Standard-Stream, URL.  
  
 Rowset  
 Ein Satz von Zeilen aus einer Datenquelle, alle das gleiche Feldschema. Ein Rowset kann alle oder einige Felder aus einer Tabelle darstellen. Ein Rowset kann auch eine virtuelle Tabelle, die von einer Abfrage oder einen von zwei oder mehr Tabellen Join erstellt darstellen. In ADO Rowsets dargestellt werden, indem **Recordset** Objekte.  
  
## <a name="s"></a>S  
 Bereich  
 Der Bereich des Verweises für ein Objekt oder eine Variable oder einen Bereich von Datensätzen in einer Sicht oder Tabelle. Lokale Variablen können beispielsweise nur innerhalb der Prozedur verwiesen werden in denen sie definiert wurden. Öffentliche Variablen, die von überall in der Anwendung zugegriffen werden. Objekte, z. B. der aktuellen Datenbank befinden sich im Gültigkeitsbereich, wenn sie in den Suchpfad für definiert sind. Datensatzbereiche können mit einer Bereichsklausel, in vielen Befehlen angegeben werden.  
  
 Dienstanbieter  
 Software, die einen Dienst kapselt, durch das erzeugen und Nutzen von Daten, die Funktionen in den ADO-Anwendungen zu erweitern. Es ist ein Anbieter, der nicht direkt Daten verfügbar macht, anstatt einen Dienst, z. B. die abfrageverarbeitung bietet. Der Dienstanbieter kann von einem Datenanbieter bereitgestellte Daten verarbeiten. Siehe auch "Datenanbieter".  
  
 geformten Recordset  
 Ein **Recordset** , deren Spalten wurden speziell enthalten nicht nur Daten, sondern auch Verweise (Kapitel bezeichnet) auf andere definiert **Recordset** Objekten und/oder berechnete Werte basierend auf anderen **Recordset** Objekte.  
  
 Gleichgeordnet  
 Alle zwei oder mehr Knoten in einer hierarchischen Struktur, die auf der gleichen Ebene in der Hierarchie sind. Der Stammknoten in einer Hierarchie werden keine Elemente verfügt.  
  
 )  
 Eine vorkompilierte Auflistung von Code, z. B. SQL-Anweisungen und optionalen Control-of-Flow-Anweisungen, die unter einem Namen gespeichert und als Einheit verarbeitet werden soll. Gespeicherte Prozeduren werden in einer Datenbank gespeichert. Sie können mit einem Aufruf in eine Anwendung ausgeführt werden, und es ermöglichen, User-deklarierten Variablen, bedingte Ausführung und andere leistungsstarke Features für die Programmierung.  
  
 Stub  
 Ein Schnittstellenspezifische-Objekt, das Parameter-Marshalling bereitstellt, und die Kommunikation, die erforderlich sind, für ein Anwendungsobjekt, die Aufrufe von einem Client zu empfangen, die in einer anderen ausführungsumgebung, z. B. in einem anderen Thread oder in einem anderen Prozess ausgeführt wird. Der Stub befindet wie das Anwendungsobjekt und kommuniziert mit einem entsprechenden Proxy aus, der mit dem Client befindet, die ihn aufruft. Siehe auch "Proxy".  
  
 untergeordnete Knoten  
 Finden Sie unter untergeordneten.  
  
 synchrone Vorgänge  
 Ein Vorgang initiiert von Code, der abgeschlossen ist, bevor der nächste Vorgang gestartet werden kann. Siehe auch: asynchronen Vorgang.  
  
## <a name="t-z"></a>T-Z  
 trEE  
 Eine Struktur, die eine hierarchische Beziehung zwischen Elementen (Knoten) darstellt. Es ist ein Knoten auf der obersten Ebene einer Struktur (Stamm). Unter dem Stamm kann mehrere untergeordnete Elemente vorhanden sein. Jedes untergeordnete Element kann wiederum das übergeordnete Element des anderen untergeordneten Knoten, Verzweigen wie eine Struktur sein. Ein Ordner mit Dokumenten und weiteren Ordner ist ein typisches Beispiel einer Baumstruktur an. Siehe auch "Hierarchie", "Knoten", "Stamm", "untergeordneten", "übergeordneten".  
  
 Webserver  
 Ein Computer, der Webdienste und Seiten für Intranet- und Internet-Benutzer bietet.
