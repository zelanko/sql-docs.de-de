---
description: sys.database_scoped_configurations (Transact-SQL)
title: sys.database_scoped_configurations (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- database_scoped_configurations
- database_scoped_configurations_TSQL
- sys.database_scoped_configurations
- sys.database_scoped_configurations_TSQL
helpviewer_keywords:
- sys.database_scoped_configurations catalog view
dev_langs:
- TSQL
ms.assetid: 8899310a-3464-4d38-9f2f-88396c4e7dc2
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current||= azure-sqldw-latest
ms.openlocfilehash: ad4e9036670f90f126ad9c1f693de43ff9660517
ms.sourcegitcommit: b3a711a673baebb2ff10d7142b209982b46973ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93364652"
---
# <a name="sysdatabase_scoped_configurations-transact-sql"></a>sys.database_scoped_configurations (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-asdb-addw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

Enthält eine Zeile pro Konfiguration. 

|Spaltenname|Datentyp|Beschreibung|
|-----------------|---------------|-----------------|
|**configuration_id**|**int**|ID der Konfigurationsoption.|
|**name**|**nvarchar(60)**|Der Name der Konfigurationsoption. Informationen zu den möglichen Konfigurationen finden Sie unter [ALTER DATABASE scoped Configuration &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|
|**value**|**sqlvariant**|Der Wert, der für diese Konfigurationsoption für das primäre Replikat festgelegt wird.|
|**value_for_secondary**|**sqlvariant**|Der für diese Konfigurationsoption für die sekundären Replikate festgelegte Wert.|
|**is_value_default**|**bit** |Gibt an, ob der festgelegte Wert der Standardwert ist.|

## <a name="permissions"></a><a name="Permissions"></a> Berechtigungen

Erfordert die Mitgliedschaft in der **public** -Rolle.

## <a name="remarks"></a>Bemerkungen

Wenn NULL als Wert für **value_for_secondary** zurückgegeben wird, bedeutet dies, dass das sekundäre Replikat auf Primary festgelegt ist.
 
Die datenbankweit gültigen Konfigurationseinstellungen werden mit der Datenbank übertragen. Dies bedeutet, dass die vorhandenen Konfigurationseinstellungen bei der Wiederherstellung oder dem Anfügen einer bestimmten Datenbank erhalten bleiben.

## <a name="see-also"></a>Weitere Informationen

[ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)
