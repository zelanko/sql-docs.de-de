---
title: managed_backup. fn_get_current_xevent_settings (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 4133f8bb64d5d7e2e2b511c2128b9ddbca1fa550
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67910246"
---
# <a name="managed_backupfn_get_current_xevent_settings-transact-sql"></a>managed_backup. fn_get_current_xevent_settings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jeden erweiterten Ereignistyp zurück, der von Smart Admin unterstützt wird.  
  
 Verwenden Sie diese Funktion, um die aktuellen Einstellungen für erweiterte Ereignisse zurückzugeben bzw. zu überprüfen. So können Sie den Typ der konfigurierbaren Ereignisse und die aktuellen Konfigurationen identifizieren.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
smart_admin.fn_get_current_xevent_settings ()   
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Argumentation  
 Diese Funktion weist keine Argumente auf.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
 Die Kanäle Admin, Analytic und Operation der erweiterten Ereignisse sind erforderlich, standardmäßig aktiviert und nicht konfigurierbar.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|Event_name|NVARCHAR(128)|Erweiterter Ereignistyp|  
|is_configurable|NVARCHAR(128)|Dieser Wert wird auf **true** festgelegt, wenn das Ereignis konfiguriert werden kann. andernfalls wird **false**festgelegt.|  
|is_enabled|NVARCHAR(128)|Ist auf True festgelegt, wenn das Ereignis aktiviert ist; ist auf False festgelegt, wenn es nicht aktiviert ist. Verwenden Sie den smart_admin.sp_set_parameter, um Debugereignisse zu aktivieren.|  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert **Select** -Berechtigungen für die Funktion.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle erweiterten Ereignisse und deren aktueller Status zurückgegeben.  
  
```  
SELECT *   
FROM smart_admin.fn_get_current_xevent_settings ()  
  
```  
  
  
