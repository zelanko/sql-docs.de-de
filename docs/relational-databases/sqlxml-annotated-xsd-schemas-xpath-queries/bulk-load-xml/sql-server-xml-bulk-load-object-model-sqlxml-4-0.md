---
title: SQL Server XML-Massen laden-Objektmodell (SQLXML)
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], object model
- ErrorLogFile property
- SGDropTables property
- SGUseID property
- KeepNulls property
- ConnectionCommand property
- SchemaGen property
- XMLFragment property
- SQLXMLBulkLoad object
- ForceTableLock property
- CheckConstraints property
- BulkLoad property
- TempFilePath property
- IgnoreDuplicateKeys property
- Transaction property
- KeepIdentity property
- ConnectionString property
- FireTriggers property
- Execute method
- XML Bulk Load [SQLXML], object model
ms.assetid: a9efbbde-ed2b-4929-acc1-261acaaed19d
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a71a5c756953c6b70e51422b5c1032b117eb7785
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75246711"
---
# <a name="sql-server-xml-bulk-load-object-model-sqlxml-40"></a>SQL Server XML Bulk Load-Objektmodell (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Das Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML Bulk Load-Objektmodell besteht aus dem SQLXMLBulkLoad-Objekt. Dieses Objekt unterstützt die folgenden Methoden und Eigenschaften.  
  
## <a name="methods"></a>Methoden  
 Ausführen  
 Lädt die Daten mithilfe der als Parameter bereitgestellten Schema- und Datendatei (oder Datenstrom) in einem Massenvorgang.  
  
## <a name="properties"></a>Eigenschaften  
 Bulkload  
 Gibt an, ob ein Massenladen durchgeführt werden soll. Diese Eigenschaft ist nützlich, wenn Sie nur die Schemas generieren möchten (Weitere Informationen finden Sie unter den folgenden Eigenschaften: SchemaGen, SGDropTables und SGUseID) und kein Massen laden ausführen. Hierbei handelt es sich um eine boolesche Eigenschaft. Wenn die Eigenschaft auf TRUE festgelegt ist, wird das XML-Massenladen ausgeführt. Wenn sie auf FALSE festgelegt ist, wird das XML-Massenladen nicht ausgeführt.  
  
 Der Standardwert ist TRUE.  
  
 CheckConstraints  
 Gibt an, ob die Einschränkungen (etwa Einschränkungen aufgrund der Primär-/Fremdschlüsselbeziehung zwischen Spalten), die für die jeweilige Spalte angegeben sind, überprüft werden sollen, sobald beim XML-Massenladen Daten in die Spalten eingefügt werden. Hierbei handelt es sich um eine boolesche Eigenschaft.  
  
 Wenn die Eigenschaft auf TRUE gesetzt ist, werden mit XML-Massenladen die Einschränkungen für jeden eingefügten Wert überprüft (was bedeutet, dass jede verletzte Einschränkung zu einem Fehler führt).  
  
> [!NOTE]  
>  Um diese Eigenschaft als false zu belassen, müssen Sie über **ALTER TABLE** -Berechtigungen für Ziel Tabellen verfügen. Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL-&#41;](../../../t-sql/statements/alter-table-transact-sql.md).  
  
 Der Standardwert ist FALSE. Wenn sie auf FALSE gesetzt ist, werden die Einschränkungen während des Einfügens ignoriert. In der aktuellen Implementierung müssen Sie die Tabellen in der Reihenfolge der Primär-/Fremdschlüsselbeziehungen im Zuordnungsschema definieren. Eine Tabelle mit einem Primärschlüssel muss also vor der entsprechenden Tabelle mit dem Fremdschlüssel definiert werden; anderenfalls schlägt das XML-Massenladen fehl.  
  
 Hinweis: Wenn ID-Propagierung erfolgt, kommt diese Option nicht zur Anwendung, und Einschränkungen werden weiter überprüft. Dies ist der Fall, wenn `KeepIdentity=False` gilt und eine Beziehung definiert ist, in der es sich beim übergeordneten Element um ein Identitätsfeld handelt und der Wert bei der Generierung an das untergeordnete Element übertragen wird.  
  
 ConnectionCommand  
 Identifiziert ein vorhandenes Verbindungs Objekt (z. b. das ADO-oder ICommand-Befehls Objekt), das von XML-Massen Laden verwendet werden soll. Sie können die ConnectionCommand-Eigenschaft verwenden, anstatt eine Verbindungs Zeichenfolge mit der ConnectionString-Eigenschaft anzugeben. Die Transaction-Eigenschaft muss auf true festgelegt werden, wenn Sie ConnectionCommand verwenden.  
  
 Wenn Sie die Eigenschaften ConnectionString und ConnectionCommand verwenden, verwendet XML-Massen laden die zuletzt angegebene Eigenschaft.  
  
 Der Standardwert ist NULL.  
  
 ConnectionString  
 Kennzeichnet die OLE DB-Verbindungszeichenfolge mit den Informationen, die notwendig sind, um eine Verbindung zu einer Instanz der Datenbank herzustellen. Wenn Sie die Eigenschaften ConnectionString und ConnectionCommand verwenden, verwendet XML-Massen laden die zuletzt angegebene Eigenschaft.  
  
 Der Standardwert ist NULL.  
  
 ErrorLogFile  
 Gibt den Dateinamen an, in dem Fehler und Meldungen protokolliert werden. Der Standardwert ist eine leere Zeichenfolge; in diesem Fall erfolgt keine Protokollierung.  
  
 FireTriggers  
 Gibt an, ob auf Zieltabellen definierte Trigger während des Massenladevorgangs ausgelöst werden sollen. Der Standardwert lautet FALSE.  
  
 Wenn dieser Wert auf TRUE gesetzt ist, werden Trigger während der Einfügevorgänge normal ausgelöst.  
  
> [!NOTE]  
>  Um diese Eigenschaft als false zu belassen, müssen Sie über **ALTER TABLE** -Berechtigungen für Ziel Tabellen verfügen. Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL-&#41;](../../../t-sql/statements/alter-table-transact-sql.md).  
  
 Hinweis: Wenn ID-Propagierung erfolgt, kommt diese Option nicht zur Anwendung, und Trigger werden weiter ausgelöst. Dies ist der Fall, wenn `KeepIdentity=False` gilt und eine Beziehung definiert ist, in der es sich beim übergeordneten Element um ein Identitätsfeld handelt und der Wert bei der Generierung an das untergeordnete Element übertragen wird.  
  
 ForceTableLock  
 Gibt an, ob die Tabellen, in die beim XML-Massenladen Daten kopiert werden, während des Massenladens gesperrt sein sollen. Hierbei handelt es sich um eine boolesche Eigenschaft. Wenn die Eigenschaft auf TRUE gesetzt ist, werden während des Massenladens Tabellensperren eingerichtet. Wenn der Wert auf FALSE gesetzt ist, wird immer dann eine Tabellensperre eingerichtet, sobald ein Datensatz in eine Tabelle eingefügt wird.  
  
 Der Standardwert ist FALSE.  
  
 Ignoreduplicatekeys  
 Gibt an, was geschieht, wenn versucht wird, doppelte Werte in einer Schlüsselspalte einzufügen. Wenn diese Eigenschaft auf TRUE gesetzt ist und versucht wird, einen Datensatz mit doppelten Werten in einer Schlüsselspalte einzufügen, fügt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] diesen Datensatz nicht ein. Stattdessen wird der nachfolgende Datensatz eingefügt; dadurch schlägt der Massenladevorgang nicht fehl. Wenn diese Eigenschaft auf FALSE gesetzt ist und versucht wird, doppelte Werte in einer Schlüsselspalte einzufügen, schlägt der Massenladevorgang fehl.  
  
 Wenn die IgnoreDuplicateKeys-Eigenschaft auf true festgelegt ist, wird für jeden Datensatz, der in die Tabelle eingefügt wird, eine COMMIT-Anweisung ausgegeben. Dies verlangsamt die Leistung. Die-Eigenschaft kann nur auf "true" festgelegt werden, wenn die Transaction-Eigenschaft auf "false" festgelegt ist, da das Transaktionsverhalten mithilfe von Dateien implementiert wird.  
  
 Der Standardwert ist FALSE.  
  
 KeepIdentity  
 Gibt an, wie mit den Werten für eine Identitätsspalte in der Quelldatei verfahren wird. Hierbei handelt es sich um eine boolesche Eigenschaft. Wenn die Eigenschaft auf TRUE gesetzt ist, werden der Identitätsspalte die in der Quelldatei angegebenen Werte zugewiesen. Wenn die Eigenschaft auf FALSE gesetzt ist, werden die in der Quelldatei für die Identitätsspalte angegebenen Werte beim Massenladen ignoriert. In diesem Fall weist [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] der Identitätsspalte einen Wert zu.  
  
 Wenn der Massenladevorgang eine Spalte betrifft, bei der es sich um einen Fremdschlüssel handelt, der auf eine Identitätsspalte verweist, in der wiederum [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-generierte Werte gespeichert sind, werden beim Massenladen diese Identitätswerte entsprechend in die Fremdschlüsselspalte propagiert.  
  
 Der Wert dieser Eigenschaft gilt für alle vom Massenladen betroffene Spalten. Der Standardwert ist TRUE.  
  
> [!NOTE]  
>  Um diese Eigenschaft als true zu belassen, müssen Sie über **ALTER TABLE** -Berechtigungen für Ziel Tabellen verfügen. Andernfalls muss sie auf FALSE gesetzt werden. Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL-&#41;](../../../t-sql/statements/alter-table-transact-sql.md).  
  
 KeepNulls  
 Gibt an, welcher Wert für eine Spalte verwendet wird, in deren XML-Dokument das entsprechende Attribut oder untergeordnete Element fehlt. Hierbei handelt es sich um eine boolesche Eigenschaft. Wenn die Eigenschaft auf TRUE gesetzt ist, wird der Spalte der Wert Null zugewiesen. Es wird nicht der gegebenenfalls auf dem Server gesetzte Standardwert der Spalte zugewiesen. Der Wert dieser Eigenschaft gilt für alle vom Massenladen betroffene Spalten.  
  
 Der Standardwert ist FALSE.  
  
 "SchemaGen"  
 Gibt an, ob die erforderlichen Tabellen vor dem Ausführen eines Massenladevorgangs erstellt werden sollen. Hierbei handelt es sich um eine boolesche Eigenschaft. Wenn diese Eigenschaft auf TRUE gesetzt ist, werden die im Zuordnungsschema angegebenen Tabellen erstellt (die Datenbank muss vorhanden sein). Wenn eine oder mehrere Tabellen bereits in der Datenbank vorhanden sind, bestimmt die SGDropTables-Eigenschaft, ob diese bereits vorhandenen Tabellen gelöscht und neu erstellt werden sollen.  
  
 Der Standardwert für die SchemaGen-Eigenschaft ist false. SchemaGen erstellt keine PRIMARY KEY-Einschränkungen für die neu erstellten Tabellen. SchemaGen erstellt jedoch Foreign Key-Einschränkungen in der Datenbank, wenn entsprechende **SQL: Relationship** **-und SQL: key-fields-** Anmerkungen im Zuordnungs Schema gefunden werden können und das Schlüsselfeld aus einer einzelnen Spalte besteht.  
  
 Beachten Sie Folgendes: Wenn Sie die SchemaGen-Eigenschaft auf true festlegen, führt XML-Massen laden Folgendes aus:  
  
-   Erstellt die notwendigen Tabellen aus dem Element und den Attributnamen. Aus diesem Grund ist es wichtig, dass Sie im Schema für die Element- und Attributnamen keine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-reservierten Wörter verwenden.  
  
-   Gibt Überlauf Daten für jede Spalte zurück, die mit dem [SQL: overflow-field](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md) im [XML-Datentyp](../../../t-sql/xml/xml-transact-sql.md) Format angegeben wird.  
  
 SGDropTables  
 Gibt an, ob vorhandene Tabellen gelöscht und neu erstellt werden sollen. Sie verwenden diese Eigenschaft, wenn die SchemaGen-Eigenschaft auf true festgelegt ist. Wenn SGDropTables den Wert false hat, werden die vorhandenen Tabellen beibehalten. Wenn diese Eigenschaft auf TRUE gesetzt ist, werden die vorhandenen Tabellen gelöscht und neu erstellt.  
  
 Der Standardwert ist FALSE.  
  
 SGUseID  
 Gibt an, ob das Attribut im Zuordnungsschema, das als **ID** -Typ identifiziert wird, beim Erstellen einer PRIMARY KEY-Einschränkung beim Erstellen der Tabelle verwendet werden kann. Verwenden Sie diese Eigenschaft, wenn die SchemaGen-Eigenschaft auf true festgelegt ist. Wenn SGUseID den Wert true aufweist, verwendet das SchemaGen-Hilfsprogramm ein Attribut, für das **dt: Type = "ID"** als Primärschlüssel Spalte angegeben ist, und fügt beim Erstellen der Tabelle die entsprechende PRIMARY KEY-Einschränkung hinzu.  
  
 Der Standardwert ist FALSE.  
  
 TempFilePath  
 Gibt den Dateipfad an, wo beim XML-Massenladen die temporären Dateien für ein transaktives Massenladen erstellt werden. (Diese Eigenschaft ist nur nützlich, wenn die Transaction-Eigenschaft auf true festgelegt ist.) Sie müssen sicherstellen, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dass das für XML-Massen laden verwendete Konto Zugriff auf diesen Pfad hat. Wenn diese Eigenschaft nicht gesetzt ist, werden die Temporärdateien in dem in der Umgebungsvariable TEMP angegebenen Verzeichnis gespeichert.  
  
 Transaktion  
 Gibt an, ob das Massenladen als Transaktion erfolgen soll. Bei einem Fehlschlagen des Massenspeicherns ist ein Rollback gewährleistet. Hierbei handelt es sich um eine boolesche Eigenschaft. Wenn die Eigenschaft auf TRUE gesetzt ist, erfolgt das Massenladen in einem Transaktionskontext. Die TempFilePath-Eigenschaft ist nur nützlich, wenn Transaction auf true festgelegt ist.  
  
> [!NOTE]  
>  Wenn Sie Binärdaten (z. b. die "bin. Hex"-, "bin. base64"-XML- [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datentypen in die binären Datentypen "Image") laden, muss die Transaktions Eigenschaft auf "false" festgelegt werden.  
  
 Der Standardwert ist FALSE.  
  
 XMLFragment  
 Gibt an, ob es sich bei den Quelldaten um ein XML-Fragment handelt. Ein XML-Fragment ist ein XML-Dokument, dem das Einzelelement der obersten Ebene (Stammelement) fehlt. Hierbei handelt es sich um eine boolesche Eigenschaft. Diese Eigenschaft muss auf TRUE gesetzt sein, wenn die Quelldatei aus einem XML-Fragment besteht.  
  
 Der Standardwert ist FALSE.  
  
  
