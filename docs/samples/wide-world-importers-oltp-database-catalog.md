---
title: WideWorldImporters-OLTP-Datenbank-Katalog – SQL | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 35228d6773e576b2d8b062c94aa8797d07f00809
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38000662"
---
# <a name="wideworldimporters-database-catalog"></a>Datenbankkatalog "wideworldimporters"
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Die Datenbank "wideworldimporters" enthält alle der Transaktionsinformationen datenkontingent von täglich für Vertrieb und Einkauf, sowie Daten von triebwerksensoren für Fahrzeuge "und" kalte Räume.

## <a name="schemas"></a>Schemas

"Wideworldimporters" verwendet die Schemas für unterschiedliche Zwecke, z. B. das Speichern von Daten definieren, wie Benutzer die Daten zugreifen können und Bereitstellung von Objekten für Datawarehouse-Entwicklung und Integration.

### <a name="data-schemas"></a>Datenschemas

Diese Schemas enthalten die Daten. Eine Reihe von Tabellen, die von allen anderen Schemas erforderlich sind, und im Anwendungsschema befinden.

|Schema|Description|
|-----------------------------|---------------------|
|Application|Anwendungsweite Benutzer, Kontakte und Parameter. Enthält außerdem Verweistabellen mit Daten, die in mehreren Schemas verwendet wird|
|Purchasing|Aktieneintrag Käufe von Lieferanten und Details zu den Lieferanten.|  
|Sales|Stock Element sales, um Einzelhandelskunden und Details zu den Kunden und Umsätze Personen. |  
|Warehouse|Aktieneintrag Inventur und Transaktionen.|  

### <a name="secure-access-schemas"></a>Secure-Access-schemas

Diese Schemas werden für externe Anwendungen verwendet, die nicht direkt auf die Tabellen zulässig sind. Sie enthalten, Sichten und gespeicherten Prozeduren, die von externen Anwendungen verwendet wird.

|Schema|Description|
|-----------------------------|---------------------|
|Website|Zugriff auf die Datenbank von der unternehmensportalwebsite ist über dieses Schema.|
|Berichte|Zugriff auf die Datenbank von Reporting Services-Berichten erfolgt über dieses Schema.|
|Power BI|Zugriff auf die Datenbank von der Power BI-Dashboards über das Enterprise-Gateway ist über dieses Schema.|

Beachten Sie, dass die Berichte und Power BI Schemas werden nicht in der ersten Version der Beispieldatenbank verwendet. Verwenden Sie diese Schemas werden jedoch alle Reporting Services und Power BI-Beispiele auf dieser Datenbank empfohlen.

### <a name="development-schemas"></a>Entwicklung von schemas

Schemas für spezielle Zwecke

|Schema|Description|
|-----------------------------|---------------------|
|Integration|Objekte und Verfahren für die Datawarehouse-Integration erforderlich sind (d. h. Migrieren Ihrer Daten in der Datenbank "wideworldimportersdw").|
|Sequenzen|Enthält die Sequenzen, die von allen Tabellen in der Anwendung verwendet.|

## <a name="tables"></a>Tabellen

Alle Tabellen in der Datenbank sind in den Daten.

### <a name="application-schema"></a>Anwendungsschema

Details der Parameter und Benutzer (Benutzer und Kontakte), zusammen mit allgemeinen Verweistabellen (häufig bei mehreren anderen Schemas).

|Tabelle|Description|
|-----------------------------|---------------------|
|SystemParameters|Enthält eine systemweite konfigurierbaren Parameter.|
|Personen|Enthält die Benutzernamen, Kontaktinformationen für alle Benutzer, die die Anwendung verwenden und für die Personen, die die Wide World Importers an kundenorganisationen behandelt. Dies schließt die Mitarbeiter, Kunden, Lieferanten und anderen Kontakte. Für Personen, die die Berechtigung zum Verwenden des Systems oder die Website erteilt wurde, enthält die Informationen über Anmeldeinformationen.|
|Städte|Es gibt viele Adressen, die im System, für Personen, Unternehmen Delivery Kundenadressen pickup-Adressen an den Lieferanten usw. gespeichert. Wenn Sie eine Adresse gespeichert ist, besteht ein Verweis auf eine Stadt in dieser Tabelle. Es gibt auch eine räumliche Position für jede Stadt.|
|StateProvinces|Städte sind Teil der Bundesstaaten oder Provinzen. Diese Tabelle enthält Details zu den Fällen, einschließlich der räumliche Daten, die die Grenzen beschreiben, jede Bundesland/Kanton.|
|Länder|Sind Bestandteil der Länder, Bundesländer oder Provinzen. Diese Tabelle enthält Details zu den Fällen, einschließlich der räumliche Daten, die die Grenzen der einzelnen Länder beschreibt.|
|DeliveryMethods|Möglichkeiten zur Bereitstellung von vorhandenen Elementen (z. B. LKW/van, Post, Start-, Courier usw.)|
|PaymentMethods|Optionen für Zahlungen (z. B. Bar, elektronische ÜBERWEISUNG, Überprüfung usw..)|
|TransactionTypes|Arten von Kunden, Lieferanten oder vordefinierten Transaktionen (z. B. Rechnung, Gutschrift usw.)|

### <a name="purchasing-schema"></a>Erwerb von Schemas

Details von Lieferanten und aktieneintrag Käufe.

|Tabelle|Description|
|-----------------------------|---------------------|
|Suppliers|Main Entitätstabelle für Lieferanten (Organisationen)|
|SupplierCategories|Kategorien für Lieferanten (z. B. Novelties, Toys, clothing, Verpacken, usw.)|
|SupplierTransactions|Alle finanzielle Transaktionen, die Lieferanten-bezogene (Rechnungen, Zahlungen)|
|Aufträge|Details des Lieferanten Bestellungen|
|PurchaseOrderLines|Bestelldetailzeilen vom Lieferanten Bestellungen|

 
### <a name="sales-schema"></a>Sales-Schema

Details des Kunden, Vertriebsmitarbeiter und der aktieneintrag Verkäufe.

|Tabelle|Description|
|-----------------------------|---------------------|
|Customers|Hauptentität-Tabellen für Kunden (Unternehmen oder Einzelpersonen)|
|CustomerCategories|Kategorien für Kunden (d. h. Neuheit speichert, Supermärkten usw.)|
|BuyingGroups|Kundenorganisationen können Gruppen angehören, die größer Marktposition auszuüben|
|CustomerTransactions|Alle finanzielle Transaktionen, die kundenbezogene (Rechnungen, Zahlungen)|
|SpecialDeals|Sonderpreise. Dies können feste Preise umfassen, für den Rabatt in Dollar oder Rabatt in Prozent.|
|Orders|Details der Kundenaufträge|
|OrderLines|Bestelldetailzeilen von kundenbestellungen|
|Rechnungen|Details von kundenrechnungen|
|InvoiceLines|Bestelldetailzeilen von kundenrechnungen|

### <a name="warehouse-schema"></a>Warehouse-Schemas

Details der vordefinierten Elemente, deren betrieben und Transaktionen.

|Tabelle|Description|
|-----------------------------|---------------------|
|StockItems|Main Entitätstabelle für vordefinierte Elemente|
|StockItemHoldings|Nicht-temporalen Spalten für vordefinierte Elemente. Dies sind häufig aktualisierten Spalten.|
|StockGroups|Gruppen für die Kategorisierung von vorhandenen Elementen (z. B. Novelties, Toys, genießbare Novelties usw.)|
|StockItemStockGroups|Welche vordefinierte Elemente werden in der Stock (m: n) gruppiert|
|Farben|Vordefinierte Elemente haben die Farben (optional)|
|PackageTypes|Methoden, mit denen Elemente Kursdiagramme verpackt werden können (z. B. Box, Karton, Palette, kg, usw.|
|StockItemTransactions|Transaktionen, die für alle Bewegungen, die mit allen vorhandenen Elementen (Empfang, Verkauf, auf null)|
|VehicleTemperatures|Regelmäßig aufgezeichneten Temperaturen des Fahrzeugs kältemaschinen|
|ColdRoomTemperatures|Regelmäßig aufgezeichnet Temperaturen von kalten Platz kältemaschinen|


## <a name="design-considerations"></a>Überlegungen zum Entwurf

Der Datenbankentwurf ist subjektiv, und es gibt keine richtigen oder falschen Weg, eine Datenbank entwerfen. Zeigen Ideen, wie Sie Ihre eigene Datenbank entwerfen können, die Schemas und Tabellen in dieser Datenbank.

### <a name="schema-design"></a>Schemadesign

"Wideworldimporters" verwendet eine kleine Anzahl von Schemas aus, sodass es einfach ist, das Datenbanksystem verstehen und veranschaulichen die Prinzipien der Datenbank.  

Wo immer dies möglich ist, stellt die Datenbank häufig zusammen im gleichen Schema Join Komplexität minimiert abgefragten Tabellen zusammen.

Das Datenbankschema wurde generierten Code basierend auf einer Reihe von Tabellen mit Replikationsmetadaten in einer anderen Datenbank WWI_Preparation. Dadurch wird "wideworldimporters" ein sehr hohes Maß an Entwurf Konsistenz, Konsistenz und Vollständigkeit. Einzelheiten wie der Generierung des Schemas finden Sie in den Quellcode: [Wide-Welt-Importers / "wwi"-Datenbank-Scripts](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/sample-scripts)

### <a name="table-design"></a>Tabellenentwurf

- Alle Tabellen weisen die einzelne Spalte der Primärschlüssel aus Gründen der Einfachheit der Join.
- Alle Schemas, Tabellen, Spalten, Indizes und Check-Einschränkungen besitzen eine Beschreibung, die erweiterte Eigenschaft, die verwendet werden kann, um den Zweck des Objekts oder der Spalte zu identifizieren. Speicheroptimierte Tabellen sind eine Ausnahme aus, da sie derzeit erweiterte Eigenschaften, die nicht unterstützen.
- Alle Fremdschlüssel werden automatisch indiziert, es sei denn, es gibt einen anderen nicht gruppierten Index, der die gleiche linken Komponente verfügt.
- In Tabellen automatischen Nummerierung basiert auf Sequenzen. Diese Sequenzen sind einfacher zu arbeiten mit verknüpften Servern und ähnlichen Umgebungen als IDENTITY-Spalten. Speicheroptimierte Tabellen verwenden IDENTITY-Spalten aus, da sie keine SQL Server 2016 unterstützen.
- Diese Tabellen eine einzigen Sequenz (Transaktions-ID) verwendet wird: CustomerTransactions SupplierTransactions und StockItemTransactions. Dieses Beispiel veranschaulicht, wie eine Gruppe von Tabellen eine einzigen Sequenz haben kann.
- Einige Spalten enthalten die entsprechenden Standardwerte.

### <a name="security-schemas"></a>Sicherheit von schemas

Aus Sicherheitsgründen lässt "wideworldimporters" nicht Datenschemas direkten Zugriff auf externe Anwendungen. Um Zugriff zu isolieren, wird "wideworldimporters" Sicherheitszugriff Schemas, die Daten nicht dauerhaft, aber enthält Sichten und gespeicherten Prozeduren verwendet. Externe Anwendungen verwenden Sie den Security-Schemas zum Abrufen der Daten, die sie berechtigt sind, anzuzeigen.  Auf diese Weise können Benutzer nur die Sichten und gespeicherten Prozeduren in den sicheren Zugriff ausführen

In diesem Beispiel wird z. B. Power BI-Dashboards enthält. Eine externe Anwendung greift diese Power BI-Dashboards aus dem Power BI-Gateway als ein Benutzer mit Leseberechtigung für das Power BI-Schema auf.  Für nur-Lese Berechtigung benötigt der Benutzer nur die SELECT- und EXECUTE-Berechtigung für das Power BI-Schema. Ein Datenbankadministrator an "wwi" weist diese Berechtigungen nach Bedarf.

## <a name="stored-procedures"></a>Gespeicherte Prozeduren

Gespeicherte Prozeduren werden in Schemas organisiert. Die meisten der Schemas werden für die Konfiguration oder Beispiel verwendet.

Die `Website` Schema enthält die gespeicherten Prozeduren, die von einer Web-Front-End verwendet werden können.

Die `Reports` und `PowerBI` Schemas für reporting Services und Power BI-Zwecke vorgesehen sind. Alle Erweiterungen des Beispiels werden empfohlen, diese Schemas, die für die berichterstellung verwendet.

### <a name="website-schema"></a>Website-schema

Hierbei handelt es sich um die Prozeduren, die von einer Clientanwendung, wie etwa einer Web-Front-End verwendet.

|Verfahren|Zweck|
|-----------------------------|---------------------|
|ActivateWebsiteLogon|Ermöglicht es eine Person (von `Application.People`) auf die Website zugreifen.|
|ChangePassword|Ändert das Kennwort eines Benutzers (für Benutzer, die keine externen Authentifizierungsmechanismen verwenden).|
|InsertCustomerOrders|Ermöglicht das Einfügen von ein oder mehrere kundenbestellungen (einschließlich der Zeilen).|
|InvoiceCustomerOrders|Akzeptiert eine Liste von Aufträgen in Rechnung gestellt werden, und verarbeitet die Rechnungen.|
|RecordColdRoomTemperatures|Akzeptiert eine Liste für den Sensor-Daten, wie ein Tabellenwertparameter (TVP), und wendet die Daten, die `Warehouse.ColdRoomTemperatures` temporalen Tabelle.|
|RecordVehicleTemperature|Nimmt ein JSON-Array und wird verwendet, um update `Warehouse.VehicleTemperatures`.|
|SearchForCustomers|Sucht nach Kunden anhand des Namens oder der Teil des Namens (Name des Unternehmens oder der Name der Person).|
|SearchForPeople|Sucht nach Personen anhand des Namens oder der Teil des Namens.|
|SearchForStockItems|Sucht nach der vordefinierten Elemente nach Namen oder einen Teil des Namens oder Kommentare marketing.|
|SearchForStockItemsByTags|Sucht nach vorhandenen Elementen mithilfe von Tags.|
|SearchForSuppliers|Sucht nach Lieferanten anhand des Namens oder der Teil des Namens (Name des Unternehmens oder der Name der Person).|

### <a name="integration-schema"></a>Integration von Schemas

Die gespeicherten Prozeduren in diesem Schema werden von der ETL-Prozess verwendet. Sie erhalten die benötigten Daten aus verschiedenen Tabellen für den erforderliche Zeitraum der [ETL-Pakets](wide-world-importers-perform-etl.md).

### <a name="dataloadsimulation-schema"></a>DataLoadSimulation-Schema

Simuliert eine Workload, die Verkäufe und Einkäufe einfügt. Die wichtigsten gespeicherte Prozedur ist `PopulateDataToCurrentDate`, dient zum Einfügen von Daten bis zum aktuellen Datum.

|Verfahren|Zweck|
|-----------------------------|---------------------|
|Configuration_ApplyDataLoadSimulationProcedures|Neu die Verfahren erforderlich für Daten Simulation geladen werden. Dies ist erforderlich, für die Daten in das aktuelle Datum.|
|Configuration_RemoveDataLoadSimulationProcedures|Dadurch werden die Verfahren wieder entfernt, nach Abschluss der Simulation von Daten.|
|DeactiveTemporalTablesBeforeDataLoad|Die temporale Art der alle temporalen Tabellen entfernt, und falls zutreffend, ein Triggers angewendet wird, damit Änderungen vorgenommen werden können, als wären sie wurden an einem Datum als die Sys-temporären Tabellen können angewendet werden.|
|PopulateDataToCurrentDate|Verwendet, um die Daten dem aktuellen Stand zu bringen. Sollte vor jeder anderen Optionen für die Datenbank nach dem Wiederherstellen der Datenbank einer anfänglichen Sicherung ausgeführt werden.|
|ReactivateTemporalTablesAfterDataLoad|Erneut wird die temporalen Tabellen, einschließlich der Überprüfung der Konsistenz von Daten. (Die zugeordneten Trigger wird entfernt).|


### <a name="application-schema"></a>Anwendungsschema

Diese Prozeduren werden verwendet, zum Konfigurieren des Beispiels. Sie werden verwendet, um Funktionen der Enterprise Edition auf die standard Edition-Version des Beispiels sowie zur Überwachung hinzufügen und die Volltextindizierung anzuwenden.

|Verfahren|Zweck|
|-----------------------------|---------------------|
|AddRoleMemberIfNonexistant|Eine Rolle ein Mitglied hinzugefügt wird, wenn das Element bereits in der Rolle nicht ist|
|Configuration_ApplyAuditing|Bietet die Überwachung. Server-Überwachung wird für standard Edition-Datenbanken übernommen. zusätzliche datenbanküberwachung ist für die Enterprise Edition hinzugefügt.|
|Configuration_ApplyColumnstoreIndexing|Columnstore-Indizierung auf gilt `Sales.OrderLines` und `Sales.InvoiceLines` und wird von entsprechend neu indiziert.|
|Configuration_ApplyFullTextIndexing|Wendet die Volltextindizes auf `Application.People`, `Sales.Customers`, `Purchasing.Suppliers`, und `Warehouse.StockItems`. Ersetzt `Website.SearchForPeople`, `Website.SearchForSuppliers`, `Website.SearchForCustomers`, `Website.SearchForStockItems`, `Website.SearchForStockItemsByTags` mit Beschreibungen der austauschvorgehensweisen, die die Volltextindizierung verwenden.|
|Configuration_ApplyPartitioning|Wendet die Tabellenpartitionierung zu `Sales.CustomerTransactions and `Purchasing.SupplierTransactions und ordnet die Indizes entsprechend anpassen.|
|Configuration_ApplyRowLevelSecurity|Zum Anwenden von Sicherheit auf Zeilenebene für Filter Kunden von Sales Territory-bezogenen Rollen.|
|Configuration_ConfigureForEnterpriseEdition|Gilt, columnstore-Indizierung, Volltextsuche, im Arbeitsspeicher, Polybase und Partitionierung.|
|Configuration_EnableInMemory|Fügt eine speicheroptimierten Dateigruppe, (wenn nicht in Azure funktioniert), ersetzt `Warehouse.ColdRoomTemperatures`, `Warehouse.VehicleTemperatures` durch InMemory-Entsprechungen und migriert die Daten, erstellt die `Website.OrderIDList`, `Website.OrderList`, `Website.OrderLineList`, `Website.SensorDataList` Tabellentypen mit Speicheroptimierte Entsprechungen, löscht und neu erstellt die Prozeduren `Website.InvoiceCustomerOrders`, `Website.InsertCustomerOrders`, und `Website.RecordColdRoomTemperatures` , verwendet dieser Tabellentypen.|
|Configuration_RemoveAuditing|Entfernt die Überwachungskonfiguration an.|
|Configuration_RemoveRowLevelSecurity|Entfernt die Zeile Sicherheit auf Zeilenebene-Konfiguration (Dies ist für Änderungen an den zugeordneten Tabellen erforderlich).|
|CreateRoleIfNonExistant|Erstellt eine Datenbankrolle aus, wenn er nicht bereits vorhanden.|


### <a name="sequences-schema"></a>Schema für Sequenzen

Vor, um die Sequenzen in der Datenbank zu konfigurieren.

|Verfahren|Zweck|
|-----------------------------|---------------------|
|ReseedAllSequences|Ruft die Prozedur ReseedSequenceBeyondTableValue für alle folgen.|
|ReseedSequenceBeyondTableValue|Wird verwendet, um den nächsten Sequenzwert über den Wert in einer beliebigen Tabelle neu zu positionieren, die dieselbe Tasksequenz verwendet. (Z. B. DBCC CHECKIDENT für die Identität Spalten entspricht, für die Sequenzen, aber auf potenziell mehrere Tabellen).|
