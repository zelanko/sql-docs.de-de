---
title: CURRENT_REQUEST_ID (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CURRENT_REQUEST_ID_TSQL
- CURRENT_REQUEST_ID
dev_langs:
- TSQL
helpviewer_keywords:
- CURRENT_REQUEST_ID
ms.assetid: 949f6e5f-bf5f-49d6-a763-c443d1d51fe2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d4eb54d5762466b19f83c1e03ce3194e1d996b19
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "87112059"
---
# <a name="current_request_id-transact-sql"></a>CURRENT_REQUEST_ID (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Diese Funktion gibt die ID der aktuellen Anforderung innerhalb der aktuellen Sitzung zurück.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
CURRENT_REQUEST_ID()  
```  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
**smallint**
  
## <a name="remarks"></a>Bemerkungen  
Verwenden Sie @@SPID, um genaue Informationen über die aktuelle Sitzung zu suchen. Genaue Informationen über die aktuelle Anforderung erhalten Sie über CURRENT_REQUEST_ID().
  
## <a name="see-also"></a>Weitere Informationen
[@@SPID &#40;Transact-SQL&#41;](../../t-sql/functions/spid-transact-sql.md)
  
  
