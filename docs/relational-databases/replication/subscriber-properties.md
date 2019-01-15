---
title: Abonnenteneigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.configdistwizard.subscribers.f1
helpviewer_keywords:
- Subscriber Properties dialog box
ms.assetid: 32aa0347-64e4-4aa4-ac57-6bd3e5d52070
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ec29a632d1125282d74c59ac511ed0c883a66c52
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54123869"
---
# <a name="subscriber-properties"></a>Abonnenteneigenschaften
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Das Dialogfeld **Abonnenteneigenschaften** enthält Informationen, die für Abonnenten wichtig sind, auf denen Versionen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]ausgeführt werden.  
  
## <a name="options"></a>enthalten  
 **Agentverbindung mit dem Abonnenten**  
 Der Kontext, in dem der Verteilungs-Agent und der Merge-Agent die Verbindung vom Verteiler zum Abonnenten herstellen. Dieser gilt nur für Versionen vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 Wählen Sie die Option **Identität des Agentprozesskontos annehmen** , um unter Verwendung des Kontexts des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Kontos auf Verteilerebene Verbindungen zum Abonnenten herzustellen. Geben Sie alternativ die **SQL Server-Authentifizierung**an, und geben Sie dann einen Wert für die **Anmeldung** und das **Kennwort**ein. [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt die Auswahl von **Identität des Agentprozesskontos annehmen**.  
  
 In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen werden die Verbindungsinformationen für jedes Abonnement im Assistent für neue Abonnements angegeben. Die Informationen können im Dialogfeld **Abonnementeigenschaften** geändert werden.  
  
 **Standardzeitpläne für Agent**  
 Der Standardzeitplan, der im Assistenten für neue Abonnements für Abonnenten verwendet wird, auf denen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]ausgeführt werden.  
  
 **Sonstiges**  
 Enthält Informationen zum Abonnenten und zum Typ des Abonnenten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
