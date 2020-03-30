---
title: Nicht-SQL Server-Abonnenten hinzufügen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.addnonsqlsubscriber.f1
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b188b7ec3b108a32a52ce888d4dfb1b5a064804
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "67929786"
---
# <a name="add-non-sql-server-subscriber"></a>Nicht-SQL Server-Abonnenten hinzufügen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die Replikation unterstützt das Erstellen von Pushabonnements für Momentaufnahme- und Transaktionsveröffentlichungen für Oracle und IBM DB2-Abonnenten.  
  
## <a name="options"></a>Tastatur  
 **Typ des hinzuzufügenden Abonnenten**  
 Wählen Sie einen Oracle-Abonnenten oder einen IBM DB2-Abonnenten aus. Weitere Informationen zur Unterstützung für diese Abonnenten finden Sie unter [Nicht-SQL Server-Abonnenten](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
 **Datenquellenname**  
 Der Name, der verwendet wird, um die Datenbank in einem Netzwerk zu suchen. Die Replikation erzeugt eine Verbindungszeichenfolge für die Datenbank mithilfe des Datenquellennamens, der mit dem Anmeldenamen, dem Kennwort und den Verbindungsoptionen kombiniert wird, die Sie auf der Seite **Sicherheit für den Verteilungs-Agent** in diesem Assistenten angegeben haben.  
  
> [!NOTE]
>  Der Datenquellenname und die Verbindungszeichenfolge werden nicht durch [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] überprüft, bevor der Verteilungs-Agent versucht, das Abonnement zu initialisieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines Abonnements für einen Nicht-SQL Server-Abonnenten](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
