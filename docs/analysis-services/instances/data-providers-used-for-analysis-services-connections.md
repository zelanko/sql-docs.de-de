---
title: Für Analysis Services-Verbindungen verwendete Datenanbieter | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f5ba97f90b877896d68cd62598f11d0845fb698e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38057848"
---
# <a name="client-libraries-data-providers-used-for-analysis-services-connections"></a>Für Analysis Services-Verbindungen verwendeten Clientbibliotheken (Datenanbieter)
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

Analysis Services stellt drei Clientbibliotheken, auch bekannt als **Datenanbieter**für Server und der Datenzugriff über Tools und Clientanwendungen. Tools wie SSMS und SSDT und Anwendungen wie Power BI Desktop und Excel zu Analysis Services herstellen von Verbindungen mithilfe dieser Bibliotheken. Zwei der Clientbibliotheken, ADOMD.NET und Analysis Services Management Objects (AMO) sind verwaltete Clientbibliotheken. Der Analysis Services OLE DB-Anbieter (MSOLAP DLL) ist eine native Clientbibliothek. Client-Bibliotheken sind für SQL Server Analysis Services und Azure Analysis Services identisch.
  
##  <a name="bkmk_downloadsite"></a> Neuere Versionen herunterladen  
 Die auf einem Clientcomputer installierte Version sollte die Hauptversion des Servers, der die Daten bereitstellt übereinstimmen. Wenn die Serverinstallation neuer als die auf den Arbeitsstationen im Netzwerk installierten Datenanbieter ist, müssen Sie u. U. neuere Bibliotheken installieren.  

Clientbibliotheken, die in früheren SQL Server Feature Packs enthalten entsprechen Version, die diese SQL; Sie können jedoch die neueste Version nicht. Herstellen einer Verbindung mit Azure Analysis Services unter Umständen höher. Alle Versionen sind abwärtskompatibel.

Um die neueste Version zu erhalten, finden Sie unter [-Clientbibliotheken für die Verbindung mit Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers). 
  
## <a name="see-also"></a>Siehe auch  
 [Verbindung mit Analysis Services herstellen](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  
