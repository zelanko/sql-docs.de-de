---
title: Importieren von Daten nach SQL Server mithilfe von BULK INSERT oder OPENROWSET(BULK...)
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- BULK INSERT statement, importing data from a remote data file
- bulk importing [SQL Server], methods
- bulk exporting [SQL Server], methods
- OPENROWSET function, BULK INSERT
- bulk importing [SQL Server], security
- bulk rowset providers [SQL Server]
- bulk exporting [SQL Server], BULK INSERT statement
- remote data access [SQL Server], bulk importing
- bulk importing [SQL Server], BULK INSERT statement
- Transact-SQL bulk export/import operations
ms.assetid: 18a64236-0285-46ea-8929-6ee9bcc020b9
author: markingmyname
ms.author: maghan
manager: jroth
ms.custom: seo-lt-2019
ms.date: 09/25/2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: deaaa783f465c5cfecb940df4b9dd56e10590bc5
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056395"
---
# <a name="use-bulk-insert-or-openrowsetbulk-to-import-data-to-sql-server"></a>Importieren von Daten nach SQL Server mithilfe von BULK INSERT oder OPENROWSET(BULK...)

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

In diesem Artikel erhalten Sie einen Überblick über die Verwendung der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung BULK INSERT und der Anweisung INSERT...SELECT * FROM OPENROWSET(BULK...), mit denen ein Massenimport von Daten aus einer Datendatei in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle oder eine Tabelle in Azure SQL-Datenbank ermöglicht wird. In diesem Artikel werden zudem Sicherheitsaspekte beim Verwenden von BULK INSERT und OPENROWSET(BULK…) sowie das Verwenden dieser Methoden für den Massenimport aus einer Remotedatenquelle beschrieben.

> [!NOTE]
> Für die Verwendung von BULK INSERT oder OPENROWSET(BULK…) ist es wichtig, nachvollziehen zu können, wie Identitätswechsel von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Versionen verarbeitet werden. Weitere Informationen finden Sie unter "Sicherheitsüberlegungen" weiter unten in diesem Thema.

## <a name="bulk-insert-statement"></a>BULK INSERT-Anweisung

BULK INSERT lädt Daten aus einer Datendatei in eine Tabelle. Die Funktionalität ähnelt derjenigen der Option **in** des **bcp** -Befehls. Die Datendatei wird jedoch vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozess gelesen. Eine Beschreibung der BULK INSERT-Syntax finden Sie unter [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md).

## <a name="bulk-insert-examples"></a>BULK INSERT-Beispiele

- [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)
- [Beispiele für den Massenimport und -export von XML-Dokumenten &#40;SQL Server&#41;](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)
- [Beibehalten von Identitätswerten beim Massenimport von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)
- [Beibehalten von NULL-Werten oder Verwenden von Standardwerten während des Massenimports &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)
- [Angeben von Feld- und Zeilenabschlusszeichen &#40;SQL Server&#41;](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)
- [Massenimport von Daten mithilfe einer Formatdatei &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)
- [Verwenden des Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)
- [Verwenden des nativen Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)
- [Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)
- [Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)
- [Überspringen einer Tabellenspalte mithilfe einer Formatdatei &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)
- [Verwenden einer Formatdatei zum Zuordnen von Tabellenspalten zu Datendateifeldern &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)

## <a name="openrowsetbulk-function"></a>OPENROWSET(BULK…) Funktion

Auf den OPENROWSET-Massenrowsetanbieter wird durch Aufrufen der OPENROWSET-Funktion und Angeben der BULK-Option zugegriffen. Mithilfe der OPENROWSET(BULK…)-Funktion können Sie auf Remotedaten zugreifen, indem Sie über einen OLE DB-Anbieter eine Verbindung mit einer Remotedatenquelle (z. B. einer Datendatei) herstellen.

Für den Massenimport von Daten wird OPENROWSET(BULK…) aus der SELECT…FROM-Klausel einer INSERT-Anweisung aufgerufen. Die grundlegende Syntax für den Massenimport von Daten lautet:

INSERT ... SELECT * FROM OPENROWSET(BULK...)

Wenn OPENROWSET(BULK...) in einer INSERT-Anweisung verwendet wird, werden damit auch Tabellenhinweise unterstützt. Zusätzlich zu den regulären Tabellenhinweisen wie TABLOCK kann die BULK-Klausel die folgenden spezialisierten Tabellenhinweise akzeptieren: IGNORE_CONSTRAINTS (ignoriert nur die CHECK-Einschränkungen), IGNORE_TRIGGERS, KEEPDEFAULTS und KEEPIDENTITY. Weitere Informationen finden Sie unter [Tabellenhinweise &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md).

Informationen zu den zusätzlichen Verwendungsmöglichkeiten der Option BULK finden Sie unter [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md).

## <a name="insertselect--from-openrowsetbulk-statements---examples"></a>INSERT...SELECT * FROM OPENROWSET(BULK...)-Anweisungen – Beispiele:

- [Beispiele für den Massenimport und -export von XML-Dokumenten &#40;SQL Server&#41;](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)
- [Beibehalten von Identitätswerten beim Massenimport von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)
- [Beibehalten von NULL-Werten oder Verwenden von Standardwerten während des Massenimports &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)
- [Massenimport von Daten mithilfe einer Formatdatei &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)
- [Verwenden des Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)
- [Überspringen einer Tabellenspalte mithilfe einer Formatdatei &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)
- [Auslassen eines Datenfelds mithilfe einer Formatdatei &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-data-field-sql-server.md)
- [Verwenden einer Formatdatei zum Zuordnen von Tabellenspalten zu Datendateifeldern &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)

## <a name="security-considerations"></a>Überlegungen zur Sicherheit

Wenn ein Benutzer einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldenamen verwendet, wird das Sicherheitsprofil des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozesskontos verwendet. Ein Anmeldename, für den die SQL Server-Authentifizierung verwendet wird, kann nicht außerhalb der Datenbank-Engine authentifiziert werden. Wenn ein BULK INSERT-Befehl durch einen Anmeldenamen initiiert wird, der die SQL Server-Authentifizierung verwendet, wird die Datenverbindung folglich mithilfe des Sicherheitskontexts des SQL Server-Prozesskontos (dem vom SQL Server-Datenbank-Engine-Dienst verwendeten Konto) hergestellt. 

Um die Quelldaten lesen zu können, müssen Sie dem von der SQL Server-Datenbank-Engine verwendeten Konto Zugriff auf die Quelldaten gewähren. Wenn sich hingegen ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Benutzer mithilfe der Windows-Authentifizierung anmeldet, können von diesem Benutzer nur die Dateien gelesen werden, auf die über das Benutzerkonto zugegriffen werden kann. Das Sicherheitsprofil des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozesses wird dabei nicht berücksichtigt.

Angenommen, ein Benutzer hat sich mithilfe der Windows-Authentifizierung an einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angemeldet. Damit der Benutzer zum Importieren von Daten aus einer Datendatei in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle BULK INSERT oder OPENROWSET verwenden kann, muss das Konto über Lesezugriff für die Datendatei verfügen. Durch den Zugriff auf die Datendatei kann der Benutzer Daten aus der Datei in eine Tabelle importieren, selbst wenn für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozess keine Berechtigung zum Zugreifen auf die Datei verfügbar ist. Der Benutzer muss dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozess keine Dateizugriffsberechtigung erteilen.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows können so konfiguriert werden, dass von einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz eine Verbindung mit einer anderen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz hergestellt wird, indem die Anmeldeinformationen eines authentifizierten Windows-Benutzers weitergeleitet werden. Diese Anordnung wird als *Identitätswechsel* oder *Delegierung*bezeichnet. Es ist wichtig zu wissen, wie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Version die Sicherheit für den Benutzeridentitätswechsel verarbeitet wird, wenn Sie BULK INSERT oder OPENROWSET verwenden. Durch einen Benutzeridentitätswechsel kann sich die Datendatei auf einem anderen Computer befinden als der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozess oder der Benutzer selbst. Wenn beispielsweise ein Benutzer auf **Computer_A** Zugriff auf eine Datendatei hat, die sich auf **Computer_B**befindet, und die Delegierung der Anmeldeinformationen entsprechend festgelegt ist, kann der Benutzer eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz herstellen, die auf **Computer_C**ausgeführt wird, auf die Datendatei auf **Computer_B**zugreifen und einen Massenimport von Daten aus der Datei in eine Tabelle auf **Computer_C**ausführen.

## <a name="bulk-importing-to-sql-server-from-a-remote-data-file"></a>Massenimport in SQL Server aus einer Remotedatendatei

Die Datendatei muss zwischen zwei Computern freigegeben sein, um mithilfe von BULK INSERT oder INSERT...SELECT \* FROM OPENROWSET(BULK...) den Massenimport von Daten von einem Computer zum anderen auszuführen. Verwenden Sie zum Angeben einer freigegebenen Datendatei den UNC-Namen (Universal Naming Convention) im allgemeinen Format **\\\\** _Servername_ **\\** _Freigabename_ **\\** _Pfad_ **\\** _Dateiname_. Zudem muss das Konto, mit dem auf die Datendatei zugegriffen wird, über die Berechtigungen verfügen, die zum Lesen der Datei auf dem Remotedatenträger erforderlich sind.

Beispielsweise wird mithilfe der folgenden `BULK INSERT` -Anweisung ein Massenimport von Daten aus der Datendatei `SalesOrderDetail` in die `AdventureWorks` -Tabelle der `newdata.txt`-Datenbank ausgeführt. Diese Datendatei befindet sich im freigegebenen Ordner `\dailyorders` auf dem `salesforce`-Netzwerkfreigabeverzeichnis des `computer2`-Systems.

```sql
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail
   FROM '\\computer2\salesforce\dailyorders\neworders.txt';
```

> [!NOTE]
> Diese Einschränkung gilt nicht für das Hilfsprogramm **bcp**, da die Datei vom Client unabhängig von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gelesen wird.

## <a name="bulk-importing-from-azure-blob-storage"></a>Massenimport aus Azure Blob Storage

Wenn Sie Daten aus Azure Blob Storage importieren, die nicht öffentlich sind (anonymer Zugriff), erstellen Sie eine [DATABASE SCOPED CREDENTIAL](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)-Anweisung, die auf einem SAS-Schlüssel basiert, der mit einer [MASTER KEY](../../t-sql/statements/create-master-key-transact-sql.md)-Anweisung verschlüsselt ist. Erstellen Sie anschließend eine [externe Datenbankquelle](../../t-sql/statements/create-external-data-source-transact-sql.md) für die Verwendung in Ihrem BULK INSERT-Befehl.

### <a name="using-bulk-insert"></a>Verwenden von BULK INSERT

Das folgende Beispiel zeigt, wie Daten mithilfe des BULK INSERT-Befehls aus einer CSV-Datei in einen Speicherort von Azure Blob Storage geladen werden, für den Sie einen SAS-Schlüssel erstellt haben. Der Speicherort von Azure Blob Storage wird als externe Datenquelle konfiguriert. Hierfür sind datenbankweit gültige Anmeldeinformationen mit einer Shared Access Signature (SAS) erforderlich, die mit einem Hauptschlüssel in der Benutzerdatenbank verschlüsselt ist.

```sql
--> Optional - a MASTER KEY is not requred if a DATABASE SCOPED CREDENTIAL is not required because the blob is configured for public (anonymous) access!
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'YourStrongPassword1';
GO
--> Optional - a DATABASE SCOPED CREDENTIAL is not required because the blob is configured for public (anonymous) access!
CREATE DATABASE SCOPED CREDENTIAL MyAzureBlobStorageCredential
 WITH IDENTITY = 'SHARED ACCESS SIGNATURE',
 SECRET = '******srt=sco&sp=rwac&se=2017-02-01T00:55:34Z&st=2016-12-29T16:55:34Z***************';

 -- NOTE: Make sure that you don't have a leading ? in SAS token, and
 -- that you have at least read permission on the object that should be loaded srt=o&sp=r, and
 -- that expiration period is valid (all dates are in UTC time)

CREATE EXTERNAL DATA SOURCE MyAzureBlobStorage
WITH ( TYPE = BLOB_STORAGE,
          LOCATION = 'https://****************.blob.core.windows.net/invoices'
          , CREDENTIAL= MyAzureBlobStorageCredential --> CREDENTIAL is not required if a blob is configured for public (anonymous) access!
);

BULK INSERT Sales.Invoices
FROM 'inv-2017-12-08.csv'
WITH (DATA_SOURCE = 'MyAzureBlobStorage');
```

> [!IMPORTANT]
> Das Lesen aus Windows-Dateien wird von Azure SQL-Datenbank nicht unterstützt.

### <a name="using-openrowset"></a>Verwenden von OPENROWSET

Das folgende Beispiel zeigt, wie Daten mithilfe des OPENROWSET-Befehls aus einer CSV-Datei in einen Speicherort von Azure Blob Storage geladen werden, für den Sie einen SAS-Schlüssel erstellt haben. Der Speicherort von Azure Blob Storage wird als externe Datenquelle konfiguriert. Hierfür sind datenbankweit gültige Anmeldeinformationen mit einer Shared Access Signature (SAS) erforderlich, die mit einem Hauptschlüssel in der Benutzerdatenbank verschlüsselt ist.

```sql
--> Optional - a MASTER KEY is not requred if a DATABASE SCOPED CREDENTIAL is not required because the blob is configured for public (anonymous) access!
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'YourStrongPassword1';
GO
--> Optional - a DATABASE SCOPED CREDENTIAL is not required because the blob is configured for public (anonymous) access!
CREATE DATABASE SCOPED CREDENTIAL MyAzureBlobStorageCredential
 WITH IDENTITY = 'SHARED ACCESS SIGNATURE',
 SECRET = '******srt=sco&sp=rwac&se=2017-02-01T00:55:34Z&st=2016-12-29T16:55:34Z***************';

 -- NOTE: Make sure that you don't have a leading ? in SAS token, and
 -- that you have at least read permission on the object that should be loaded srt=o&sp=r, and
 -- that expiration period is valid (all dates are in UTC time)

CREATE EXTERNAL DATA SOURCE MyAzureBlobStorage
WITH ( TYPE = BLOB_STORAGE,
          LOCATION = 'https://****************.blob.core.windows.net/invoices'
          , CREDENTIAL= MyAzureBlobStorageCredential --> CREDENTIAL is not required if a blob is configured for public (anonymous) access!
);

INSERT INTO achievements with (TABLOCK) (id, description)
SELECT * FROM OPENROWSET(
   BULK  'csv/achievements.csv',
   DATA_SOURCE = 'MyAzureBlobStorage',
   FORMAT ='CSV',
   FORMATFILE='csv/achievements-c.xml',
   FORMATFILE_DATA_SOURCE = 'MyAzureBlobStorage'
    ) AS DataFile;
```

> [!IMPORTANT]
> Das Lesen aus Windows-Dateien wird von Azure SQL-Datenbank nicht unterstützt.

## <a name="see-also"></a>Siehe auch

- [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)
- [SELECT-Klausel &#40;Transact-SQL&#41;](../../t-sql/queries/select-clause-transact-sql.md)
- [Massenimport und -export von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)
- [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)
- [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)
- [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)
- [bcp (Hilfsprogramm)](../../tools/bcp-utility.md)
- [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)  
