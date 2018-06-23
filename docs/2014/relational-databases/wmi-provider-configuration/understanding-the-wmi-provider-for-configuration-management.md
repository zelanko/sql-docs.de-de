---
title: Grundlegendes zum WMI-Anbieter für die Konfigurationsverwaltung | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 459bb3bb7843a0f962d9747ac702da23909ca9fc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160618"
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a>Grundlegendes zum WMI-Anbieter für die Konfigurationsverwaltung
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Stellt den WMI-Anbieter für die Konfigurationsverwaltung bereit. So können Sie die Windows-Verwaltungsinstrumentation (WMI) verwenden, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Client- und Servernetzwerkeinstellungen sowie Serveraliase zu verwalten. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienste, Netzwerkeinstellungen und Aliasnamen werden von WMI-Objekten im Root\Microsoft\SqlServer\ComputerManagement dargestellt*Nn* -Namespace des Computers. Nachdem eine Verbindung mit dem WMI-Anbieter auf dem angegebenen Computer hergestellt wurde, können mithilfe von WQL oder einer Skriptsprache Abfragen auf die Dienste, Netzwerkeinstellungen und Aliasnamen ausgeführt werden.  
  
 Der WMI-Anbieter ist ein Instanzanbieter. Er gibt Instanzen der dem [WMI-Klassen](../wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md) und unterstützt die folgenden asynchronen Vorgänge.  
  
 Instanzabruf  
 Abrufen einer bestimmten Klassentypinstanz.  
  
 Enumeration  
 Enumeration aller Instanzen eines Klassentyps.  
  
 Modifikation (Modification)  
 Änderung einer bestimmten Instanz eines Klassentyps.  
  
 Klassen verfügen über Methoden, die die Änderung ihrer Eigenschaften ermöglichen.  
  
 Löschen  
 Entfernen einer bestimmten Instanz eines Klassentyps.  
  
 Verarbeiten von Abfragen  
 Enumeration der Instanzen eines Klassentyps auf Grundlage eines Filters.  
  
 Beispiele für die verwaltungsanwendung, die mithilfe der WMI-Anbieter für die Konfigurationsverwaltung finden Sie unter [Verwenden von WQL und Skriptsprachen, mit dem WMI-Anbieter für die Konfigurationsverwaltung](using-wql-and-scripting-languages-with-the-wmi-provider.md).  
  
 Weitere Informationen über das Programmieren von verwaltungsanwendungen mithilfe der WMI-Anbieter finden Sie in der WMI-Dokumentation in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework SDK.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit dem WMI-Anbieter für die Verwaltung](working-with-the-wmi-provider-for-configuration-management.md)   
 [Verwenden von WQL und Skriptsprachen mit dem WMI-Anbieter für die Konfigurationsverwaltung](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  