---
title: Grundlegendes zum WMI-Anbieter für die Konfigurationsverwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: de76b774083c6744e5bfad34aa0fed24952793be
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68139402"
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a>Grundlegendes zum WMI-Anbieter für die Konfigurationsverwaltung
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Stellt den WMI-Anbieter für die Konfigurationsverwaltung bereit. So können Sie die Windows-Verwaltungsinstrumentation (WMI) verwenden, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Client- und Servernetzwerkeinstellungen sowie Serveraliase zu verwalten. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienste, Netzwerkeinstellungen und Aliasnamen werden von WMI-Objekten im Root\Microsoft\SqlServer\ComputerManagement dargestellt*Nn* -Namespace des Computers. Nachdem eine Verbindung mit dem WMI-Anbieter auf dem angegebenen Computer hergestellt wurde, können mithilfe von WQL oder einer Skriptsprache Abfragen auf die Dienste, Netzwerkeinstellungen und Aliasnamen ausgeführt werden.  
  
 Der WMI-Anbieter ist ein Instanzanbieter. Er gibt Instanzen der dem [WMI-Klassen](../../relational-databases/wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md) und unterstützt die folgenden asynchronen Vorgänge.  
  
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
  
 Beispiele für die verwaltungsanwendung, die den WMI-Anbieter für die Konfigurationsverwaltung verwenden, finden Sie unter [Verwenden von WQL und Skriptsprachen mit dem WMI-Anbieter für die Konfigurationsverwaltung](../../relational-databases/wmi-provider-configuration/using-wql-and-scripting-languages-with-the-wmi-provider.md).  
  
 Weitere Informationen über das Programmieren von verwaltungsanwendungen mithilfe der WMI-Anbieter finden Sie unter der WMI-Dokumentation in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework SDK.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit dem WMI-Anbieter für die Konfigurationsverwaltung](../../relational-databases/wmi-provider-configuration/working-with-the-wmi-provider-for-configuration-management.md)   
 [Verwenden von WQL und Skriptsprachen mit dem WMI-Anbieter für die Konfigurationsverwaltung](../../relational-databases/wmi-provider-configuration/using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
