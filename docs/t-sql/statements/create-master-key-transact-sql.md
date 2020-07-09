---
title: CREATE MASTER KEY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CREATE_MASTER_KEY_TSQL
- MASTER_KEY_TSQL
- MASTER KEY
- CREATE MASTER KEY
dev_langs:
- TSQL
helpviewer_keywords:
- encryption [SQL Server], Database Master Key
- database master key [SQL Server]
- CREATE MASTER KEY statement
- cryptography [SQL Server], Database Master Key
- database master key [SQL Server], creating
ms.assetid: 1710a305-1a4f-48ec-836c-11ffd0356d76
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: beba354431da2b0f97c3965148cbf3d09f93d9f4
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86010761"
---
# <a name="create-master-key-transact-sql"></a>CREATE MASTER KEY (Transact-SQL)

[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Erstellen Sie einen Datenbankhauptschlüssel in der Masterdatenbank.

![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Syntax

```syntaxsql
CREATE MASTER KEY [ ENCRYPTION BY PASSWORD ='password' ]
[ ; ]
```

## <a name="arguments"></a>Argumente

PASSWORD ='*password*': Ist das zum Verschlüsseln des Hauptschlüssels in der Datenbank verwendete Kennwort. *password* muss den Anforderungen der Windows-Kennwortrichtlinien des Computers entsprechen, auf dem die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird. *password* ist in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] und [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] optional.

## <a name="remarks"></a>Bemerkungen

Der Datenbank-Hauptschlüssel ist ein symmetrischer Schlüssel, der zum Schützen von privaten Schlüsseln der in der Datenbank vorhandenen Zertifikate und asymmetrischen Schlüssel verwendet wird. Beim Erstellen wird der Hauptschlüssel mithilfe des AES_256-Algorithmus und eines vom Benutzer angegebenen Kennworts verschlüsselt. In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]wird der Triple DES-Algorithmus verwendet. Die automatische Entschlüsselung für den Hauptschlüssel kann aktiviert werden, indem eine Kopie des Schlüssels mit dem Diensthauptschlüssel verschlüsselt und sowohl in der Datenbank als auch in master gespeichert wird. In der Regel wird die in master gespeicherte Kopie im Hintergrund aktualisiert, sobald der Hauptschlüssel geändert wird. Dieses Standardverhalten kann mithilfe der DROP ENCRYPTION BY SERVICE MASTER KEY-Option von [ALTER MASTER KEY](../../t-sql/statements/alter-master-key-transact-sql.md) geändert werden. Ein Hauptschlüssel, der nicht mit dem Diensthauptschlüssel verschlüsselt ist, muss mithilfe der [OPEN MASTER KEY](../../t-sql/statements/open-master-key-transact-sql.md)-Anweisung und eines Kennworts geöffnet werden.

In der is_master_key_encrypted_by_server-Spalte der sys.databases-Katalogsicht in master wird angezeigt, ob der Datenbank-Hauptschlüssel mit dem Diensthauptschlüssel verschlüsselt ist.

Informationen zum Datenbank-Hauptschlüssel werden in der sys.symmetric_keys-Katalogsicht angezeigt.

Für SQL Server und Parallel Data Warehouse wird der Hauptschlüssel in der Regel durch den Diensthauptschlüssel und mindestens ein Kennwort geschützt. Wenn die Datenbank physisch auf einen anderen Server verschoben wird (z. B. beim Protokollversand oder der Wiederherstellung einer Sicherungskopie), enthält sie eine Kopie des Hauptschlüssels, die mit dem ursprünglichen Diensthauptschlüssel des Servers verschlüsselt wurde, falls diese Verschlüsselung nicht explizit durch `ALTER MASTER KEY DDL` entfernt wurde. Außerdem enthält die Datenbank eine Kopie des Hauptschlüssels, die mit allen Kennwörtern verschlüsselt wurde, die entweder während des `CREATE MASTER KEY`-Vorgangs oder bei nachfolgenden `ALTER MASTER KEY DDL`-Vorgängen angegeben wurden. Wenn Benutzer den Hauptschlüssel und alle verschlüsselten Daten wiederherstellen möchten, die nach dem Verschieben der Datenbank durch den Hauptschlüssel als Stamm in der Schlüsselhierarchie verschlüsselt wurden, haben sie dazu drei Möglichkeiten: Sie können die `OPEN MASTER KEY`-Anweisung mit einem der Kennworte nutzen, die zum Schutz des Hauptschlüssels verwendet wurden, die Sicherung des Hauptschlüssels wiederherstellen oder aber die Sicherung des ursprünglichen Diensthauptschlüssels auf dem neuen Server wiederherstellen.

Im Fall von [!INCLUDE[ssSDS](../../includes/sssds-md.md)] und [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] wird der Kennwortschutz nicht als Sicherheitsmechanismus betrachtet, mit dem sich ein Datenverlust in Situationen verhindern lässt, in denen möglicherweise die Datenbank von einem Server zu einem anderen verschoben wird. Dies liegt daran, dass der Schutz des Diensthauptschlüssels für den Hauptschlüssel von der Microsoft Azure-Plattform verwaltet wird. Das Kennwort für den Hauptschlüssel ist daher in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] und [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] optional.

> [!IMPORTANT]
> Es wird empfohlen, dass Sie mithilfe von [BACKUP MASTER KEY](../../t-sql/statements/backup-master-key-transact-sql.md) eine Sicherung des Hauptschlüssels erstellen und an einem sicheren Ort außerhalb Ihrer Geschäftsräume aufbewahren.

Der Diensthauptschlüssel und die Datenbank-Hauptschlüssel werden mit dem AES-256-Algorithmus geschützt.

## <a name="permissions"></a>Berechtigungen

Erfordert die CONTROL-Berechtigung für die Datenbank.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird ein Datenbankhauptschlüssel für die `master`-Datenbank erstellt. Der Schlüssel wird mit dem Kennwort `23987hxJ#KL95234nl0zBe` verschlüsselt.

```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';
GO
```

## <a name="see-also"></a>Weitere Informationen

- [sys.symmetric_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)
- [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)
- [OPEN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-master-key-transact-sql.md)
- [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md)
- [DROP MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-master-key-transact-sql.md)
- [CLOSE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/close-master-key-transact-sql.md)
- [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)
