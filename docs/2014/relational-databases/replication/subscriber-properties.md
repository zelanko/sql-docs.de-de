---
title: Abonnenteneigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.subscribers.f1
helpviewer_keywords:
- Subscriber Properties dialog box
ms.assetid: 32aa0347-64e4-4aa4-ac57-6bd3e5d52070
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3142a78fcf3a2413e43b1a7598b5d3b282aba1c7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62629444"
---
# <a name="subscriber-properties"></a>Abonnenteneigenschaften
  Das Dialogfeld **Abonnenteneigenschaften** enthält Informationen zu den Abonnenten, die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Versionen verwenden, die älter als [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] sind.  
  
## <a name="options"></a>Tastatur  
 **Agentverbindung mit dem Abonnenten**  
 Der Kontext, in dem der Verteilungs-Agent und der Merge-Agent die Verbindung vom Verteiler zum Abonnenten herstellen. Dieser gilt nur für Versionen vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 Wählen Sie die Option **Identität des Agentprozesskontos annehmen** , um unter Verwendung des Kontexts des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Kontos auf Verteilerebene Verbindungen zum Abonnenten herzustellen. Geben Sie alternativ die **SQL Server-Authentifizierung**an, und geben Sie dann einen Wert für die **Anmeldung** und das **Kennwort**ein. [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt die Auswahl von **Identität des Agentprozesskontos annehmen**.  
  
 In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen werden die Verbindungsinformationen für jedes Abonnement im Assistent für neue Abonnements angegeben. Die Informationen können im Dialogfeld **Abonnementeigenschaften** geändert werden.  
  
 **Standardzeitpläne für Agent**  
 Der Standardzeitplan, der im Assistenten für neue Abonnements für Abonnenten verwendet wird, auf denen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]ausgeführt werden.  
  
 **Verschiedenes**  
 Enthält Informationen zum Abonnenten und zum Typ des Abonnenten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](view-and-modify-distributor-and-publisher-properties.md)   

 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)  
  
  
