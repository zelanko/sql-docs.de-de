---
title: Änderungen am Verhalten von Ablaufverfolgungsflags | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- trace flags [SQL Server], behavior changes
ms.assetid: d739df96-2659-4383-8e10-194657632526
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 447e6d4d35fa77f71f1a7a1b90a5a782e0ccebcc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66096621"
---
# <a name="changes-to-behavior-of-trace-flags"></a>Änderungen am Verhalten von Ablaufverfolgungsflags
  Globale Ablaufverfolgungsflags, die von einer Sitzung festgelegt werden, treten in anderen Sitzungen sofort in Kraft. Einige Ablaufverfolgungsflags von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] sind in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nicht verfügbar.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Es empfiehlt sich, alle Ablaufverfolgungsflags zu deaktivieren, bevor Sie ein Upgrade durchführen. Ablaufverfolgungsflags, die die Daten Bank Verfügbarkeit oder Wiederherstellungsmodi ändern, können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verhindern [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dass Ihre Instanz von erfolgreich aktualisiert. [!INCLUDE[ssDE](../../includes/ssde-md.md)] Sie können die Ablaufverfolgungsflags aktivieren, nachdem Sie überprüft haben, ob die Ablaufverfolgungsflags erforderlich und in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] immer noch gültig sind. Falls Sie die Ablaufverfolgungsflags erneut aktivieren müssen, sollten Sie zusätzliche Tests für Ihre Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durchführen.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] unterstützt globale Ablaufverfolgungsflags und Ablaufverfolgungsflags auf Sitzungsebene. Ablaufverfolgungsflags können in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] als lokal oder global festgelegt werden, indem Sie ein zusätzliches Argument (-1) im DBCC TRACEON-Befehl verwenden. Wenn Sie dieses Argument nicht angeben, ist der Standardwert lokal.  
  
 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]Außerdem wird ein in Sitzung a fest gelegenes Ablaufverfolgungsflag in einer bereits vorhandenen Sitzung B nicht automatisch wirksam. Stattdessen tritt dieses Ablaufverfolgungsflag erst dann in Kraft, wenn in Sitzung B das erste Ablaufverfolgungsflag festgelegt ist. Dieses Verhalten ist in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] nicht deterministisch und in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen deterministisch, wobei globale Ablaufverfolgungsflags, die in Sitzung A festgelegt werden, sofort in anderen gleichzeitigen Sitzungen festgelegt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
