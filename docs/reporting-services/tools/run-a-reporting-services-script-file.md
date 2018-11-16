---
title: Ausführen einer Reporting Services-Skriptdatei | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: tools
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], running
ms.assetid: 0de4995c-85ec-4d4c-aaef-fbd30edfb20f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: da90014c17b0540a8bee4e691835361068227565
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51814153"
---
# <a name="run-a-reporting-services-script-file"></a>Ausführen einer Reporting Services-Skriptdatei
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Skriptdateien werden von der Eingabeaufforderung in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Skriptumgebung (RS.exe) ausgeführt. In RS.exe stehen Ihnen viele Befehlszeileargumente zur Verfügung. Weitere Informationen zu den Befehlszeilenoptionen finden Sie unter [Hilfsprogramm „RS.exe“ (SSRS)](../../reporting-services/tools/rs-exe-utility-ssrs.md). Weitere Skriptbeispiele finden Sie unter [SQL Server Reporting Services-Produktbeispiele](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="sample-command-lines"></a>Beispielbefehlszeilen  
  
-   Führen Sie Script.rss in der Skriptumgebung für den Zielberichtsserver aus. Standardmäßig wird die Windows-Authentifizierung angewendet:  
  
    ```  
    rs –i Script.rss -s https://servername/reportserver  
    ```  
  
-   Führen Sie Script.rss in der Skriptumgebung unter Angabe eines Benutzernamens und eines Kennworts für die Authentifizierung der Webdienstaufrufe aus:  
  
    ```  
    rs –i Script.rss -s https://servername/reportserver -u myusername -p mypassword  
    ```  
  
-   Führen Sie Script.rss in der Skriptumgebung unter Angabe eines Timeouts von 30 Sekunden für den Server aus:  
  
    ```  
    rs –i Script.rss -s https://servername/reportserver -l 30  
    ```  
  
-   Führen Sie Script.rss in der Skriptumgebung unter Angabe einer globalen Skriptvariablen mit der Bezeichnung *report*aus:  
  
    ```  
    rs –i Script.rss -s https://servername/reportserver -v report="Company Sales"  
    ```  
  
-   Führen Sie Script.rss in der Skriptumgebung aus, und geben Sie dabei an, dass die Webdienstvorgänge in der Skriptdatei als Batch ausgeführt werden.  
  
    ```  
    rs –i Script.rss -s https://servername/reportserver -b  
    ```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Technische Referenz &#40;SSRS&#41;](../../reporting-services/technical-reference-ssrs.md)  
  
  
