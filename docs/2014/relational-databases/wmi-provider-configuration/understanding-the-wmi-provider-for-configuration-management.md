---
title: Grundlegendes zum WMI-Anbieter für die Konfigurationsverwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 238e8e52ec238e8387fd49d82f15368ef9be3d0b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222331"
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
  
 Beispiele für die verwaltungsanwendung, die den WMI-Anbieter für die Konfigurationsverwaltung verwenden, finden Sie unter [Verwenden von WQL und Skriptsprachen mit dem WMI-Anbieter für die Konfigurationsverwaltung](using-wql-and-scripting-languages-with-the-wmi-provider.md).  
  
 Weitere Informationen über das Programmieren von verwaltungsanwendungen mithilfe der WMI-Anbieter finden Sie unter der WMI-Dokumentation in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework SDK.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit dem WMI-Anbieter für die Konfigurationsverwaltung](working-with-the-wmi-provider-for-configuration-management.md)   
 [Verwenden von WQL und Skriptsprachen mit dem WMI-Anbieter für die Konfigurationsverwaltung](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
