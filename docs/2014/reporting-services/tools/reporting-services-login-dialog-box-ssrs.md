---
title: Reporting Services-Anmeldung (Dialogfeld) (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rtp.rptdesigner.reportservicelogin.f1
ms.assetid: 2037d797-0b61-44c7-931f-6c689c3fc733
caps.latest.revision: 29
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: e4a3feeca737e1d4db6627af5ece9fa9d36c6b7b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148104"
---
# <a name="reporting-services-login-dialog-box-ssrs"></a>Reporting Services-Anmeldung (Dialogfeld) (SSRS)
  Verwenden Sie das Dialogfeld **Reporting Services-Anmeldung** , um die Anmeldeinformationen zum Veröffentlichen von Berichten auf dem Berichtsserver bereitzustellen.  
  
-   **Hinweis** ist dies das erste Mal einen Bericht auf einem Berichtsserver, seit festlegen veröffentlicht haben legen Sie die Bereitstellungseigenschaft **TargetServerURL** für ein Projekt, stellen Sie sicher, dass der angegebene Servername ähnelt `http://localhost/reportserver`, und nicht `http://localhost/reports`. Durch Angeben des `reports` -Verzeichnisses auf dem lokalen Server anstelle des `reportserver` -Verzeichnisses wird indirekt bewirkt, dass dieses Dialogfeld geöffnet wird. Weitere Informationen zum Festlegen von **TargetServerURL** finden Sie unter [Festlegen von Bereitstellungseigenschaften (Reporting Services)](set-deployment-properties-reporting-services.md).  
  
## <a name="options"></a>Tastatur  
 **Server**  
 Zeigt den Namen des Berichtsservers an. Beispiel: `http://localhost/reportserver`. Für Berichtsserver, die einen anderen Port verwenden als Standardport 80, schließen Sie die Portnummer ein. Beispiel: `http://localhost:81/reportserver`.  
  
 **Benutzername**  
 Geben Sie den Benutzernamen ein, der beim Anmelden am Webdienst verwendet werden soll.  
  
 **Kennwort**  
 Geben Sie das Kennwort ein, das beim Anmelden am Webdienst verwendet werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](../report-data/specify-credential-and-connection-information-for-report-data-sources.md) [Berichts-Designer-F1-Hilfe](report-designer-f1-help.md)  
  
  