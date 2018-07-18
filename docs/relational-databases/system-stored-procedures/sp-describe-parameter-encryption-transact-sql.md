---
title: "\"sp_describe_parameter_encryption\" (Transact-SQL) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 07/27/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_describe_parameter_encryption
- sp_describe_parameter_encryption_TSQL
- sys.sp_describe_parameter_encryption
- sys.sp_describe_parameter_encryption_TSQL
helpviewer_keywords:
- sp_describe_parameter_encryption
ms.assetid: 706ed441-2881-4934-8d5e-fb357ee067ce
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 810f73e16599f153c604c605e33ad1b6f282811b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37974495"
---
# <a name="spdescribeparameterencryption-transact-sql"></a>"sp_describe_parameter_encryption" (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Analysiert das angegebene [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung und die entsprechenden Parameter, um zu bestimmen, welche Parameter Datenbankspalten entsprechen, die geschützt werden, mithilfe von Always Encrypted-Funktion. Gibt die verschlüsselungsmetadaten für die Parameter, die den verschlüsselten Spalten entsprechen.  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_describe_parameter_encryption   
    [ @tsql = ] N'Transact-SQL_batch' ,   
    [ @params = ] N'parameters'   
[ ;]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @tsql =] "Transact SQL_batch"  
 Eine oder mehrere [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen. Transact-SQL_batch kann nvarchar (n) oder nvarchar(max) sein.  
  
 [ @params =] 'N'parameters  
 *@params* Stellt eine deklarationszeichenfolge für Parameter für den Transact-SQL-Batch, handelt es sich analog zu Sp_executesql bereit. Parameter können nvarchar (n) oder nvarchar(max) sein.  
  
 Eine Zeichenfolge, die die Definitionen aller Parameter enthält, die in eingebettet wurden die [!INCLUDE[tsql](../../includes/tsql-md.md)]_batch. Die Zeichenfolge muss eine Unicode-Konstante oder eine Unicode-Variable sein. Jede Parameterdefinition besteht aus einem Parameternamen und einem Datentyp. *n* ist ein Platzhalter, der zusätzliche Parameterdefinitionen. Jeder in Parameter in der Anweisung muss definiert werden, *@params*. Wenn die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung oder der Batch in der Anweisung keine Parameter, *@params* ist nicht erforderlich. NULL, ist der Standardwert für diesen Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 0 steht für Erfolg. Sonstige geben Fehler an.  
  
## <a name="result-sets"></a>Resultsets  
 **"sp_describe_parameter_encryption"** zwei Resultsets zurückgibt:  
  
-   Das Ergebnis festlegen kryptografische Schlüsseln konfiguriert für Datenbankspalten, die Parameter der angegebenen Beschreibung [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung entsprechen.  
  
-   Das Resultset, wie bestimmte Parameter beschreibt sollten verschlüsselt werden. Dieses Resultset verweisen die Schlüssel in das erste Resultset beschrieben.  
  
 Jede Zeile das erste Resultset beschreibt ein Schlüsselpaar; ein Verschlüsselungsschlüssel der verschlüsselten Spalte und der entsprechenden spaltenhauptschlüssel.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**column_encryption_key_ordinal**|**int**|Die ID der Zeile im Resultset.|  
|**database_id**|**int**|Id der Datenbank.|  
|**column_encryption_key_id**|**int**|Die Id des spaltenverschlüsselungsschlüssels. Hinweis: Diese Id gibt eine Zeile in der [Sys. column_encryption_keys &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md) -Katalogsicht angezeigt.|  
|**column_encryption_key_version**|**int**|Zur künftigen Verwendung reserviert. Derzeit enthält immer 1.|  
|**column_encryption_key_metadata_version**|**binary(8)**|Ein Zeitstempel, der Uhrzeit der Erstellung des spaltenverschlüsselungsschlüssels darstellt.|  
|**column_encryption_key_encrypted_value**|**varbinary(4000)**|Der verschlüsselte Wert des spaltenverschlüsselungsschlüssels.|  
|**column_master_key_store_provider_name**|**sysname**|Der Name des Anbieters für den Schlüsselspeicher mit dem spaltenhauptschlüssel, der verwendet wurde, um den verschlüsselten Wert des spaltenverschlüsselungsschlüssels zu erzeugen.|  
|**column_master_key_path**|**nvarchar(4000)**|Den Schlüsselpfad, der den spaltenhauptschlüssel, der verwendet wurde, um den verschlüsselten Wert des spaltenverschlüsselungsschlüssels zu erstellen.|  
|**column_encryption_key_encryption_algorithm_name**|**sysname**|Der Name des Verschlüsselungsalgorithmus verwendet, um den Verschlüsselungswert des spaltenverschlüsselungsschlüssels zu erzeugen.|  
  
 Jede Zeile das zweite Resultset enthält die verschlüsselungsmetadaten für einen Parameter.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**parameter_ordinal**|**int**|Die ID der Zeile im Resultset.|  
|**parameter_name**|**sysname**|Name eines der die angegebenen Parameter die *@params* Argument.|  
|**column_encryption_algorithm**|**tinyint**|Code, der angibt, der des Verschlüsselungsalgorithmus für die Spalte, die den Parameter konfiguriert entspricht. Die derzeit unterstützten Werte sind: 2 für **AEAD_AES_256_CBC_HMAC_SHA_256**.|  
|**column_encryption_type**|**tinyint**|Code, der angibt, des Verschlüsselungstyp für die Spalte, die den Parameter konfiguriert entspricht. Die unterstützten Werte sind:<br /><br /> 0 – nur-Text (die Spalte ist nicht verschlüsselt)<br /><br /> 1 – die zufällige Verschlüsselung<br /><br /> 2 – die deterministische Verschlüsselung.|  
|**column_encryption_key_ordinal**|**int**|Code, der Zeile in der das erste Ergebnis festgelegt. Die Zeile, auf die verwiesen werden, des spaltenverschlüsselungsschlüssels, die für die Spalte konfiguriert, die der Parameter entspricht.|  
|**column_encryption_normalization_rule_version**|**tinyint**|Versionsnummer des-Algorithmus, den Typ Normalisierung.|  
  
## <a name="remarks"></a>Hinweise  
 Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ruft der Client-Treiber, die Unterstützung von Always Encrypted, automatisch **"sp_describe_parameter_encryption"** zum Abrufen von verschlüsselungsmetadaten für parametrisierte Abfragen, die von der Anwendung ausgegeben. Anschließend kann der Treiber die verschlüsselungsmetadaten verwendet, um die Werte der Parameter zu verschlüsseln, die mit Always Encrypted geschützte Datenbankspalten entsprechen, und ersetzt die Parameterwerte nur-Text, von der Anwendung, mit dem übermittelten die Parameterwerte, vor dem Senden der Abfrage der Datenbank-Engine.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **VIEW ANY COLUMN ENCRYPTION KEY DEFINITION** und **VIEW ANY COLUMN MASTER KEY DEFINITION** Berechtigungen in der Datenbank.  
  
## <a name="examples"></a>Beispiele  
  
```  
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
0x016E000001630075007200720065006E00740075007300650072002F006D007  
9002F00610036003600620062003000660036006400640037003000620064006  
6006600300032006200360032006400300066003800370065003300340030003  
200380038006500360066003900330030003500CA0D0CEC74ECADD1804CF991  
37B4BD06BBAB15D7EA74E0C249A779C7768A5B659E0125D24FF827F5EA8CA51  
7A8E197ECA1353BA814C2B0B2E6C8AB36E3AE6A1E972D69C3C573A963ADAB6  
686CF5D24F95FE43140C4F9AF48FBA7DF2D053F3B4A1F5693A1F905440F8015B  
DB43AF8A04BE4E045B89876A0097E5FBC4E6A3B9C3C0D278C540E46C53938B8  
C957B689C4DC095821C465C73117CBA95B758232F9E5B2FCC7950B8CA00AFE3  
74DE42847E3FBC2FDD277035A2DEF529F4B735C20D980073B4965B4542A3472  
3276A1646998FC6E1C40A3FDB6ABCA98EE2B447F114D2AC7FF8C7D51657550E  
C5C2BABFFE8429B851272086DCED94332CF18FA854C1D545A28B1EF4BE64F8E0  
35175C1650F6FC5C4702ACF99850A4542B3747EAEC0CC726E091B36CE24392D8  
01ECAA684DE344FECE05812D12CD72254A014D42D0EABDA41C89FC4F545E88B  
4B8781E5FAF40D7199D4842D2BFE904D209728ED4F527CBC169E2904F6E711FF8  
1A8F4C25382A2E778DD2A58552ED031AFFDA9D9D891D98AD82155F93C58202F  
C24A77F415D4F8EF22419D62E188AC609330CCBD97CEE1AEF8A18B0195883360  
4707FDF03B2B386487CC679D7E352D0B69F9FB002E51BCD814D077E82A09C14E  
9892C1F8E0C559CFD5FA841CEF647DAB03C8191DC46B772E94D579D8C80FE93C  
3827C9F0AE04D5325BC73111E07EEEDBE67F1E2A73580085  
);  
GO  
  
CREATE TABLE t1 (  
c1 INT ENCRYPTED WITH (  
    COLUMN_ENCRYPTION_KEY = [CEK_Auto1],   
    ENCRYPTION_TYPE = Randomized,   
    ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NULL,  
);  
  
EXEC sp_describe_parameter_encryption N'INSERT INTO t1 VALUES(@c1)',  N'@c1 INT';  
```  
  
 Hier ist das erste Resultset:  
  
|column_encryption_key_ordinal|database_id|column_encryption_key_id|column_encryption_key_version|column_encryption_key_metadata_version|column_encryption_key_encrypted_value|  
|--------------------------------------|------------------|---------------------------------|--------------------------------------|------------------------------------------------|-----------------------------------------------|  
|1|5|1|1|0x99EDA60083A50000|0x016E000001630075007200720065006E00740075007300650072002F006D0079002F006100360036006200620030006600360064006400370030006200640066006600300032006200360032006400300066003800370065003300340030003200380038006500360066003900330030003500CA0D0CEC74ECADD1804CF99137B4BD06BBAB15D7EA 74E0C249A779C7768A5B659E0125D24FF827F5EA8CA517A8E197ECA1353BA814C2B0B2E6C8AB36E3AE6A1E972D69C3C573A963ADAB6686CF5D24F95FE43140C4F9AF48FBA7DF2D053F3B4A1F5693A1F905440F8015BDB43AF8A04BE4E045B89876A0097E5FBC4E6A3B9C3C0D278C540E46C53938B8C957B689C4DC095821C465C73117CBA95B758232 F9E5B2FCC7950B8CA00AFE374DE42847E3FBC2FDD277035A2DEF529F4B735C20D980073B4965B4542A34723276A1646998FC6E1C40A3FDB6ABCA98EE2B447F114D2AC7FF8C7D51657550EC5C2BABFFE8429B851272086DCED94332CF18FA854C1D545A28B1EF4BE64F8E035175C1650F6FC5C4702ACF99850A4542B3747EAEC0CC726E091B36CE2439 2D801ECAA684DE344FECE05812D12CD72254A014D42D0EABDA41C89FC4F545E88B4B8781E5FAF40D7199D4842D2BFE904D209728ED4F527CBC169E2904F6E711FF81A8F4C25382A2E778DD2A58552ED031AFFDA9D9D891D98AD82155F93C58202FC24A77F415D4F8EF22419D62E188AC609330CCBD97CEE1AEF8A18B01958833604707FDF03B2B3864 87CC679D7E352D0B69F9FB002E51BCD814D077E82A09C14E9892C1F8E0C559CFD5FA841CEF647DAB03C8191DC46B772E94D579D8C80FE93C3827C9F0AE04D5325BC73111E07EEEDBE67F1E2A73580085|  
  
 (Ergebnisse weiterhin.)  
  
|column_master_key_store_provider_name|column_master_key_path|column_encryption_key_encryption_algorithm_name|  
|------------------------------------------------|-------------------------------|----------------------------------------------------------|  
|MSSQL_CERTIFICATE_STORE|CurrentUser/my/A66BB0F6DD70BDFF02B62D0F87E340288E6F9305|RSA_OAEP|  
  
 Hier ist das zweite Resultset:  
  
|parameter_ordinal|parameter_name|column_encryption_algorithm|column_encryption_type|  
|------------------------|---------------------|-----------------------------------|------------------------------|  
|1|@c1|1|1|  
  
 (Ergebnisse weiterhin.)  
  
|column_encryption_key_ordinal|column_encryption_normalization_rule_version|  
|--------------------------------------|------------------------------------------------------|  
|1|1|  
  
## <a name="see-also"></a>Siehe auch  
 
  [Always Encrypted &amp;#40;Datenbank-Engine&amp;#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Always Encrypted &#40;Cliententwicklung&#41;](../../relational-databases/security/encryption/always-encrypted-client-development.md)  
  
  
