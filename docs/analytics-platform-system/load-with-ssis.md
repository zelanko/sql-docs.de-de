---
title: Laden mit Integration Services
description: Bietet Referenz-und Bereitstellungs Informationen zum Laden von Daten in parallele Data Warehouse (PDW) mithilfe von SQL Server Integration Services-Paketen (SSIS).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: b0bcb5cfe1ec4111aaea7153f35bca084df62b76
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401014"
---
# <a name="load-data-with-integration-services-to-parallel-data-warehouse"></a>Laden von Daten mit Integration Services in parallele Data Warehouse
Bietet Referenz-und Bereitstellungs Informationen zum Laden von Daten in SQL Server parallele Data Warehouse mithilfe von SQL Server Integration Services-Paketen (SSIS).  
  
<!-- MISSING LINKS

## <a name="BeforeBegin"></a>Before You Begin  
Before you can start loading data, use the following topics to install the Integration Services Destination Adapters and to create an Integration Services package that connects SQL Server PDW:  


-   [Install Integration Services destination adapters](install-integration-services-destination-adapters.md)  
  
-   [Connect With Integration Services for loading](connect-with-ssis-for-loading.md)  
  
For general information about developing Integration Services packages, see [Designing and Implementing Packages (Integration Services)](https://msdn.microsoft.com/library/ms141091\(v=sql11\).aspx) on MSDN.  

-->
  
## <a name="basics"></a><a name="Basics"></a>Grundlagen  
Integration Services ist die Komponente von SQL Server für das Extrahieren, Transformieren und Laden von Daten (ETL) mit hoher Leistung und wird häufig verwendet, um ein Data Warehouse aufzufüllen und zu aktualisieren.  
  
Der PDW-Ziel Adapter ist eine Integration Services Komponente, mit der Sie Daten mithilfe Integration Services dzx-Paketen in PDW laden können. In einem Paket Workflow für SQL serverpdw können Sie Daten aus mehreren Quellen laden und Zusammenführen sowie Daten in mehrere Ziele laden. Die Ladevorgänge erfolgen parallel innerhalb eines Pakets und unter mehreren gleichzeitig ausgeführten Paketen, bis zu einem Maximum von 10 in der gleichen Anwendung parallel ausgeführten Ladevorgängen.  
  
Zusätzlich zu den in diesem Thema beschriebenen Aufgaben können Sie andere Funktionen von Integration Services verwenden, um Ihre Daten zu filtern, zu transformieren, zu analysieren und zu bereinigen, bevor Sie Sie in die Data Warehouse laden. Sie können auch den Workflow des Pakets verbessern, indem Sie SQL-Anweisungen ausführen, untergeordnete Pakete ausführen oder E-Mails versenden.  
  
Eine umfassende Dokumentation zu Integration Services finden Sie unter [SQL Server Integration Services](../integration-services/sql-server-integration-services.md).  
  
## <a name="methods-for-running-an-integration-services-package"></a><a name="HowToDeployPackage"></a>Methoden zum Ausführen eines Integration Services Pakets  
Verwenden Sie eine dieser Methoden, um ein Integration Services Paket auszuführen.  
  
### <a name="run-from-sql-server-2008-r2-business-intelligence-development-studio-bids"></a>Ausführen von SQL Server 2008 R2 Business Intelligence Development Studio (Angebote)  
Um das Paket innerhalb von angeboten auszuführen, klicken Sie mit der rechten Maustaste auf das Paket, und wählen Sie **Paket ausführen**aus.  
  
Standardmäßig führt Angebote Pakete mit 64-Bit-Binärdateien aus. Dies wird durch die **Run64BitRuntime** -Paket Eigenschaft bestimmt. Um diese Eigenschaft festzulegen, wechseln Sie zu **Projektmappen-Explorer**, klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**aus. Wechseln Sie auf der Eigenschaften **Seite Integration Services**zu **Konfigurations Eigenschaften** , und wählen Sie **Debuggen**aus. Die Eigenschaft **Run64BitRuntime** wird unter den **Optionen Debuggen**angezeigt. Wenn Sie 32-Bit-Runtimes verwenden möchten, legen Sie diese Einstellung auf **false**fest. Wenn Sie 64-Bit-Runtimes verwenden möchten, legen Sie diese Eigenschaft auf **true**fest.  
  
### <a name="run-from-sql-server-2012-sql-server-data-tools"></a>Ausführen von SQL Server 2012 SQL Server Data Tools  
Klicken Sie mit der rechten Maustaste auf das Paket, und wählen Sie **Paket ausführen**aus, um das Paket in SQL Server Data Tools auszuführen.  
  
### <a name="run-from-powershell"></a>Ausführen von PowerShell  
So führen Sie das Paket mithilfe des Hilfsprogramms **dtexec** aus Windows PowerShell aus:`dtexec /FILE <packagePath>`  
  
Zum Beispiel, `dtexec /FILE "C:\Users\User1\Desktop\Package.dtsx"`  
  
### <a name="run-from-a-windows-command-prompt"></a>Ausführen über eine Windows-Eingabeaufforderung 
So führen Sie das Paket mithilfe des Hilfsprogramms **dtexec** von einer Windows-Eingabeaufforderung aus:`dtexec /FILE <packagePath>`  
  
Beispiel: `dtexec /FILE "C:\Users\User1\Desktop\Package.dtsx"`  
  
## <a name="data-types"></a><a name="DataTypes"></a>Datentypen  
Wenn Integration Services zum Laden von Daten aus einer Datenquelle in eine SQL Server PDW-Datenbank verwendet wird, werden die Daten zunächst aus den Quelldaten Integration Services-Datentypen zugeordnet. Dies ermöglicht die Zuordnung von Daten aus mehreren Datenquellen zu einem allgemeinen Satz von Datentypen.  
  
Anschließend werden die Daten aus Integration Services SQL Server PDW-Datentypen zugeordnet. In der folgenden Tabelle werden für jeden SQL Server PDW Datentyp die Integration Services-Datentypen aufgelistet, die in den SQL Server PDW-Datentyp konvertiert werden können.  
  
|PDW-Datentyp|Integration Services Datentypen, die dem PDW-Datentyp zugeordnet sind.|  
|---------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|  
|BIT|DT_BOOL|  
|bigint|DT_I1, DT_I2, DT_I4, DT_I8, DT_UI1, DT_UI2, DT_UI4|  
|CHAR|DT_STR|  
|DATE|DT_DBDATE|  
|DATETIME|DT_DATE, DT_DBDATE, DT_DBTIMESTAMP, DT_DBTIMESTAMP2|  
|DATETIME2|DT_DATE, DT_DBDATE, DT_DBTIMESTAMP, DT_DBTIMESTAMP2|  
|DATETIMEOFFSET|DT_WSTR|  
|DECIMAL|DT_DECIMAL, DT_I1, DT_I2, DT_I4, DT_I4, DT_I8, DT_NUMERIC, DT_UI1, DT_UI2, DT_UI4, DT_UI8|  
|GLEITKOMMAZAHL|DT_R4, DT_R8|  
|INT|DT_I1, DTI2, DT_I4, DT_UI1, DT_UI2|  
|MONEY|DT_CY|  
|NCHAR|DT_WSTR|  
|NUMERIC|DT_DECIMAL, DT_I1, DT_I2, DT_I4, DT_I8, DT_NUMERIC, DT_UI1, DT_UI2, DT_UI4, DT_UI8|  
|NVARCHAR|DT_WSTR, DT_STR|  
|real|DT_R4|  
|SMALLDATETIME|DT_DBTIMESTAMP2|  
|SMALLINT|DT_I1, DT_I2, DT_UI1|  
|SMALLMONEY|DT_R4|  
|TIME|DT_WSTR|  
|TINYINT|DT_I1|  
|VARBINARY|DT_BYTES|  
|VARCHAR|DT_STR|  
  
**Eingeschränkte Unterstützung für Datentyp Genauigkeit**  
  
PDW generiert einen Validierungs Fehler, wenn Sie eine DT_NUMERIC oder DT_DECIMAL Eingabe Spalte zuordnen, die einen Wert mit einer Genauigkeit von mehr als 28 enthält.  
  
**Nicht unterstützte Datentypen**  
  
SQL Server PDW unterstützt die folgenden Integration Services-Datentypen nicht:  
  
-   DT_DBTIMESTAMPOFFSET  
  
-   DT_DBTIME2  
  
-   DT_GUID  
  
-   DT_IMAGE  
  
-   DT_NTEXT  
  
-   DT_TEXT  
  
Wenn Sie Spalten, die Daten dieser Typen enthalten, in SQL Server PDW laden möchten, müssen Sie im Datenfluss eine streamingtransformation für Datenkonvertierung hinzufügen, um die Daten in einen kompatiblen Datentyp zu konvertieren.  
  
## <a name="permissions"></a>Berechtigungen  
Zum Ausführen eines Integration Services Lade Pakets benötigen Sie Folgendes:  
  
-   Load-Berechtigung für die Datenbank.  
  
-   Anwendbare INSERT-, Update-und DELETE-Berechtigungen für die Ziel Tabelle.  
  
-   Wenn eine Staging-Datenbank verwendet wird, erstellen Sie die-Berechtigung für die Stagingdatenbank. Dies dient zum Erstellen einer temporären Tabelle.  
  
-   Wenn keine Staging-Datenbank verwendet wird, erstellen Sie die-Berechtigung für die Zieldatenbank. Dies dient zum Erstellen einer temporären Tabelle.  
  
## <a name="general-remarks"></a><a name="GenRemarks"></a>Allgemeine Hinweise  
Wenn für ein Integration Services Paket mehrere SQL Server PDW Ziele ausgeführt werden und eine Verbindung beendet wird, beendet Integration Services das Übertragen von Daten an alle SQL Server PDW Ziele.  
  
## <a name="limitations-and-restrictions"></a><a name="Limits"></a>Einschränkungen  
Bei einem Integration Services Paket wird die Anzahl der SQL Server PDW Ziele für die gleiche Datenquelle durch die maximale Anzahl aktiver Ladevorgänge beschränkt. Das Maximum ist vorkonfiguriert und kann nicht durch den Benutzer konfiguriert werden. 

<!-- MISSING LINKS
For the maximum number of loads and queued loads per appliance, see [Minimum and maximum values](minimum-and-maximum-values.md).  
-->
  
Jedes Integration Services Paket Ziel für die gleiche Datenquelle zählt bei Ausführung des Pakets als ein Ladevorgang. Angenommen die maximale Anzahl aktiver Ladevorgänge ist z. B. 10. Das Paket wird nicht ausgeführt, wenn es versucht, 11 oder mehr Ziele für die gleiche Datenquelle zu öffnen.  
  
Es können mehrere Pakete gleichzeitig ausgeführt werden, solange jedes Paket nicht mehr als die maximale Anzahl aktiver Ladevorgänge verwendet. Wenn die maximale Anzahl aktiver Ladevorgänge beispielsweise 10 beträgt, können Sie zwei Pakete mit je 10 Zielen gleichzeitig ausführen. Ein Paket wird ausgeführt während das andere in der Warteschlange steht.  
  
Das Paket wird nicht ausgeführt, wenn die Anzahl der Ladevorgänge in der Warteschlange die maximal zulässige Anzahl der in Warteschlange gestellten Ladevorgänge überschreitet. Wenn z. b. die maximale Anzahl von Ladevorgängen 10 pro Gerät beträgt und die maximale Anzahl von Ladevorgängen in der Warteschlange 40 pro Gerät beträgt, können Sie gleichzeitig fünf Integration Services Pakete ausführen, von denen jeweils 10 Ziele geöffnet werden. Ein sechstes Paket kann nicht ausgeführt werden.  

> [!IMPORTANT]
> Die Verwendung einer OLE DB Datenquelle in SSIS mit dem PDW-Ziel Adapter kann zu Daten Beschädigungen führen, wenn die Quell Tabelle char-und varchar-Spalten mit SQL-Sortierungen enthält. Es wird empfohlen, eine ADO.NET-Quelle zu verwenden, wenn die Quell Tabelle char-oder varchar-Spalten mit SQL-Sortierungen enthält. 

  
## <a name="locking-behavior"></a><a name="Locks"></a>Sperr Verhalten  
Beim Laden von Daten mit Integration Services verwendet SQL Server PDW Sperren auf Zeilenebene, um Daten in der Ziel Tabelle zu aktualisieren. Dies bedeutet, dass jede Zeile während des Updates für den Lese- und Schreibzugriff gesperrt wird. Die Zeilen in der Zieltabelle werden nicht gesperrt, während die Daten in die Stagingtabelle geladen werden.  
  
## <a name="examples"></a><a name="Examples"></a>Beispiele  
  
### <a name="a-simple-load-from-flat-file"></a><a name="Walkthrough"></a>A. Einfaches Laden aus Flatfile  
In der folgenden exemplarischen Vorgehensweise wird eine einfache Daten Auslastung mithilfe Integration Services veranschaulicht, um Flatfiledaten in eine SQL Server PDW Appliance zu laden.  In diesem Beispiel wird davon ausgegangen, dass Integration Services bereits auf dem Client Computer installiert wurde und das SQL Server PDW Ziel wie oben beschrieben installiert wurde.  
  
In diesem Beispiel werden wir in die `Orders` -Tabelle laden, die die folgende DDL enthält. Die `Orders` Tabelle ist Teil der `LoadExampleDB` Datenbank.  
  
```sql  
CREATE TABLE LoadExampleDB.dbo.Orders (  
   id INT,  
   city varchar(25),  
   lastUpdateDate DATE,  
   orderDate DATE)  
;  
```  
  
Dies sind die Daten, die geladen werden:  
  
```  
id        city           lastUpdateDate     orderdate  
--------- -------------- ------------------ ----------  
1         Seattle        2010-05-01         2010-01-01  
2         Denver         2002-06-25         1999-01-02  
```  
  
Erstellen Sie zur Vorbereitung der Auslastung die Flatfile `exampleLoad.txt`, die die Auslastungs Daten enthält:  
  
```  
id,city,lastUpdateDate,orderDate  
1,Seattle,2010-05-01,2010-01-01  
2,Denver,2002-06-25,1999-01-02  
```  
  
Erstellen Sie zunächst ein Integration Services Paket, indem Sie die folgenden Schritte ausführen:  
  
1.  Wählen Sie \(in SQL Server Data Tools\)SSDT **Datei**, **neu**und dann **Projekt**aus. Wählen Sie **Integration Services Projekt** aus den aufgeführten Optionen aus. Nennen Sie dieses `ExampleLoad`Projekt, und klicken Sie auf **OK**.  
  
2.  Klicken Sie auf die Registerkarte **Ablauf Steuerung** , und ziehen Sie dann den **Datenfluss Task** aus der **Toolbox** in den Bereich **Ablauf Steuerung** .  
  
3.  Klicken Sie auf die Registerkarte **Datenfluss** , und ziehen Sie **Flatfilequelle** aus der **Toolbox** in den Bereich **Datenfluss** . Doppelklicken Sie auf das Feld, das Sie gerade erstellt haben, um den **Quelleditor für Flatfiles**zu öffnen.  
  
4.  Klicken Sie auf **Verbindungs-Manager** und dann auf **neu**.  
  
5.  Geben Sie im Feld **Name des Verbindungs-Managers** einen anzeigen Amen für die Verbindung ein. In diesem Beispiel `Example Load Flat File CM`.  
  
6.  Klicken Sie auf **Durchsuchen** , und wählen Sie die `ExampleLoad.txt` Datei auf dem lokalen Computer.  
  
7.  Da die Flatfile eine Zeile mit Spaltennamen enthält, klicken Sie auf die **Spaltennamen im Feld erste Daten Zeile** .  
  
8.  Klicken Sie in der linken Spalte auf **Spalten** , und führen Sie eine Vorschau der Daten aus, die geladen werden, um sicherzustellen, dass die Spaltennamen und Daten korrekt interpretiert wurden.  
  
9. Klicken Sie in der linken Spalte auf **erweitert** . Klicken Sie auf die einzelnen Spaltennamen, um den Datentyp zu überprüfen, der den Daten zugeordnet ist. Geben Sie im Feldänderungen ein, sodass die Datentypen der geladenen Daten mit den Ziel Spaltentypen kompatibel sind.  
  
10. Klicken Sie zum Speichern Ihres Verbindungs-Managers auf **OK** .  
  
11. Klicken Sie auf **OK** , um den **Quelleditor für Flatfiles**zu schließen.  
  
Geben Sie das Ziel für den Datenfluss an.  
  
1.  Ziehen Sie das **SQL Server PDW Ziel** aus der **Toolbox** in den Bereich **Datenfluss** .  
  
2.  Doppelklicken Sie auf das Feld, das Sie gerade erstellt haben, um den **SQL Server PDW Ziel-Editor**zu laden.  
  
3.  Klicken Sie neben dem Verbindungs- **Manager**auf den Pfeil nach unten.  
  
4.  Wählen Sie **neue Verbindung erstellen**aus.  
  
5.  Geben Sie die Informationen für den Server, den Benutzer, das Kennwort und die Zieldatenbank mit Informationen an, die für Ihr Gerät spezifisch sind. (Beispiele sind unten dargestellt). Klicken Sie dann auf **OK**.  
  
    Für Infiniband-Verbindungen: **Server Name**: Geben Sie <Appliance-Name>-SQLCTL01, 17001 ein.  
  
    Für Ethernet-Verbindungen: **Server Name**: Geben Sie die IP-Adresse des Steuerelement Knoten Clusters (Komma, Port 17001) ein. Beispiel: 10.192.63.134, 17001.  
  
    **Bedienungs**`user1`  
  
    **Anmelden**`password1`  
  
    **Zieldatenbank:**`LoadExampleDB`  
  
6.  Wählen Sie die Ziel Tabelle `Orders`aus:.  
  
7.  Wählen Sie als Lade Modus **Anfügen** aus, und klicken Sie auf **OK**.  
  
Geben Sie den Datenfluss von der Quelle zum Ziel an.  
  
1.  Ziehen Sie im Bereich **Datenfluss** den grünen Pfeil aus dem Feld **Flatfilequelle** in das Feld **SQL Server PDW Ziel** .  
  
2.  Doppelklicken Sie auf das Feld **SQL Server PDW Ziel** , damit der **SQL Server PDW Ziel-Editor** wieder angezeigt wird. Die Spaltennamen sollten auf der linken Seite unter nicht zugeordnete **Eingabe Spalten**aus der Flatfile angezeigt werden. Die Spaltennamen sollten auf der rechten Seite unter nicht zugeordnete **Ziel Spalten**aus der Ziel Tabelle angezeigt werden. Ordnen Sie die Spalten durchziehen oder Doppelklicken auf die entsprechenden Spaltennamen in den Listen nicht zugeordnete **Eingabe Spalten** und nicht zugeordnete **Ziel Spalten** dem Feld zugeordnete **Spalten** zu. Klicken Sie auf **OK**, um die Einstellungen zu speichern.  
  
3.  Speichern Sie das Paket, indem Sie im Menü **Datei** auf **Speichern** klicken.  
  
Führen Sie das Paket auf dem Computer Integration Services aus.  
  
1.  Klicken Sie in der Integration Services**Projektmappen-Explorer** (Rechte Spalte) mit der `Package.dtsx` rechten Maustaste, und wählen Sie **Ausführen**aus.  
  
2.  Das Paket wird ausgeführt, und **der Fortschritt** sowie alle Fehler werden im Statusbereich angezeigt. Verwenden Sie einen SQL-Client, um die Last zu bestätigen, oder überwachen Sie die Last über die SQL Server PDW Admin Console.  
  
## <a name="see-also"></a>Weitere Informationen  
[Erstellen eines Skript Tasks, der den SSIS-PDW-Ziel Adapter verwendet](create-ssis-script-task-using-pdw-destination-adapter.md)  
[SQL Server Integration Services](../integration-services/sql-server-integration-services.md)  
[Entwerfen und Implementieren von Paketen (Integration Services)](https://msdn.microsoft.com/library/ms141091\(v=sql11\).aspx)  
[Lernprogramm: Erstellen eines einfachen Pakets mithilfe eines Assistenten](https://technet.microsoft.com/library/ms365330\(v=sql11\).aspx)  
[Erste Schritte (Integration Services)](https://go.microsoft.com/fwlink/?LinkId=202412)  
[Beispiel für die dynamische Paket Generierung](https://go.microsoft.com/fwlink/?LinkId=202413)  
[Entwerfen der SSIS-Pakete für Parallelität (SQL Server-Video)](https://msdn.microsoft.com/library/dd795221.aspx)  
[Beispiele für die Microsoft SQL Server Community: Integration Services](https://go.microsoft.com/fwlink/?LinkId=202415)  
[Verbessern des inkrementellen Ladens mit Change Data Capture](../integration-services/change-data-capture/change-data-capture-ssis.md)  
[Transformation für langsam veränderliche Dimensionen](../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md)  
[Masseneinfügungstask](../integration-services/control-flow/bulk-insert-task.md)  
  
<!-- MISSING LINKS
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Common metadata query examples](metadata-query-examples.md)
-->
