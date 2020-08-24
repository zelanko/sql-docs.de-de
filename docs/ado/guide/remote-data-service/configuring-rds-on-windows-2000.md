---
description: Konfigurieren von RDS unter Windows 2000
title: Konfigurieren von RDS unter Windows 2000 | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS configuration [ADO], Windows 2000
ms.assetid: ef37e858-c05f-4f52-a65f-3ce6037e0d03
author: rothja
ms.author: jroth
ms.openlocfilehash: 73ab5507d755fed32fa54b36a82f9ca915a8e194
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88758640"
---
# <a name="configuring-rds-on-windows-2000"></a>Konfigurieren von RDS unter Windows 2000
Wenn Sie Schwierigkeiten haben, RDS nach dem Upgrade auf Windows 2000 ordnungsgemäß zu verwenden, führen Sie die folgenden Schritte aus, um das Problem zu beheben:  
  
1.  Stellen Sie zunächst sicher, dass der World Wide Web Publishing Dienst ausgeführt wird, indem Sie mit Internet Explorer zu https://Server navigieren. Wenn Sie auf diese Weise keinen Zugriff auf den Webserver haben, öffnen Sie eine Eingabeaufforderung, und geben Sie den folgenden Befehl ein: "net start W3SVC".  
  
2.  Wählen Sie im Menü Start die Option Ausführen aus. Geben Sie msdfmap.ini ein, und klicken Sie dann auf OK, um die msdfmap.ini Datei in Editor zu öffnen. Überprüfen Sie den Abschnitt [Connect default], und wenn der Access-Parameter auf "NoAccess" festgelegt ist, ändern Sie ihn in "schreibgeschützt".  
  
3.  Navigieren Sie mithilfe des Hilfsprogramms regedit zu "HKEY_LOCAL_MACHINE \software\microsoft\datafactor \handlerinfo", und stellen Sie sicher, dass " **HandlerRequired** " auf "0" und " **DefaultHandler** " auf "" (NULL-Zeichenfolge) festgelegt ist.  
  
     **Hinweis** Wenn Sie Änderungen an diesem Abschnitt der Registrierung vornehmen, müssen Sie den World Wide Web Publishing-Dienst starten und neu starten, indem Sie die folgenden Befehle an einer Eingabeaufforderung eingeben: "NET stoppt W3SVC" und "net start W3SVC".  
  
4.  Navigieren Sie mithilfe des Hilfsprogramms regedit in der Registrierung zu "HKEY_LOCAL_MACHINE \system\currentcontrolset\services\w3svc\parameters\adclaunch", und vergewissern Sie sich, dass ein Schlüssel mit dem Namen **RDSServer. DataFactory**vorhanden ist. Falls nicht, erstellen Sie ihn.  
  
5.  Suchen Sie mithilfe Internetdienste-Manager die Standard Website, und zeigen Sie die Eigenschaften des virtuellen MSADC-Stamm Verzeichnisses an. Überprüfen Sie die Einschränkungen für Verzeichnis Sicherheit/IP-Adresse und Domänen Name. Wenn die Option "Zugriff verweigert" aktiviert ist, wählen Sie "erteilt" aus.  
  
 Stellen Sie sicher, dass Sie den Server neu starten, wenn die Änderungen auf dem ersten Punkt nicht zum Lösen des Problems angezeigt werden.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden. Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten. Migrieren Sie Anwendungen, die RDS verwenden, zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zu RDS](./rds-fundamentals.md)