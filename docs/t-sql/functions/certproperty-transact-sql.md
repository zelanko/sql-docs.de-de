---
title: CERTPROPERTY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CERTPROPERTY
- CERTPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], schema names
- schemas [SQL Server], names
- CERTPROPERTY function
ms.assetid: 966c09aa-bc4e-45b0-ba53-c8381871f638
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 6a0f2fc8c2af69832150ab5ab229ffc50c84e831
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68010481"
---
# <a name="certproperty-transact-sql"></a>CERTPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt den Wert einer angegebenen Zertifikateigenschaft zurück.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
CertProperty ( Cert_ID , '<PropertyName>' )  
  
<PropertyName> ::=  
   Expiry_Date | Start_Date | Issuer_Name   
   | Cert_Serial_Number | Subject | SID | String_SID   
```  
  
## <a name="arguments"></a>Argumente  
*Cert_ID*  
Der ID-Wert des Zertifikats, der den Datentyp „int“ aufweist.
  
*Expiry_Date*  
Das Ablaufdatum des Zertifikats.
  
*Start_Date*  
Das Datum, an dem das Zertifikat gültig wird.
  
*Issuer_Name*  
Der Name des Zertifikatausstellers.
  
*Cert_Serial_Number*  
Die Seriennummer des Zertifikats.
  
*Subject*  
Der Zertifikatantragsteller.
  
 *SID*  
Die SID des Zertifikats. Dies ist auch die SID eines diesem Zertifikat zugeordneten Anmeldenamens oder Benutzers.
  
*String_SID*  
Die SID des Zertifikats als Zeichenfolge. Dies ist auch die SID eines diesem Zertifikat zugeordneten Anmeldenamens oder Benutzers.
  
## <a name="return-types"></a>Rückgabetypen
Die Angabe der Eigenschaft muss in einfache Anführungszeichen eingeschlossen werden.
  
Der Rückgabetyp hängt von der im Funktionsaufruf angegebenen Eigenschaft ab. Der Rückgabetyp **sql_variant** umschließt alle Rückgabewerte.
-   *Expiry_Date* und *Start_Date* geben **datetime**zurück.  
-   *Cert_Serial_Number*, *Issuer_Name*, *String_SID* und *Subject* geben **nvarchar** zurück.  
-   *SID* gibt **varbinary**zurück.  
  
## <a name="remarks"></a>Bemerkungen  
Weitere Informationen zu Zertifikaten finden Sie in der Katalogsicht [sys.certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md).
  
## <a name="permissions"></a>Berechtigungen  
Erfordert geeignete Berechtigungen für das Zertifikat, und dem Aufrufer darf die VIEW-Berechtigung für das Zertifikat nicht verweigert worden sein. Weitere Informationen zu Zertifikatberechtigungen finden Sie unter [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md) und [GRANT CERTIFICATE PERMISSIONS &#40;Transact-SQL&#41;](../../t-sql/statements/grant-certificate-permissions-transact-sql.md).
  
## <a name="examples"></a>Beispiele  
Im folgenden Beispiel wird der Zertifikatsantragsteller zurückgegeben.
  
```sql
-- First create a certificate.  
CREATE CERTIFICATE Marketing19 WITH   
    START_DATE = '04/04/2004' ,  
    EXPIRY_DATE = '07/07/2040' ,  
    SUBJECT = 'Marketing Print Division';  
GO  
  
-- Now use CertProperty to examine certificate  
-- Marketing19's properties.  
DECLARE @CertSubject sql_variant;  
set @CertSubject = CertProperty( Cert_ID('Marketing19'), 'Subject');  
PRINT CONVERT(nvarchar, @CertSubject);  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
[ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)  
[CERT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/cert-id-transact-sql.md)
[Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)
[sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)
[Security Catalog Views &#40;Transact-SQL&#41; (Sicherheitskatalogsichten (Transact-SQL))](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)
  
  
