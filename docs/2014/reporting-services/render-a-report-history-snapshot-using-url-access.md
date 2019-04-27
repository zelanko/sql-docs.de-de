---
title: Rendern von Berichtsverlaufs-Momentaufnahmen mit URL-Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], report history
- history snapshots [Reporting Services]
- historical data [Reporting Services]
- snapshots [Reporting Services], URL access
- snapshots [Reporting Services], rendering report history
ms.assetid: 3f87f82d-0e61-4492-9c4b-f5238c39e8cd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 423fd4d3b5a04b17d9e4fa92f701673ce4782ac5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62657334"
---
# <a name="render-a-report-history-snapshot-using-url-access"></a>Rendern von Berichtsverlaufs-Momentaufnahmen mit URL-Zugriff
  Sie können einen Bericht auf der Grundlage einer Berichtsverlaufs-Momentaufnahme rendern, indem Sie den Parameter *rs:Snapshot* angeben und seinen Wert auf eine gültige Momentaufnahme-ID festlegen. Der Parameterwert hat das Format YYYY-MM-DDTHH:MM:SS und basiert auf dem ISO-Standard 8601 (Standard International Organization for Standardization).  
  
 Wenn Sie diesen Parameter weglassen, wird der Bericht gemäß den Optionseinstellungen für die Berichtsausführung und Cacheverwaltung des Berichtsservers gerendert. Weitere Informationen zur Ausführung von Berichten finden Sie unter [Festlegen von Berichtsverarbeitungseigenschaften](report-server/set-report-processing-properties.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine URL, die eine Berichtsverlaufs-Momentaufnahme abruft:  
  
```  
http://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02  
```  
  
## <a name="see-also"></a>Siehe auch  
 [URL-Zugriff &#40;SSRS&#41;](url-access-ssrs.md)   
 [URL-Zugriffsparameterverweis](url-access-parameter-reference.md)  
  
  
