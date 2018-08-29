---
title: Sys.trusted_assemblies (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- trusted_assemblies_TSQL
- trusted_assemblies
- sys.trusted_assemblies_TSQL
- sys.trusted_assemblies
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trusted_assemblies
ms.assetid: ''
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 989233e4e13a26b316a554a908a1282d384565f6
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43081083"
---
# <a name="systrustedassemblies-transact-sql"></a>Sys.trusted_assemblies (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Enthält eine Zeile für jeden vertrauenswürdigen Assembly für den Server an.

 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


|Spaltenname |Datentyp |Description |
|--- |--- |--- |
|Hashindizes |varbinary(8000) |SHA2_512 Hash dem Inhalt der Assembly. |
|description |nvarchar(4000) |Optionale benutzerdefinierte Beschreibung der Assembly. Microsoft empfiehlt die Verwendung des kanonischen Namens, der den einfachen Namen, Versionsnummer, Kultur, öffentlichen Schlüssel und Architektur der Assembly, die vertrauen codiert. Dieser Wert eindeutig identifiziert die Assembly, auf der Seite der common Language Runtime (CLR) und entspricht der Wert Clr_name in sys.assemblies. |
|create_date |datetime2 |Datum, an die Assembly zur Liste der vertrauenswürdigen Assemblys hinzugefügt wurde. |
|created_by |nvarchar(128) |Der Anmeldename des Prinzipals, der die Assembly zur Liste hinzugefügt. |
| | | |


## <a name="remarks"></a>Hinweise  

Verwendung **müssen Sp_add_trusted_assembly hinzufügen** und **müssen sys.trusted_assemblies hinzufügen** hinzufügen oder Entfernen von Assemblys aus `sys.trusted_assemblies`.

## <a name="see-also"></a>Siehe auch  
  [sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md) [sys.sp_drop_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md) [DROP ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  

