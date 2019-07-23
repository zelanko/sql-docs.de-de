---
title: DROP EXTERNAL DATA SOURCE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 3f65a2f5-a6c6-4be5-8ca4-6057078fe10e
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 54922dc96874142d216e7aedb8c80a44ce40ab31
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67898033"
---
# <a name="drop-external-data-source-transact-sql"></a>DROP EXTERNAL DATA SOURCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Entfernt eine externe PolyBase-Datenquelle.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Drop an external data source  
DROP EXTERNAL DATA SOURCE external_data_source_name  
[;]  
```  
  
## <a name="arguments"></a>Argumente  
 *external_data_source_name*  
 Der Name der zu entfernenden externen Datenquelle.  
  
## <a name="metadata"></a>Metadaten  
 Verwenden Sie die Systemansicht sys.external_data_sources, um eine Liste mit externen Datenquellen anzuzeigen.  
  
```  
SELECT * FROM sys.external_data_sources;  
```  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert ALTER ANY EXTERNAL DATA SOURCE.  
  
## <a name="locking"></a>Sperren  
 Akzeptiert eine gemeinsame Sperre für das externe Datenquellenobjekt.  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Durch das Löschen einer externen Datenquelle werden die externen Daten nicht entfernt.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-basic-syntax"></a>A. Verwenden einer grundlegenden Syntax  
  
```  
DROP EXTERNAL DATA SOURCE mydatasource;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)  
  
  

