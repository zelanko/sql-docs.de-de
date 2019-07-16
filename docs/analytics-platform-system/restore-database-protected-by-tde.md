---
title: 'Wiederherstellen eine Datenbank mit TDE: Parallel Data Warehouse geschützt | Microsoft-Dokumentation'
description: Verwenden Sie die folgenden Schritte zum Wiederherstellen einer Datenbank, die in Analytics Platform System Parallel Data Warehouse mithilfe von transparente datenverschlüsselung verschlüsselt wird.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 7c2f676f75c5a8c79bfc2f2417ff30c9806e3c80
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960169"
---
# <a name="restore-a-database-protected-by-tde-in-parallel-data-warehouse"></a>Wiederherstellen einer Datenbank mit TDE in Parallel Data Warehouse geschützt
Verwenden Sie die folgenden Schritte zum Wiederherstellen einer Datenbank, die mithilfe der transparenten datenverschlüsselung verschlüsselt wird.  
  
Die [Transparent Data Encryption mithilfe von](transparent-data-encryption.md#using-tde) Beispiel enthält Code zum Aktivieren von TDE für die `AdventureWorksPDW2012` Datenbank. Der folgende Code wird dieses Beispiel erstellen eine Sicherung der Datenbank auf dem ursprünglichen Analytics Platform System (APS)-Gerät, und klicken Sie dann wiederherstellen, das Zertifikat und die Datenbank auf einem anderen Gerät fortgesetzt.  
  
Der erste Schritt ist die Erstellung eine Sicherung der Quelldatenbank.  
  
```sql  
BACKUP DATABASE AdventureWorksPDW2012   
TO DISK = '\\SECURE_SERVER\Backups\AdventureWorksPDW2012';  
```  
  
Vorbereiten der neuen SQL Server PDW für TDE durch einen Hauptschlüssel erstellen, Aktivieren der Verschlüsselung und Erstellen von Netzwerkanmeldeinformationen an.  
  
```sql  
USE master;  
GO  
  
-- Create a database master key in the master database  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';  
GO  
  
-- Enable encryption for PDW  
EXEC sp_pdw_database_encryption 1;  
GO  
  
EXEC sp_pdw_add_network_credentials 'SECURE_SERVER', '<domain>\<Windows_user>', '<password>';  
```  
  
Die letzten beiden Schritte erstellen Sie das Zertifikat mit die Sicherungen der ursprünglichen SQL Server PDW neu. Verwenden Sie das Kennwort, das Sie bei der Erstellung der Sicherung des Zertifikats verwendet haben.  
  
```sql  
-- Create certificate in master  
CREATE CERTIFICATE MyServerCert  
    FROM FILE = '\\SECURE_SERVER\cert\MyServerCert.cer'   
    WITH PRIVATE KEY (FILE = '\\SECURE_SERVER\cert\MyServerCert.key',   
    DECRYPTION BY PASSWORD = '<password>');  
  
RESTORE DATABASE AdventureWorksPDW2012   
    FROM DISK = '\\SECURE_SERVER\Backups\AdventureWorksPDW2012';  
```  
  
## <a name="see-also"></a>Siehe auch  
[DATENBANK SICHERN](../t-sql/statements/backup-database-parallel-data-warehouse.md)  
[CREATE MASTER KEY](../t-sql/statements/create-master-key-transact-sql.md) 
[Sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)  
[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
[ZERTIFIKAT ERSTELLEN](../t-sql/statements/create-certificate-transact-sql.md)  
[RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md)
  
