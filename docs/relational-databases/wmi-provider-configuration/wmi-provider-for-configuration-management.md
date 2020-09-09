---
title: Konzepte des WMI-Anbieters für die Konfigurationsverwaltung
description: Erfahren Sie mehr über den WMI-Anbieter, der mit SQL Server-Konfigurations-Manager in der Microsoft Management Console und Microsoft SQL Server Configuration Manager verwendet wird.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management
- SQL Server WMI Provider
- configuration management [WMI]
- WMI Provider for Configuration Management, about WMI Provider for Configuration Management
ms.assetid: 7e41db24-b915-4eb8-a1d6-e6948ee915b7
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8a93cebef339d72a80139d079f5f14fffaa119f7
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545202"
---
# <a name="wmi-provider-for-configuration-management"></a>WMI-Anbieter für die Konfigurationsverwaltung
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Der WMI-Anbieter ist eine veröffentlichte Ebene, die mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager-Snap-in für die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (MMC) und die Configuration Manager verwendet wird [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Sie bietet eine vereinheitlichte Schnittstellenfunktion zu API-Aufrufen, mit denen die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager angeforderten Registrierungsvorgänge verwaltet werden, und ermöglicht eine verbesserte Steuerung und Bearbeitung der ausgewählten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-WMI-Anbieter besteht aus einer DLL- und einer MOF-Datei, die automatisch von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup kompiliert werden.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-WMI-Anbieter enthält einen Satz Objektklassen, die zur Steuerung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste mittels folgender Methoden verwendet werden:  
  
-   Eine Skriptsprache wie VBScript, [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] oder Perl, in die Windows Query Language (WQL) eingebettet werden kann  
  
-   Das <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>-Objekt in einem von SMO verwalteten Codeprogramm  
  
-   Den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager oder MMC mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI-Anbieter-Snap-In  
  
## <a name="using-a-script-language"></a>Verwenden einer Skriptsprache  
 Die Verwendung einer Skriptsprache bietet folgende Vorteile:  
  
-   Eine Entwicklungsumgebung ist nicht erforderlich.  
  
-   Die Dateien, die die Skriptsprache unterstützen, sind überall verfügbar.  
  
 Das Skript kann neben dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI-Anbieter auch in Verbindung mit anderen WMI-Anbietern verwendet werden. Ein Domänenadministrator kann ein Skript verwenden, um Dienste, Netzwerkeinstellungen und Aliaseinstellungen auf mehreren Computern in einem Netzwerk einzurichten.  
  
 In diesem Abschnitt wird detaillierter darauf eingegangen, wie von Skripts auf den WMI-Anbieter für die Konfigurationsverwaltung zugegriffen wird.  
  
## <a name="using-the-smo-managedcomputer-object"></a>Verwenden des SMO-Objekts 'ManagedComputer'  
 Das <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>-Objekt ist ein verwaltetes SMO-Objekt, das Zugriff auf den WMI-Anbieter für die Konfigurationsverwaltung bietet. In Verbindung mit einem SMO-Programm kann das <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>-Objekt zur Anzeige und Änderung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Diensten, Netzwerkeinstellungen und Aliaseinstellungen verwendet werden. Weitere Informationen finden Sie unter [Verwalten von Diensten und Netzwerkeinstellungen mit dem WMI-Anbieter](../../relational-databases/server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).  
  
## <a name="using-the-microsoft-management-console-or-sql-server-configuration-manager"></a>Verwenden von Microsoft Management Console oder des SQL Server-Konfigurations-Managers  
 Microsoft Management Console (MMC) bietet statt einer Skriptsprache oder eines verwalteten Codeprogramms eine Schnittstelle für die Verwaltung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Diensten. Das MMC-Snap-In für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verwaltung kann dazu verwendet werden, Dienste anzuhalten und zu starten und Dienstkonten zu ändern.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager kann ebenfalls zur Verwaltung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Diensten, Client- und Serverprotokollen sowie Serveraliasen verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zum WMI-Anbieter für die Konfigurations Verwaltung](../../relational-databases/wmi-provider-configuration/understanding-the-wmi-provider-for-configuration-management.md)   
 [Arbeiten mit dem WMI-Anbieter für die Konfigurations Verwaltung](../../relational-databases/wmi-provider-configuration/working-with-the-wmi-provider-for-configuration-management.md)   
 [Verwenden von WQL und Skriptsprachen mit dem WMI-Anbieter für die Konfigurationsverwaltung](../../relational-databases/wmi-provider-configuration/using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
