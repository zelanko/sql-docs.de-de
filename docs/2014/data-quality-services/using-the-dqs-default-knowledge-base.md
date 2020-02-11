---
title: Verwenden der DQS-Standard-Wissensdatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d0fa10fa26f46857bd4f6848bd98bdcf1d65253a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65484072"
---
# <a name="using-the-dqs-default-knowledge-base"></a>Verwenden der DQS-Standard-Wissensdatenbank
  In diesem Thema wird die Standard-Wissensdatenbank **DQS-Daten**beschrieben, die mit [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) installiert wird. Dies ist eine vordefinierte Standardwissensdatenbank, die die folgenden Domänen enthält:  
  
-   **Land/Region**: enthält die konventionellen langen Namen (offizieller Name wie von Land/Region festgelegt) und Kurznamen (allgemeiner Name, der in Listen, auf Karten usw. verwendet wird), zwei buchstabige Abkürzung, drei buchstabige Abkürzung und dreistelligen Code für jeden Standort.  Der führende Wert wird auf den langen Landnamen festgelegt.  
  
-   **Land/Region (drei buchstabig führend)**: enthält die konventionellen langen Namen (offizieller Name wie von Land/Region festgelegt) und Kurznamen (allgemeiner Name, der in Listen, auf Karten usw. verwendet wird), zwei buchstabige Abkürzung, drei buchstabige Abkürzung und dreistelligen Code für jeden Standort.  Führende Werte ist auf die dreibuchstabige Abkürzung des Lands festgelegt.  
  
-   **Land/Region (zwei buchstabig führend)**: enthält die konventionellen langen Namen (offizieller Name wie von Land/Region festgelegt) und Kurznamen (allgemeiner Name, der in Listen, auf Karten usw. verwendet wird), zwei buchstabige Abkürzung, drei buchstabige Abkürzung und dreistelligen Code für jeden Standort.  Führender Wert ist auf die zweibuchstabige Abkürzung des Lands festgelegt.  
  
-   **US-** Countys: enthält eine Liste von US-Countys.  
  
-   **US-Nachname**: enthält eine Liste von Nachnamen (surnames), die 100 oder mehrmals in der Census 2000 auftreten.  
  
-   **US-Orte**: enthält eine Liste von Orten für die Zustände 50, den Bezirk von Columbia und Puerto Rico, die aus der Census 2010 extrahiert wurden.  
  
-   **US-Bundesstaat**: enthält den konventionellen langen (offiziellen) Namen und die zwei buchstabige Abkürzung für jeden Staat in US. Führender Wert ist auf den konventionellen Staatennamen festgelegt.  
  
-   **US-Bundesstaat (zwei buchstabige Überschrift)**: enthält den konventionellen langen (offiziellen) Namen und die zwei buchstabige Abkürzung für jeden Staat in US. Führender Wert ist auf die zweibuchstabige Abkürzung des Bundesstaats festgelegt.  
  
## <a name="using-the-default-knowledge-base"></a>Verwenden der Standard-Wissensdatenbank  
 Sie können die DQS-Standardwissensdatenbank (DQS-Daten) auf folgende Weise verwenden:  
  
-   Schnelles Starten und Ausführen eines Data Quality-Bereinigungsprojekts mithilfe der Standardwissensdatenbank, ohne zuerst in DQS eine neue Wissensdatenbank erstellen zu müssen.  
  
-   Ausführen der Aktivitäten Domänenverwaltung, Wissensermittlung oder Abgleichsrichtlinie für die Standardwissensdatenbank. Klicken Sie hierzu auf dem **Data Quality Client Home Screen** auf [Wissensdatenbank öffnen](../../2014/data-quality-services/data-quality-client-home-screen.md), wählen Sie die Wissensdatenbank **DQS-Daten** auf dem Bildschirm **Wissensdatenbank öffnen** aus, und wählen Sie dann die erforderliche Aktivität im Bereich **Aktivität auswählen** aus. Klicken Sie zum Fortfahren auf **Weiter** .  
  
-   Erstellen einer neuen Wissensdatenbank mithilfe der Standardwissensdatenbank. Informationen zum Erstellen einer Wissensdatenbank aus einer vorhandenen Wissensdatenbank finden Sie unter [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md).  
  
-   Verwendung in der [Komponente zur DQS-Bereinigung in Integration Services](https://go.microsoft.com/fwlink/?LinkId=238830) und im [Master Data Services-Add-In für Excel](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [DQS-Wissensdatenbanken und -Domänen](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
