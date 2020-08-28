---
description: Ausführen der Adress Book-Beispielanwendung
title: Ausführen der Address Book-Beispielanwendung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: 3a2644e9-d634-4ae6-a5b7-13fb7b317ec7
author: rothja
ms.author: jroth
ms.openlocfilehash: 9c616d23d1491876425089877bf5242d34549ed5
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88977691"
---
# <a name="running-the-address-book-sample-application"></a>Ausführen der Adress Book-Beispielanwendung
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 Gehen Sie folgendermaßen vor, um die Adressbuch Anwendung auszuführen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
### <a name="to-run-this-application"></a>So führen Sie diese Anwendung aus  
  
1.  Stellen Sie sicher, dass Microsoft SQL Server ausgeführt wird. Klicken Sie auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Microsoft SQL Server 7,0**, und klicken Sie dann auf **Service Manager**. Wenn der weiße Kreis einen grünen Pfeil enthält, wird SQL Server ausgeführt. Wenn dies nicht der Fall ist (es wird ein rotes Quadrat im weißen Kreis angezeigt), klicken Sie auf **Start/weiter**.  
  
2.  Geben Sie in Microsoft Internet Explorer 4,0 oder höher die folgende Adresse ein:  
  
     **https://** - *Webserver* **/RDS/addressbook/AddrBook.ASP**  
  
     Dabei ist *Webserver* der Name des Webservers, auf dem die RDS-Serverkomponenten installiert sind.  
  
3.  Sie können dann verschiedene Szenarien in der Address Book-Beispielanwendung ausprobieren, wie z. b. das Suchen nach einer Person anhand ihres e-Mail-Namens, das Auflisten aller Personen mit dem Titel "Programm-Manager" oder das Bearbeiten vorhandener Datensätze. Klicken Sie auf **Suchen** , um das Datenraster mit allen verfügbaren Namen zu füllen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Adress Book-Datenbindungsobjekt](./address-book-data-binding-object.md)