---
title: CERT_ID (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CERT_ID
- CERT_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- identification numbers [SQL Server], certificates
- CERT_ID function
- IDs [SQL Server], certificates
- certificates [SQL Server], IDs
ms.assetid: 59cc06f5-272e-4936-8afe-afba7aba8eea
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: e90d32ca718990c6b75f796e8df32bf45797b8f8
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65945852"
---
# <a name="certid-transact-sql"></a>CERT_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Diese Funktion gibt den ID-Wert eines Zertifikats zurück.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
Cert_ID ( 'cert_name' )  
```  
  
## <a name="arguments"></a>Argumente  
**'** *cert_name* **'**  

Der Name des Zertifikats in der Datenbank.
  
## <a name="return-types"></a>Rückgabetypen
 **ssNoversion**  
  
## <a name="remarks"></a>Remarks  
Zertifikatsnamen werden in der Katalogsicht [sys.certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md) angezeigt.
  
## <a name="permissions"></a>Berechtigungen  
Erfordert geeignete Berechtigungen für das Zertifikat, und dem Aufrufer darf die VIEW DEFINITION-Berechtigung für das Zertifikat nicht verweigert worden sein. Weitere Informationen zu Zertifikatberechtigungen finden Sie unter [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md#permissions).
  
## <a name="examples"></a>Beispiele  
In diesem Beispiel wird die ID eines Zertifikats namens `ABerglundCert3` zurückgegeben.
  
```sql
SELECT Cert_ID('ABerglundCert3');  
GO  
```  
  
## <a name="see-also"></a>Siehe auch
[sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)  
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
[Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)
  
  
