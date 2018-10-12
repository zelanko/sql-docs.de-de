---
title: BACKUP CERTIFICATE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/04/2018
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DUMP_CERTIFICATE_TSQL
- BACKUP CERTIFICATE
- sql13.swb.exportcertificate.f1
- DUMP CERTIFICATE
- BACKUP_CERTIFICATE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- encryption [SQL Server], certificates
- decryption [SQL Server], certificates
- exporting certificates
- certificates [SQL Server], exporting
- BACKUP CERTIFICATE statement
- backing up certificates [SQL Server]
- decryption [SQL Server]
- cryptography [SQL Server], certificates
ms.assetid: 509b9462-819b-4c45-baae-3d2d90d14a1c
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: bf65c24924d7e585131d90d01c42cf551ae4997d
ms.sourcegitcommit: 7d702a1d01ef72ad5e133846eff6b86ca2edaff1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2018
ms.locfileid: "48798560"
---
# <a name="backup-certificate-transact-sql"></a>BACKUP CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Exportiert ein Zertifikat in eine Datei.  
  
 ![Linksymbol](../../database-engine/configure-windows/media/topic-link.gif "Linksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Syntax for SQL Server  
  
BACKUP CERTIFICATE certname TO FILE = 'path_to_file'  
    [ WITH PRIVATE KEY   
      (   
        FILE = 'path_to_private_key_file' ,  
        ENCRYPTION BY PASSWORD = 'encryption_password'   
        [ , DECRYPTION BY PASSWORD = 'decryption_password' ]   
      )   
    ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
BACKUP CERTIFICATE certname TO FILE ='path_to_file'  
      WITH PRIVATE KEY   
      (   
        FILE ='path_to_private_key_file',  
        ENCRYPTION BY PASSWORD ='encryption_password'   
      )   
```  
  
## <a name="arguments"></a>Argumente  
 *path_to_file*  
 Gibt den vollständigen Pfad einschließlich des Dateinamens zu der Datei an, in der das Zertifikat gespeichert werden soll. Dieser Pfad kann ein lokaler Pfad oder ein UNC-Pfad zu einer Netzwerkadresse sein. Standardmäßig wird der Pfad zum DATA-Ordner von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet.  
  
 *path_to_private_key_file*  
 Gibt den vollständigen Pfad einschließlich des Dateinamens zu der Datei an, in der der private Schlüssel gespeichert werden soll. Dieser Pfad kann ein lokaler Pfad oder ein UNC-Pfad zu einer Netzwerkadresse sein. Standardmäßig wird der Pfad zum DATA-Ordner von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet.  

 *encryption_password*  
 Das Kennwort, das zum Verschlüsseln des privaten Schlüssels verwendet wird, bevor der Schlüssel in die Sicherungsdatei geschrieben wird. Das Kennwort unterliegt Komplexitätsüberprüfungen.  
  
 *decryption_password*  
 Das Kennwort, das zum Entschlüsseln des privaten Schlüssels verwendet wird, bevor der Schlüssel gesichert wird. Dieses Argument ist nicht erforderlich, wenn das Zertifikat mit dem Hauptschlüssel verschlüsselt ist. 
  
## <a name="remarks"></a>Remarks  
 Falls der private Schlüssel mit einem Kennwort in der Datenbank verschlüsselt wird, muss das Kennwort für die Entschlüsselung angegeben werden.  
  
 Bei der Sicherung des privaten Schlüssels in einer Datei ist eine Verschlüsselung erforderlich. Das Kennwort, mit dem das Zertifikat geschützt wird, ist nicht dasselbe Kennwort, mit dem der private Schlüssel des Zertifikats verschlüsselt wird.  
  
 Ein gesichertes Zertifikat kann mithilfe der [CREATE CERTIFICATE](../../t-sql/statements/create-certificate-transact-sql.md)-Anweisung wiederhergestellt werden.
 
 Bei einer Sicherung werden die Dateien für das Dienstkonto der SQL Server-Instanz der ACL hinzugefügt. Wenn Sie das Zertifikat auf einem Server wiederherstellen müssen, der unter einem anderen Konto ausgeführt wird, müssen Sie die Berechtigungen für die Dateien so anpassen, dass sie von dem neuen Konto gelesen werden können. 
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL-Berechtigung für das Zertifikat und die Kenntnis des Kennworts, das zum Verschlüsseln des privaten Schlüssels verwendet wurde. Falls nur der öffentliche Teil des Zertifikats gesichert wird, sind bei diesem Befehl bestimmte Berechtigungen für das Zertifikat erforderlich, und dem Aufrufer darf die VIEW-Berechtigung für das Zertifikat nicht verweigert worden sein.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-exporting-a-certificate-to-a-file"></a>A. Exportieren eines Zertifikats in eine Datei  
 Im folgenden Beispiel wird ein Zertifikat in eine Datei exportiert.  
  
```  
BACKUP CERTIFICATE sales05 TO FILE = 'c:\storedcerts\sales05cert';  
GO  
```  
  
### <a name="b-exporting-a-certificate-and-a-private-key"></a>B. Exportieren eines Zertifikats und eines privaten Schlüssels  
 Im folgenden Beispiel wird der private Schlüssel des zu sichernden Zertifikats mit dem Kennwort `997jkhUbhk$w4ez0876hKHJH5gh` verschlüsselt.  
  
```  
BACKUP CERTIFICATE sales05 TO FILE = 'c:\storedcerts\sales05cert'  
    WITH PRIVATE KEY ( FILE = 'c:\storedkeys\sales05key' ,   
    ENCRYPTION BY PASSWORD = '997jkhUbhk$w4ez0876hKHJH5gh' );  
GO  
```  
  
### <a name="c-exporting-a-certificate-that-has-an-encrypted-private-key"></a>C. Exportieren eines Zertifikats mit einem verschlüsselten privaten Schlüssel  
 Im folgenden Beispiel ist der private Schlüssel des Zertifikats in der Datenbank verschlüsselt. Der private Schlüssel muss mit dem Kennwort `9875t6#6rfid7vble7r` entschlüsselt werden. Beim Speichern des Zertifikats in der Sicherungsdatei wird der private Schlüssel mit dem Kennwort `9n34khUbhk$w4ecJH5gh` verschlüsselt.  
  
```  
BACKUP CERTIFICATE sales09 TO FILE = 'c:\storedcerts\sales09cert'   
    WITH PRIVATE KEY ( DECRYPTION BY PASSWORD = '9875t6#6rfid7vble7r' ,  
    FILE = 'c:\storedkeys\sales09key' ,   
    ENCRYPTION BY PASSWORD = '9n34khUbhk$w4ecJH5gh' );  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-certificate-transact-sql.md)  
  
  

