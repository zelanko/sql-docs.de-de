---
title: Bereitstellen von Argumenten für Webdienstmethoden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- methods [Reporting Services], arguments
- XML Web service [Reporting Services], methods
ms.assetid: f7b9ca05-fc4c-4b30-8e5d-172dd0f4a832
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3ef5188934628589751fe92d1839da0efb265766
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60154396"
---
# <a name="supplying-web-service-method-arguments"></a>Bereitstellen von Argumenten für Webdienstmethoden
  Eine Report Server-Webdienstmethode sendet eine Anforderung an den Dienst unter einer bestimmten URL, wobei SOAP über HTTP verwendet wird. Der Dienst empfängt die Anforderung, verarbeitet sie und gibt dann eine Antwort zurück. Diese Anforderungen und Antworten haben die Form von XML-Dokumenten.  
  
## <a name="optional-parameters"></a>Optionale Parameter  
 In manchen Fällen kann eine Webdienstmethode optionale Eingabeparameter haben. Selbst wenn ein Eingabeparameter für eine Webdienstmethode optional ist, müssen Sie ihn trotzdem aufnehmen und den Parameterwert auf `null` festlegen (`Nothing` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]). Wenn Sie einen Parameterwert auf `null` festlegen, wird der Elementwert für diesen Parameter in der SOAP-Anforderung auf `null` festgelegt.  
  
 Im folgenden Beispiel wird die <xref:ReportService2010.ReportingService2010.CreateFolder%2A>-Methode zum Erstellen eines neuen Ordners mit dem Namen Product Sales im Ordner Sales verwendet. Wenn der Wert `null` für die Ordnereigenschaften verwendet wird, werden für den Ordner keine benutzerspezifischen Eigenschaften angegeben:  
  
```  
// C#  
rs.CreateFolder("Product Sales", "/Sales", null);  
```  
  
## <a name="complex-data-types"></a>Komplexe Datentypen  
 Die Kernklasse des Report Server-Webdiensts ist <xref:ReportService2010.ReportingService2010>. Sie wird verwendet, um die SOAP-Vorgänge oder Webmethoden der Proxyklasse aufzurufen. Damit diese Klasse und ihre Methoden unterstützt werden, enthält [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] benutzerdefinierte, komplexe Datentypen, die für die Eingabe- und Ausgabeparameter der Webdienstmethoden spezifisch sind. Diese komplexen Datentypen sind Teil der erzeugten Proxyklasse, die Sie beim Entwickeln in der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Umgebung verwenden können.  
  
 Wenn Sie eine Proxyklasse erzeugen, werden die in der WSDL-Datei definierten komplexen Datentypen durch die Klassen des Proxys dargestellt, die Eigenschaften enthalten, welche den verschiedenen SOAP-Elementen der komplexen Datentypen entsprechen. Sequenzen dieser Datentypen werden zu Objektarrays, die Sie im Code durchlaufen können. Dadurch ist es nicht notwendig, direkt mit den in SOAP-Nachrichten gesendeten XML-Strukturen zu arbeiten. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] behandelt diese Übersetzung für Sie.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Berichtsserver-Webdienst](../report-server-web-service.md)   
 [Technische Referenz (SSRS)](../../technical-reference-ssrs.md)  
  
  
