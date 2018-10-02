---
title: 'rsModelGenerationError: Reporting Services-Fehler | Microsoft-Dokumentation'
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: troubleshooting
ms.topic: conceptual
helpviewer_keywords:
- rsModelGenerationError
ms.assetid: 3a0ad63f-87f9-4ca1-b0c2-c85fa991634a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9a8c2dc17bbb6599acbb363d7d8f8b9c51bc061a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47707678"
---
# <a name="rsmodelgenerationerror---reporting-services-error"></a>rsModelGenerationError – Reporting Services-Fehler
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|rsRenderingError|  
|Ereignisquelle|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Komponente|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Meldungstext|Fehler beim Generieren des Modells. (rsModelGenerationError) (ReportingServicesLibrary) %1|  
  
## <a name="explanation"></a>Erklärung  
 Das Berichtsmodell konnte nicht generiert werden. In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 SP1 und früheren Versionen wird der Fehler meist angezeigt, wenn das System.Data.DataSet-Objekt eine Tabelle oder Beziehung innerhalb des Datenbankschemas nicht behandeln kann, beispielsweise wenn für dieselbe Spalte in einer Tabelle zwei Fremdschlüssel definiert wurden.  
  
## <a name="user-action"></a>Benutzeraktion  
 Überprüfen Sie die Berichtsserver-Protokolldateien, um die spezifische Ursache dieser Meldung zu bestimmen. Diese Dateien finden Sie unter \Microsoft SQL Server\\<SQL Server-Instanz\>\Reporting Services\LogFiles.  
  
## <a name="internal-only"></a>Nur intern  
  
