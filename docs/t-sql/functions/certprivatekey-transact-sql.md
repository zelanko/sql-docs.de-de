---
title: CERTPRIVATEKEY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CERTPRIVATEKEY
- CERTPRIVATEKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CERTPRIVATEKEY
ms.assetid: 33e0f01e-39ac-46da-94ff-fe53b1116df4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f58f6859c57a16f5715d8a0f54c30775277b0c8d
ms.sourcegitcommit: 5d6e1c827752c3aa2d02c4c7653aefb2736fffc3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "49071824"
---
# <a name="certprivatekey-transact-sql"></a>CERTPRIVATEKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Diese Funktion gibt den privaten Schlüssel eines Zertifikats im Binärformat zurück. Diese Funktion akzeptiert drei Argumente.
-   Eine Zertifikat-ID.  
-   Ein Verschlüsselungskennwort, das verwendet wird, um die Bits des privaten Schlüssels zu verschlüsseln, die von der Funktion zurückgegeben werden. Diese Vorgehensweise legt die Schlüssel nicht als Klartext für Benutzer offen.  
-   Ein optionales Entschlüsselungskennwort. Ein angegebenes Entschlüsselungskennwort wird verwendet, um den privaten Schlüssel für dieses Zertifikat zu entschlüsseln. Andernfalls wird der Hauptschlüssel der Datenbank verwendet.  
  
Diese Funktion kann nur von Benutzern mit Zugriff auf den privaten Zertifikatschlüssel verwendet werden. Diese Funktion gibt den privaten Schlüssel im PVK-Format zurück.
  
## <a name="syntax"></a>Syntax  
  
```sql
CERTPRIVATEKEY   
    (  
          cert_ID   
        , ' encryption_password '   
      [ , ' decryption_password ' ]  
    )  
```  
  
## <a name="arguments"></a>Argumente  
*certificate_ID*  
Die **certificate_id** des Zertifikats. Rufen Sie diesen Wert von „sys.certificates“ oder von [CERT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/cert-id-transact-sql.md) ab. *cert-id* weist den Datentyp **int** auf.
  
*encryption_password*  
Das Kennwort, das verwendet wird, um den zurückgegebenen Binärwert zu verschlüsseln.
  
*decryption_password*  
Das Kennwort, das verwendet wird, um den zurückgegebenen Binärwert zu entschlüsseln.
  
## <a name="return-types"></a>Rückgabetypen
**varbinary**
  
## <a name="remarks"></a>Remarks  
Verwenden Sie **CERTENCODED** und **CERTPRIVATEKEY** zusammen, um andere Teile eines Zertifikats in binärer Form zurückzugeben.
  
## <a name="permissions"></a>Berechtigungen  
**CERTPRIVATEKEY** ist öffentlich verfügbar.
  
## <a name="examples"></a>Beispiele  
  
```sql
CREATE DATABASE TEST1;  
GO  
USE TEST1  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'Use 5tr0ng P^55Words'  
GO  
CREATE CERTIFICATE Shipping04   
WITH SUBJECT = 'Sammamish Shipping Records',   
EXPIRY_DATE = '20401031';  
GO  
SELECT CERTPRIVATEKEY(CERT_ID('Shipping04'), 'jklalkaa/; uia3dd');  
```  
  
Ein komplexeres Beispiel für die Verwendung von [CERTPRIVATEKEY](../../t-sql/functions/certencoded-transact-sql.md) und **CERTENCODED** zum Kopieren eines Zertifikats in eine andere Datenbank finden Sie in Beispiel B im Artikel zu **CERTENCODED &#40;Transact-SQL&#41;**.
  
## <a name="see-also"></a>Siehe auch
[Sicherheitsfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)
[Sicherheitsfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)
[sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)
  
  
