---
title: ALTER CERTIFICATE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/18/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER_CERTIFICATE_TSQL
- ALTER CERTIFICATE
dev_langs:
- TSQL
helpviewer_keywords:
- ENCRYPTION BY PASSWORD option
- encryption [SQL Server], certificates
- modifying certificates
- private keys [SQL Server]
- ALTER CERTIFICATE statement
- certificates [SQL Server], modifying
ms.assetid: da4dc25e-72e0-4036-87ce-22de83160836
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1e83bc2c83f654ae82ed5a84c33f5801c5a06549
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47781338"
---
# <a name="alter-certificate-transact-sql"></a>ALTER CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  Ändert den privaten Schlüssel, mit dem ein Zertifikat verschlüsselt wird, oder fügt einen privaten Schlüssel hinzu, falls keiner vorhanden ist. Ändert die Verfügbarkeit eines Zertifikats für [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
ALTER CERTIFICATE certificate_name   
      REMOVE PRIVATE KEY  
    | WITH PRIVATE KEY ( <private_key_spec> [ ,... ] )  
    | WITH ACTIVE FOR BEGIN_DIALOG = [ ON | OFF ]  
  
<private_key_spec> ::=   
      FILE = 'path_to_private_key'   
    | DECRYPTION BY PASSWORD = 'key_password'   
    | ENCRYPTION BY PASSWORD = 'password'   
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
ALTER CERTIFICATE certificate_name   
{  
      REMOVE PRIVATE KEY  
    | WITH PRIVATE KEY (   
        FILE = '<path_to_private_key>',  
        DECRYPTION BY PASSWORD = '<key password>' )
}  
```  
  
## <a name="arguments"></a>Argumente  
 *certificate_name*  
 Der eindeutige Name, unter dem das Zertifikat in der Datenbank bekannt ist.  
  
 FILE **='**_path\_to\_private\_key_**'**  
 Gibt den vollständigen Pfad einschließlich des Dateinamens für den privaten Schlüssel an. Dieser Parameter kann ein lokaler Pfad oder ein UNC-Pfad zu einem Netzwerkspeicherort sein. Auf diese Datei wird im Sicherheitskontext des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienstkontos zugegriffen. Wenn Sie diese Option verwenden, müssen Sie sicherstellen, dass das Dienstkonto Zugriff auf die angegebene Datei hat.  
  
 DECRYPTION BY PASSWORD **='**_key\_password_**'**  
 Gibt das zum Entschlüsseln des privaten Schlüssels erforderliche Kennwort an.  
  
 ENCRYPTION BY PASSWORD **='**_password_**'**  
 Gibt das Kennwort an, mit dem der private Schlüssel des Zertifikats in der Datenbank verschlüsselt wird. *password* muss den Anforderungen der Windows-Kennwortrichtlinien des Computers entsprechen, auf dem die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird. Weitere Informationen finden Sie unter [Password Policy](../../relational-databases/security/password-policy.md).  
  
 REMOVE PRIVATE KEY  
 Gibt an, dass der private Schlüssel nicht mehr in der Datenbank verwaltet werden soll.  
  
 ACTIVE FOR BEGIN_DIALOG **=** { ON | OFF }  
 Stellt das Zertifikat für den Initiator einer [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Dialogkonversation zur Verfügung.  
  
## <a name="remarks"></a>Remarks  
 Der private Schlüssel muss dem öffentlichen Schlüssel entsprechen, der mit *certificate_name* angegeben ist.  
  
 Die DECRYPTION BY PASSWORD-Klausel kann ausgelassen werden, falls das Kennwort in der Datei mit einem NULL-Kennwort geschützt ist.  
  
 Wenn der private Schlüssel eines Zertifikats, das bereits in der Datenbank vorhanden ist, aus einer Datei importiert wird, wird der private Schlüssel automatisch mit dem Datenbank-Hauptschlüssel geschützt. Verwenden Sie die ENCRYPTION BY PASSWORD-Klausel, um den privaten Schlüssel mit einem Kennwort zu schützen.  
  
 Mit der Option REMOVE PRIVATE KEY wird der private Schlüssel des Zertifikats aus der Datenbank gelöscht. Sie können den privaten Schlüssel entfernen, wenn das Zertifikat zum Überprüfen von Signaturen oder für [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Szenarien, die keinen privaten Schlüssel erfordern, verwendet wird. Den privaten Schlüssel eines Zertifikats, das einen symmetrischen Schlüssel schützt, dürfen Sie nicht entfernen.  
  
 Sie müssen kein Entschlüsselungskennwort angeben, wenn der private Schlüssel mithilfe des Datenbank-Hauptschlüssels verschlüsselt wird.  
  
> [!IMPORTANT]  
>  Erstellen Sie immer eine Archivierungskopie eines privaten Schlüssels, bevor Sie ihn aus einer Datenbank entfernen. Weitere Informationen finden Sie unter [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md).  
  
 Die Option WITH PRIVATE KEY ist in einer enthaltenen Datenbank nicht verfügbar.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER-Berechtigung für das Zertifikat.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-changing-the-password-of-a-certificate"></a>A. Ändern des Kennworts für ein Zertifikat  
  
```  
ALTER CERTIFICATE Shipping04   
    WITH PRIVATE KEY (DECRYPTION BY PASSWORD = 'pGF$5DGvbd2439587y',  
    ENCRYPTION BY PASSWORD = '4-329578thlkajdshglXCSgf');  
GO  
```  
  
### <a name="b-changing-the-password-that-is-used-to-encrypt-the-private-key"></a>B. Ändern des Kennworts, das zum Verschlüsseln des privaten Schlüssels verwendet wird  
  
```  
ALTER CERTIFICATE Shipping11   
    WITH PRIVATE KEY (ENCRYPTION BY PASSWORD = '34958tosdgfkh##38',  
    DECRYPTION BY PASSWORD = '95hkjdskghFDGGG4%');  
GO  
```  
  
### <a name="c-importing-a-private-key-for-a-certificate-that-is-already-present-in-the-database"></a>C. Importieren eines privaten Schlüssels für ein Zertifikat, das bereits in der Datenbank vorhanden ist  
  
```  
ALTER CERTIFICATE Shipping13   
    WITH PRIVATE KEY (FILE = 'c:\\importedkeys\Shipping13',  
    DECRYPTION BY PASSWORD = 'GDFLKl8^^GGG4000%');  
GO  
```  
  
### <a name="d-changing-the-protection-of-the-private-key-from-a-password-to-the-database-master-key"></a>D. Ändern des Schutzes für den privaten Schlüssel von einem Kennwort in den Datenbank-Hauptschlüssel  
  
```  
ALTER CERTIFICATE Shipping15   
    WITH PRIVATE KEY (DECRYPTION BY PASSWORD = '95hk000eEnvjkjy#F%');  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

