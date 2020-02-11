---
title: Nicht-SQL Server-Abonnenten hinzufügen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.addnonsqlsubscriber.f1
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cc291a9677efe2acf875f5b5a37d9153fcb3eee3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62676921"
---
# <a name="add-non-sql-server-subscriber"></a>Nicht-SQL Server-Abonnenten hinzufügen
  Die Replikation unterstützt das Erstellen von Pushabonnements für Momentaufnahme- und Transaktionsveröffentlichungen für Oracle und IBM DB2-Abonnenten.  
  
## <a name="options"></a>Tastatur  
 **Typ des hinzuzufügenden Abonnenten**  
 Wählen Sie einen Oracle-Abonnenten oder einen IBM DB2-Abonnenten aus. Weitere Informationen zur Unterstützung für diese Abonnenten finden Sie unter [Nicht-SQL Server-Abonnenten](non-sql/non-sql-server-subscribers.md).  
  
 **Datenquellenname**  
 Der Name, der verwendet wird, um die Datenbank in einem Netzwerk zu suchen. Die Replikation erzeugt eine Verbindungszeichenfolge für die Datenbank mithilfe des Datenquellennamens, der mit dem Anmeldenamen, dem Kennwort und den Verbindungsoptionen kombiniert wird, die Sie auf der Seite **Sicherheit für den Verteilungs-Agent** in diesem Assistenten angegeben haben.  
  
> [!NOTE]  
>  Der Datenquellenname und die Verbindungszeichenfolge werden nicht durch [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] überprüft, bevor der Verteilungs-Agent versucht, das Abonnement zu initialisieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines Abonnements für einen Nicht-SQL Server-Abonnenten](create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)  
  
  
