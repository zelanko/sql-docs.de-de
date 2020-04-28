---
title: sys. crypt_properties (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- crypt_properties
- crypt_properties_TSQL
- sys.crypt_properties_TSQL
- sys.crypt_properties
dev_langs:
- TSQL
helpviewer_keywords:
- sys.crypt_properties catalog view
ms.assetid: d5684f5a-30b1-418e-ae4d-ab040db9257e
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9655866d4fd2d6f98b38532f77f94bc12f16f9b4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68109481"
---
# <a name="syscrypt_properties-transact-sql"></a>sys.crypt_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede Kryptografieeigenschaft zurück, die einem sicherungsfähigen Element zugeordnet ist.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**class**|**tinyint**|Identifiziert die Klasse des Objekts, für das die Eigenschaft vorhanden ist.<br /><br /> 1 = Objekt oder Spalte<br /> 5 = Assembly|  
|**class_desc**|**nvarchar(60)**|Beschreibung der Klasse des Objekts, für das die Eigenschaft vorhanden ist.<br /><br /> OBJECT_OR_COLUMN<br /> ASSEMBLY|  
|**major_id**|**int**|ID des Objekts, für das die Eigenschaft vorhanden ist, interpretiert nach der Klasse.|  
|**Fingerabdruck**|**varbinary(32)**|SHA-1-Hash des verwendeten Zertifikats oder des verwendeten asymmetrischen Schlüssels.|  
|**crypt_type**|**char (4)**|Verschlüsselungstyp.<br /><br /> SPVC = mit privatem Zertifikat Schlüssel signiert<br /><br /> SPVA = mit asymmetrischem privatem Schlüssel signiert<br /><br /> CPVC = Gegensignatur mit privatem Zertifikatschlüssel<br /><br /> CPVA = Gegensignatur mit asymmetrischem Schlüssel|  
|**crypt_type_desc**|**nvarchar(60)**|Beschreibung des Verschlüsselungstyps.<br /><br /> SIGNATURE BY CERTIFICATE<br /><br /> SIGNATURE BY ASYMMETRIC KEY<br /><br /> COUNTER SIGNATURE BY CERTIFICATE<br /><br /> COUNTER SIGNATURE BY ASYMMETRIC KEY|  
|**crypt_property**|**varbinary(max)**|Signierte oder verschlüsselte Bits. Bei einem signierten Modul sind dies die Signatur Bits des Moduls.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheits Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Verschlüsselungs Hierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Sicherungs fähige Elemente](../../relational-databases/security/securables.md)   
 [Erstellen eines Zertifikats &#40;Transact-SQL-&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [Erstellen eines symmetrischen Schlüssels &#40;Transact-SQL-&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Erstellen eines asymmetrischen Schlüssels &#40;Transact-SQL-&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
