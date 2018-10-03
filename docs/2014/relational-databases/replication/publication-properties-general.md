---
title: Veröffentlichungseigenschaften (Allgemein) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.pubproperties.general.f1
ms.assetid: 7912362f-c4d6-4f60-bd39-dee1f656ed18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f6337e69df7b7d6fe0984a843bf82124f90cc4d2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48112670"
---
# <a name="publication-properties-general"></a>Veröffentlichungseigenschaften (Allgemein)
  Auf der Seite **Allgemein** des Dialogfelds **Veröffentlichungseigenschaften** sind grundlegende Informationen wie Name, Beschreibung und Abonnementablaufrichtlinie der Veröffentlichung enthalten  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Der Name der Veröffentlichung (schreibgeschützt).  
  
 **Datenbank**  
 Der Name der Veröffentlichungsdatenbank (schreibgeschützt).  
  
 **Beschreibung**  
 Die Beschreibung der Veröffentlichung.  
  
 **Typ**  
 Der Typ der Veröffentlichung (schreibgeschützt).  
  
 **Abonnementablauf**  
 Wählen Sie eine der Optionen für Abonnementablauf aus: **Abonnements laufen nie ab** oder **Abonnements laufen ab**, und geben Sie einen expliziten Zeitraum an (**Intervall**).  
  
 Bei Momentaufnahme- und Transaktionsveröffentlichungen empfiehlt [!INCLUDE[msCoName](../../includes/msconame-md.md)] , die Standardeinstellung **Abonnements laufen nie ab**zu übernehmen.  
  
 Bei Mergereplikationen empfiehlt [!INCLUDE[msCoName](../../includes/msconame-md.md)] , die Standardeinstellung **Abonnements laufen ab** zu übernehmen und einen möglichst niedrigen Wert für **Intervall**festzulegen. Je länger der Ablaufzeitraum des Abonnements ist, desto mehr Metadaten werden auch gespeichert, was sich nachteilig auf die Leistung auswirken kann. Wägen Sie die Notwendigkeit, die Verbindung mit Abonnenten zu trennen oder diese über einen längeren Zeitraum nicht zu synchronisieren, gegen die Leistungsprobleme ab, die das Speichern und Verarbeiten großer Datenmengen nach sich ziehen kann.  
  
 Weitere Informationen finden Sie unter [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
 **Kompatibilitätsgrad**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höher; nur für Mergeveröffentlichungen. Wählen Sie die niedrigste [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Version aus, die für Abonnenten, die mit dieser Veröffentlichung synchronisiert werden, erforderlich ist. Für die Bestimmung des Kompatibilitätsgrades gibt es eine Reihe von Regeln.  
  
## <a name="see-also"></a>Siehe auch  
 [Create a Publication](publish/create-a-publication.md)   
 [Anzeigen und Ändern von Veröffentlichungseigenschaften](publish/view-and-modify-publication-properties.md)   
 [Veröffentlichen von Daten und Datenbankobjekten](publish/publish-data-and-database-objects.md)  
  
  
