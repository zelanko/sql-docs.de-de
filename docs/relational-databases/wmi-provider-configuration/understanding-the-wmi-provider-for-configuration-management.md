---
title: WMI-Anbieter für die Konfigurationsverwaltung
description: Erfahren Sie, wie der WMI-Anbieter für die Konfigurations Verwaltung WMI verwendet, um Dienste, Server Aliase und Client/Server-Netzwerkeinstellungen in SQL Server zu verwalten.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8f915756b2d2e0e340c296e767738f8589fb5a5d
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542788"
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a>Grundlegendes zum WMI-Anbieter für die Konfigurationsverwaltung
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]stellt den WMI-Anbieter für die Konfigurations Verwaltung bereit. So können Sie die Windows-Verwaltungsinstrumentation (WMI) verwenden, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Client- und Servernetzwerkeinstellungen sowie Serveraliase zu verwalten. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienste, Netzwerkeinstellungen und Aliase werden durch WMI-Objekte im Namespace root\Microsoft\SqlServer\ComputerManagement*NN* des Computers dargestellt. Nachdem eine Verbindung mit dem WMI-Anbieter auf dem angegebenen Computer hergestellt wurde, können mithilfe von WQL oder einer Skriptsprache Abfragen auf die Dienste, Netzwerkeinstellungen und Aliasnamen ausgeführt werden.  
  
 Der WMI-Anbieter ist ein Instanzanbieter. Sie stellt Instanzen der [WMI-Klassen](../../relational-databases/wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md) bereit und unterstützt die folgenden asynchronen Vorgänge.  
  
 Instanzabruf  
 Abrufen einer bestimmten Klassentypinstanz.  
  
 Enumeration  
 Enumeration aller Instanzen eines Klassentyps.  
  
 Modifikation (Modification)  
 Änderung einer bestimmten Instanz eines Klassentyps.  
  
 Klassen verfügen über Methoden, die die Änderung ihrer Eigenschaften ermöglichen.  
  
 Löschen  
 Entfernen einer bestimmten Instanz eines Klassentyps.  
  
 Abfrageverarbeitung  
 Enumeration der Instanzen eines Klassentyps auf Grundlage eines Filters.  
  
 Beispiele für Verwaltungs Anwendungen, die den WMI-Anbieter für die Konfigurations Verwaltung verwenden, finden [Sie unter Verwenden von WQL und Skriptsprachen mit dem WMI-Anbieter für die Konfigurations Verwaltung](../../relational-databases/wmi-provider-configuration/using-wql-and-scripting-languages-with-the-wmi-provider.md).  
  
 Weitere Informationen zu Programmier Verwaltungs Anwendungen, die den WMI-Anbieter verwenden, finden Sie in der WMI-Dokumentation im [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework SDK.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit dem WMI-Anbieter für die Konfigurations Verwaltung](../../relational-databases/wmi-provider-configuration/working-with-the-wmi-provider-for-configuration-management.md)   
 [Verwenden von WQL und Skriptsprachen mit dem WMI-Anbieter für die Konfigurationsverwaltung](../../relational-databases/wmi-provider-configuration/using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
