---
description: CERT_ID (Transact-SQL)
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
ms.openlocfilehash: 70e1cb5ea77b6bd779d63cd349f1478cda31598f
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91114950"
---
# <a name="cert_id-transact-sql"></a>CERT_ID (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Diese Funktion gibt den ID-Wert eines Zertifikats zurück.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
Cert_ID ( 'cert_name' )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
**'** *cert_name* **'**  

Der Name des Zertifikats in der Datenbank.
  
## <a name="return-types"></a>Rückgabetypen
 **int**  
  
## <a name="remarks"></a>Bemerkungen  
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
  
  
