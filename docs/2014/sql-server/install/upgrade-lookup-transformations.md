---
title: Transformationen für das Upgrade von Lookup | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation and upgrading
- upgrading caching for Lookup transformation
- upgrading Lookup transformation
ms.assetid: d9b2c281-91ee-4e20-bdf0-0cd77d4a4241
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 74430ab1bed232b8d510a8c28a8a690d88d1f6ba
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85041647"
---
# <a name="upgrade-lookup-transformations"></a>Aktualisieren von Transformationen für die Suche
  Beim Upgrade von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sollten Sie die Pakete ggf. ändern, um die Vorteile der neuen Funktionen in der Transformation für Suche zu nutzen. Die Transformation unterstützt die in [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] verfügbaren Zwischenspeicherungstypen und Datenausgabeoptionen. Weitere Informationen zu zusätzlichen Caching-und Daten Ausgaben finden Sie unter [Transformation für Suche](../../integration-services/data-flow/transformations/lookup-transformation.md).  
  
 In [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] sind die vollständige Zwischenspeicherung, die teilweise Zwischenspeicherung sowie keine Zwischenspeicherung als Zwischenspeicherungstypen verfügbar. In [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] können Sie eine Transformation für Suche so konfigurieren, dass einer dieser Zwischenspeicherungstypen verwendet wird. Weitere Informationen zum Implementieren der partiellen Zwischenspeicherung oder zum Zwischenspeichern finden Sie unter [Implementieren einer Suche im Modus "kein Cache" oder "Teilcache](../../integration-services/data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md)". Weitere Informationen zum Implementieren der vollständigen Zwischenspeicherung finden Sie unter [Implementieren einer Transformation für Suche im voll Cache Modus mit dem](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md) Cacheverbindungs-Manager und [Implementieren einer Such Transformation im voll Cache Modus mit dem OLE DB-Verbindungs-Manager](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).  
  
 In [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] hatte die Transformation für Suche eine Eingabe, eine Ausgabe und eine Fehlerausgabe. Zeilen in der Eingabe, die über übereinstimmende Einträge im Verweisdataset verfügten, wurden von der Ausgabe verarbeitet. Zeilen in der Eingabe, die über keine übereinstimmenden Einträge verfügten, wurden als Fehler behandelt und konnten an die Fehlerausgabe weitergeleitet werden. In [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] verfügte die Transformation für Suche über zwei Ausgaben: eine Ausgabe mit Übereinstimmung und eine Ausgabe ohne Übereinstimmung.  
  
 Standardmäßig werden bei Verwendung einer Transformation für Suche, die in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] erstellt wurde, die Zeilen ohne übereinstimmende Einträge von [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] als Fehler behandelt, sodass Sie die Zeilen an eine Fehlerausgabe weiterleiten können. Sie haben die Möglichkeit, die Transformation für Suche so zu konfigurieren, dass die Zeilen nicht als Fehler behandelt und die Zeilen an die Ausgabe ohne Übereinstimmung weitergeleitet werden.  
  
 Weitere Informationen finden Sie unter [Lookup Transformation Editor &#40;Seite Allgemeine Seite&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Suchtransformation](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  
