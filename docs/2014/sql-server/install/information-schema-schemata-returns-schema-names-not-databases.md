---
title: INFORMATION_SCHEMA. Schemata gibt Schema Namen in einer Datenbank zurück, nicht Datenbanken in einer Instanz. Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0e3683ee043785ec6adc349ac52301280c7bc2b8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66094731"
---
# <a name="information_schemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a>INFORMATION_SCHEMA.SCHEMATA gibt Schemanamen in einer Datenbank, nicht Datenbanken in einer Instanz zurück
  Der Upgrade Advisor hat Anweisungen erkannt, die auf die INFORMATION_SCHEMA.SCHEMATA-Sicht verweisen. In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gab diese Sicht alle Datenbanken in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurück. In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höher gibt die Sicht alle Schemas in einer Datenbank zurück.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gab die INFORMATION_SCHEMA.SCHEMATA-Sicht alle Datenbanken in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurück. Jetzt gibt die Sicht alle Schemas in einer Datenbank zurück, die dem SQL-Standard entsprechen.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Ändern Sie die Anwendung so, dass Sie auf die **sys. Datenbanken** -Katalog Sicht verweist, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]alle Datenbanken in einer Instanz von zurückzugeben  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
