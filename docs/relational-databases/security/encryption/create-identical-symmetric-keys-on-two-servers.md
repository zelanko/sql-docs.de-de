---
title: Erstellen identischer symmetrischer Schlüssel auf zwei Servern | Microsoft Dokumentation
description: Hier erfahren Sie, wie Sie mithilfe von Transact-SQL identische symmetrische Schlüssel für zwei Server in SQL Server erstellen. Dabei wird die Verschlüsselung in separaten Datenbanken oder Servern unterstützt.
ms.custom: ''
ms.date: 05/30/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- symmetric keys [SQL Server], creating
ms.assetid: a13d0b21-a43b-43c0-9c22-7ba8f3d15e80
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c0cdf5dee29f2035ddb700f29df9c0bbb993c0aa
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97479371"
---
# <a name="create-identical-symmetric-keys-on-two-servers"></a>Erstellen identischer symmetrischer Schlüssel auf zwei Servern
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  In diesem Thema wird beschrieben, wie identische symmetrische Schlüssel in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[tsql](../../../includes/tsql-md.md)]auf zwei verschiedenen Servern erstellt werden. Zum Entschlüsseln von verschlüsseltem Text benötigen Sie den Schlüssel, der beim Verschlüsseln verwendet wurde. Wenn eine Datenbank sowohl Verschlüsselungen als auch Entschlüsselungen enthält, ist der Schlüssel in der Datenbank gespeichert, und er ist entsprechend den Berechtigungen sowohl für die Verschlüsselung als auch für die Entschlüsselung verfügbar. Wenn sich Verschlüsselung und Entschlüsselung jedoch in separaten Datenbanken oder auf separaten Servern befinden, kann der in einer Datenbank gespeicherte Schlüssel nicht für die zweite Datenbank verwendet werden.
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
### <a name="limitations-and-restrictions"></a>Einschränkungen  
  
- Beim Erstellen eines symmetrischen Schlüssels muss der symmetrische Schlüssel mithilfe mindestens eines der folgenden Elemente verschlüsselt werden: Zertifikat, Kennwort, symmetrischer Schlüssel, asymmetrischer Schlüssel oder PROVIDER. Der Schlüssel kann mehrere Verschlüsselungen jedes Typs aufweisen. Ein einzelner symmetrischer Schlüssel kann demnach mit mehreren Zertifikaten, Kennwörtern, symmetrischen Schlüsseln und asymmetrischen Schlüsseln gleichzeitig verschlüsselt sein.  
  
- Wenn ein symmetrischer Schlüssel mit einem Kennwort anstatt mit einem öffentlichen Schlüssel des Datenbank-Hauptschlüssels verschlüsselt ist, wird der TRIPLE_DES-Verschlüsselungsalgorithmus verwendet. Daher werden Schlüssel, die mit einem starken Verschlüsselungsalgorithmus wie z. B. AES erstellt werden, selbst mit einem schwächeren Algorithmus verschlüsselt.  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY SYMMETRIC KEY-Berechtigung in der Datenbank. Falls die AUTHORIZATION-Klausel angegeben ist, ist die IMPERSONATE-Berechtigung für den Datenbankbenutzer oder die ALTER-Berechtigung für die Anwendungsrolle erforderlich. Falls die Verschlüsselung mit einem Zertifikat oder asymmetrischen Schlüssel erfolgt, ist die VIEW DEFINITION-Berechtigung für das Zertifikat oder den asymmetrischen Schlüssel erforderlich. Nur Windows-Anmeldungen, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldungen und Anwendungsrollen können symmetrische Schlüssel besitzen. Gruppen und Rollen können keine symmetrischen Schlüssel besitzen.  
  
## <a name="using-transact-sql"></a>Verwenden von Transact-SQL  
  
### <a name="to-create-identical-symmetric-keys-on-two-different-servers"></a>So erstellen Sie identische symmetrische Schlüssel auf zwei verschiedenen Servern  
  
1. Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Instanz her.  
  
2. Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3. Erstellen Sie einen Schlüssel, indem Sie die folgenden CREATE MASTER KEY-, CREATE CERTIFICATE- und CREATE SYMMETRIC KEY-Anweisungen ausführen.  
  
    ```sql
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'My p@55w0Rd';  
    GO  
    CREATE CERTIFICATE [cert_keyProtection] WITH SUBJECT = 'Key Protection';  
    GO  
    CREATE SYMMETRIC KEY [key_DataShare] WITH  
        KEY_SOURCE = 'My key generation bits. This is a shared secret!',  
        ALGORITHM = AES_256,   
        IDENTITY_VALUE = 'Key Identity generation bits. Also a shared secret'  
        ENCRYPTION BY CERTIFICATE [cert_keyProtection];  
    GO  
    ```  
  
4. Stellen Sie eine Verbindung mit einer separaten Serverinstanz her, öffnen Sie ein anderes Abfragefenster, und führen Sie die oben erwähnten SQL-Anweisungen aus, um den gleichen Schlüssel auf dem zweiten Server zu erstellen.  
  
5. Testen Sie die Schlüssel, indem Sie zunächst die OPEN SYMMETRIC KEY-Anweisung und die SELECT-Anweisung unten auf dem ersten Server ausführen.  
  
    ```sql
    OPEN SYMMETRIC KEY [key_DataShare]   
        DECRYPTION BY CERTIFICATE cert_keyProtection;  
    GO  
    SELECT encryptbykey(key_guid('key_DataShare'), 'MyData' )  
    GO  
    -- For example, the output might look like this: 0x2152F8DA8A500A9EDC2FAE26D15C302DA70D25563DAE7D5D1102E3056CE9EF95CA3E7289F7F4D0523ED0376B155FE9C3  
    ```  
  
6. Fügen Sie auf dem zweiten Server das Ergebnis der vorherigen SELECT-Anweisung als Wert für `@blob` in den folgenden Code ein, und führen Sie den folgenden Code aus, um zu überprüfen, ob der verschlüsselte Text mit dem doppelten Schlüssel entschlüsselt werden kann.  
  
    ```sql
    OPEN SYMMETRIC KEY [key_DataShare]   
        DECRYPTION BY CERTIFICATE cert_keyProtection;  
    GO  
    DECLARE @blob varbinary(8000);  
    SET @blob = SELECT CONVERT(varchar(8000), decryptbykey(@blob));  
    GO  
    ```  
  
7. Schließen Sie den symmetrischen Schlüssel auf beiden Servern.  
  
    ```sql
    CLOSE SYMMETRIC KEY [key_DataShare];  
    GO  
    ```  

### <a name="encryption-changes-in-sql-server-2017-cu2"></a>Änderungen der Verschlüsselung in SQL Server 2017 CU2

SQL Server 2016 verwendet den Hashalgorithmus SHA1 für die Verschlüsselung. Ab SQL Server 2017 wird stattdessen SHA2 verwendet. Das bedeutet, dass zusätzliche Schritte erforderlich sein können, damit Ihre SQL Server 2017-Installation Elemente entschlüsselt, die von SQL Server 2016 verschlüsselt wurden. Nachfolgend sind diese zusätzlichen Schritte aufgeführt:

- Stellen Sie sicher, dass Ihre SQL Server 2017-Installation mindestens auf das kumulative Update 2 (CU2) aktualisiert ist.
  - Wichtige Details finden Sie unter [Kumulatives Update 2 (CU2) für SQL Server 2017](https://support.microsoft.com/help/4052574).
- Nach der Installation von CU2 aktivieren Sie das Ablaufverfolgungsflag 4631 in SQL Server 2017: `DBCC TRACEON(4631, -1);`
  - Das Ablaufverfolgungsflag 4631 ist neu in SQL Server 2017. Das Ablaufverfolgungsflag 4631 muss global auf `ON` gesetzt sein, bevor Sie den Hauptschlüssel, das Zertifikat oder den symmetrischen Schlüssel in SQL Server 2017 erstellen. Dadurch können diese erstellten Elemente mit SQL Server 2016 und früheren Versionen zusammenarbeiten.

Weitere Anleitungen finden Sie unter folgenden Themen:

- [FIX: SQL Server 2017 kann Daten, die von früheren SQL Server-Versionen verschlüsselt wurden, nicht mit demselben symmetrischen Schlüssel entschlüsseln](https://support.microsoft.com/help/4053407/sql-server-2017-cannot-decrypt-data-encrypted-by-earlier-versions)
- [Für SQL Server 2017 und andere SQL Server-Versionen können keine identischen symmetrischen Schlüssel verwendet werden](https://feedback.azure.com/forums/908035-sql-server/suggestions/33116269-identical-symmetric-keys-do-not-work-between-sql-s) <!-- Issue 2225. Thank you Stephen W and Sam Rueby. -->

## <a name="for-more-information"></a>Weitere Informationen finden Sie unter

-   [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-master-key-transact-sql.md)  
  
-   [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../../t-sql/statements/create-certificate-transact-sql.md)  
  
-   [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-symmetric-key-transact-sql.md)  
  
-   [ENCRYPTBYKEY &#40;Transact-SQL&#41;](../../../t-sql/functions/encryptbykey-transact-sql.md)  
  
-   [DECRYPTBYKEY &#40;Transact-SQL&#41;](../../../t-sql/functions/decryptbykey-transact-sql.md)  
  
-   [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/open-symmetric-key-transact-sql.md)  
