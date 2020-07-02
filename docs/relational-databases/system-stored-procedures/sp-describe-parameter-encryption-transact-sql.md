---
title: sp_describe_parameter_encryption (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/27/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_describe_parameter_encryption
- sp_describe_parameter_encryption_TSQL
- sys.sp_describe_parameter_encryption
- sys.sp_describe_parameter_encryption_TSQL
helpviewer_keywords:
- sp_describe_parameter_encryption
ms.assetid: 706ed441-2881-4934-8d5e-fb357ee067ce
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 583536c1b69951b18e6d30910f4e4d9d44b8d99f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717370"
---
# <a name="sp_describe_parameter_encryption-transact-sql"></a>sp_describe_parameter_encryption (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asdw](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asdw.md)]

  Analysiert die angegebene [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung und ihre Parameter, um zu bestimmen, welche Parameterdaten Bank Spalten entsprechen, die mit dem Always Encrypted Feature geschützt werden. Gibt Verschlüsselungs Metadaten für die Parameter zurück, die verschlüsselten Spalten entsprechen.  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_describe_parameter_encryption   
    [ @tsql = ] N'Transact-SQL_batch' ,   
    [ @params = ] N'parameters'   
[ ;]  
```  
  
## <a name="arguments"></a>Argumente  
 [ \@ tionql =] ' Transact-SQL_batch '  
 Eine oder mehrere [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen. Transact-SQL_batch kann vom Datentyp nvarchar (n) oder nvarchar (max) sein.  
  
 [ \@ Parameter =] n ' Parameter '  
 Parameter stellt eine Deklarations Zeichenfolge für Parameter für den Transact-SQL-Batch bereit, der sp_executesql ähnelt. * \@ * Parameter können nvarchar (n) oder nvarchar (max) sein.  
  
 Ist eine Zeichenfolge, die die Definitionen aller Parameter enthält, die in die _batch eingebettet wurden [!INCLUDE[tsql](../../includes/tsql-md.md)] . Die Zeichenfolge muss eine Unicode-Konstante oder eine Unicode-Variable sein. Jede Parameterdefinition besteht aus einem Parameternamen und einem Datentyp. *n* ist ein Platzhalter, der zusätzliche Parameter Definitionen angibt. Jeder in der-Anweisung angegebene Parameter muss in * \@ para*Metern definiert werden. Wenn die- [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung oder der-Batch in der Anweisung keine Parameter enthält, ist die Angabe * \@ von para* Metern nicht erforderlich. Der Standardwert für diesen Parameter ist NULL.  
  
## <a name="return-value"></a>Rückgabewert  
 0 gibt einen Erfolg an. Alles deutet auf einen Fehler hin.  
  
## <a name="result-sets"></a>Resultsets  
 **sp_describe_parameter_encryption** gibt zwei Resultsets zurück:  
  
-   Das Resultset, das für Daten Bank Spalten konfigurierte kryptografische Schlüssel beschreibt, entspricht den Parametern der angegebenen [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung.  
  
-   Das Resultset, das beschreibt, wie bestimmte Parameter verschlüsselt werden sollen. Dieses Resultset verweist auf die Schlüssel, die im ersten Resultset beschrieben werden.  
  
 Jede Zeile des ersten Resultsets beschreibt ein paar von Schlüsseln. ein verschlüsselter Spalten Verschlüsselungsschlüssel und der zugehörige Spalten Hauptschlüssel.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**column_encryption_key_ordinal**|**int**|ID der Zeile im Resultset.|  
|**database_id**|**int**|Datenbank-ID.|  
|**column_encryption_key_id**|**int**|Die ID des Spalten Verschlüsselungsschlüssels. Hinweis: Diese ID bezeichnet eine Zeile in der&#41;-Katalog Sicht [sys. column_encryption_keys &#40;Transact-SQL](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md) .|  
|**column_encryption_key_version**|**int**|Für die zukünftige Verwendung reserviert. Derzeit enthält immer 1.|  
|**column_encryption_key_metadata_version**|**Binär (8)**|Ein Zeitstempel, der die Erstellungszeit des Spalten Verschlüsselungsschlüssels darstellt.|  
|**column_encryption_key_encrypted_value**|**varbinary (4000)**|Der verschlüsselte Wert des Spalten Verschlüsselungsschlüssels.|  
|**column_master_key_store_provider_name**|**sysname**|Der Name des Anbieters für den Schlüsselspeicher, der den Spalten Hauptschlüssel enthält, der verwendet wurde, um den verschlüsselten Wert des Spalten Verschlüsselungsschlüssels zu erhalten.|  
|**column_master_key_path**|**nvarchar(4000)**|Der Schlüssel Pfad des Spalten Hauptschlüssels, der verwendet wurde, um den verschlüsselten Wert des Spalten Verschlüsselungsschlüssels zu erhalten.|  
|**column_encryption_key_encryption_algorithm_name**|**sysname**|Der Name des Verschlüsselungsalgorithmus, mit dem der Verschlüsselungs Wert des Spalten Verschlüsselungsschlüssels erzeugt wird.|  
  
 Jede Zeile des zweiten Resultsets enthält Verschlüsselungs Metadaten für einen Parameter.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**parameter_ordinal**|**int**|ID der Zeile im Resultset.|  
|**parameter_name**|**sysname**|Der Name eines Parameters, der im * \@ params* -Argument angegeben ist.|  
|**column_encryption_algorithm**|**tinyint**|Code, der den für die Spalte konfigurierten Verschlüsselungsalgorithmus angibt, entspricht dem-Parameter. Die derzeit unterstützten Werte sind: 2 für **AEAD_AES_256_CBC_HMAC_SHA_256**.|  
|**column_encryption_type**|**tinyint**|Code, der den Verschlüsselungstyp angibt, der für die Spalte konfiguriert ist. der-Parameter entspricht. Die unterstützten Werte sind:<br /><br /> 0-Klartext (die Spalte ist nicht verschlüsselt)<br /><br /> 1: zufällige Verschlüsselung<br /><br /> 2-deterministische Verschlüsselung.|  
|**column_encryption_key_ordinal**|**int**|Code der Zeile im ersten Resultset. In der Zeile, auf die verwiesen wird, wird der für die Spalte konfigurierte Spalten Verschlüsselungsschlüssel beschrieben. der Parameter entspricht.|  
|**column_encryption_normalization_rule_version**|**tinyint**|Versionsnummer des typnormalisierungs Algorithmus.|  
  
## <a name="remarks"></a>Hinweise  
 Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Treiber, der Always Encrypted unterstützt, ruft automatisch **sp_describe_parameter_encryption** auf, um Verschlüsselungs Metadaten für parametrisierte Abfragen abzurufen, die von der Anwendung ausgegeben werden. Anschließend verwendet der Treiber die Verschlüsselungs Metadaten, um die Werte von Parametern zu verschlüsseln, die Daten Bank Spalten entsprechen, die mit Always Encrypted geschützt sind, und ersetzt die klar Text Parameterwerte, die von der Anwendung gesendet werden, mit den verschlüsselten Parameterwerten, bevor die Abfrage an die Datenbank-Engine gesendet wird.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Berechtigungen **View any Column Encryption Key Definition** und **View any Column Master Key Definition** in der Datenbank.  
  
## <a name="examples"></a>Beispiele  
  
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
|1|5|1|1|0x99eda60083a50000|0x016E000001630075007200720065006E00740075007300650072002F006D0079002F006100360036006200620030006600360064006400370030006200640066006600300032006200360032006400300066003800370065003300340030003200380038006500360066003900330030003500CA0D0CEC74ECADD1804CF99137B4BD06BBAB15D7EA74E0C249A779C7768A5B659E0125D24FF827F5EA8CA517A8E197ECA1353BA814C2B0B2E6C8AB36E3AE6A1E972D69C3C573A963ADAB6686CF5D24F95FE43140C4F9AF48FBA7DF2D053F3B4A1F5693A1F905440F8015BDB43AF8A04BE4E045B89876A0097E5FBC4E6A3B9C3C0D278C540E46C53938B8C957B689C4DC095821C465C73117CBA95B758232F9E5B2FCC7950B8CA00AFE374DE42847E3FBC2FDD277035A2DEF529F4B735C20D980073B4965B4542A34723276A1646998FC6E1C40A3FDB6ABCA98EE2B447F114D2AC7FF8C7D51657550EC5C2BABFFE8429B851272086DCED94332CF18FA854C1D545A28B1EF4BE64F8E035175C1650F6FC5C4702ACF99850A4542B3747EAEC0CC726E091B36CE24392D801ECAA684DE344FECE05812D12CD72254A014D42D0EABDA41C89FC4F545E88B4B8781E5FAF40D7199D4842D2BFE904D209728ED4F527CBC169E2904F6E711FF81A8F4C25382A2E778DD2A58552ED031AFFDA9D9D891D98 AD82155F93C58202FC24A77F415D4F8EF22419D62E188AC609330CCBD97CEE1AEF8A18B01958833604707FDF03B2B386487CC679D7E352D0B69F9FB002E51BCD814D077E82A09C14E9892C1F8E0C559CFD5FA841CEF647DAB03C8191DC46B772E94D579D8C80FE93C3827C9F0AE04D5325BC73111E07EEEDBE67F1E2A73580085|  
  
 (Die Ergebnisse werden fortgesetzt.)  
  
|column_master_key_store_provider_name|column_master_key_path|column_encryption_key_encryption_algorithm_name|  
|------------------------------------------------|-------------------------------|----------------------------------------------------------|  
|MSSQL_CERTIFICATE_STORE|CurrentUser/My/A66BB0F6DD70BDFF02B62D0F87E340288E6F9305|RSA_OAEP|  
  
 Hier ist das zweite Resultset:  
  
|parameter_ordinal|parameter_name|column_encryption_algorithm|column_encryption_type|  
|------------------------|---------------------|-----------------------------------|------------------------------|  
|1|\@C1|1|1|  
  
 (Die Ergebnisse werden fortgesetzt.)  
  
|column_encryption_key_ordinal|column_encryption_normalization_rule_version|  
|--------------------------------------|------------------------------------------------------|  
|1|1|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Entwickeln von Anwendungen mit Always Encrypted](../../relational-databases/security/encryption/always-encrypted-client-development.md)  
  
  
