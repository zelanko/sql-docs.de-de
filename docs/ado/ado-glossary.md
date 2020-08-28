---
description: ADO-Glossar Begriffe
title: Begriffe zu ADO-Glossar | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, glossary
ms.assetid: b0478836-4123-4357-969a-c5784fc28be5
author: rothja
ms.author: jroth
ms.openlocfilehash: dd781612557faebd4b6eefb710ffad2379928aee
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980851"
---
# <a name="ado-glossary-terms"></a>ADO-Glossar Begriffe
In diesem Thema werden die für ADO relevanten Begriffe definiert.

## <a name="a"></a>Ein
 absolute URL eine voll qualifizierte URL, die den Speicherort einer Ressource angibt, die sich im Internet oder in einem Intranet befindet. Siehe auch *URL* und *relative URL*.

 ActiveX-Steuerelement Selbstregistrierung, Prozess interne COM-Komponente, die häufig über ein visuelles Element verfügt, entweder zur Entwurfs-und zur Laufzeit. ActiveX-Steuerelemente können auch mit einem aktiven Dokument Container (z. b. Microsoft Internet Explorer) kommunizieren.

 ADISAPI (Advanced Data Internet Server Application Programming Interface) eine ISAPI-DLL, die Analyse, Automatisierungssteuerung, Recordsetmarshalling und MIME-Verpackung bereitstellt. Die ADISAPI-Komponente funktioniert über die von Internetinformationsdienste (IIS) bereitgestellte API. Siehe auch *ISAPI*.

 Aggregatfunktion in einer Abfrage, eine Funktion wie count, AVG oder StDev, die einen Wert mit allen Zeilen in einer Spalte einer Tabelle berechnet. Beim Schreiben von Ausdrücken und in der Programmierung können Sie SQL-Aggregatfunktionen (einschließlich der drei oben aufgeführten) und Domänen Aggregatfunktionen verwenden, um verschiedene Statistiken zu bestimmen.

 Alias ein alternativer Name, den Sie an eine Spalte oder einen Ausdruck in einer SQL-SELECT-Anweisung übergeben, oft kürzer oder sinnvoller. Beispielsweise ist "bobsales" der Alias in der folgenden SELECT-Anweisung: "Select WR-Sales as bobsales from salesdb". Ein Alias kann verwendet werden, um dynamisch Spalten zum Steuern von Bindungen im DataControl-Objekt zuzuweisen.

 Apartment Threading ein COM-Threading Modell, in dem alle Aufrufe an ein Objekt in einem Thread erfolgen. In Apartment Threading synchronisiert und Marshalls com Aufrufe. Siehe auch *commddefcom*.

 asynchroner Vorgang ein Vorgang, der die Steuerung an das aufrufende Programm zurückgibt, ohne auf den Abschluss des Vorgangs zu warten. Bevor der Vorgang beendet ist, wird die Codeausführung fortgesetzt. Siehe auch *synchronen Vorgang*.

## <a name="b"></a>B
 Bindungs Eintrag eine Zuordnung zwischen einem Feld in einer Tabelle und einer Variablen. In den ADO-Visual C++ Erweiterungen werden **Recordsetfelder** C/C++-Variablen zugeordnet.

 Bitmaske ein numerischer Wert, der für einen bitweisen Wert Vergleich mit anderen numerischen Werten gedacht ist, in der Regel Optionen in Parameter-oder Rückgabe Werten. In der Regel erfolgt dieser Vergleich mit bitweisen logischen Operatoren, wie z. b. **and** und **or** in Visual Basic **&** und **&#124;** in C++.

 Beispielsweise können die ADO **FieldAttributeEnum** -Werte als Bitmasken verwendet werden, um die Attribute eines Felds zu bestimmen. Angenommen, Sie möchten ermitteln, ob ein Feld aktualisierbar ist. Dies können Sie mit dem folgenden Ausdruck in Visual Basic testen:`Field.Attributes AND adFldUpdatable`

 Wenn das Ergebnis true ist, ist das Feld aktualisierbar.

 Lesezeichen eines Markers, mit dem eine Zeile innerhalb einer Gruppe von Zeilen eindeutig identifiziert wird, damit ein Benutzer schnell dorthin navigieren kann.

 Geschäftsobjekt ein Objekt, das einen definierten Satz von Vorgängen ausführt, z. b. Datenvalidierung oder Geschäftsregel Logik. Geschäftsobjekte befinden sich normalerweise auf der mittleren Ebene.

 Geschäftsregel: die Kombination von Validierungs bearbeitvorgängen, Anmelde Überprüfungen, Daten Bank Suchvorgängen, Richtlinien und algorithmischen Transformationen, die die Geschäftstätigkeit eines Unternehmens darstellen. Wird auch als *Geschäftslogik*bezeichnet.

## <a name="c"></a>C
 Berechneter Ausdruck ein Ausdruck, der nicht konstant ist, aber dessen Wert von anderen Werten abhängt. Um ausgewertet zu werden, muss ein berechneter Ausdruck Werte aus anderen Quellen abrufen und berechnen, normalerweise in anderen Feldern oder Zeilen.

 Kapitel ein Verweis auf einen Bereich von Zeilen aus einer Datenquelle. In ADO ist ein Kapitel in der Regel ein Verweis auf ein anderes **Recordset**.

 Mit Kapitel Spalten können Sie eine Beziehung zwischen über *geordneten* und untergeordneten Elementen definieren, wobei das übergeordnete Element das **Recordset** ist, das die Kapitel-Spalte enthält, *und das unter* *geordnete* Element das **Recordset** , das durch das Kapitel

 Chapter-Alias ein Alias, der auf die Spalte verweist, die an das übergeordnete Element angehängt ist.

 Zeichensatz: eine Zuordnung eines Satzes von Zeichen zu den numerischen Werten. Beispielsweise ist Unicode ein 16-Bit-Zeichensatz, der alle bekannten Zeichen codieren und als weltweiten Zeichen Codierungsstandard verwendet werden kann.

 untergeordnetes Element der abhängigen Seite einer hierarchischen Beziehung. Ein untergeordnetes Element ist ein Knoten in einer hierarchischen Struktur, der über einen anderen übergeordneten Knoten verfügt (näher an der Wurzel). Siehe auch untergeordneter *Alias*, über-/Unterordnungsbeziehung, über *geordnetes*Element. *parent-child relationship*

 untergeordneter Alias ein Alias, der auf das untergeordnete Element verweist. Siehe auch *Alias*, *unter*geordnet.

 CLSID (Klassen Bezeichner) ein universell eindeutiger Bezeichner (UUID), der eine COM-Komponente identifiziert. Jede COM-Komponente verfügt über Ihre CLSID in der Windows-Registrierung, sodass Sie von anderen Anwendungen geladen werden kann. Siehe auch *ProgID*, *com*.

 Client Ebene eine logische Ebene eines verteilten Systems, das in der Regel Daten für den Benutzer darstellt und verarbeitet, manchmal auch als Front- *End*bezeichnet. In der Regel fordert die Client Ebene Daten von einem Server basierend auf der Eingabe an und formatiert und zeigt dann das Ergebnis an. Siehe auch *mittlere Ebene*, *Datenquellen Ebene*, *verteilte Anwendung*.

 COM (Component Object Model) ein binärer Standard, der es Objekten ermöglicht, in einer vernetzten Umgebung unabhängig von der Sprache, in der Sie entwickelt wurden, oder auf den Computern, in denen Sie sich befinden, zusammenzuarbeiten. Zu den COM-basierten Technologien zählen ActiveX-Steuerelemente, Automation und Object Linking and Embedding (OLE). COM ermöglicht einem Objekt, seine Funktionalität für andere Komponenten und für das Hosten von Anwendungen verfügbar zu machen. Es definiert sowohl, wie das Objekt sich selbst verfügbar macht, als auch, wie diese Offenlegung zwischen Prozessen und Netzwerk übergreifend funktioniert. COM definiert auch den Lebenszyklus des Objekts.

 Binärdatei für COM-Komponenten, z. b. dll-Dateien, OCX-Dateien und einige exe-Dateien, die den com-Standard für die Bereitstellung von Objekten unterstützt. Eine solche Datei enthält Code für eine oder mehrere Klassenfactorys, com-Klassen, Registrierungs Eintrags Mechanismen, das Laden von Code usw.

 Vergleichs Operator ein Operator, der zwei Ausdrücke vergleicht und einen booleschen Wert zurückgibt.

 Ein Kriterienparameter, der als ">" (größer als), " \<" (less than), "=" (equal), "> =" (größer als oder gleich), "<=" (kleiner als oder gleich), "<>" (nicht gleich) oder "like" (Muster Vergleich) ausgedrückt werden kann.

 Komponente ein Objekt, das Daten und Code kapselt und einen gut angegebenen Satz öffentlich verfügbarer Dienste bereitstellt.

 Verbund Datei eine Implementierung von com-strukturiertem Speicher für Dateien. In einer Verbund Datei werden separate Objekte in einer einzelnen, strukturierten Datei gespeichert, die aus zwei Hauptelementen besteht: Speicher Objekte und Streamobjekte. In der gleichen Weise funktionieren Sie wie ein Dateisystem in einer Datei.

 Eine Reihe von einzelnen Dateien, die in einer physischen Datei miteinander verbunden sind. Auf jede einzelne Datei in einer Verbund Datei kann genauso zugegriffen werden, als ob es sich um eine einzelne physische Datei handelt.

 Konstante ein numerischer Wert oder ein Zeichen folgen Wert, der nicht geändert wird. Benannte ADO-Enumerationen (Enumerationskonstanten) können in Ihrem Code anstelle von tatsächlichen Werten verwendet werden. **adUseClient** ist z. b. eine Konstante, deren Wert 3 ist. (Konstant adUseClient = 3). Siehe auch *Enumeration*.

 Cursor ein Daten Bank Element, das die Daten Satz Navigation, die Aktualisierbarkeit von Daten und die Sichtbarkeit von Änderungen, die von anderen Benutzern an der Datenbank vorgenommen wurden, steuert.

## <a name="d"></a>D
 Datenbindung der Prozess der Zuordnung der Objekte oder Steuerelemente einer Anwendung zu einer Datenquelle. Ein Steuerelement, das einer Datenquelle zugeordnet ist, wird als *Daten gebundenes Steuer*Element bezeichnet.

 Der Inhalt eines Daten gebundenen Steuer Elements ist den Werten aus einer Datenbank zugeordnet. Beispielsweise kann ein Raster Steuerelement, das an ein **Recordset** -Objekt gebunden ist, aktualisiert werden, wenn die Zeilen im **Recordset** aktualisiert werden. Wenn neue Werte durch das **Recordset**abgerufen werden, werden im Raster neue Werte angezeigt.

 Datenanbieter Software, die Daten entweder direkt oder über einen Dienstanbieter für eine ADO-Anwendung verfügbar macht. Siehe auch Dienstanbieter.

 Daten, die eine Technik verwenden, die eine formalisierte Syntax (sogenannte **Shape-Sprache**) verwendet, um ein spezielles **Recordset** -Objekt (als *geformtes Recordset*bezeichnet) zu definieren, das nicht nur Daten enthält, sondern auch Verweise auf andere **Recordsetobjekte** und/oder berechnete Werte basierend auf diesen anderen **Recordset** -Objekten.

 Datenquellen Ebene eine logische Ebene eines verteilten Systems, die einen Computer darstellt, auf dem ein DBMS ausgeführt wird, z. b. eine SQL Server Datenbank. Siehe auch *Client Ebene*, *mittlere Ebene*, *verteilte Anwendung*.

 DCOM ein Wire-Protokoll, das COM-Komponenten die direkte Kommunikation über ein Netzwerk ermöglicht. Siehe auch *com*, *Komponente*.

 DDL (Data Definition Language, Datendefinitionssprache) diese Anweisungen in SQL, die im Gegensatz zur Bearbeitung von Daten definieren. Das Schema einer Datenbank wird mit DDL erstellt oder geändert. **CREATE TABLE**, **Create Index**, **Grant**und **revosind z** . b. SQL-DDL-Anweisungen.

 Standardmäßig streamen Sie einen Text-oder Binärdaten Strom (dargestellt durch ein **Streamobjekt** ), der **Daten Satz** -oder recordsetobjekten zugeordnet ist, wenn bestimmte OLE DB Anbieter verwendet werden, z. b. der Microsoft OLE DB-Anbieter für die Internet **Recordset** Der Standarddaten Strom enthält normalerweise den Inhalt einer Datei, z. b. den HTML-Code für den Stamm einer Website.

 verteilte Anwendung: ein Programm, das so geschrieben ist, dass die Verarbeitung über ein Netzwerk auf mehrere Computer aufgeteilt werden kann. Eine verteilte Anwendung ist in der Regel in Präsentations-, Geschäftslogik-und Daten *Speicherebenen unterteilt.* Siehe auch Client Ebene, mittlere Ebene, Datenquellen Ebene.

 getrennte Recordsets ein **Recordset** -Objekt in einem Client Cache, das keine Live Verbindung mit dem Server mehr aufweist. Wenn die ursprüngliche Datenquelle aus irgendeinem Grund erneut aufgerufen werden muss, z. b. beim Aktualisieren von Daten, muss die Verbindung wieder hergestellt werden. Auf die Auflistungen, Eigenschaften und Methoden eines getrennten **Recordsets** kann jedoch weiterhin zugegriffen werden.

 DML (Daten Bearbeitungs Sprache) diese Anweisungen in SQL, die im Gegensatz zum Definieren von Daten bearbeitet werden. Die Werte in einer Datenbank werden mit DML ausgewählt und geändert. **Insert**, **Update**, **Delete**und **Select** sind z. b. SQL DML-Anweisungen.

 Dokument Quellen Anbieter eine spezielle Klasse von Anbietern, die Ordner und Dokumente verwalten. Wenn ein Dokument durch ein **Datensatz** -Objekt dargestellt wird oder ein Ordner mit Dokumenten durch ein **Recordset** -Objekt dargestellt wird, füllt der Dokument Quellen Anbieter diese Objekte mit einem eindeutigen Satz von Feldern auf, die die Merkmale des Dokuments beschreiben, anstelle des eigentlichen Dokuments. Siehe auch Ressourcen Daten Satz.

 DSN (Datenquellen Name) die Sammlung von Informationen, die zum Verbinden Ihrer Anwendung mit einer bestimmten ODBC-Datenbank verwendet werden. Der ODBC-Treiber-Manager verwendet diese Informationen, um eine Verbindung mit der-Datenbank herzustellen. Ein DSN kann in einer Datei (einem Datei-DSN) oder in der Windows-Registrierung (einem Computer-DSN) gespeichert werden.

 dynamische Eigenschaft eine Eigenschaft, die für einen Datenanbieter oder den Cursor Dienst spezifisch ist. Die **Properties** -Auflistung eines Objekts wird automatisch (dynamisch) aufgefüllt. Ein-Objekt besitzt keine dynamischen Eigenschaften, bis es über einen bestimmten Datenanbieter mit einer Datenquelle verbunden ist. Siehe auch Datenanbieter, Cursor.

## <a name="e"></a>E
 Enumeration eine Liste benannter Konstanten. Enumerationswerte müssen nicht eindeutig sein. Allerdings muss der Name jedes Werts innerhalb des Bereichs, in dem die Enumeration definiert ist, eindeutig sein. In ADO werden Enumerationen für numerische Parameter und Rückgabewerte verwendet, um die Bedeutung von ADO-Code hinzuzufügen und um den Entwickler vor den numerischen Werten zu schützen (die sich von Version zu Version ändern können). Verwenden Sie z. b. den Enumerationswert " **adOpenStatic** ", um ein statisches **Recordset**zu öffnen:`Recordset.Open ,,adOpenStatic`

 Wird auch als *Enumerationskonstante*bezeichnet. Siehe auch *Konstante*.

 Ereignis eine Aktion, die von einem-Objekt erkannt wird, für das Sie Code schreiben können, der antwortet. Ereignisse können unter anderem durch Befehlsausführung, Transaktions Vervollständigung, Recordsetnavigation und Datenaktualisierungen generiert werden. Siehe auch *Ereignishandler*.

 Ereignishandler ein Ereignishandler ist der Code, der ausgeführt wird, wenn ein Ereignis auftritt. Siehe auch Ereignis.

## <a name="h"></a>H
 Handler eine Routine, die eine gängige und relativ einfache Bedingung oder Operation verwaltet, z. b. Fehlerwiederherstellung oder Datenverwaltung.

 Hierarchisches Recordset ein **Recordset** , das ein anderes **Recordset**enthält. Weitere Informationen finden Sie unter Daten Strukturierung (Kapitel).

 Weitere Informationen finden Sie unter [zugreifen auf Zeilen in einem hierarchischen Recordset](./guide/data/accessing-rows-in-a-hierarchical-recordset.md).

 Hierarchie im Allgemeinen ist eine Hierarchie eine Rangstruktur mit einer obersten Ebene und untergeordneten Ebenen. In ADO werden hierarchische **Recordsets** verwendet, um die über-/Unterordnungsbeziehung zwischen einem Datensatz und einem Kapitel darzustellen. In ADO können auch **Datensatz** -und **Stream** -Objekte verwendet werden, um auf hierarchische Struktur Strukturen wie z. b. einen Ordner und Dokumente zuzugreifen. ADO MD umfasst auch **Hierarchy** -Objekte, die eine Beziehung zwischen den Ebenen einer Dimension in einem OLAP-Cube darstellen. Siehe auch hierarchische Recordsets, über-/Unterordnungsbeziehung, Chapter, Tree.

## <a name="i-l"></a>I-L
 ISAPI (Internet Server Application Programming Interface) eine Reihe von Funktionen für Internet Server, z. b. ein Windows NT &reg; -Server/Windows 2000-Server, auf dem Microsoft &reg; Internetinformationsdienste (IIS) ausgeführt wird.

 Schlüssel eine Spalte oder Spalten in einer Tabelle, die eine Zeile eindeutig identifizieren; wird häufig verwendet, um eine Tabelle zu indizieren.

## <a name="m"></a>M
 Marshalling des Prozesses zum Verpacken, senden und entpacken von Schnittstellen Methoden Parametern über Thread-oder Prozess Grenzen hinweg.

 mittlere Ebene die logische Ebene in einem verteilten System zwischen einer Benutzeroberfläche oder einem Webclient und der Datenbank. In der Regel werden Geschäftsobjekte instanziiert. Die mittlere Ebene ist eine Auflistung von Geschäftsregeln und-Funktionen, die nach dem Empfang von Informationen generieren und verarbeiten. Dies erreichen Sie mithilfe von Geschäftsregeln, die sich häufig ändern können und daher in Komponenten gekapselt werden, die physisch von der Anwendungslogik getrennt sind. Wird auch als *Anwendungsserver Ebene*bezeichnet. Siehe auch verteilte Anwendung, Client Ebene, Datenquellen Ebene.

 MIME (Mehrzweck-Internet Mail Erweiterung) ein Internetprotokoll, das ursprünglich für den Austausch von elektronischen e-Mail-Nachrichten mit umfangreichen Inhalten in heterogenen Netzwerk-, Computer-und e-Mail-Umgebungen entwickelt In der Praxis wurde MIME auch von nicht-e-Mail-Anwendungen übernommen und erweitert.

 MIME ist ein Standard, der das Veröffentlichen und Lesen von Binärdaten im Internet ermöglicht. Der Header einer Datei mit Binärdaten enthält den MIME-Typ der Daten. Dadurch werden Client Programme (z.b. Webbrowser und e-Mail-Pakete) darüber informiert, dass Sie die Daten auf eine andere Weise verarbeiten müssen, als Sie gerade Text verarbeiten. Beispielsweise enthält der-Header eines Webdokuments, das eine JPEG-Grafik enthält, den MIME-Typ, der für das JPEG-Dateiformat spezifisch ist. Dadurch kann ein Browser die Datei mit dem zugehörigen JPEG-Viewer anzeigen, sofern vorhanden.

## <a name="n-o"></a>N-O
 Knoten ein Element in einer hierarchischen Baumstruktur. Ein Knoten kann der Stamm oder das untergeordnete Element eines anderen Knotens sein. Ein Knoten kann auch das übergeordnete Element mehrerer untergeordneter Elemente sein. Siehe auch Hierarchy, Tree, root, Child, Parent.

 Objekt Variable eine Variable, die einen Verweis auf ein Objekt enthält. Beispielsweise `objCustomObject` ist eine Variable, die auf ein Objekt vom Typ customobject zeigt:`Set objCustomObject = CreateObject(adodb.Recordset)`

 ODBC (Open Database Connectivity) eine Schnittstelle für die Programmiersprache Standard, die zum Herstellen einer Verbindung mit einer Vielzahl von Datenquellen verwendet wird. Dies erfolgt in der Regel über die Systemsteuerung, in der Datenquellen Namen (DSNs) zugewiesen werden können, um bestimmte ODBC-Treiber zu verwenden.

 OLE DB einen Satz von Schnittstellen, die Daten aus einer Vielzahl von Quellen mithilfe von com verfügbar machen. OLE DB-Schnittstellen bieten Anwendungen einheitlichen Zugriff auf Daten, die in verschiedenen Informationsquellen gespeichert sind. Diese Schnittstellen unterstützen die Menge der DBMS-Funktionalität, die für die Datenquelle geeignet ist, sodass Sie Ihre Daten gemeinsam nutzen können. Siehe auch com.

 vollständiges Sperren eines Sperrtyps, bei dem die Datenseite mit einem oder mehreren Datensätzen, einschließlich des zu bearbeitenden Datensatzes, für andere Benutzer nicht verfügbar ist, während der Datensatz von der **Update** -Methode aktualisiert wird, aber vor und nach dem **Update Update**verfügbar ist.

 Die optimistische Sperre wird verwendet, wenn das **Recordset** -Objekt geöffnet wird, wobei der **LockType** -Parameter oder die-Eigenschaft auf **adlockoptimioder** **adlockbatchoptimifest**gelegt ist. Siehe auch Pessimistisches Sperren.

 Ordinalwert die numerische Position eines Elements in einer Bestellung. In einer ADO-Auflistung ist der Ordinalwert des ersten Elements NULL (0). Das nächste Element ist eins (1) usw.

## <a name="p"></a>P
 parametrisierter Befehl: eine Abfrage oder ein Befehl, mit dem Sie Parameterwerte festlegen können, bevor der Befehl ausgeführt wird. Beispielsweise kann eine SQL-Zeichenfolge parametrisiert werden, indem Parameter Markierungen in der SQL-Zeichenfolge eingebettet werden (durch das Zeichen "?" gekennzeichnet). Die Anwendung gibt dann Werte für jeden Parameter an und führt den Befehl aus.

 übergeordnetes Element der Steuerungs Seite einer hierarchischen Beziehung. In einer hierarchischen Struktur hat ein übergeordnetes Element mindestens einen untergeordneten Knoten in der Hierarchie direkt darunter. Siehe auch übergeordnete-Alias-, über-/Unterordnungsbeziehung, untergeordnet.

 Parent-Alias ein Alias, der auf das übergeordnete Element verweist. Siehe auch Alias, übergeordnetes Element.

 über-/Unterordnungsbeziehung eine Beziehung in einer hierarchischen Struktur, in der das übergeordnete Element eine Ebene höher und direkt mit einem oder mehreren untergeordneten Elementen verknüpft ist. Ein untergeordnetes Element ist eine Ebene niedriger und muss über ein übergeordnetes Element verfügen. Siehe auch übergeordnete, untergeordnete Elemente.

 Pessimistisches Sperren eines Sperrtyps, bei dem die Seite, die einen oder mehrere Datensätze enthält, einschließlich des Datensatzes, der bearbeitet wird, für andere Benutzer nicht verfügbar ist, um sicherzustellen, dass ein Update durchgeführt wird. Das pessimistische Sperr Verhalten wird vom OLE DB-Anbieter definiert. In der Regel werden Datensätze bei der Bearbeitung gesperrt und bleiben solange nicht verfügbar, bis die **Update** -Methode abgeschlossen ist.

 Die pessimistische Sperrung wird aktiviert, wenn das **Recordset** -Objekt geöffnet wird, wenn der **LockType** -Parameter oder die Eigenschaft auf **adlockpessimifest**gelegt ist. Siehe auch optimistische Sperren.

 Pooling einer Leistungsoptimierung basierend auf der Verwendung von Sammlungen vorab zugeordneter Ressourcen, z. b. von Objekten oder Datenbankverbindungen. Es ist effizienter, eine vorhandene Ressource aus dem Pool zu zeichnen, als eine neue Ressource zu erstellen.

 ProgID (programmgesteuerte Kennung) ein eindeutiger Name, der der Windows-Registrierung durch eine COM-Anwendung zugeordnet ist. Die ProgID für eine ADO-Verbindung ist "ADODB. Verbindung ". Siehe auch CLSID, com.

 Proxy ein Schnittstellen spezifisches Objekt, das den Parametermarshalling und die Kommunikation bereitstellt, die ein Client zum Aufrufen eines Anwendungs Objekts benötigt, das in einer anderen Ausführungsumgebung ausgeführt wird, z. b. in einem anderen Thread oder in einem anderen Prozess. Der Proxy befindet sich beim Client und kommuniziert mit einem entsprechenden Stub, der sich mit dem aufgerufenen Anwendungs Objekt befindet. Siehe auch Stub.

## <a name="r"></a>R
 relative URL eine teilweise qualifizierte URL, die eine Ressource im Internet oder ein Intranet angibt, dessen Standort relativ zu einem Startpunkt ist, der durch ein absolute URL oder ein entsprechendes ADO-Verbindungs Objekt angegeben wird. In der Tat werden die verketteten absoluten und relativen URLs eine komplette URL. Siehe auch URL und absolute URL.

 Remote Datenquelle: eine Datenquelle, die auf einem anderen Computer vorhanden ist, und nicht auf dem lokalen System (auf dem die Client Anwendung ausgeführt wird).

 Ressource zeichnet einen Datensatz von einem Dokument Quellen Anbieter auf, der Felder für die Definition und Beschreibung eines Ordners oder Dokuments enthält. Das Dokument selbst ist nicht im Ressourcen Daten Satz enthalten, aber in der Regel kann der Standarddaten Strom oder ein Feld im Ressourcen Daten Satz mit einer URL darauf zugreifen. Siehe auch Dokument Quellen Anbieter, Standardstream, URL.

 Rowset eine Reihe von Zeilen aus einer Datenquelle, die alle über das gleiche Feld Schema verfügen. Ein Rowset kann alle oder einige Felder aus einer Tabelle darstellen. Ein Rowset kann auch eine virtuelle Tabelle darstellen, die durch eine Abfrage oder einen Join von mindestens zwei Tabellen erstellt wird. In ADO werden Rowsets durch **Recordset** -Objekte dargestellt.

## <a name="s"></a>E
 Bereich der Verweis Bereich für ein Objekt oder eine Variable oder einen Bereich von Datensätzen in einer Sicht oder Tabelle. Beispielsweise kann auf lokale Variablen nur innerhalb der Prozedur verwiesen werden, in der Sie definiert wurden. Auf öffentliche Variablen kann von überall in der Anwendung aus zugegriffen werden. -Objekte, z. b. die aktuelle Datenbank, befinden sich im Gültigkeitsbereich, wenn Sie sich im definierten Suchpfad befinden. Daten Satz Bereiche können in vielen Befehlen mit einer Scope-Klausel angegeben werden.

 Dienstanbieter Software, die einen Dienst kapselt, indem Daten erstellt und genutzt werden, wodurch Features in Ihren ADO-Anwendungen erweitert werden. Es ist ein Anbieter, der keine Daten direkt verfügbar macht, sondern einen Dienst bereitstellt, z. b. die Verarbeitung von Abfragen. Der Dienstanbieter kann Daten verarbeiten, die von einem Datenanbieter bereitgestellt werden. Siehe auch Datenanbieter.

 geformtes Recordset: ein **Recordset** , dessen Spalten speziell so definiert wurden, dass es nicht nur Daten enthält, sondern auch auf andere **Recordsetobjekte** und/oder berechnete Werte basierend auf anderen **Recordset** -Objekten verweist.

 gleich geordnetes Element mit zwei oder mehr Knoten in einer hierarchischen Struktur, die sich auf derselben Ebene in der Hierarchie befinden. Der Stamm Knoten in einer Hierarchie hat keine gleich geordneten Elemente.

 gespeicherte Prozedur eine vorkompilierte Auflistung von Code, wie z. b. SQL-Anweisungen und optionale Ablauf Steuerungs Anweisungen, die unter einem Namen gespeichert und als Einheit verarbeitet werden. Gespeicherte Prozeduren werden in einer Datenbank gespeichert. Sie können mit einem-Befehl von einer Anwendung ausgeführt werden und Benutzer deklarierte Variablen, bedingte Ausführung und andere leistungsstarke Programmierfunktionen zulassen.

 Stub ein Schnittstellen spezifisches Objekt, das den Parameter Marshalling und die Kommunikation bereitstellt, die für ein Anwendungs Objekt erforderlich sind, um Aufrufe von einem Client zu empfangen, der in einer anderen Ausführungsumgebung ausgeführt wird, z. b. in einem anderen Thread oder in einem anderen Prozess. Der Stub befindet sich mit dem Anwendungs Objekt und kommuniziert mit einem entsprechenden Proxy, der sich auf dem Client befindet, der ihn aufruft. Siehe auch Proxy.

 untergeordneter Knoten siehe Child.

 synchroner Vorgang ein Vorgang, der von Code initiiert wird, der vor dem nächsten Vorgang abgeschlossen wird. Siehe auch asynchroner Vorgang.

## <a name="t-z"></a>T-Z
 Struktur eine Struktur, die eine hierarchische Beziehung zwischen Elementen (Knoten) darstellt. Es ist ein Knoten auf der obersten Ebene einer Struktur (der Stamm) vorhanden. Unterhalb des Stamms können mehrere untergeordnete Elemente vorhanden sein. Jedes untergeordnete Element kann wiederum das übergeordnete Element anderer untergeordneter Elemente sein und somit wie eine Struktur verzweigen. Ein Ordner, der Dokumente und andere Ordner enthält, ist ein typisches Beispiel für eine Baumstruktur. Siehe auch Hierarchie, Knoten, root, Child, Parent.

 Webserver: ein Computer, der Webdienste und Seiten für Intranet-und Internet Benutzer bereitstellt.