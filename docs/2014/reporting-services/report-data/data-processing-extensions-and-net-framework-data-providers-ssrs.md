---
title: Datenverarbeitungserweiterungen und .NET Framework-Datenanbieter (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], data
- data processing extensions [Reporting Services]
- data providers [Reporting Services]
- data retrieval [Reporting Services]
- Reporting Services, data sources
- report data [Report Builder], accessing
ms.assetid: 42a5afb5-f4c8-4957-b1fd-77bf39afa5be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e91dd470b4810fc13c95cbb335b1cf8d2b10430e
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66107383"
---
# <a name="data-processing-extensions-and-net-framework-data-providers-ssrs"></a>Datenverarbeitungserweiterungen und .NET Framework-Datenanbieter (SSRS)
  Eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Datenverarbeitungserweiterung ist eine Komponente, die mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]installiert wird und zum Abrufen von Daten von einem bestimmten Datenquellentyp sowie zum Bereitstellen zusätzlicher Funktionalität zur Unterstützung des Berichtsentwurfs und der Berichtsverarbeitung verwendet wird. Eine [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -Datenanbieter ist eine Komponente, die von [!INCLUDE[msCoName](../../includes/msconame-md.md)] oder Drittanbieterquellen verfügbar ist und <xref:System.Data> -Schnittstellen unterstützt, über die Sie Daten von einem bestimmten Datenquellentyp abrufen und ändern können.  
  
## <a name="understanding-a-data-processing-extension"></a>Grundlegendes zu Datenverarbeitungserweiterungen  
 Eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Datenverarbeitungserweiterung unterstützt eine Teilmenge der <xref:System.Data> -Schnittstellen. Für Datenverarbeitungserweiterungen ist lediglich schreibgeschützter Zugriff auf eine Datenquelle erforderlich. Deshalb werden die Schnittstellen zum Schreiben und Aktualisieren nicht implementiert. Jede Datenverarbeitungserweiterung kann benutzerdefinierte funktionen bereitstellen, um die Berichtsverarbeitung zu unterstützen. Zum Beispiel könnte eine Datenverarbeitungserweiterung die folgenden Funktionstypen unterstützen:  
  
-   Verwalten der Anmeldeinformationen getrennt von der Verbindungszeichenfolge  
  
-   Unterstützen von mehrwertigen Parametern  
  
-   Abrufen von Serveraggregaten, die anhand der Datenquelle berechnet werden  
  
-   Abrufen von Dateneigenschaften und Datenwerten von der Datenquelle  
  
## <a name="understanding-a-data-provider"></a>Grundlegendes zu einem Datenanbieter  
 Eine [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -Datenanbieter (manchmal als Treiber bezeichnet) unterstützt einen Standardsatz von <xref:System.Data> -Schnittstellen zum Schreiben, Lesen und Aktualisieren von Daten in einer Datenquelle. Ein Datenanbieter kann verwendet werden, wenn für einen bestimmten Datenquellentyp keine Datenverarbeitungserweiterung verfügbar ist. Ihnen stehen viele standardmäßige [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -Datenanbieter von Drittanbietern zur Verfügung.  
  
 Da [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] über eine erweiterbare Datenanbieterarchitektur verfügt, können Sie eine benutzerdefinierte Datenverarbeitungserweiterung erstellen, um die von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Datenverarbeitungserweiterungen bereitgestellte zusätzliche Funktionalität einzuschließen. Weitere Informationen finden Sie unter [Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md). Informationen zu Datenverarbeitungserweiterungen von Drittanbietern finden Sie in der mit der Datenverarbeitungserweiterung des Drittanbieters gelieferten Dokumentation.  
  
> [!NOTE]  
>  Ein [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -Datenanbieter oder eine benutzerdefinierte Datenverarbeitungserweiterung muss installiert und registriert werden, bevor Sie damit auf Daten aus einer Datenquelle zugreifen können. Die Datenverarbeitungserweiterung muss zum Verfassen des Berichts auf dem Berichterstellungsclient installiert und registriert werden sowie auf dem Berichtsserver, um den veröffentlichten Bericht anzuzeigen. Nicht alle Datenanbieter funktionieren in einer Serverumgebung. Weitere Informationen finden Sie unter [Registrieren eines .NET Framework-Standarddatenproviders (SSRS)](register-a-standard-net-framework-data-provider-ssrs.md) und [Bereitstellen von Datenverarbeitungserweiterungen](../extensions/data-processing/deploying-a-data-processing-extension.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Datenverarbeitungserweiterungen](../extensions/data-processing/data-processing-extensions-overview.md)   
 [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
