---
title: Installieren des Upgrade Advisors | Microsoft Docs
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
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: 1b7d6eca-1df1-47df-bbba-0fc485706a95
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6cde30d3dd12f6f072d4cb83f869700c7357484f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148047"
---
# <a name="installing-upgrade-advisor"></a>Installieren des Upgrade Advisors
  Der Speicherort für das Installieren des Upgrade Advisors für SQL Server 2014 ist abhängig davon, was analysiert werden soll. Der Upgrade Advisor unterstützt die Remoteanalyse aller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten mit Ausnahme von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Wenn Sie keine Instanzen von Scannen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], Sie können Upgrade Advisor installieren, auf jedem Computer, die eine Verbindung herstellen kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und erfüllt sind, die die [Upgrade Advisor Voraussetzungen](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md). Wenn Sie Instanzen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] scannen, müssen Sie den Upgrade Advisor auf dem Berichtsserver installieren.  
  
 Führen Sie die **SQLUA.msi** Datei zum Installieren des Upgrade Advisors. Sie können über die Eingabeaufforderung für unbeaufsichtigte und automatisierte Installationen installieren. Finden Sie unter [Installation von Upgrade Advisor von der Befehlszeile aus](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md) Syntax und Beispiele.  
  
 Rufen Sie die SQLUA.msi auf:  
  
-   In der **Redist** Ordner, der die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Produktmedien.  
  
-   Als Teil der [SQL 2014 Feature Pack-Download](http://www.microsoft.com/download/details.aspx?id=42295).  
  
## <a name="uninstalling-upgrade-advisor"></a>Deinstallieren des Upgrade Advisors  
 Sie können Upgrade Advisor mithilfe Deinstallieren **Software**. Die Syntax der Eingabeaufforderung unterstützt auch das Entfernen/Deinstallieren.  
  
  