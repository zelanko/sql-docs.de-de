---
description: DROP EXTERNAL FILE FORMAT (Transact-SQL)
title: DROP EXTERNAL FILE FORMAT (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8cf9009b-59f9-4aac-bef1-dcf2cf0708b2
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2b5a652162f8dc80c7406913bb17c6c23119153b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88478850"
---
# <a name="drop-external-file-format-transact-sql"></a>DROP EXTERNAL FILE FORMAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Entfernt ein externes PolyBase-Dateiformat.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
-- Drop an external file format  
DROP EXTERNAL FILE FORMAT external_file_format_name  
[;]  
```  
  
## <a name="arguments"></a>Argumente  
 *external_file_format_name*  
 Der Name des zu löschenden externen Dateiformats.  
  
## <a name="metadata"></a>Metadaten  
 In der Systemansicht [sys.external_file_formats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md) finden Sie eine Liste mit den externen Dateiformaten.  
  
```sql  
SELECT * FROM sys.external_file_formats;  
```  
  
## <a name="permissions"></a>Berechtigungen  
 Macht das ALTER ANY EXTERNAL FILE FORMAT erforderlich.  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Durch das Löschen eines externen Dateiformats werden die externen Daten nicht entfernt.  
  
## <a name="locking"></a>Sperren  
 Akzeptiert eine gemeinsame Sperre für das Objekt im externen Dateiformat.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-basic-syntax"></a>A. Verwenden einer grundlegenden Syntax  
  
```sql  
DROP EXTERNAL FILE FORMAT myfileformat;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)  
  
  

