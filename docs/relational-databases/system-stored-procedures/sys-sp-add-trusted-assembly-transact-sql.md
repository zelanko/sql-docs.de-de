---
title: sp_add_trusted_assembly (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_trusted_assembly_TSQL
- sp_add_trusted_assembly
- sys.sp_add_trusted_assembly_TSQL
- sys.sp_add_trusted_assembly
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_add_trusted_assembly
ms.assetid: ''
caps.latest.revision: ''
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 04462f743de60857717e978c5b3f454b18994439
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43086783"
---
# <a name="sysspaddtrustedassembly-transact-sql"></a>sp_add_trusted_assembly (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Fügt eine Assembly zur Liste der vertrauenswürdigen Assemblys für den Server an.

 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


## <a name="syntax"></a>Syntax
```  
sp_add_trusted_assembly 
    [ @hash = ] 'value'
    [ , [ @description = ] 'description' ]
```  

## <a name="remarks"></a>Hinweise  

Diese Prozedur fügt eine Assembly [sys.trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md).

## <a name="arguments"></a>Argumente

[ @hash =] '*Wert*"  
Der Hashwert des SHA2_512 der Assembly, die die Liste der vertrauenswürdigen Assemblys für den Server hinzu. Vertrauenswürdige können Assemblys laden, wenn [CLR strict Security](../../database-engine/configure-windows/clr-strict-security.md) aktiviert ist, auch wenn die Assembly nicht signiert ist oder die Datenbank ist nicht als vertrauenswürdig gekennzeichnet.

[ @description =] '*Beschreibung*"  
Optionale benutzerdefinierte Beschreibung der Assembly. Microsoft empfiehlt die Verwendung des kanonischen Namens, der den einfachen Namen, Versionsnummer, Kultur, öffentlichen Schlüssel und Architektur der Assembly, die vertrauen codiert. Dieser Wert eindeutig identifiziert die Assembly, auf der Seite der common Language Runtime (CLR) und entspricht der Wert Clr_name in sys.assemblies. 

## <a name="permissions"></a>Berechtigungen

Erfordert die Mitgliedschaft in der `sysadmin` -Serverrolle sein oder `CONTROL SERVER` Berechtigung.

## <a name="examples"></a>Beispiele  

Im folgenden Beispiel wird eine Assembly namens `pointudt` zur Liste der vertrauenswürdigen Assemblys für den Server. Diese Werte stehen über [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md).     

```  
EXEC sp_add_trusted_assembly 0x8893AD6D78D14EE43DF482E2EAD44123E3A0B684A8873C3F7BF3B5E8D8F09503F3E62370CE742BBC96FE3394477214B84C7C1B0F7A04DCC788FA99C2C09DFCCC, 
N'pointudt, version=0.0.0.0, culture=neutral, publickeytoken=null, processorarchitecture=msil';
```  

## <a name="see-also"></a>Siehe auch  
  [sys.sp_drop_trusted_assembly](sys-sp-drop-trusted-assembly-transact-sql.md)  
  [sys.trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md)  
  [CREATE ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/create-assembly-transact-sql.md)  
  [CLR strict security](../../database-engine/configure-windows/clr-strict-security.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  

