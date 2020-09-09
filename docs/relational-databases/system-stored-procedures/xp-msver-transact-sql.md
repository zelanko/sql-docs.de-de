---
description: xp_msver (Transact-SQL)
title: xp_msver (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_msver_TSQL
- xp_msver
dev_langs:
- TSQL
helpviewer_keywords:
- xp_msver
ms.assetid: 9264cf8c-92ba-45ad-b2d6-15d26d805a16
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a736447de4215d7f9c630036ae13872ff9d58bff
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89544705"
---
# <a name="xp_msver-transact-sql"></a>xp_msver (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt Versionsinformationen zu zurück [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . **xp_msver** gibt auch Informationen über die tatsächliche Buildnummer des Servers und Informationen zur Serverumgebung zurück. Die Informationen, die **xp_msver** zurückgibt, können in [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen,-Batches, gespeicherten Prozeduren usw. verwendet werden, um die Logik für plattformunabhängigen Code zu verbessern.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
xp_msver [ optname ]  
```  
  
## <a name="arguments"></a>Argumente  
 *optname*  
 Der Name einer Option. Die folgenden Werte sind möglich.  
  
|Options-/Spaltenname|BESCHREIBUNG|  
|-------------------------|-----------------|  
|**ProductName**|Produktname; Beispiel: [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|**ProductVersion**|Die Produktversion.|  
|**Sprache**|Die Sprachversion von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Plattform**|Der Name des Betriebssystems, des Herstellers und der Chipfamilie für den Computer, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.|  
|**Kommentare**|Verschiedene Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**CompanyName**|Der Name der Firma, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellt. Beispiel: [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corporation.|  
|**FileDescription**|Dem Betriebssystem|  
|**File Version**|Version der ausführbaren Datei von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**InternalName**|Von [!INCLUDE[msCoName](../../includes/msconame-md.md)] verwendeter interner Name für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Beispiel: SQLSERVR.|  
|**LegalCopyright**|Urheberrechtliche Informationen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Beispiel: Copyright© [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corp. 1988-2005.|  
|**LegalTrademarks**|Markeninformationen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[msCoName](../../includes/msconame-md.md)] ist z. B. eine eingetragene Marke der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corporation.|  
|**OriginalFilename**|Der Name der Datei, die beim Start von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird. Beispiel: Sqlservr.exe.|  
|**PrivateBuild**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**SpecialBuild**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**WindowsVersion**|Version von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, die auf dem Computer installiert ist, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.|  
|**ProcessorCount**|Die Anzahl der Prozessoren in dem Computer, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.|  
|**ProcessorActiveMask**|Gibt die Prozessoren in dem Computer an, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, die gestartet werden und von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows verwendet werden können.|  
|**ProcessorType**|Der Prozessortyp. Vergleichbar mit **Platform**.|  
|**PhysicalMemory**|Die Menge an Arbeitsspeicher (RAM) in Megabyte (MB), die auf dem Computer installiert ist, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.|  
|**Produkt-ID**|Product ID (PID). Wird bei der Installation angegeben. Diese Nummer finden Sie auf dem Aufkleber der Hülle der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Original-CD.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 1 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 **xp_msver**ohne Parameter gibt ein vier spaltige Resultset zurück, das alle Optionswerte auflistet. **xp_msver**gibt für jeden Parameter das vier spaltige Resultset mit Werten für diese Option zurück.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Systemfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-category-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Allgemeine erweiterte gespeicherte Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [@@VERSION &#40;Transact-SQL&#41;](../../t-sql/functions/version-transact-sql-configuration-functions.md)  
  
  
