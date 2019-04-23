---
title: 'rsModelGenerationError: Reporting Services-Fehler | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsModelGenerationError
ms.assetid: 3a0ad63f-87f9-4ca1-b0c2-c85fa991634a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 248187189db1270439e16b21139c40e9440b2ba3
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59962646"
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
  
