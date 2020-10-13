---
description: Direkte Konfiguration der Spaltenverschlüsselung mit Transact-SQL
title: Direkte Konfiguration der Spaltenverschlüsselung mit Transact-SQL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/10/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 90bb710e57e87bfb6bf86f4ae0543329a4500940
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91863645"
---
# <a name="configure-column-encryption-in-place-with-transact-sql"></a>Direkte Konfiguration der Spaltenverschlüsselung mit Transact-SQL
[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

In diesem Artikel wird beschrieben, wie kryptografische Vorgänge direkt in Spalten durchgeführt werden, die Always Encrypted mit Secure Enclaves mit der [ALTER TABLE-Anweisung](../../../odbc/microsoft/alter-table-statement.md)/`ALTER COLUMN`-Anweisung verwenden. Grundlegende Informationen zur direkten Verschlüsselung und zu den allgemeinen Voraussetzungen finden Sie unter [Konfigurieren einer direkten Spaltenverschlüsselung mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-configure-encryption.md).

Mit der `ALTER TABLE`- oder `ALTER COLUMN`-Anweisung können Sie die Zielverschlüsselungskonfiguration für eine Spalte festlegen. Wenn Sie die Anweisung ausführen, führt die serverseitige Secure Enclave die Verschlüsselung, erneute Verschlüsselung oder Entschlüsselung der in der Spalte gespeicherten Daten durch, und zwar abhängig von der aktuellen und der Ziel-Verschlüsselungskonfiguration, die in der Spaltendefinition in der Anweisung angegeben ist. 
- Wenn die Spalte derzeit nicht verschlüsselt ist, wird sie verschlüsselt, wenn Sie die `ENCRYPTED WITH`-Klausel in der Spaltendefinition angeben.
- Wenn die Spalte derzeit verschlüsselt ist, wird sie entschlüsselt (in eine Klartextspalte konvertiert), wenn Sie die `ENCRYPTED WITH`-Klausel nicht in der Spaltendefinition angeben.
- Wenn die Spalte derzeit verschlüsselt ist, wird sie erneut verschlüsselt, wenn Sie die `ENCRYPTED WITH`-Klausel angeben und der angegebene Spaltenverschlüsselungstyp oder der Spaltenverschlüsselungsschlüssel nicht mit dem aktuell verwendeten Verschlüsselungstyp oder dem Spaltenverschlüsselungsschlüssel identisch ist. 

> [!NOTE]
> Kryptografische Vorgänge können nicht mit anderen Änderungen in einer einzigen `ALTER TABLE`/`ALTER COLUMN`-Anweisung kombiniert werden, es sei denn, Sie ändern die Spalte in `NULL` oder `NOT NULL` oder ändern eine Sortierung. Beispiel: Sie können nicht in einer einzigen `ALTER TABLE`/`ALTER COLUMN`-Transact-SQL-Anweisung eine Spalte verschlüsseln UND den Datentyp der Spalte ändern. Sie müssen zwei separate Anweisungen verwenden.

Wie jede Abfrage, die eine serverseitige Secure Enclave verwendet, muss eine `ALTER TABLE`/`ALTER COLUMN`-Anweisung, die eine direkte Verschlüsselung auslöst, über eine Verbindung mit aktiviertem Always Encrypted und aktivierten Enclave-Berechnungen gesendet werden. 

Im weiteren Verlauf dieses Artikels wird beschrieben, wie Sie eine direkte Verschlüsselung mithilfe der `ALTER TABLE`/`ALTER COLUMN`-Anweisung aus SQL Server Management Studio auslösen. Alternativ können Sie `ALTER TABLE`/`ALTER COLUMN` aus Ihrer Anwendung ausgeben. 

> [!NOTE]
> Derzeit unterstützen andere Tools als SSMS, einschließlich des [Invoke-Sqlcmd](/powershell/module/sqlserver/invoke-sqlcmd)-Cmdlets im SqlServer PowerShell-Modul und [sqlcmd](../../../tools/sqlcmd-utility.md),nicht die Verwendung von `ALTER TABLE`/`ALTER COLUMN` für direkte Kryptografievorgänge.

## <a name="perform-in-place-encryption-with-transact-sql-in-ssms"></a>Durchführen einer direkten Verschlüsselung mit Transact-SQL in SSMS
### <a name="pre-requisites"></a>Voraussetzungen
- Die Voraussetzungen werden unter [Konfigurieren einer direkten Spaltenverschlüsselung mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-configure-encryption.md) beschrieben.
- SQL Server Management Studio 18.3 oder höher

### <a name="steps"></a>Schritte
1. Öffnen Sie ein Abfragefenster, für das Always Encrypted und Enclave-Berechnungen in der Datenbankverbindung aktiviert sind. Einzelheiten dazu finden Sie unter [Aktivieren und Deaktivieren von Always Encrypted für eine Datenbankverbindung](always-encrypted-query-columns-ssms.md#en-dis) weiter unten.
2. Geben Sie im Abfragefenster die `ALTER TABLE`/`ALTER COLUMN`-Anweisung aus, und geben Sie in der `ENCRYPTED WITH`-Klausel einen Enclave-fähigen Spaltenverschlüsselungsschlüssel an. Wenn Ihre Spalte eine Zeichenfolgenspalte ist (z. B. `char`, `varchar`, `nchar`, `nvarchar`), müssen Sie möglicherweise auch die Sortierung in eine BIN2-Sortierung ändern. 
    
    > [!NOTE]
    > Wenn Ihr Spaltenhauptschlüssel in Azure Key Vault gespeichert ist, werden Sie ggf. dazu aufgefordert, sich bei Azure anzumelden.

3. Leeren Sie den Plancache für alle Batches und gespeicherten Prozeduren, die Zugriff auf die Tabelle haben, um die Informationen für die Parameterverschlüsselung zu aktualisieren. 
 
    ```sql
    ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
    ```
    > [!NOTE]
    > Wenn Sie den Plan für die betroffene Abfrage nicht aus dem Cache entfernen, kann bei der ersten Abfrageausführung nach der Verschlüsselung ein Fehler auftreten.

    > [!NOTE]
    > Verwenden Sie `ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE` oder `DBCC FREEPROCCACHE`, um den Plancache sorgfältig zu leeren, da dies zu einer vorübergehenden Verschlechterung der Abfrageleistung führen kann. Um die negativen Auswirkungen des Leerens des Caches zu minimieren, können Sie nur die Pläne für die betroffenen Abfragen selektiv entfernen.

4.  Rufen Sie [sp_refresh_parameter_encryption](../../system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md) auf, um die Metadaten für die Parameter jedes Moduls (Stored Procedure, Function, View, Trigger) zu aktualisieren, die in [sys.parameters](../..//system-catalog-views/sys-parameters-transact-sql.md) beibehalten werden und möglicherweise durch Verschlüsselung der Spalten ungültig wurden.

### <a name="examples"></a>Beispiele
#### <a name="encrypting-a-column-in-place"></a>Direktes Verschlüsseln einer Spalte
Im Beispiel unten wird folgendes vorausgesetzt:
- `CEK1` ist ein Enclave-fähiger Spaltenverschlüsselungsschlüssel.
- Die `SSN`-Spalte ist eine Klartextspalte und verwendet gegenwärtig die Standarddatenbanksortierung, z. B. eine Sortierung Latin1, Nicht-BIN2 (beispielsweise `Latin1_General_CI_AI_KS_WS`).

Die Anweisung verschlüsselt die `SSN`-Spalte mit einer Verschlüsselung nach dem Zufallsprinzip und dem Enclave-fähigen Spalten-Direktverschlüsselungsschlüssel. Außerdem wird die standardmäßige Datenbanksortierung mit der entsprechenden (in der gleichen Codepage) BIN2-Sortierung überschrieben.

Der Vorgang erfolgt online (`ONLINE = ON`). Beachten Sie auch den Aufruf von `ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE`, der die Pläne der Abfragen neu erstellt, die von der Änderung des Tabellenschemas betroffen sind.

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char] COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
WITH
(ONLINE = ON);
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

#### <a name="re-encrypt-a-column-in-place-to-change-encryption-type"></a>Erneutes direktes Verschlüsseln einer Spalte, um den Verschlüsselungstyp zu ändern
Im Beispiel unten wird folgendes vorausgesetzt:
- Die `SSN`-Spalte wird mit einer deterministischen Verschlüsselung und einem Enclave-fähigen Spaltenverschlüsselungsschlüssel, `CEK1`, verschlüsselt.
- Die aktuelle Sortierung, die auf Spaltenebene festgelegt wird, ist `Latin1_General_BIN2`.

Mit der folgenden Anweisung wird die Spalte mithilfe der Verschlüsselung nach dem Zufallsprinzip und demselben Schlüssel (`CEK1`) erneut verschlüsselt.

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1]
, ENCRYPTION_TYPE = Randomized
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL;
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

#### <a name="re-encrypt-a-column-in-place-to-rotate-a-column-encryption-key"></a>Erneutes direktes Verschlüsseln einer Spalte zum Rotieren eines Spaltenverschlüsselungsschlüssels
Im Beispiel unten wird folgendes vorausgesetzt:
- Die `SSN`-Spalte wird mit einer der Verschlüsselung nach dem Zufallsprinzip und einem Enclave-fähigem Spaltenverschlüsselungsschlüssel, `CEK1`, verschlüsselt.
- `CEK2` ist ein Enclave-fähiger Spaltenverschlüsselungsschlüssel (der nicht mit `CEK1` übereinstimmt).
- Die aktuelle Sortierung, die auf Spaltenebene festgelegt wird, ist `Latin1_General_BIN2`.

Mit der folgenden Anweisung wird die Spalte mit `CEK2` erneut verschlüsselt.

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK2]
, ENCRYPTION_TYPE = Randomized
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL;
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```
#### <a name="decrypt-a-column-in-place"></a>Direkte Entschlüsselung einer Spalte
Im Beispiel unten wird folgendes vorausgesetzt:
- Die `SSN`-Spalte wird mit einem Enclave-fähigen Spaltenverschlüsselungsschlüssel verschlüsselt.
- Die aktuelle Sortierung, die auf Spaltenebene festgelegt wird, ist `Latin1_General_BIN2`.

Die nachfolgende Anweisung verschlüsselt die Spalte (und behält die Sortierung unverändert bei – alternativ können Sie die Sortierung ändern, z. B. in eine Nicht-BIN2-Sortierung in derselben Anweisung).

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
WITH (ONLINE = ON);
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

## <a name="next-steps"></a>Nächste Schritte
- [Abfragen von Spalten mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-query-columns.md)
- [Erstellen und Verwenden von Indizes in Spalten mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-create-use-indexes.md)
- [Entwickeln von Anwendungen mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-client-development.md)

## <a name="see-also"></a>Weitere Informationen  
- [Konfigurieren einer direkten Spaltenverschlüsselung mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-configure-encryption.md)
- [Aktivieren von Always Encrypted mit Secure Enclaves für vorhandene verschlüsselte Spalten](always-encrypted-enclaves-enable-for-encrypted-columns.md)
- [Tutorial: Erste Schritte mit Always Encrypted mit Secure Enclaves mithilfe von SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md)