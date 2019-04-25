---
title: Verwenden der DQS-Standard-Wissensdatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2012
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 5767515d290ed6933af55f1405b06f735f704b63
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62470735"
---
# <a name="using-the-dqs-default-knowledge-base"></a>Verwenden der DQS-Standard-Wissensdatenbank

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In diesem Thema wird die Standard-Wissensdatenbank **DQS-Daten**beschrieben, die mit [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) installiert wird. Dies ist eine vordefinierte Standardwissensdatenbank, die die folgenden Domänen enthält:  
  
-   **Land/Region:** Enthält die konventionellen langen Namen (offizielle, von „Land/Region“ festgelegte Namen) und kurze Namen (allgemeine Namen, die in Listen, auf Karten usw. verwendet werden), Abkürzungen mit zwei Buchstaben, Abkürzungen mit drei Buchstaben sowie dreistelligen Code für jeden Standort.  Der führende Wert wird auf den langen Landnamen festgelegt.  
  
-   **Country/Region (three-letter leading)** (Land/Region (dreibuchstabig führend)): Enthält die konventionellen langen Namen (offizielle, von „Land/Region“ festgelegte Namen) und kurze Namen (allgemeine Namen, die in Listen, auf Karten usw. verwendet werden), Abkürzungen mit zwei Buchstaben, Abkürzungen mit drei Buchstaben sowie dreistelligen Code für jeden Standort.  Führende Werte ist auf die dreibuchstabige Abkürzung des Lands festgelegt.  
  
-   **Country/Region (two-letter leading)** (Land/Region (zweibuchstabig führend)): Enthält die konventionellen langen Namen (offizielle, von „Land/Region“ festgelegte Namen) und kurze Namen (allgemeine Namen, die in Listen, auf Karten usw. verwendet werden), Abkürzungen mit zwei Buchstaben, Abkürzungen mit drei Buchstaben sowie dreistelligen Code für jeden Standort.  Führender Wert ist auf die zweibuchstabige Abkürzung des Lands festgelegt.  
  
-   **US – Counties** (US-Countys): Enthält eine Liste von US-Countys  
  
-   **US -– Last Name** (US-Nachname): Enthält eine Liste von Nachnamen, die in der Volkszählung 2000 mindestens 100 Mal vorkamen.  
  
-   **US – Places** (US-Orte): Enthält eine Liste von Orten für die 50 Staaten, den District of Columbia und Puerto Rico, die aus der Volkszählung 2010 stammen.  
  
-   **US – State** (US-Staat): Enthält den konventionellen langen (offiziellen) Namen und die zweibuchstabige Abkürzung für jeden Staat der USA. Führender Wert ist auf den konventionellen Staatennamen festgelegt.  
  
-   **US – State (2-letter heading)** (US-Bundesstaat (zweibuchstabige Überschrift)): Enthält den konventionellen langen (offiziellen) Namen und die zweibuchstabige Abkürzung für jeden Staat der USA. Führender Wert ist auf die zweibuchstabige Abkürzung des Bundesstaats festgelegt.  
  
## <a name="using-the-default-knowledge-base"></a>Verwenden der Standard-Wissensdatenbank  
 Sie können die DQS-Standardwissensdatenbank (DQS-Daten) auf folgende Weise verwenden:  
  
-   Schnelles Starten und Ausführen eines Data Quality-Bereinigungsprojekts mithilfe der Standardwissensdatenbank, ohne zuerst in DQS eine neue Wissensdatenbank erstellen zu müssen.  
  
-   Ausführen der Aktivitäten Domänenverwaltung, Wissensermittlung oder Abgleichsrichtlinie für die Standardwissensdatenbank. Klicken Sie hierzu auf dem **Data Quality Client Home Screen** auf [Wissensdatenbank öffnen](../data-quality-services/data-quality-client-home-screen.md), wählen Sie die Wissensdatenbank **DQS-Daten** auf dem Bildschirm **Wissensdatenbank öffnen** aus, und wählen Sie dann die erforderliche Aktivität im Bereich **Aktivität auswählen** aus. Klicken Sie auf **Weiter** , um den Vorgang fortzusetzen.  
  
-   Erstellen einer neuen Wissensdatenbank mithilfe der Standardwissensdatenbank. Informationen zum Erstellen einer Wissensdatenbank aus einer vorhandenen Wissensdatenbank finden Sie unter [Create a Knowledge Base](../data-quality-services/create-a-knowledge-base.md).  
  
-   Verwendung in der [Komponente zur DQS-Bereinigung in Integration Services](https://go.microsoft.com/fwlink/?LinkId=238830) und im [Master Data Services-Add-In für Excel](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Siehe auch  
 [DQS-Wissensdatenbanken und -Domänen](../data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
