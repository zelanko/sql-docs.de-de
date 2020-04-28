---
title: Die Berichts Server-Datenbank ist nicht konfiguriert (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: b964300c-b220-4244-9fa6-c0c6a57760f6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: bb5dd5968930319532a29ff7c3909c36af99b3a0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952111"
---
# <a name="report-server-database-is-not-configured-upgrade-advisor"></a>Berichtsserver-Datenbank ist nicht konfiguriert (Upgrade Advisor)
  Das Upgrade wird aufgrund einer unvollständigen Berichtsserverkonfiguration blockiert. Die Berichtsserver-Datenbank ist nicht konfiguriert.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Setup kann nur eine vollständig konfigurierte Berichtsserverinstanz aktualisieren. Um den Vorgang fortzusetzen, müssen Sie entweder die Berichts Server-Datenbank konfigurieren oder die Microsoft Windows- **Systemsteuerung** verwenden, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Berichts Server Funktion aus der-Installation zu entfernen. Nachdem Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] entfernt haben, können Sie andere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten aktualisieren.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Wenn Sie die Berichtsserver-Datenbank nicht konfiguriert haben, ist der Berichtsserver nicht betriebsbereit und muss vor dem Upgrade entfernt werden.  
  
 Weitere Informationen zum Deinstallieren von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] finden Sie unter [Deinstallieren von Reporting Services 2012](https://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\)). Im Thema wird beschrieben, wie eine bestimmte Version deinstalliert wird; die Vorgehensweise dabei ist für frühere Versionen ähnlich.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services Upgradeprobleme &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
