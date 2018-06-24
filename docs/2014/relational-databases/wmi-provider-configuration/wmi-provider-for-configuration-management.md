---
title: WMI-Provider for Configuration Management Concepts | Microsoft Docs
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
- WMI Provider for Configuration Management
- SQL Server WMI Provider
- configuration management [WMI]
- WMI Provider for Configuration Management, about WMI Provider for Configuration Management
ms.assetid: 7e41db24-b915-4eb8-a1d6-e6948ee915b7
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5185d55296d1b5cd2adcbb6c61139e06195588be
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057540"
---
# <a name="wmi-provider-for-configuration-management-concepts"></a>Konzepte des WMI-Anbieters für die Konfigurationsverwaltung
  Der WMI-Anbieter ist eine veröffentlichte Ebene, die mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager-Snap-in für [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (MMC) und die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager. Sie bietet eine vereinheitlichte Schnittstellenfunktion zu API-Aufrufen, mit denen die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager angeforderten Registrierungsvorgänge verwaltet werden, und ermöglicht eine verbesserte Steuerung und Bearbeitung der ausgewählten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste.  
  
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
 Das <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>-Objekt ist ein verwaltetes SMO-Objekt, das Zugriff auf den WMI-Anbieter für die Konfigurationsverwaltung bietet. In Verbindung mit einem SMO-Programm kann das <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>-Objekt zur Anzeige und Änderung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Diensten, Netzwerkeinstellungen und Aliaseinstellungen verwendet werden. Weitere Informationen finden Sie unter [Verwalten von Diensten und Netzwerkeinstellungen durch die Verwendung der WMI-Anbieter](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).  
  
## <a name="using-the-microsoft-management-console-or-sql-server-configuration-manager"></a>Verwenden von Microsoft Management Console oder des SQL Server-Konfigurations-Managers  
 Microsoft Management Console (MMC) bietet statt einer Skriptsprache oder eines verwalteten Codeprogramms eine Schnittstelle für die Verwaltung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Diensten. Das MMC-Snap-In für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verwaltung kann dazu verwendet werden, Dienste anzuhalten und zu starten und Dienstkonten zu ändern.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager kann ebenfalls zur Verwaltung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Diensten, Client- und Serverprotokollen sowie Serveraliasen verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zum WMI-Anbieter für die Konfigurationsverwaltung](understanding-the-wmi-provider-for-configuration-management.md)   
 [Arbeiten mit dem WMI-Anbieter für die Verwaltung](working-with-the-wmi-provider-for-configuration-management.md)   
 [Verwenden von WQL und Skriptsprachen mit dem WMI-Anbieter für die Konfigurationsverwaltung](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  