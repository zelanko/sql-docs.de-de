---
title: Abonnententypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.subscribertypes.f1
ms.assetid: a70656cb-21c9-4489-be77-ccd396747e3b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e40209c05e42b7da8f46b5c1e40b287a79669418
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48194020"
---
# <a name="subscriber-types"></a>Abonnententypen
  Mithilfe der Mergereplikation können Sie die Typen der Abonnenten angeben, die eine Veröffentlichung unterstützen muss. Die Auswahl der Abonnententypen legt den *Veröffentlichungskompatibilitätsgrad*fest, der bestimmt, welche Funktionen von einer Veröffentlichung verwendet werden können.  
  
 Nachdem eine Veröffentlichungsmomentaufnahme erstellt wurde, kann der Veröffentlichungskompatibilitätsgrad im Dialogfeld **Veröffentlichungseigenschaften** auf der Seite **Allgemein** gesteigert (restriktiver gemacht) werden. Der Veröffentlichungskompatibilitätsgrad kann nicht gesenkt werden.  
  
## <a name="options"></a>Tastatur  
 Wählen Sie jeden Abonnententypen aus, der von der Veröffentlichung unterstützt werden muss.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Die Veröffentlichung kann alle Funktionen verwenden.  
  
 [!INCLUDE[ssEW](../../includes/ssew-md.md)]  
 Momentaufnahmedateien für die Veröffentlichung müssen ein Zeichenformat aufweisen (dies wird automatisch vom Momentaufnahme-Agent gehandhabt). Für[!INCLUDE[ssEW](../../includes/ssew-md.md)] gilt auch eine Reihe von Einschränkungen ohne Bezug zum Kompatibilitätsgrad.  
  
 Wenn diese Option ausgewählt ist, dann ist die Option zur Websynchronisierung für die Veröffentlichung aktiviert. Weitere Informationen zur Websynchronisierung finden Sie unter [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von Daten und Datenbankobjekten](publish/publish-data-and-database-objects.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](view-and-modify-distributor-and-publisher-properties.md)   
 [Eigenschaftenreferenz &#40;Replikation&#41;](properties-reference-replication.md)  
  
  
