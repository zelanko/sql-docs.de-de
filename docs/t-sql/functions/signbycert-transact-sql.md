---
description: SIGNBYCERT (Transact-SQL)
title: SIGNBYCERT (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SIGNBYCERT
- SIGNBYCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- text signing [SQL Server]
- encryption [SQL Server], certificates
- certificates [SQL Server], text signing
- SignByCert function
- signing text [SQL Server]
- SIGNBYCERT function
- cryptography [SQL Server], certificates
ms.assetid: b4c6bced-4473-4bae-85b9-56deced495f9
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: acc73e861b0c27b4a1fa46e7c4c2efa0e23cb55d
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2020
ms.locfileid: "91378837"
---
# <a name="signbycert-transact-sql"></a>SIGNBYCERT (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Signiert Text mit einem Zertifikat und gibt die Signatur zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql 
SignByCert ( certificate_ID , @cleartext [ , 'password' ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *certificate_ID*  
 Die ID eines Zertifikats in der aktuellen Datenbank. *certificate_ID* ist vom Datentyp **int**.  
  
 *\@cleartext*  
 Eine Variable vom Typ **nvarchar**, **char**, **varchar**oder **nchar**, die mit einem Zertifikat signierte Daten enthält.  
  
 **'** *password* **'**  
 Das Kennwort, mit dem der private Schlüssel des Zertifikats verschlüsselt wurde. *password* ist vom Datentyp **nvarchar(128)**.  
  
## <a name="return-types"></a>Rückgabetypen  
 **varbinary** mit einer maximalen Größe von 8.000 Bytes.  
  
## <a name="remarks"></a>Hinweise  
 Erfordert die CONTROL-Berechtigung für das Zertifikat.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Text in `@SensitiveData` mit dem Zertifikat `ABerglundCert07` signiert, nachdem zuvor das Zertifikat mit dem Kennwort "pGFD4bb925DGvbd2439587y" entschlüsselt wurde. Anschließend werden der Klartext und die Signatur in die `SignedData04`-Tabelle eingefügt.  
  
```sql  
DECLARE @SensitiveData NVARCHAR(max);  
SET @SensitiveData = N'Saddle Price Points are   
    2, 3, 5, 7, 11, 13, 17, 19, 23, 29';  
INSERT INTO [SignedData04]  
    VALUES( N'data signed by certificate ''ABerglundCert07''',  
    @SensitiveData, SignByCert( Cert_Id( 'ABerglundCert07' ),   
    @SensitiveData, N'pGFD4bb925DGvbd2439587y' ));  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VERIFYSIGNEDBYCERT &#40;Transact-SQL&#41;](../../t-sql/functions/verifysignedbycert-transact-sql.md)   
 [CERT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/cert-id-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
