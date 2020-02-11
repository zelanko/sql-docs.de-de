---
title: Installieren von Upgrade Advisor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: 1b7d6eca-1df1-47df-bbba-0fc485706a95
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7f70d1cbb879f8fc91e48478fb820b71b51bfd2d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66094317"
---
# <a name="installing-upgrade-advisor"></a>Installieren des Upgrade Advisors
  Der Speicherort für das Installieren des Upgrade Advisors für SQL Server 2014 ist abhängig davon, was analysiert werden soll. Der Upgrade Advisor unterstützt die Remoteanalyse aller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten mit Ausnahme von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Wenn Sie keine Instanzen von Scannen, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]können Sie den Upgrade Advisor auf einem beliebigen Computer installieren, der eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Verbindung mit herstellen kann und die die [Voraussetzungen des Upgrade Advisors](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)erfüllt. Wenn Sie Instanzen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] scannen, müssen Sie den Upgrade Advisor auf dem Berichtsserver installieren.  
  
 Führen Sie die Datei **SQLUA. msi** aus, um den Upgrade Advisor zu installieren. Sie können über die Eingabeaufforderung für unbeaufsichtigte und automatisierte Installationen installieren. Syntax und Beispiele finden Sie [unter Installieren von Upgrade Advisor von der Eingabeaufforderung aus](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md) .  
  
 Rufen Sie die SQLUA.msi auf:  
  
-   Im Ordner **Redist** des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Produkt Mediums.  
  
-   Als Teil des [SQL 2014 Feature Pack-Downloads](https://www.microsoft.com/download/details.aspx?id=42295).  
  
## <a name="uninstalling-upgrade-advisor"></a>Deinstallieren des Upgrade Advisors  
 Sie können den Upgrade **Advisor mithilfe der**Option Software deinstallieren. Die Syntax der Eingabeaufforderung unterstützt auch das Entfernen/Deinstallieren.  
  
  
