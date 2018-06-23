---
title: Überprüfung (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98eb49e7-b190-4a21-8316-08c07cde14ed
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 769e3e1cba3179ab9a3040094f1d88f79c3c6d55
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160018"
---
# <a name="validation-master-data-services"></a>Überprüfung (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]werden Daten überprüft, um deren Genauigkeit sicherzustellen. Ein Teil der Überprüfung erfolgt automatisch und ein Teil basiert auf Geschäftsregeln, die von Administratoren erstellt werden.  
  
## <a name="when-data-validation-occurs"></a>Durchführen von Überprüfungen  
 Die Überprüfung tritt zu unterschiedlichen Zeiten auf und wird in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Webanwendung unterschiedlich angezeigt.  
  
|Überprüfungstyp|Standards bestimmt durch|Zeitpunkt des Auftretens|Angezeigt in der MasterData Manager-Webbenutzeroberfläche als|Angezeigt im Add-In für Excel als|Werden Daten im MDS-Repository gespeichert?|  
|---------------------|-----------------------------|--------------------|---------------------------------------------------|-------------------------------------------|------------------------------------------|  
|Überprüfung anhand Geschäftsregeln|MDS-Administrator|Automatisch beim Hinzufügen oder Bearbeiten von Daten.<br /><br /> Manuell, wenn ein Benutzer Geschäftsregeln anwendet.<br /><br /> Manuell, wenn ein Administrator im Funktionsbereich **Versionsverwaltung** der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung eine Version anhand von Geschäftsregeln überprüft.|Überprüfungsfehler|ValidationStatus|ja|  
|Datentyp und Inhaltsüberprüfung|MDS-Administrator beim Erstellen von Modellobjekten (z. B. Länge oder Datentyp eines Attributs)|Automatisch beim Hinzufügen oder Bearbeiten von Daten|Eingabefehler|InputStatus|nein|  
|Datentyp und Inhaltsüberprüfung|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] oder [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|Automatisch beim Hinzufügen oder Bearbeiten von Daten|Eingabefehler|InputStatus|nein|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Erstellen Sie Geschäftsregeln zum Überprüfen von Daten, und veröffentlichen Sie sie.|[Erstellen und Veröffentlichen einer Geschäftsregel &#40;Master Data Services&#41;](create-and-publish-a-business-rule-master-data-services.md)|  
|Überprüfen Sie eine Version der Daten anhand von Geschäftsregeln. Nur Administratoren.|[Überprüfen einer Datenbankversion anhand von Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)|  
|Überprüfen Sie bestimmte Teilmengen der Daten anhand von Geschäftsregeln. Alle Benutzer mit Zugriffsberechtigung auf den Funktionsbereich **Explorer** .|[Überprüfen von bestimmten Elementen anhand von Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|Überprüfen Sie bestimmte Teilmengen der Daten anhand von Geschäftsregeln. Alle Benutzer mit der Zugriffsberechtigung auf den Funktionsbereich **Explorer** und die mit [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]arbeiten.|[Anwenden von Geschäftsregeln &#40;MDS-Add-in für Excel&#41;](microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  