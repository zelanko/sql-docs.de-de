---
title: Distributed Replay Client-Konfiguration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: ccf03e32-6bd9-43c0-b9b6-9fe0d9163339
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e8b179d54ff39ffbb67193f88cd192aac6992d7d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48112790"
---
# <a name="distributed-replay-client-configuration"></a>Distributed Replay Client-Konfiguration
  Verwenden Sie die Seite für die **Distributed Replay Client-Konfiguration** des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installations-Assistenten, um die Benutzer anzugeben, denen Sie Administratorberechtigungen für den Distributed Replay Client-Dienst gewähren möchten.  
  
 Benutzer, die über Administratorberechtigungen verfügen, besitzen unbeschränkten Zugriff auf den Distributed Replay Client-Dienst.  
  
## <a name="options"></a>Tastatur  
 **Name des Domänencontrollers**  
 Dies ist ein optionaler Parameter, und der Standardwert ist \< *leere*>.  
  
 Geben Sie den Namen des Controllers ein, mit dem der Clientcomputer für den Distributed Replay Client-Dienst kommuniziert. Beachten Sie Folgendes:  
  
-   Der Name muss ein vollqualifizierter Domänenname sein. Ein Host mit dem Namen "server1" kann in der Produkthierarchie von Microsoft z. B. den vollqualifizierten Domänennamen "server1.products.microsoft.com" haben.  
  
-   Wenn Sie bereits einen Controller eingerichtet haben, geben Sie den Namen des Controllers beim Konfigurieren jedes Clients ein.  
  
-   Wenn Sie noch keinen Controller eingerichtet haben, können Sie das Feld für den Controllernamen leer lassen. Sie müssen den Controllernamen jedoch in der **Clientkonfigurationsdatei** manuell eingeben.  
  
 **Arbeitsverzeichnis**  
 Geben Sie das Arbeitsverzeichnis für den Distributed Replay Client-Dienst an.  
  
 Das Standardarbeitsverzeichnis ist \<*Laufwerkbuchstabe*>:\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\.  
  
 **Ergebnisverzeichnis**  
 Geben Sie das Ergebnisverzeichnis für den Distributed Replay Client-Dienst an.  
  
 Das Standardergebnisverzeichnis ist \<*Laufwerkbuchstabe*>:\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\.  
  
  
