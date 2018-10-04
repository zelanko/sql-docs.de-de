---
title: managed_backup.fn_get_current_xevent_settings (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_get_current_xevent_settings
- smart_admin.fn_get_current_xevent_settings_TSQL
- fn_get_current_xevent_settings_TSQL
- smart_admin.fn_get_current_xevent_settings
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_get_current_xevent_settings
- fn_get_current_xevent_settings
ms.assetid: 95d3adaa-bb9d-4833-b8b4-3d9fd4f9c82a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1fa350d9ff9d5e90eb595f1f693b8e62a46fa555
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47741058"
---
# <a name="managedbackupfngetcurrentxeventsettings-transact-sql"></a>managed_backup.fn_get_current_xevent_settings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jeden erweiterten Ereignistyp zurück, der von Smart Admin unterstützt wird.  
  
 Verwenden Sie diese Funktion, um die aktuellen Einstellungen für erweiterte Ereignisse zurückzugeben bzw. zu überprüfen. So können Sie den Typ der konfigurierbaren Ereignisse und die aktuellen Konfigurationen identifizieren.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
smart_admin.fn_get_current_xevent_settings ()   
```  
  
##  <a name="Arguments"></a> Argumente  
 Diese Funktion weist keine Argumente auf.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
 Die Kanäle Admin, Analytic und Operation der erweiterten Ereignisse sind erforderlich, standardmäßig aktiviert und nicht konfigurierbar.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|Event_name|NVARCHAR(128)|Erweiterter Ereignistyp|  
|is_configurable|NVARCHAR(128)|Dieser Wert auf festgelegt **"true"** Wenn das Ereignis konfigurierbar ist, andernfalls festgelegt werden, **"false"**.|  
|is_enabled|NVARCHAR(128)|Ist auf True festgelegt, wenn das Ereignis aktiviert ist; ist auf False festgelegt, wenn es nicht aktiviert ist. Verwenden Sie den smart_admin.sp_set_parameter, um Debugereignisse zu aktivieren.|  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert **wählen** Berechtigungen für die Funktion.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle erweiterten Ereignisse und deren aktueller Status zurückgegeben.  
  
```  
SELECT *   
FROM smart_admin.fn_get_current_xevent_settings ()  
  
```  
  
  
