---
description: sys.sp_add_trusted_assembly (Transact-SQL)
title: sys. sp_add_trusted_assembly (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql
ms.technology: system-objects
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
author: VanMSFT
ms.author: vanto
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2e59cd1836a838294904970f00a677a0fdfe6c03
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480882"
---
# <a name="syssp_add_trusted_assembly-transact-sql"></a>sys.sp_add_trusted_assembly (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdbmi-xxxx-xxx-md.md)]

Fügt der Liste der vertrauenswürdigen Assemblys für den Server eine Assembly hinzu.

 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


## <a name="syntax"></a>Syntax
```  
sp_add_trusted_assembly 
    [ @hash = ] 'value'
    [ , [ @description = ] 'description' ]
```  

## <a name="remarks"></a>Bemerkungen  

Diese Prozedur fügt  [sys. trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md)eine Assembly hinzu.

## <a name="arguments"></a>Argumente

[ @hash =] '*Wert*'  
Der SHA2_512 Hashwert der Assembly, die der Liste der vertrauenswürdigen Assemblys für den Server hinzugefügt werden soll. Vertrauenswürdige Assemblys werden möglicherweise geladen, wenn [CLR Strict Security](../../database-engine/configure-windows/clr-strict-security.md) aktiviert ist, auch wenn die Assembly nicht signiert ist oder die Datenbank nicht als vertrauenswürdig gekennzeichnet ist.

[ @description =] '*Beschreibung*'  
Optionale benutzerdefinierte Beschreibung der Assembly. Microsoft empfiehlt die Verwendung des kanonischen Namens, der den einfachen Namen, die Versionsnummer, die Kultur, den öffentlichen Schlüssel und die Architektur der Assembly codiert, die als vertrauenswürdig eingestuft wird. Durch diesen Wert wird die Assembly auf der Seite Common Language Runtime (CLR) eindeutig identifiziert, und Sie entspricht dem clr_name Wert in sys. Assemblys. 

## <a name="permissions"></a>Berechtigungen

Erfordert die Mitgliedschaft in der `sysadmin` Server Rolle oder der Berechtigung "Fixed" `CONTROL SERVER` .

## <a name="examples"></a>Beispiele  

Im folgenden Beispiel wird eine Assembly `pointudt` mit dem Namen zur Liste der vertrauenswürdigen Assemblys für den Server hinzugefügt. Diese Werte sind in  [sys.](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)Assemblys verfügbar.     

```  
EXEC sp_add_trusted_assembly 0x8893AD6D78D14EE43DF482E2EAD44123E3A0B684A8873C3F7BF3B5E8D8F09503F3E62370CE742BBC96FE3394477214B84C7C1B0F7A04DCC788FA99C2C09DFCCC, 
N'pointudt, version=0.0.0.0, culture=neutral, publickeytoken=null, processorarchitecture=msil';
```  

## <a name="see-also"></a>Siehe auch  
  [sys. sp_drop_trusted_assembly](sys-sp-drop-trusted-assembly-transact-sql.md)  
  [sys. trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md)  
  [CREATE ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/create-assembly-transact-sql.md)  
  [CLR Strict Security](../../database-engine/configure-windows/clr-strict-security.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  

