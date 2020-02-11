---
title: Wiederherstellen einer über TDE geschützten Datenbank
description: Führen Sie die folgenden Schritte aus, um eine Datenbank wiederherzustellen, die mithilfe der transparenten Datenverschlüsselung in Analytics Platform System parallel Data Warehouse verschlüsselt ist.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 53707c62e018b9923f2bb923a4df46f6917d2902
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400441"
---
# <a name="restore-a-database-protected-by-tde-in-parallel-data-warehouse"></a>Wiederherstellen einer durch TDE geschützten Datenbank parallel Data Warehouse
Führen Sie die folgenden Schritte aus, um eine mit transparenter Datenverschlüsselung verschlüsselte Datenbank wiederherzustellen.  
  
Das [transparent Data Encryption Beispiel verwendet](transparent-data-encryption.md#using-tde) Code zum Aktivieren von TDE für die `AdventureWorksPDW2012` Datenbank. Im folgenden Code wird das Beispiel fortgesetzt, indem eine Sicherung der Datenbank auf dem ursprünglichen Gerät (Analytics Platform System) erstellt und anschließend das Zertifikat und die Datenbank auf einer anderen Appliance wieder hergestellt werden.  
  
Der erste Schritt besteht darin, eine Sicherung der Quelldatenbank zu erstellen.  
  
```sql  
BACKUP DATABASE AdventureWorksPDW2012   
TO DISK = '\\SECURE_SERVER\Backups\AdventureWorksPDW2012';  
```  
  
Bereiten Sie den neuen SQL Server PDW für TDE vor, indem Sie einen Hauptschlüssel erstellen, die Verschlüsselung aktivieren und Netzwerk Anmelde Informationen erstellen.  
  
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
  
In den letzten beiden Schritten wird das Zertifikat mithilfe der Sicherungen aus dem ursprünglichen SQL Server PDW neu erstellt. Verwenden Sie das Kennwort, das Sie beim Erstellen der Sicherung des Zertifikats verwendet haben.  
  
```sql  
-- Create certificate in master  
CREATE CERTIFICATE MyServerCert  
    FROM FILE = '\\SECURE_SERVER\cert\MyServerCert.cer'   
    WITH PRIVATE KEY (FILE = '\\SECURE_SERVER\cert\MyServerCert.key',   
    DECRYPTION BY PASSWORD = '<password>');  
  
RESTORE DATABASE AdventureWorksPDW2012   
    FROM DISK = '\\SECURE_SERVER\Backups\AdventureWorksPDW2012';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md)  
[Hauptschlüssel](../t-sql/statements/create-master-key-transact-sql.md) 
[sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) erstellen  
[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
[Zertifikat erstellen](../t-sql/statements/create-certificate-transact-sql.md)  
[RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md)
  
