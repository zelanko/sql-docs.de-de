---
title: Nach Servern suchen (Netzwerkserver) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.browseservers.network.f1
ms.assetid: a59ffcd6-4b69-4c5c-9740-699ccb2183fb
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a9efc4b78f1f1b15fbbba54a1b59e3a8995051c2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48208680"
---
# <a name="browse-for-servers-network-servers"></a>Nach Servern suchen (Netzwerkserver)
  Wenn Sie eine Verbindung mit einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Komponente herstellen und nicht den genauen Namen der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz kennen, klicken Sie im Feld **Servername** auf **Suche fortsetzen** , um das Dialogfeld **Nach Servern suchen** zu öffnen.  
  
 Dieses Dialogfeld wird vom [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Browser-Dienst aufgefüllt, sofern dieser auf den Servercomputern ausgeführt wird. Es gibt mehrere Gründe, warum der Name einer Instanz ggf. nicht in der Liste angezeigt wird:  
  
-   Der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Browser-Dienst wird auf dem Computer, auf dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ausgeführt wird, möglicherweise nicht ausgeführt.  
  
-   UDP-Port 1434 wird möglicherweise von einer Firewall blockiert.  
  
-   Das **HideInstance** -Flag wurde möglicherweise festgelegt.  
  
 Um eine Verbindung mit einer Instanz herzustellen, die nicht in der Liste angezeigt wird, geben Sie eine vollständige Verbindungszeichenfolge für die Instanz ein, einschließlich der TCP/IP-Portnummer oder des Pipenamens der Named Pipes.  
  
## <a name="options"></a>Tastatur  
 **Wählen Sie für Ihre Verbindung eine SQL Server-Instanz im Netzwerk aus**  
 Legen Sie den Server fest, zu dem eine Verbindung hergestellt werden soll, indem Sie auf die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz klicken, die in der Baumstruktur angezeigt wird. Sie können Teile der Strukturansicht durch Klicken auf die Knoten ein- bzw. ausblenden, die mit den Symbolen **+** bzw. **–** gekennzeichnet sind.  
  
  
