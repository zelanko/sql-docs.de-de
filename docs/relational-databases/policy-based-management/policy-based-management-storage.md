---
title: Speicher der richtlinienbasierten Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, storage
ms.assetid: d0cbf214-fc2e-4917-8d31-1d71c9ffa61d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 7b927398f565720412bbd9f15b9520a17ef0a960
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727296"
---
# <a name="policy-based-management-storage"></a>Speicher der richtlinienbasierten Verwaltung
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Richtlinien werden in der msdb-Datenbank gespeichert. Nachdem eine Richtlinie oder Bedingung geändert wurde, sollte die msdb-Datenbank gesichert werden. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen von Systemdatenbanken &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
## <a name="storing-policies"></a>Speichern von Richtlinien  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] enthält Richtlinien, die verwendet werden können, um eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu überwachen. Diese Richtlinien sind standardmäßig nicht in [!INCLUDE[ssDE](../../includes/ssde-md.md)]installiert, aber sie können aus ihrem Standardinstallationspfad C:\Programme (x86)\Microsoft SQL Server\140\Tools\Policies\DatabaseEngine\1033 importiert werden.  
  
 Sie können Richtlinien über das Menü **Datei/Neu** direkt erstellen und diese dann in einer Datei speichern. Auf diese Weise können Sie Richtlinien erstellen, wenn Sie nicht mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]verbunden sind.  
  
 Der Richtlinienverlauf für Richtlinien, die in der aktuellen Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] ausgewertet werden, wird in msdb-Systemtabellen verwaltet. Der Richtlinienverlauf für Richtlinien, die auf andere Instanzen von [!INCLUDE[ssDE](../../includes/ssde-md.md)] oder auf [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] oder [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] angewendet werden, bleibt nicht erhalten.  
  
  
