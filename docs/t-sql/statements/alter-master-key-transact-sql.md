---
title: ALTER MASTER KEY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: fasttrack-edit
ms.date: 02/21/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER MASTER KEY
- ALTER_MASTER_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- REGENERATE phrase
- ALTER MASTER KEY statement
- decryption [SQL Server], Database Master Key
- FORCE option
- encryption [SQL Server], Database Master Key
- database master key [SQL Server], modifying
- cryptography [SQL Server], Database Master Key
- modifying Database Master Key
- service master key [SQL Server], modifying
- DROP ENCRYPTION BY SERVICE MASTER KEY phrase
ms.assetid: 8ac501c3-4280-4d5b-b58a-1524fa715b50
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d5a7600f9657a11a25732aa9527bd6a775234eda
ms.sourcegitcommit: f66804e93cf4a7624bfa10168edbf1ed9a83cb86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2020
ms.locfileid: "83868419"
---
# <a name="alter-master-key-transact-sql"></a>ALTER MASTER KEY (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Ändert die Eigenschaften eines Datenbank-Hauptschlüssels.

![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Syntax

```syntaxsql
-- Syntax for SQL Server

ALTER MASTER KEY <alter_option>

<alter_option> ::=
    <regenerate_option> | <encryption_option>

<regenerate_option> ::=
    [ FORCE ] REGENERATE WITH ENCRYPTION BY PASSWORD = 'password'

<encryption_option> ::=
    ADD ENCRYPTION BY { SERVICE MASTER KEY | PASSWORD = 'password' }
    |
    DROP ENCRYPTION BY { SERVICE MASTER KEY | PASSWORD = 'password' }
```

```syntaxsql
-- Syntax for Azure SQL Database
-- Note: DROP ENCRYPTION BY SERVICE MASTER KEY is not supported on Azure SQL Database.

ALTER MASTER KEY <alter_option>

<alter_option> ::=
    <regenerate_option> | <encryption_option>

<regenerate_option> ::=
    [ FORCE ] REGENERATE WITH ENCRYPTION BY PASSWORD = 'password'

<encryption_option> ::=
    ADD ENCRYPTION BY { SERVICE MASTER KEY | PASSWORD = 'password' }
    |
    DROP ENCRYPTION BY { PASSWORD = 'password' }
```

```syntaxsql
-- Syntax for Azure SQL Data Warehouse and Analytics Platform System

ALTER MASTER KEY <alter_option>

<alter_option> ::=
    <regenerate_option> | <encryption_option>

<regenerate_option> ::=
    [ FORCE ] REGENERATE WITH ENCRYPTION BY PASSWORD ='password'

<encryption_option> ::=
    ADD ENCRYPTION BY SERVICE MASTER KEY
    |
    DROP ENCRYPTION BY SERVICE MASTER KEY
```

## <a name="arguments"></a>Argumente

PASSWORD ='*password*' Gibt ein Kennwort an, mit dem der Datenbank-Hauptschlüssel ver- oder entschlüsselt wird. *password* muss den Anforderungen der Windows-Kennwortrichtlinien des Computers entsprechen, auf dem die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.

## <a name="remarks"></a>Bemerkungen

Mit der REGENERATE-Option werden der Datenbank-Hauptschlüssel und alle durch ihn geschützten Schlüssel neu erstellt. Die Schlüssel werden zunächst mit dem alten Hauptschlüssel entschlüsselt und anschließend mit dem neuen Hauptschlüssel verschlüsselt. Die Ausführung dieses ressourcenintensiven Vorgangs sollte außerhalb der Hauptzeiten geplant werden, es sei denn, der Hauptschlüssel ist nicht mehr sicher.

[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SQL Server 2016 schützt den Diensthauptschlüssel (Service Master Key, SMK) und den Datenbank-Hauptschlüssel (Database Master Key, DMK) mithilfe des AES-Verschlüsselungsalgorithmus. AES ist ein neuerer Verschlüsselungsalgorithmus als der in früheren Versionen verwendete 3DES-Algorithmus. Nach dem Aktualisieren einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] auf [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] sollten SMK und DMK erneut generiert werden, um die Hauptschlüssel auf AES zu aktualisieren. Weitere Informationen zum Neugenerieren des SMK finden Sie unter [ALTER SERVICE MASTER KEY](../../t-sql/statements/alter-service-master-key-transact-sql.md).

Bei Verwendung der FORCE-Option wird die Schlüsselneugenerierung fortgesetzt, auch wenn der Hauptschlüssel nicht verfügbar ist oder wenn der Server nicht alle verschlüsselten privaten Schlüssel entschlüsseln kann. Falls der Hauptschlüssel nicht geöffnet werden kann, können Sie den Hauptschlüssel mit der [RESTORE MASTER KEY](../../t-sql/statements/restore-master-key-transact-sql.md)-Anweisung aus einer Sicherung wiederherstellen. Die FORCE-Option sollte nur verwendet werden, wenn der Hauptschlüssel nicht abgerufen werden kann oder wenn bei der Entschlüsselung ein Fehler aufgetreten ist. Informationen, die nur mit dem nicht abrufbaren Schlüssel verschlüsselt sind, gehen verloren.

Mit der DROP ENCRYPTION BY SERVICE MASTER KEY-Option wird die Verschlüsselung des Datenbank-Hauptschlüssels durch den Diensthauptschlüssel entfernt.

Mit ADD ENCRYPTION BY SERVICE MASTER KEY wird eine Kopie des Hauptschlüssels mithilfe des Diensthauptschlüssels verschlüsselt. Der Hauptschlüssel wird dann sowohl in der aktuellen Datenbank als auch in der master-Datenbank gespeichert.

## <a name="permissions"></a>Berechtigungen

Erfordert die CONTROL-Berechtigung für die Datenbank. Falls der Datenbank-Hauptschlüssel mit einem Kennwort verschlüsselt wurde, muss das Kennwort bekannt sein.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird ein neuer Datenbank-Hauptschlüssel für `AdventureWorks` erstellt, und die Schlüssel, die sich in der Verschlüsselungshierarchie unter diesem Schlüssel befinden, werden neu verschlüsselt.

```sql
USE AdventureWorks2012;
ALTER MASTER KEY REGENERATE WITH ENCRYPTION BY PASSWORD = 'dsjdkflJ435907NnmM#sX003';
GO
```

## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

Im folgenden Beispiel wird ein neuer Datenbank-Hauptschlüssel für `AdventureWorksPDW2012` erstellt, und die Schlüssel, die sich in der Verschlüsselungshierarchie unter diesem Schlüssel befinden, werden neu verschlüsselt.

```sql
USE master;
ALTER MASTER KEY REGENERATE WITH ENCRYPTION BY PASSWORD = 'dsjdkflJ435907NnmM#sX003';
GO
```

## <a name="see-also"></a>Weitere Informationen

- [CREATE MASTER KEY](../../t-sql/statements/create-master-key-transact-sql.md)
- [OPEN MASTER KEY](../../t-sql/statements/open-master-key-transact-sql.md)
- [CLOSE MASTER KEY](../../t-sql/statements/close-master-key-transact-sql.md)
- [BACKUP MASTER KEY](../../t-sql/statements/backup-master-key-transact-sql.md)
- [RESTORE MASTER KEY](../../t-sql/statements/restore-master-key-transact-sql.md)
- [DROP MASTER KEY](../../t-sql/statements/drop-master-key-transact-sql.md)
- [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)
- [CREATE DATABASE](../../t-sql/statements/create-database-transact-sql.md?view=sql-server-2017)
- [Anfügen und Trennen von Datenbanken](../../relational-databases/databases/database-detach-and-attach-sql-server.md)
