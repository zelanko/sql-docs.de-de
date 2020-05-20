---
title: dbo. syscategories (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.syscategories_TSQL
- syscategories
- syscategories_TSQL
- dbo.syscategories
dev_langs:
- TSQL
helpviewer_keywords:
- syscategories system table
ms.assetid: eb2cb75c-dc58-4a5b-b329-664e9fe20ce0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fc4d6f55ca4e131abef21772911da923b854c81b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82813885"
---
# <a name="dbosyscategories-transact-sql"></a>dbo.syscategories (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält die Kategorien, die von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] zur Organisation von Aufträgen, Warnungen und Operatoren verwendet werden. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|ID der Kategorie|  
|**category_class**|**int**|Elementart in der Kategorie:<br /><br /> **1** = Auftrag<br /><br /> **2** = Warnung<br /><br /> **3** =-Operator|  
|**category_type**|**tinyint**|Typ der Kategorie:<br /><br /> **1** = lokal<br /><br /> **2** = MultiServer<br /><br /> **3** = keine|  
|**name**|**sysname**|Name der Kategorie|  
  
  
