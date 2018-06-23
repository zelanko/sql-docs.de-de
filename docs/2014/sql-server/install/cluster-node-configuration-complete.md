---
title: Cluster-Knotenkonfiguration (vollständig) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64174d54-edee-49b8-9b43-039574bf2ca1
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 61643e7a5d21d106430d0bc9fbd4672efe0924f0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161056"
---
# <a name="cluster-node-configuration-complete"></a>Clusterknotenkonfiguration (Vollständig)
  Auf der Seite Clusterknotenkonfiguration (Vollständig) können Sie eine vorhandene Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angeben, die für das Clustering vorbereitet wurde. Zum Installieren oder Aktualisieren eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Failoverclusters müssen Sie das Setupprogramm für jeden einzelnen Knoten des Failoverclusters ausführen. Zum Hinzufügen eines Knotens zu einem vorhandenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster müssen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup für den Knoten ausführen, der der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverclusterinstanz hinzugefügt werden soll.  
  
## <a name="options"></a>Tastatur  
 Auswahl aus den Dropdownfeldern:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanzname – Wählen Sie den Namen der Instanz für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Failovercluster aus.  
  
-   Name dieses Knotens – Dieses Feld wird mit dem Namen des Computers aufgefüllt, auf dem das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup ausgeführt wird.  
  
-   Netzwerkname des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Failoverclusters – Dieses Feld ist nicht im Voraus ausgefüllt. Geben Sie den Netzwerknamen für die neue Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverclusters an. Anhand dieses Namens wird die Failoverclusterinstanz im Netzwerk identifiziert.  
  
  