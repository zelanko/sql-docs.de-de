---
description: Verbindung mit Server herstellen (Oracle), Anmeldename
title: Verbindung mit Server herstellen (Oracle), Anmeldename | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.oracleconnection.login.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b585e2a17e577aab7ade2c5906bdcd184a12e8dd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88455593"
---
# <a name="connect-to-server-oracle-login"></a>Verbindung mit Server herstellen (Oracle), Anmeldename
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Auf der Registerkarte **Anmeldename** des Dialogfelds **Verbindung mit Server herstellen** können Sie das Konto angeben, unter dem der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verteiler Verbindungen mit dem Oracle-Verleger herstellt. Sie müssen dafür dasselbe Konto verwenden wie für das Schema des administrativen Replikationsbenutzers, das Sie bei der Konfiguration des Verlegers angegeben haben. Weitere Informationen finden Sie unter [Konfigurieren eines Oracle-Verlegers](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Tastatur  
 **Serverinstanz**  
 Der TNS-Name (Transparent Network Substrate) des Oracle-Verlegers, der bei Konfiguration der auf dem Verteiler installierten Oracle-Clientsoftware angegeben wurde.  
  
 **Authentifizierung**  
 Wählen Sie **Oracle-Standardauthentifizierung** (empfohlen) oder **Windows-Authentifizierung**aus. Bei Auswahl von **Windows-Authentifizierung**:  
  
-   Der Oracle-Server muss so konfiguriert sein, dass mit den Windows-Anmeldeinformationen Verbindungen hergestellt werden können. Weitere Informationen finden Sie in der Oracle-Dokumentation.  
  
-   Sie müssen dazu auf demselben [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto angemeldet sein, wie für das Schema des administrativen Replikationsbenutzers angegeben wurde.  
  
 **Anmeldename** und **Kennwort**  
 Wenn Sie für die **Authentifizierung** die Option **Oracle-Standardauthentifizierung** ausgewählt haben, geben Sie den zu verwendenden Anmeldenamen und das Kennwort an. Verwenden Sie dabei dieselben Angaben wie für das Schema des administrativen Replikationsbenutzers.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Begriffe im Zusammenhang mit dem Veröffentlichen von Oracle-Daten](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  
