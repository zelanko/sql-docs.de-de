---
title: Änderungen am Verhalten von Ablaufverfolgungsflags | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- trace flags [SQL Server], behavior changes
ms.assetid: d739df96-2659-4383-8e10-194657632526
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f03a9db47c6296e7d1c4ab764488c44d343393c7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061311"
---
# <a name="changes-to-behavior-of-trace-flags"></a>Änderungen am Verhalten von Ablaufverfolgungsflags
  Globale Ablaufverfolgungsflags, die von einer Sitzung festgelegt werden, treten in anderen Sitzungen sofort in Kraft. Einige Ablaufverfolgungsflags von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] sind in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nicht verfügbar.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Es empfiehlt sich, alle Ablaufverfolgungsflags zu deaktivieren, bevor Sie ein Upgrade durchführen. Ablaufverfolgungsflags, die die datenbankverfügbarkeit oder wiederherstellungsmodi ändern, könnten verhindern, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] erfolgreich aktualisiert die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können die Ablaufverfolgungsflags aktivieren, nachdem Sie überprüft haben, ob die Ablaufverfolgungsflags erforderlich und in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] immer noch gültig sind. Falls Sie die Ablaufverfolgungsflags erneut aktivieren müssen, sollten Sie zusätzliche Tests für Ihre Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durchführen.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] unterstützt globale Ablaufverfolgungsflags und Ablaufverfolgungsflags auf Sitzungsebene. Ablaufverfolgungsflags können in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] als lokal oder global festgelegt werden, indem Sie ein zusätzliches Argument (-1) im DBCC TRACEON-Befehl verwenden. Wenn Sie dieses Argument nicht angeben, ist der Standardwert lokal.  
  
 Auch in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], das Ablaufverfolgungsflag in Sitzung A festgelegt wird nicht automatisch wirksam in einer bereits vorhandenen Sitzung B. Stattdessen tritt dieses Ablaufverfolgungsflag Auswirkungen erst nach der ersten Mal, das ein Ablaufverfolgungsflag in Sitzung b festgelegt ist Dieses Verhalten ist nicht deterministisch in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] und deterministisch, in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen ist, wobei globale Ablaufverfolgungsflags festgelegt, die in Sitzung A sofort in anderen gleichzeitigen Sitzungen festgelegt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
