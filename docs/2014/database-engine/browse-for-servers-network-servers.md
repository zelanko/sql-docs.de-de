---
title: Nach Servern suchen (Netzwerkserver) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.browseservers.network.f1
ms.assetid: a59ffcd6-4b69-4c5c-9740-699ccb2183fb
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: db0e235abb91181ac2090000b9d307181f720768
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147746"
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
  
  