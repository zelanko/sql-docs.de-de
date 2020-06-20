---
title: Grundlegendes zum WMI-Anbieter für die Konfigurations Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a2ecd601b1329b3b95f1c3827cd04775c93304f6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061279"
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a>Grundlegendes zum WMI-Anbieter für die Konfigurationsverwaltung
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]stellt den WMI-Anbieter für die Konfigurations Verwaltung bereit. So können Sie die Windows-Verwaltungsinstrumentation (WMI) verwenden, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Client- und Servernetzwerkeinstellungen sowie Serveraliase zu verwalten. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Dienste, Netzwerkeinstellungen und Aliase werden durch WMI-Objekte im Namespace root\Microsoft\SqlServer\ComputerManagement*NN* des Computers dargestellt. Nachdem eine Verbindung mit dem WMI-Anbieter auf dem angegebenen Computer hergestellt wurde, können mithilfe von WQL oder einer Skriptsprache Abfragen auf die Dienste, Netzwerkeinstellungen und Aliasnamen ausgeführt werden.  
  
 Der WMI-Anbieter ist ein Instanzanbieter. Sie stellt Instanzen der [WMI-Klassen](../wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md) bereit und unterstützt die folgenden asynchronen Vorgänge.  
  
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
  
 Beispiele für Verwaltungs Anwendungen, die den WMI-Anbieter für die Konfigurations Verwaltung verwenden, finden [Sie unter Verwenden von WQL und Skriptsprachen mit dem WMI-Anbieter für die Konfigurations Verwaltung](using-wql-and-scripting-languages-with-the-wmi-provider.md).  
  
 Weitere Informationen zu Programmier Verwaltungs Anwendungen, die den WMI-Anbieter verwenden, finden Sie in der WMI-Dokumentation im [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework SDK.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit dem WMI-Anbieter für die Konfigurations Verwaltung](working-with-the-wmi-provider-for-configuration-management.md)   
 [Verwenden von WQL und Skriptsprachen mit dem WMI-Anbieter für die Konfigurationsverwaltung](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
