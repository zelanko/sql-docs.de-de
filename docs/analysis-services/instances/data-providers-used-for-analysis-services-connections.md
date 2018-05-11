---
title: Für Analysis Services-Verbindungen verwendete Datenanbieter | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 135ef70178cc3ce231171eafbe429fd21f284535
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="client-libraries-data-providers-used-for-analysis-services-connections"></a>Für Analysis Services-Verbindungen verwendete Clientbibliotheken (Datenanbieter)
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

Analysis Services stellt drei Clientbibliotheken, auch bekannt als **Datenanbieter**für Server- und Datenzugriff von Tools und -Clientanwendungen. Tools wie SSMS und SSDT und Anwendungen, wie Power BI Desktop und Excel mit Analysis Services herstellen, mit diese Bibliotheken. Zwei der Clientbibliotheken, ADOMD.NET, und Analysis Services Management Objects (AMO), sind verwaltete Client-Bibliotheken. Der Analysis Services-OLE DB-Anbieter (MSOLAP DLL) ist eine native Client-Bibliothek. -Clientbibliotheken sind für SQL Server Analysis Services und Azure Analysis Services identisch.
  
##  <a name="bkmk_downloadsite"></a> Herunterladen einer neuere Versionen  
 Auf einem Clientcomputer installierte Version übereinstimmen, die Hauptversion des Servers, der die Daten bereitstellt. Wenn die Serverinstallation neuer als die auf den Arbeitsstationen im Netzwerk installierten Datenanbieter ist, müssen Sie u. U. neuere Bibliotheken installieren.  

Clientbibliotheken, die in früheren SQL Server-Feature Packs enthalten entsprechen auf die SQL-Version. Allerdings können sie nicht die neuesten sein. Herstellen einer Verbindung mit Azure Analysis Services erfordern eine höhere Versionen. Alle Versionen sind abwärtskompatibel.

Um die neuesten zu erhalten, finden Sie unter [Clientbibliotheken für Verbindungen mit Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers). 
  
## <a name="see-also"></a>Siehe auch  
 [Verbindung mit Analysis Services herstellen](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  
