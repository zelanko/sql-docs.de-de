---
title: Sicherheitsanforderungen für das Verwalten von Diensten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent service, security
- services [SQL Server], security
- SQL Server services, security
- WMI Providers [SQL Server]
- server configuration [SQL Server]
- security [SQL Server], services
- services [SQL Server], WMI
ms.assetid: 1874a317-ddb2-425d-98d9-b53e1be6fc6a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 46a777858c01bf3057093d34b29b9a2093668e97
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935011"
---
# <a name="security-requirements-for-managing-services"></a>Sicherheitsanforderungen für das Verwalten von Diensten
  Verwenden Sie entweder den SQL Server-Konfigurations-Manager oder [!INCLUDE[msCoName](../../includes/msconame-md.md)], um den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-und den [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]-Agent-Dienst zu verwalten. Auf gruppierten Servern verwalten Sie die Dienste mit der Clusterverwaltung.  
  
 Um den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst zu verwalten und die Konfigurationsoptionen für den Server festzulegen, müssen Sie Mitglied der festen Serverrolle **serveradmin** oder der festen Serverrolle **sysadmin** sein. Mitglieder der Windows-Gruppe **Administratoren** können Dienste starten und beenden und die unter Windows verfügbaren Serveroptionen konfigurieren.  
  
> [!NOTE]  
>  Um eine ordnungsgemäße Funktionsweise sicherzustellen, müssen die für die Dienste verwendeten Konten mit der richtigen Domäne, dem richtigen Dateisystem und den richtigen Registrierungsberechtigungen konfiguriert werden. Weitere Informationen zu erforderlichen Berechtigungen finden Sie unter [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](configure-windows-service-accounts-and-permissions.md).  
  
## <a name="windows-management-instrumentation"></a>Windows-Verwaltungsinstrumentation  
 Der SQL Server-Konfigurations-Manager und [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwenden zum Anzeigen und Bearbeiten einiger Servereigenschaften die Windows-Verwaltungsinstrumentation (WMI, Windows Management Instrumentation). Um Dienste zu verwalten und den Status der Dienste abzufragen, muss der Benutzer über eine Zugriffsberechtigung für das WMI-Objekt verfügen. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]wird die WMI auf den folgenden Servereigenschaftenseiten verwendet:  
  
-   Dienste automatisch starten  
  
-   Startparameter  
  
-   Sicherheit  
  
-   Sonstige Servereinstellungen  
  
## <a name="related-tasks"></a>Related Tasks  
 [Konfigurieren von WMI zum Anzeigen des Serverstatus in SQL Server-Tools](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Konzepte des WMI-Anbieters für die Konfigurationsverwaltung](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
