---
title: Cluster-Netzwerkkonfiguration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- cluster network selection, Setup
- cluster network selection
ms.assetid: 579482ef-a023-45b2-9176-b4a4188adf9d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3cd117a9f873de13938d8a6946faf4f1c00d522d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63064422"
---
# <a name="cluster-network-configuration"></a>Netzwerkkonfiguration für Cluster
  Verwenden Sie die Seite **Netzwerkauswahl für Cluster** , um die Netzwerkressourcen für die Failoverclusterinstanz anzugeben.  
  
## <a name="options"></a>Optionen  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverclusters** – Mit diesem Namen wird die Failoverclusterinstanz im Netzwerk identifiziert.  
  
 **Netzwerkeinstellungen** – Geben Sie den IP-Typ und die IP-Adresse für die Failoverclusterinstanz an.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zeigt während der Vorgänge Knoten hinzufügen und Knoten entfernen eine schreibgeschützte Liste vorhandener IP-Adressen für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster an.  
  
-   Integrierte Installation:  
  
    -   Wenn Sie einen Knoten hinzufügen, der einen identischen Satz von Netzwerksubnetzen unterstützt, der von den vorhandenen Knoten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverclusters unterstützt wird, können keine zusätzlichen IP-Adressen hinzugefügt werden. Die Abhängigkeitseinstellung bleibt unverändert.  
  
    -   Wenn Sie einen Knoten hinzufügen, der eine Teilmenge der Subnetze unterstützt, die von den vorhandenen Knoten im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster unterstützt werden, können keine zusätzlichen IP-Adressressourcen hinzugefügt werden. Die Abhängigkeit der IP-Adressressource ist auf OR festgelegt, da nicht alle angegebenen IP-Adressen für alle Clusterknoten gültig sind.  
  
    -   Wenn Sie einen Knoten hinzufügen, der zusätzlich zu den Subnetzen, die von den bereits im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster vorhandenen Knoten unterstützt werden, weitere Subnetze unterstützt, können Sie neue gültige IP-Adressen hinzufügen. Bei der Angabe neuer IP-Adressen wird die Abhängigkeit der IP-Adressressource auf OR festgelegt, da nicht alle angegebenen IP-Adressen für alle Clusterknoten gültig sind.  
  
    -   Wenn Sie einen Knoten hinzufügen, der zusätzliche Netzwerksubnetze unterstützt, jedoch keines der Subnetze, das von den im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster vorhandenen Knoten unterstützt wird, müssen Sie zusätzliche IP-Adressen hinzufügen. Die Abhängigkeit der IP-Adressressource ist auf OR festgelegt, da nicht alle angegebenen IP-Adressen für alle Clusterknoten gültig sind.  
  
-   Erweiterte Installation: Geben Sie während des Schritts Abschließen der Installation die IP-Adresse für alle Knoten und Subnetze der Failoverclusterinstanz an. Sie können für einen Multisubnetz-Failovercluster mehrere IP-Adressen angeben, jedoch wird nur eine IP-Adresse pro Subnetz unterstützt. Jeder vorbereitete Knoten sollte Besitzer von mindestens einer IP-Adresse sein. Wenn im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster mehrere Subnetze vorhanden sind, werden Sie aufgefordert, die Abhängigkeit der IP-Adressressource auf OR festzulegen. Knoten entfernen:  
  
    -   Wenn die restlichen IP-Adressen in allen restlichen Knoten unterstützt werden, werden Sie aufgefordert, die Abhängigkeit der IP-Adressressource auf AND festzulegen.  
  
    -   Wenn die restlichen IP-Adressen nicht in allen restlichen Knoten unterstützt werden, bleibt die Abhängigkeit der IP-Adressressource auf OR festgelegt.  
  
  
