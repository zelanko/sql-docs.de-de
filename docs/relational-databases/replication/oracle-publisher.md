---
description: Oracle-Verleger
title: Oracle-Verleger | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.selectoraclepublisher.f1
ms.assetid: 019b7c49-dcca-445d-8969-5982a8ccbc1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fb2b2f519ed8b548c6c1f149a72f28528d9fd26f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88455555"
---
# <a name="oracle-publisher"></a>Oracle-Verleger
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Ab [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] erlaubt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Ihnen das Veröffentlichen von Daten aus einer Oracle-Datenbank mithilfe einer Momentaufnahme und der Transaktionsreplikation. Weitere Informationen finden Sie unter [Veröffentlichungen mit Oracle (Übersicht)](../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
 Der Oracle-Verleger muss einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Remoteverteiler verwenden, und auf diesem Server muss der Assistent ausgeführt werden, nachdem die erforderliche Oracle-Netzwerksoftware installiert und getestet wurde. Weitere Informationen finden Sie unter [Konfigurieren eines Oracle-Verlegers](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
> [!IMPORTANT]  
>  Wenn ein anderer Administrator die Oracle-Datenbank als Verleger konfiguriert hat, werden Sie nach dem Klicken auf **Weiter** aufgefordert, das Kennwort für die Replikationsanmeldung einzugeben, die zum Herstellen der Verbindung mit der Oracle-Datenbank verwendet wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt dann eine Zuordnung zwischen der Anmeldung und der Verbindung des Verbindungsservers mit der Oracle-Datenbank. Bei den folgenden Verbindungen mit der Oracle-Datenbank werden Sie nicht mehr aufgefordert, ein Kennwort einzugeben.  
  
## <a name="options"></a>Optionen  
 **Oracle-Verleger**  
 Wählen Sie einen Oracle-Verleger aus der Liste aus. Die Liste enthält die Oracle-Verleger, die zuvor für die Verwendung des Servers konfiguriert wurden, für den der Assistent nun als Verteiler ausgeführt wird. Wenn die Liste keine Einträge enthält oder den von Ihnen gewünschten Oracle-Verleger nicht beinhaltet, klicken Sie auf **Oracle-Verleger hinzufügen**.  
  
 **Oracle-Verleger hinzufügen**  
 Klicken Sie auf diese Option, um das Dialogfeld **Verteilereigenschaften** zu starten. Klicken Sie im Dialogfeld auf **Hinzufügen**, und klicken Sie auf **Oracle-Verleger hinzufügen**. Geben Sie im Dialogfeld **Verbindung mit Server herstellen** den Oracle-Servernamen sowie den Anmeldenamen und das Kennwort für das Schema des administrativen Replikationsbenutzers an. Weitere Informationen finden Sie unter [Verbindung mit Server herstellen &#40;Oracle&#41;, Anmeldename](../../relational-databases/replication/connect-to-server-oracle-login.md).  
  
> [!NOTE]  
>  Wenn der Server, für den der Assistent ausgeführt wird, noch nicht als Verteiler konfiguriert ist, werden Sie aufgefordert, ihn jetzt zu konfigurieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Veröffentlichung aus einer Oracle-Datenbank](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)   

  
  
