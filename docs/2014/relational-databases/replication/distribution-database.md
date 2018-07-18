---
title: Verteilungsdatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.configuredistributionwizard.distributiondatabase.f1
ms.assetid: 5b42a083-7a11-41d8-9e3f-320c7c907237
caps.latest.revision: 25
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f49e1f71897906d8ac3d947c43cd284cbee5289e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37256666"
---
# <a name="distribution-database"></a>Verteilungsdatenbank
  Die Verteilungsdatenbank speichert Metadaten und Verlaufsdaten für alle Replikationstypen und Transaktionen für die Transaktionsreplikation.  
  
 In vielen Fällen reicht eine Verteilungsdatenbank aus. Wenn jedoch mehrere Verleger einen Verteiler verwenden, sollten Sie die Erstellung einer Verteilungsdatenbank für jeden Verleger in Betracht ziehen. Auf diese Weise stellen Sie sicher, dass die durch jede Verteilungsdatenbank fließenden Daten eindeutig sind. Mit dem Verteilungskonfigurations-Assistenten können Sie eine Verteilungsdatenbank für den Verteiler angeben. Geben Sie bei Bedarf im Dialogfeld **Verteilereigenschaften** weitere Verteilungsdatenbanken an.  
  
## <a name="options"></a>Tastatur  
 **Name der Verteilungsdatenbank**  
 Geben Sie einen Namen für die Verteilungsdatenbank ein. Der Standardname für die Verteilungsdatenbank lautet 'distribution'. Wenn Sie einen Namen angeben, darf dieser maximal 128 Zeichen umfassen, und es muss sich um einen innerhalb der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz eindeutigen Namen handeln, der den Regeln für Bezeichner entspricht. Weitere Informationen finden Sie unter [Datenbankbezeichner](../databases/database-identifiers.md).  
  
 **Ordner für die Verteilungs-Datenbankdatei** und **Ordner für die Verteilungsdatenbank-Protokolldatei**  
 Geben Sie den Pfad für die Verteilungsdatenbank und die Protokolldateien ein. Pfade müssen auf Datenträger verweisen, die für den Verteiler lokal sind, und mit einem lokalen Laufwerkbuchstaben und Doppelpunkt (z. B. C:) beginnen. Zugeordnete Laufwerkbuchstaben und Netzwerkpfade sind ungültig.  
  
> [!NOTE]  
>  Sie können Schreibvorgänge für Transaktionen beschleunigen und die Replikationsleistung verbessern, indem Sie das Verteilungsdatenbankprotokoll nicht auf dem gleichen Datenträger wie die Verteilungsdatenbank speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Verteilung konfigurieren](configure-distribution.md)   
 [Konfigurieren der Veröffentlichung und der Verteilung](configure-publishing-and-distribution.md)   
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](view-and-modify-distributor-and-publisher-properties.md)  
  
  
