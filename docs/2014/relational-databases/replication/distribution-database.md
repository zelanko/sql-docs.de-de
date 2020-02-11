---
title: Verteilungsdatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configuredistributionwizard.distributiondatabase.f1
ms.assetid: 5b42a083-7a11-41d8-9e3f-320c7c907237
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 283fd67d14d57c3d1d5d60dd9d8de2a159ca6d5e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62721373"
---
# <a name="distribution-database"></a>Verteilungsdatenbank
  Die Verteilungsdatenbank speichert Metadaten und Verlaufsdaten für alle Replikationstypen und Transaktionen für die Transaktionsreplikation.  
  
 In vielen Fällen reicht eine Verteilungsdatenbank aus. Wenn jedoch mehrere Verleger einen Verteiler verwenden, sollten Sie die Erstellung einer Verteilungsdatenbank für jeden Verleger in Betracht ziehen. Auf diese Weise stellen Sie sicher, dass die durch jede Verteilungsdatenbank fließenden Daten eindeutig sind. Mit dem Verteilungskonfigurations-Assistenten können Sie eine Verteilungsdatenbank für den Verteiler angeben. Geben Sie bei Bedarf im Dialogfeld **Verteilereigenschaften** weitere Verteilungsdatenbanken an.  
  
## <a name="options"></a>Tastatur  
 **Name der Verteilungs Datenbank**  
 Geben Sie einen Namen für die Verteilungsdatenbank ein. Der Standardname für die Verteilungsdatenbank lautet 'distribution'. Wenn Sie einen Namen angeben, kann der Name maximal 128 Zeichen lang sein, muss innerhalb einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]eindeutig sein und den Regeln für Bezeichner entsprechen. Weitere Informationen finden Sie unter [Datenbankbezeichner](../databases/database-identifiers.md).  
  
 **Ordner für die Verteilungs-Datenbankdatei** und **den Ordner für die Verteilungs Datenbank-Protokolldatei**  
 Geben Sie den Pfad für die Verteilungsdatenbank und die Protokolldateien ein. Pfade müssen auf Datenträger verweisen, die für den Verteiler lokal sind, und mit einem lokalen Laufwerkbuchstaben und Doppelpunkt (z. B. C:) beginnen. Zugeordnete Laufwerkbuchstaben und Netzwerkpfade sind ungültig.  
  
> [!NOTE]  
>  Sie können Schreibvorgänge für Transaktionen beschleunigen und die Replikationsleistung verbessern, indem Sie das Verteilungsdatenbankprotokoll nicht auf dem gleichen Datenträger wie die Verteilungsdatenbank speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verteilung konfigurieren](configure-distribution.md)   
 [Konfigurieren der Veröffentlichung und der Verteilung](configure-publishing-and-distribution.md)   
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](view-and-modify-distributor-and-publisher-properties.md)  
  
  
