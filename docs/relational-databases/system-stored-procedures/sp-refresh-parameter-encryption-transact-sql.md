---
description: sp_refresh_parameter_encryption (Transact-SQL)
title: sp_refresh_parameter_encryption (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sp_refresh_parameter_encryption
- sp_refresh_parameter_encryption_TSQL
- sys.sp_refresh_parameter_encryption
- sys.sp_refresh_parameter_encryption_TSQL
helpviewer_keywords:
- sp_refresh_parameter_encryption
- Always Encrypted, sp_refresh_parameter_encryption
ms.assetid: 00b44baf-fcf0-4095-aabe-49fa87e77316
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 64ca46d46ac648fdebeb8c028df312472e4f5d58
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88645063"
---
# <a name="sp_refresh_parameter_encryption-transact-sql"></a>sp_refresh_parameter_encryption (Transact-SQL)

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

Aktualisiert die Always Encrypted Metadaten für die Parameter der angegebenen nicht Schema gebundenen gespeicherten Prozedur, der benutzerdefinierten Funktion, der Sicht, des DML-Triggers, des DDL-Triggers auf Datenbankebene oder des DDL-Triggers auf Serverebene in der aktuellen Datenbank. 

 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sys.sp_refresh_parameter_encryption [ @name = ] 'module_name' 
    [ , [ @namespace = ] '<class>' ]
[ ; ]

<class> ::=
{ DATABASE_DDL_TRIGGER | SERVER_DDL_TRIGGER }
```

## <a name="arguments"></a>Argumente

`[ @name = ] 'module_name'` Der Name der gespeicherten Prozedur, der benutzerdefinierten Funktion, der Sicht, des DML-Triggers, des DDL-Triggers auf Datenbankebene oder des DDL-Triggers auf Serverebene. *module_name* kann keine gespeicherte Prozedur Common Language Runtime (CLR) oder eine CLR-Funktion sein. *module_name* kann nicht Schema gebunden werden. *module_name* ist vom Typ `nvarchar` und hat keinen Standardwert. *module_name* kann ein mehrteilige Bezeichner sein, kann jedoch nur auf Objekte in der aktuellen Datenbank verweisen.

`[ @namespace = ] ' < class > '` Die Klasse des angegebenen Moduls. Wenn *module_name* ein DDL-auslöst ist, `<class>` ist erforderlich. `<class>` ist `nvarchar(20)`. Gültige Eingaben sind `DATABASE_DDL_TRIGGER` und `SERVER_DDL_TRIGGER` .    

## <a name="return-code-values"></a>Rückgabecodewerte  

0 (Erfolg) oder eine Zahl ungleich Null (Fehler)


## <a name="remarks"></a>Hinweise

Die Verschlüsselungs Metadaten für die Parameter eines Moduls können veraltet sein, wenn:   
* Die Verschlüsselungs Eigenschaften einer Spalte in einer Tabelle, auf die das Modul verweist, wurden aktualisiert. Beispielsweise wurde eine Spalte gelöscht, und es wurde eine neue Spalte mit demselben Namen, aber ein anderer Verschlüsselungstyp, ein verschlüsselter Verschlüsselungsschlüssel oder ein Verschlüsselungsalgorithmus hinzugefügt.  
* Das Modul verweist auf ein anderes Modul mit veralteten Parameter Verschlüsselungs Metadaten.  

Wenn die Verschlüsselungs Eigenschaften einer Tabelle geändert werden, `sp_refresh_parameter_encryption` sollte für alle Module, die direkt oder indirekt auf die Tabelle verweisen, ausgeführt werden. Diese gespeicherte Prozedur kann für diese Module in beliebiger Reihenfolge aufgerufen werden, ohne dass der Benutzer zuerst das innere Modul aktualisieren muss, bevor es zu den Aufrufern wechselt.

`sp_refresh_parameter_encryption` wirkt sich nicht auf Berechtigungen, erweiterte Eigenschaften oder Optionen aus, die `SET` dem-Objekt zugeordnet sind. 

Um einen DDL-Trigger auf Serverebene zu aktualisieren, führen Sie diese gespeicherte Prozedur aus dem Kontext einer beliebigen Datenbank aus.

> [!NOTE]
>  Alle Signaturen, die dem-Objekt zugeordnet sind, werden gelöscht, wenn Sie Ausführen `sp_refresh_parameter_encryption` .

## <a name="permissions"></a>Berechtigungen

Erfordert `ALTER` die-Berechtigung für das Modul und die- `REFERENCES` Berechtigung für alle benutzerdefinierten CLR-Typen und XML-Schema Auflistungen, auf die vom-Objekt verwiesen wird.   

Wenn das angegebene Modul ein DDL-Auslösers auf Datenbankebene ist, wird `ALTER ANY DATABASE DDL TRIGGER` in der aktuellen Datenbank die-Berechtigung benötigt.    

Wenn das angegebene Modul ein DDL-Auslösers auf Serverebene ist, ist die- `CONTROL SERVER` Berechtigung erforderlich.

Für Module, die mit der- `EXECUTE AS` Klausel definiert sind, `IMPERSONATE` ist für den angegebenen Prinzipal eine Berechtigung erforderlich. Beim Aktualisieren eines Objekts ändert sich der Prinzipal in der Regel nicht `EXECUTE AS` , es sei denn, das Modul wurde mit definiert, `EXECUTE AS USER` und der Benutzername des Prinzipals wird nun zu einem anderen Benutzer aufgelöst als zum Zeitpunkt der Erstellung des Moduls.
 
## <a name="examples"></a>Beispiele

Im folgenden Beispiel werden eine Tabelle und eine Prozedur erstellt, die auf die-Tabelle verweist, always Encrypted konfiguriert und dann das Ändern der Tabelle und das Ausführen der `sp_refresh_parameter_encryption` Prozedur veranschaulicht.  

Erstellen Sie zuerst die anfängliche Tabelle und eine gespeicherte Prozedur, die auf die Tabelle verweist.
```sql
CREATE TABLE [Patients]([PatientID] [int] IDENTITY(1,1) NOT NULL,
    [SSN] [char](11), 
    [FirstName] [nvarchar](50) NULL,
    [LastName] [nvarchar](50) NOT NULL,
    [MiddleName] [nvarchar](50) NULL,
    [StreetAddress] [nvarchar](50) NOT NULL,
    [City] [nvarchar](50) NOT NULL,
    [ZipCode] [char](5) NOT NULL,
    [State] [char](2) NOT NULL,
    [BirthDate] [date] NOT NULL,
 CONSTRAINT [PK_Patients] PRIMARY KEY CLUSTERED 
(
    [PatientID] ASC
) WITH 
    (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, 
     IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, 
     ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY];
GO

CREATE PROCEDURE [find_patient] @SSN [char](11)
AS
BEGIN
    SELECT * FROM [Patients] WHERE SSN=@SSN
END;
GO
```

Richten Sie dann Always Encrypted Schlüssel ein.
```sql
CREATE COLUMN MASTER KEY [CMK1]
WITH
(
       KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',
    KEY_PATH = N'CurrentUser/my/A66BB0F6DD70BDFF02B62D0F87E340288E6F9305'
);
GO

CREATE COLUMN ENCRYPTION KEY [CEK1]
WITH VALUES
(
       COLUMN_MASTER_KEY = [CMK1],
    ALGORITHM = 'RSA_OAEP',
    ENCRYPTED_VALUE = 
       0x016E000001630075007200720065006E00740075007300650072002F006D0079002F006100360036006200620030006600360064006400370030006200640066006600300032006200360032006400300066003800370065003300340030003200380038006500360066003900330030003500CA0D0CEC74ECADD1804CF99137B4BD06BBAB15D7EA74E0C249A779C7768A5B659E0125D24FF827F5EA8CA517A8E197ECA1353BA814C2B0B2E6C8AB36E3AE6A1E972D69C3C573A963ADAB6686CF5D24F95FE43140C4F9AF48FBA7DF2D053F3B4A1F5693A1F905440F8015BDB43AF8A04BE4E045B89876A0097E5FBC4E6A3B9C3C0D278C540E46C53938B8C957B689C4DC095821C465C73117CBA95B758232F9E5B2FCC7950B8CA00AFE374DE42847E3FBC2FDD277035A2DEF529F4B735C20D980073B4965B4542A34723276A1646998FC6E1C40A3FDB6ABCA98EE2B447F114D2AC7FF8C7D51657550EC5C2BABFFE8429B851272086DCED94332CF18FA854C1D545A28B1EF4BE64F8E035175C1650F6FC5C4702ACF99850A4542B3747EAEC0CC726E091B36CE24392D801ECAA684DE344FECE05812D12CD72254A014D42D0EABDA41C89FC4F545E88B4B8781E5FAF40D7199D4842D2BFE904D209728ED4F527CBC169E2904F6E711FF81A8F4C25382A2E778DD2A58552ED031AFFDA9D9D891D98AD82155F93C58202FC24A77F415D4F8EF22419D62E188AC609330CCBD97CEE1AEF8A18B01958833604707FDF03B2B386487CC679D7E352D0B69F9FB002E51BCD814D077E82A09C14E9892C1F8E0C559CFD5FA841CEF647DAB03C8191DC46B772E94D579D8C80FE93C3827C9F0AE04D5325BC73111E07EEEDBE67F1E2A73580085
);
GO
```


Zum Schluss ersetzen wir die Spalte "SSN" durch die verschlüsselte Spalte und führt dann das Verfahren aus, `sp_refresh_parameter_encryption` um die Always Encrypted Komponenten zu aktualisieren.
```sql
ALTER TABLE [Patients] DROP COLUMN [SSN];
GO

ALTER TABLE [Patients] 
    ADD [SSN] [char](11) COLLATE Latin1_General_BIN2 
    ENCRYPTED WITH 
        (COLUMN_ENCRYPTION_KEY = [CEK1], 
        ENCRYPTION_TYPE = Deterministic, 
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') 
    NOT NULL;
GO

EXEC sp_refresh_parameter_encryption [find_patient];
GO
```

## <a name="see-also"></a>Weitere Informationen 

[Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
[Always Encrypted Wizard](../../relational-databases/security/encryption/always-encrypted-wizard.md)   

