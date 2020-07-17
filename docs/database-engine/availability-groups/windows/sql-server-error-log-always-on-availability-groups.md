---
title: SQL Server-Fehlerprotokoll (Verfügbarkeitsgruppen)
description: Hier erfahren Sie mehr über die Ereignisse im SQL Server-Fehlerprotokoll, die sich auf Always On-Verfügbarkeitsgruppen auswirken, sowie darüber, bei welchen Anzeichen Sie Fehlerprotokolle untersuchen sollten.
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 39d0c98d-75af-4dd1-b908-30d31af56f2a
author: rothja
ms.author: jroth
ms.openlocfilehash: 4c44f65761fcb54d8ad9b8eac0fc5e02bce82181
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85898075"
---
# <a name="sql-server-error-log-always-on-availability-groups"></a>SQL Server-Fehlerprotokoll (Always On-Verfügbarkeitsgruppen)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Folgende Ereignisse von SQL Server-Fehlerprotokollberichten wirken sich auf Always On-Verfügbarkeitsgruppen aus:  
  
-   Kommunikation mit dem WSFC-Cluster (Windows Server Failover Clustering)    
-   Statusübergänge von Verfügbarkeitsreplikaten    
-   Statusübergänge von Verfügbarkeitsdatenbanken    
-   Konnektivitätsstatus von Verfügbarkeitsdatenbanken zwischen primären und sekundären Replikaten    
-   Status der Verfügbarkeitsgruppenendpunkte    
-   Status der Verfügbarkeitsgruppenlistener    
-   Status der Leasedauer zwischen der SQL Server-Ressourcen-DLL (die im WSFC-Cluster ausgeführt wird) und der SQL Server-Instanz (weitere Informationen finden Sie unter [How It Works: SQL Server Always On Lease Timeout](https://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-alwayson-lease-timeout.aspx) (Funktionsweise: SQL Server Always On-Leasetimeout))    
-   Fehlerereignisse in der Verfügbarkeitsgruppe  

Wenn die folgenden Aussagen zutreffen, sollten Sie sich das SQL Server-Fehlerprotokoll ansehen:  

-   Der Zugriff auf Verfügbarkeitsdatenbanken ist nicht möglich.    
-   Es gab einen unerwarteten Failover einer Verfügbarkeitsgruppe.    
-   Eine Verfügbarkeitsgruppe befindet sich unerwartet im Status „Wird aufgelöst“.    
-   Eine Verfügbarkeitsgruppe befindet sich in einem unbestimmten Status.  
  
Weitere Informationen finden Sie unter [View the SQL Server error log &#40;SQL Server Management Studio&#41; (Anzeigen des SQL Server-Fehlerprotokolls &#40;SQL Server Management Studio&#41;)](~/relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md).  
  
  
