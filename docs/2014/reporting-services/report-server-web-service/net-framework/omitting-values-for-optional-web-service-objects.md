---
title: Weglassen von Werten für optionale Webdienstobjekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], omitted values
- XML Web service [Reporting Services], omitted values
- Report Server Web service, omitted values
- omitting values [Reporting Services]
ms.assetid: ceb68b8b-9214-4745-abc9-f47f33ecd6f7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3858f73e1b332acfa1a1bbc640007f6f0884abff
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60157735"
---
# <a name="omitting-values-for-optional-web-service-objects"></a>Weglassen von Werten für optionale Webdienstobjekte
  Eigenschaften von mehreren der komplexen Typen eines Berichtsserver-Webdiensts besitzen eine zugehörige Eigenschaft, die als die Specified-Eigenschaft bekannt ist. Der Name der Eigenschaft setzt sich aus dem ursprünglichen Eigenschaftennamen und dem daran angefügten Wort "Specified" zusammen. Wenn diese Eigenschaft vorhanden ist, bedeutet dies, dass ein Wert für die ursprüngliche Eigenschaft unter Umständen manchmal weggelassen wird. Das ist das direkte Ergebnis der Übersetzung aus WSDL (Web Service Description Language) in eine [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Proxyklasse. Beispiel: Die Webdiensteigenschaft <xref:ReportService2010.DataSourceDefinition.Enabled%2A> des komplexen Typs <xref:ReportService2010.DataSourceDefinition> besitzt eine zugehörige Eigenschaft mit dem Namen <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>. Wenn Sie eine Anwendung erstellen und keinen Wert für die <xref:ReportService2010.DataSourceDefinition.Enabled%2A>-Eigenschaft festlegen möchten, müssen keinen Wert für <xref:ReportService2010.DataSourceDefinition.Enabled%2A> angeben. Es wird der Standardwert `true` verwendet. Sie müssen <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> jedoch trotzdem auf `false` festlegen. Wenn Sie einen Wert für die <xref:ReportService2010.DataSourceDefinition.Enabled%2A>-Eigenschaft angeben, müssen Sie <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> gleich `true` festlegen. Das ist bei schreibbaren Eigenschaften der Fall. Für schreibgeschützte Eigenschaften müssen Sie keine Aktion durchführen.  
  
> [!IMPORTANT]  
>  Wird keine Eigenschaft mit den oben genannten Vorgehensweisen festgelegt, kann dies zu unvorgesehenem Verhalten des Webdiensts führen.  
  
 Die Datentypen, die in der Regel Sie die zusätzliche Specified-Eigenschaft zu behandeln müssen sind `Boolean`, `DateTime`, und `Enumeration`.  
  
 Ein Beispiel hierzu finden Sie unter <xref:ReportService2010.ReportingService2010.CreateDataSource%2A>-Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Technische Referenz (SSRS)](../../technical-reference-ssrs.md)  
  
  
