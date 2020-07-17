---
title: Konfigurieren von Datenbank-Engine-Instanzen (SQL Server) | Microsoft-Dokumentation
description: In diesem Artikel lernen Sie SQL Server-Konfigurationsaufgaben kennen, mit denen Sie eine Datenbank-Engine-Instanz konfigurieren können, um Leistungs- und Verfügbarkeitsanforderungen zu erfüllen.
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 84e36fcb-2c78-48e8-8e4b-bf784a3ee557
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b2b3900c41067e7f46f392ceab913f1d8d096816
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85751933"
---
# <a name="configure-database-engine-instances-sql-server"></a>Konfigurieren von Datenbank-Engine-Instanzen (SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Jede Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] muss so konfiguriert werden, dass sie die für die Datenbanken, die von der Instanz gehostet werden, definierten Anforderungen in Bezug auf Leistung und Verfügbarkeit erfüllen. [!INCLUDE[ssDE](../../includes/ssde-md.md)] enthält Konfigurationsoptionen, die Verhaltensweisen wie Ressourcenauslastung und Verfügbarkeit von Funktionen, z. B. Überwachung oder Triggerrekursion, steuern.  
  
## <a name="instance-configuration"></a>Instanzkonfiguration  
 Wenn eine Datenbank in der Produktionsumgebung bereitgestellt wird, gibt es oft eine Vereinbarung zum Servicelevel (SLA), in der Bereiche wie die erforderlichen Leistungsstufen der Datenbank und die erforderliche Verfügbarkeitsstufe der Datenbank festgelegt sind. Die Konfigurationsanforderungen für die Instanz orientieren sich in der Regel an den SLA-Bedingungen.  
  
 Eine Instanz wird normalerweise sofort nach ihrer Installation konfiguriert. Die Erstkonfiguration wird normalerweise von den SLA-Anforderungen der Typen von Datenbanken bestimmt, die auf der Instanz bereitgestellt werden sollen. Nach der Bereitstellung der Datenbanken überwachen die Datenbankadministratoren die Leistung der Instanz und passen die Konfigurationseinstellungen ggf. an, wenn die Leistungsmetrik anzeigt, dass SAL-Anforderungen nicht von der Instanz erfüllt werden.  
  
## <a name="configuration-tasks"></a>Konfigurationstasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt die verschiedenen Optionen zur Instanzkonfiguration und das Anzeigen oder Ändern dieser Optionen.|[Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)|  
|Beschreibt, wie Sie die Standardspeicherorte von neuen Daten- und Protokolldateien in der Instanz anzeigen und konfigurieren.|[Anzeigen oder Ändern der Standardspeicherorte für Daten- und Protokolldateien &#40;SQL Server Management Studio&#41;](../../database-engine/configure-windows/view-or-change-the-default-locations-for-data-and-log-files.md)|  
|Beschreibt, wie Sie SQL Server für die Verwendung von Soft-NUMA konfigurieren.|[Soft-NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md)|  
|Beschreibt, wie ein TCP/IP-Port einer Affinität von TCP/IP-Ports zu NUMA-Knoten (Non-Uniform Memory Access) zugeordnet wird.|[Zuordnen von TCP/IP-Ports zu NUMA-Knoten &#40;SQL Server&#41;](../../database-engine/configure-windows/map-tcp-ip-ports-to-numa-nodes-sql-server.md)|  
|Beschreibt, wie Sie die Windows-Richtlinie Lock Pages In Memory aktivieren. Mit dieser Richtlinie werden die Konten bestimmt, die einen Prozess zum Speichern von Daten im physischen Speicher verwenden können, um das systemgesteuerte Auslagern der Daten in den virtuellen Arbeitsspeicher zu vermeiden.|[Aktivieren der Option Sperren von Seiten im Speicher &#40;Windows&#41;](../../database-engine/configure-windows/enable-the-lock-pages-in-memory-option-windows.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine-Instanzen &#40;SQL Server&#41;](../../database-engine/configure-windows/database-engine-instances-sql-server.md)  
  
  
