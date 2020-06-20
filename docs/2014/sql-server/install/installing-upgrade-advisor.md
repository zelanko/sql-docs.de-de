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
ms.openlocfilehash: 40f214b01f3e2066708a060c5f3ad1e8aa4a0a23
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065342"
---
# <a name="installing-upgrade-advisor"></a>Installieren des Upgrade Advisors
  Der Speicherort für das Installieren des Upgrade Advisors für SQL Server 2014 ist abhängig davon, was analysiert werden soll. Der Upgrade Advisor unterstützt die Remoteanalyse aller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten mit Ausnahme von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Wenn Sie keine Instanzen von Scannen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , können Sie den Upgrade Advisor auf einem beliebigen Computer installieren, der eine Verbindung mit herstellen kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und die die [Voraussetzungen des Upgrade Advisors](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)erfüllt. Wenn Sie Instanzen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] scannen, müssen Sie den Upgrade Advisor auf dem Berichtsserver installieren.  
  
 Führen Sie die **SQLUA.msi** Datei aus, um den Upgrade Advisor zu installieren. Sie können über die Eingabeaufforderung für unbeaufsichtigte und automatisierte Installationen installieren. Syntax und Beispiele finden Sie [unter Installieren von Upgrade Advisor von der Eingabeaufforderung aus](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md) .  
  
 Rufen Sie die SQLUA.msi auf:  
  
-   Im Ordner **Redist** des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Produkt Mediums.  
  
-   Als Teil des [SQL 2014 Feature Pack-Downloads](https://www.microsoft.com/download/details.aspx?id=42295).  
  
## <a name="uninstalling-upgrade-advisor"></a>Deinstallieren des Upgrade Advisors  
 Sie können den Upgrade **Advisor mithilfe der**Option Software deinstallieren. Die Syntax der Eingabeaufforderung unterstützt auch das Entfernen/Deinstallieren.  
  
  
