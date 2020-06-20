---
title: Verbindung mit Server herstellen (Oracle), Anmeldename | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.login.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 23f5b515fcb1e80416d860e2ff3a2e6be5431819
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010929"
---
# <a name="connect-to-server-oracle-login"></a>Verbindung mit Server herstellen (Oracle), Anmeldename
  Auf der Registerkarte **Anmeldename** des Dialogfelds **Verbindung mit Server herstellen** können Sie das Konto angeben, unter dem der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verteiler Verbindungen mit dem Oracle-Verleger herstellt. Sie müssen dafür dasselbe Konto verwenden wie für das Schema des administrativen Replikationsbenutzers, das Sie bei der Konfiguration des Verlegers angegeben haben. Weitere Informationen finden Sie unter [Konfigurieren eines Oracle-Verlegers](non-sql/configure-an-oracle-publisher.md).  
  
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
 [Begriffe im Zusammenhang mit dem Veröffentlichen von Oracle-Daten](non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  
