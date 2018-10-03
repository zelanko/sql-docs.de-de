---
title: Konfigurieren von RDS unter Windows 2000 | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS configuration [ADO], Windows 2000
ms.assetid: ef37e858-c05f-4f52-a65f-3ce6037e0d03
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5fcff12760076a47e31fc6b140e0f3cdb7fc590e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47657748"
---
# <a name="configuring-rds-on-windows-2000"></a>Konfigurieren von RDS unter Windows 2000
Gehen folgendermaßen Sie vor, um das Problem zu beheben, wenn erste RDS ordnungsgemäß nach einem upgrade auf Windows 2000 Probleme auftreten, haben:  
  
1.  Stellen Sie sicher, dass der WWW-Publishingdienst zuerst ausgeführt wird, navigieren Sie zu http:// Server mit Internet Explorer. Wenn Sie den Webserver, auf diese Weise zugreifen können, öffnen Sie eine Eingabeaufforderung, und geben Sie den folgenden Befehl "NET START W3SVC".  
  
2.  Wählen Sie im Startmenü ausführen. Geben Sie "Msdfmap.ini", und klicken Sie dann auf OK, um die Datei "Msdfmap.ini" im Editor zu öffnen. Überprüfen Sie den Abschnitt [verbinden Standard], und wenn der Parameter für den Zugriff auf NOACCESS festgelegt ist, ändern Sie ihn auf READONLY.  
  
3.  Verwenden das Dienstprogramm "regedit" ein, navigieren Sie zu "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DataFactory\HandlerInfo", und stellen Sie sicher, dass **HandlerRequired** auf 0 festgelegt ist und **DefaultHandler** ist "" (leere Zeichenfolge).  
  
     **Beachten Sie** , wenn Sie Änderungen an diesem Abschnitt der Registrierung vornehmen, müssen Sie beenden und den WWW-Publishingdienst neu starten, durch die folgenden Befehle an einer Eingabeaufforderung eingeben: "NET STOP W3SVC" und "NET START W3SVC".  
  
4.  Verwenden das Dienstprogramm "regedit" ein, navigieren Sie in der Registrierung auf "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\W3SVC\Parameters\ADCLaunch", und überprüfen Sie, ob ein Schlüssel namens **RDSServer.Datafactory**. Wenn dies nicht der Fall ist, erstellen Sie ihn.  
  
5.  Verwenden die Internetdienste-Manager, suchen Sie die Standardwebsite, und zeigen Sie die Eigenschaften des virtuellen Stammverzeichnisses MSADC. Überprüfen Sie die Sicherheit/IP-Adresse und Einschränkungen nach Domänenname. Wählen Sie "Granted" ein, um die "Zugriff verweigert" aktiviert ist.  
  
 Achten Sie darauf, um zu versuchen, einen Neustart des Servers ein, wenn die Änderungen nicht zur Lösung des Problems zuerst angezeigt werden.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565). Ab Windows 8 und Windows Server 2012, sind RDS-Server-Komponenten nicht mehr im Windows-Betriebssystem enthalten. Migrieren von Anwendungen, mit denen RDS an [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


