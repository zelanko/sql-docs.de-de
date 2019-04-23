---
title: Ausführen einer Reporting Services-Skriptdatei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], running
ms.assetid: 0de4995c-85ec-4d4c-aaef-fbd30edfb20f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8d4023d5fb434f58fd031e6512f3fa84fa551fec
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59958856"
---
# <a name="run-a-reporting-services-script-file"></a>Ausführen einer Reporting Services-Skriptdatei
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Skriptdateien werden von der Eingabeaufforderung in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Skriptumgebung (RS.exe) ausgeführt. In RS.exe stehen Ihnen viele Befehlszeileargumente zur Verfügung. Weitere Informationen zu den Befehlszeilenoptionen finden Sie unter [Hilfsprogramm „RS.exe“ (SSRS)](rs-exe-utility-ssrs.md). Weitere Skriptbeispiele finden Sie unter [SQL Server Reporting Services-Produktbeispiele](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="sample-command-lines"></a>Beispielbefehlszeilen  
  
-   Führen Sie Script.rss in der Skriptumgebung für den Zielberichtsserver aus. Standardmäßig wird die Windows-Authentifizierung angewendet:  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver  
    ```  
  
-   Führen Sie Script.rss in der Skriptumgebung unter Angabe eines Benutzernamens und eines Kennworts für die Authentifizierung der Webdienstaufrufe aus:  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -u myusername -p mypassword  
    ```  
  
-   Führen Sie Script.rss in der Skriptumgebung unter Angabe eines Timeouts von 30 Sekunden für den Server aus:  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -l 30  
    ```  
  
-   Führen Sie Script.rss in der Skriptumgebung unter Angabe einer globalen Skriptvariablen mit der Bezeichnung *report*aus:  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -v report="Company Sales"  
    ```  
  
-   Führen Sie Script.rss in der Skriptumgebung aus, und geben Sie dabei an, dass die Webdienstvorgänge in der Skriptdatei als Batch ausgeführt werden.  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -b  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Technische Referenz &#40;SSRS&#41;](../technical-reference-ssrs.md)  
  
  
