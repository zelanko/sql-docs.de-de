---
title: Rendern von Berichtsverlaufs-Momentaufnahmen mit URL-Zugriff | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie einen Bericht auf der Grundlage einer Berichtsverlaufs-Momentaufnahme rendern, indem Sie den Parameter rs:Snapshot angeben und seinen Wert auf eine gültige Momentaufnahme-ID festlegen.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
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
ms.openlocfilehash: 01a173da6f22b2f2ed1cc5c273b4e1f0f1c0ec1a
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247477"
---
# <a name="render-a-report-history-snapshot-using-url-access"></a>Rendern von Berichtsverlaufs-Momentaufnahmen mit URL-Zugriff
  Sie können einen Bericht auf der Grundlage einer Berichtsverlaufs-Momentaufnahme rendern, indem Sie den Parameter *rs:Snapshot* angeben und seinen Wert auf eine gültige Momentaufnahme-ID festlegen. Der Parameterwert hat das Format YYYY-MM-DDTHH:MM:SS und basiert auf dem ISO-Standard 8601 (Standard International Organization for Standardization).  
  
 Wenn Sie diesen Parameter weglassen, wird der Bericht gemäß den Optionseinstellungen für die Berichtsausführung und Cacheverwaltung des Berichtsservers gerendert. Weitere Informationen zur Ausführung von Berichten finden Sie unter [Festlegen von Berichtsverarbeitungseigenschaften](../reporting-services/report-server/set-report-processing-properties.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine URL, die eine Berichtsverlaufs-Momentaufnahme abruft:  
  
```  
https://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [URL-Zugriff &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [URL Access Parameter Reference (URL-Zugriffsparameterverweis)](../reporting-services/url-access-parameter-reference.md)  
  
  
