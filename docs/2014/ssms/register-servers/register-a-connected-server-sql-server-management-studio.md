---
title: Registrieren eines verbundenen Servers (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.f1
helpviewer_keywords:
- Registered Servers [SQL Server], register connected servers
- connected server registrations [SQL Server]
ms.assetid: 77deb5f5-0f80-484f-8b8b-29afa67ec18f
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b8642792984041c225aa0a3179abf5fc275c30f7
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43820106"
---
# <a name="register-a-connected-server-sql-server-management-studio"></a>Registrieren eines verbundenen Servers (SQL Server Management Studio)
  In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Server registrieren. Indem Sie den Server registrieren, können Sie die Verbindungsinformationen für Server, auf die Sie häufig zugreifen, speichern. Ein Server kann vor dem Verbinden oder bei der Verbindung im Objekt-Explorer registriert werden.  
  
 **In diesem Thema**  
  
-   **So registrieren Sie einen Server mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-register-a-connected-server"></a>So registrieren Sie einen Server  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, zu dem Sie bereits eine Verbindung hergestellt haben, und klicken Sie dann auf **Registrieren**.  
  
     **Servername**  
     Geben Sie den Namen ein, der für den registrierten Server verwendet werden soll. Mit dem Registrieren eines lokalen oder eines Remoteservers mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] können Sie die Serververbindungsinformationen für spätere Verbindungen speichern. Als Standardwert wird in diesem Feld der Servername verwendet, den Sie bei der Verbindung zum Server eingegeben haben. Sie können diesen Servernamen beibehalten oder einen anderen leicht verwendbaren Namen für den Server eingeben.  
  
     **Serverbeschreibung**  
     Geben Sie eine optionale Beschreibung des Servers ein. Es können maximal 250 Zeichen eingegeben werden.  
  
     **Wählen Sie eine Servergruppe**  
     Wählen Sie die Servergruppe aus, in der die Serverregistrierung gespeichert werden soll.  
  
     **Neue Gruppe**  
     Klicken Sie auf diese Option, um das Dialogfeld **Neue Gruppe** zu öffnen, mit dem Sie eine neue Servergruppe für den registrierten Server erstellen können.  
  
     **Speichern**  
     Speichert die von Ihnen eingegebenen Informationen und erstellt einen registrierten Server.  
  
  
