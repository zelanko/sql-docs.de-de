---
title: 'Der Datenverbindungspfad in der Arbeitsmappe verweist auf eine Datei auf dem lokalen Laufwerk oder entspricht einem ungültigen URI. Die folgenden Verbindungen wurden nicht aktualisiert: Power Pivot-Daten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: bd22e41a-0931-4d32-888a-633a3046fc5e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0cc18a2c7111c71b62f77f5f52727a4a50a661ba
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66071035"
---
# <a name="the-data-connection-path-in-the-workbook-points-to-a-file-on-the-local-drive-or-is-an-invalid-uri-the-following-connections-failed-to-refresh-powerpivot-data"></a>Der Datenverbindungspfad in der Arbeitsmappe verweist auf eine Datei auf dem lokalen Laufwerk oder entspricht einem ungültigen URI. Die folgenden Verbindungen wurden nicht aktualisiert: PowerPivot-Daten
  Für Excel-Arbeitsmappen, die PowerPivot-Daten enthalten, gibt Excel Services diesen Fehler zurück, wenn keine Verbindung mit eingebetteten Datenquellen hergestellt werden kann.  
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Gilt für|PowerPivot für SharePoint|  
|Produktversion|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Ursache|Excel Services werden dafür konfiguriert, nur Datenverbindungen von ODC-Dateien zuzulassen, die sich in einer vertrauenswürdigen Datenverbindungsbibliothek befinden.|  
|Meldungstext|Der Datenverbindungspfad in der Arbeitsmappe verweist auf eine Datei auf dem lokalen Laufwerk oder entspricht einem ungültigen URI. Die folgenden Verbindungen wurden nicht aktualisiert: PowerPivot-Daten|  
  
## <a name="explanation"></a>Erläuterung  
 PowerPivot-Arbeitsmappen enthalten eingebettete Datenverbindungen. Um die Interaktion mit Arbeitsmappen über Slicer und Filter zu unterstützen, müssen Excel Services so konfiguriert sein, dass der externe Datenzugriff über eingebettete Verbindungsinformationen möglich ist. Externer Datenzugriff ist zum Abrufen von PowerPivot-Daten erforderlich, die auf PowerPivot-Server in der Farm geladen wurden.  
  
## <a name="user-action"></a>Benutzeraktion  
 Ändern Sie die Konfigurationseinstellungen, um eingebettete Datenquellenverbindungen zuzulassen.  
  
1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.  
  
2.  Klicken Sie auf **Excel Services-Anwendung**.  
  
3.  Klicken Sie auf **Vertrauenswürdiger Dateispeicherort**.  
  
4.  Klicken Sie auf **http://** oder den Speicherort, den Sie konfigurieren möchten.  
  
5.  Klicken Sie unter Externe Daten in **Externe Daten zulassen**auf Vertrauenswürdige Datenverbindungsbibliotheken und eingebettete Verbindungen.  
  
6.  Klicken Sie auf **OK**.  
  
 Alternativ können Sie einen neuen vertrauenswürdigen Speicherort für Websites erstellen, die PowerPivot-Arbeitsmappen enthalten, und dann die Konfigurationseinstellungen nur für diese Website ändern. Weitere Informationen finden Sie unter [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  
