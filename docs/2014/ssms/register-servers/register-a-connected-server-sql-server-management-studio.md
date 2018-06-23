---
title: Registrieren eines verbundenen Servers (SQL Server Management Studio) | Microsoft-Dokumentation
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
- sql12.swb.registerserver.f1
helpviewer_keywords:
- Registered Servers [SQL Server], register connected servers
- connected server registrations [SQL Server]
ms.assetid: 77deb5f5-0f80-484f-8b8b-29afa67ec18f
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dca757868f8db41003b1515634238f2566d31200
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046801"
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
  
     **Beschreibung des Servers**  
     Geben Sie eine optionale Beschreibung des Servers ein. Es können maximal 250 Zeichen eingegeben werden.  
  
     **Wählen Sie eine Servergruppe**  
     Wählen Sie die Servergruppe aus, in der die Serverregistrierung gespeichert werden soll.  
  
     **Neue Gruppe**  
     Klicken Sie auf diese Option, um das Dialogfeld **Neue Gruppe** zu öffnen, mit dem Sie eine neue Servergruppe für den registrierten Server erstellen können.  
  
     **Speichern**  
     Speichert die von Ihnen eingegebenen Informationen und erstellt einen registrierten Server.  
  
  