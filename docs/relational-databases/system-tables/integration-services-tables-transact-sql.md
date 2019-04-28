---
title: Integration Services-Tabellen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- SQL Server Integration Services system tables
- system tables [SQL Server], Integration Services
- system tables [Integration Services]
- SSIS, system tables
ms.assetid: 683b181b-0091-4a9c-86db-bc577af43cec
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: d622158b639c912028144ab5003faef91a2030f7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62719431"
---
# <a name="integration-services-tables-transact-sql"></a>Integration Services-Tabellen (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In den Themen in diesem Abschnitt werden die Systemtabellen in der msdb-Datenbank beschrieben, in denen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwendete Informationen gespeichert werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [sysssislog](../../relational-databases/system-tables/sysssislog-transact-sql.md)  
 Enthält eine Zeile für jeden Protokolleintrag, der von einem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paket zur Laufzeit generiert wird.  
  
 Diese Tabelle wird nur verwendet, wenn Pakete den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Protokollanbieter verwenden.  
  
 [sysssispackagefolders](../../relational-databases/system-tables/sysssispackagefolders-transact-sql.md)  
 Enthält eine Zeile für jeden logischen Ordner, den der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Dienst zum Organisieren von Paketen verwendet. Spaltenwerte definieren die Über-/Unterordnungsbeziehungen zwischen geschachtelten Ordnern.  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] zeigt gespeicherte Pakete in einer hierarchischen Sicht an, wenn Sie eine Verbindung zu dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Dienst herstellen.  
  
 [sysssispackages](../../relational-databases/system-tables/sysssispackages-transact-sql.md)  
 Enthält eine Zeile für jedes [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paket.  
  
 Diese Tabelle wird nur verwendet, wenn Sie Pakete in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] speichern.  
  
  
