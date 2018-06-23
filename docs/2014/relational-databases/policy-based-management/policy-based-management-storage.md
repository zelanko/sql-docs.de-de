---
title: Speicher der richtlinienbasierten Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, storage
ms.assetid: d0cbf214-fc2e-4917-8d31-1d71c9ffa61d
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b741f03de6a1c36678752b1d0f926479dec91c0b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056914"
---
# <a name="policy-based-management-storage"></a>Speicher der richtlinienbasierten Verwaltung
  Richtlinien werden in der msdb-Datenbank gespeichert. Nachdem eine Richtlinie oder Bedingung geändert wurde, sollte die msdb-Datenbank gesichert werden. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen von Systemdatenbanken &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
## <a name="storing-policies"></a>Speichern von Richtlinien  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] enthält Richtlinien, die verwendet werden können, um eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu überwachen. Standardmäßig werden diese Richtlinien nicht auf installiert die [!INCLUDE[ssDE](../../includes/ssde-md.md)]jedoch aus dem Standardspeicherort für die Installation von C:\Program Files (x86) \Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033 importiert werden.  
  
 Sie können Richtlinien über das Menü **Datei/Neu** direkt erstellen und diese dann in einer Datei speichern. Auf diese Weise können Sie Richtlinien erstellen, wenn Sie nicht mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]verbunden sind.  
  
 Der Richtlinienverlauf für Richtlinien, die in der aktuellen Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] ausgewertet werden, wird in msdb-Systemtabellen verwaltet. Der Richtlinienverlauf für Richtlinien, die auf andere Instanzen von [!INCLUDE[ssDE](../../includes/ssde-md.md)] oder auf [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] oder [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] angewendet werden, bleibt nicht erhalten.  
  
  