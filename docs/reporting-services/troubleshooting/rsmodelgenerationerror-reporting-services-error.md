---
title: 'rsModelGenerationError: Reporting Services-Fehler | Microsoft-Dokumentation'
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: troubleshooting
ms.topic: conceptual
helpviewer_keywords:
- rsModelGenerationError
ms.assetid: 3a0ad63f-87f9-4ca1-b0c2-c85fa991634a
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 870f1fbc49e99e2cd43c6adb857137776c275550
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "65574091"
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
  
