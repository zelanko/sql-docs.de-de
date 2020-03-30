---
title: SQL Server-Fehlerprotokoll (Verfügbarkeitsgruppen)
description: Hier finden Sie eine Beschreibung der Fehlerprotokollereignisse, die von einer Always On-Verfügbarkeitsgruppe gemeldet werden.
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 39d0c98d-75af-4dd1-b908-30d31af56f2a
author: rothja
ms.author: jroth
ms.openlocfilehash: 81d31225838ec029a020af2df25753b26acd2fb1
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "75251249"
---
# <a name="sql-server-error-log-always-on-availability-groups"></a>SQL Server-Fehlerprotokoll (Always On-Verfügbarkeitsgruppen)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Folgende Ereignisse von SQL Server-Fehlerprotokollberichten wirken sich auf Always On-Verfügbarkeitsgruppen aus:  
  
-   Kommunikation mit dem WSFC-Cluster (Windows Server Failover Clustering)    
-   Statusübergänge von Verfügbarkeitsreplikaten    
-   Statusübergänge von Verfügbarkeitsdatenbanken    
-   Konnektivitätsstatus von Verfügbarkeitsdatenbanken zwischen primären und sekundären Replikaten    
-   Status der Verfügbarkeitsgruppenendpunkte    
-   Status der Verfügbarkeitsgruppenlistener    
-   Status der Leasedauer zwischen der SQL Server-Ressourcen-DLL (die im WSFC-Cluster ausgeführt wird) und der SQL Server-Instanz (weitere Informationen finden Sie unter [How It Works: SQL Server Always On lease timeout (Funktionsweise: Ablauf der Leasedauer der SQL Server-Option „Always On“)](https://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-alwayson-lease-timeout.aspx))    
-   Fehlerereignisse in der Verfügbarkeitsgruppe  

Wenn die folgenden Aussagen zutreffen, sollten Sie sich das SQL Server-Fehlerprotokoll ansehen:  

-   Der Zugriff auf Verfügbarkeitsdatenbanken ist nicht möglich.    
-   Es gab einen unerwarteten Failover einer Verfügbarkeitsgruppe.    
-   Eine Verfügbarkeitsgruppe befindet sich unerwartet im Status „Wird aufgelöst“.    
-   Eine Verfügbarkeitsgruppe befindet sich in einem unbestimmten Status.  
  
Weitere Informationen finden Sie unter [View the SQL Server error log &#40;SQL Server Management Studio&#41; (Anzeigen des SQL Server-Fehlerprotokolls &#40;SQL Server Management Studio&#41;)](~/relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md).  
  
  
