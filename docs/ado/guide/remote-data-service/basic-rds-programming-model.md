---
title: Grundlegendes RDS-Programmiermodell | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS programming model [ADO]
ms.assetid: 0bdd236b-edff-4aac-94c3-93e1465ca6c5
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4b8f08cda158c21d556b251d3e141b333418ca38
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704356"
---
# <a name="basic-rds-programming-model"></a>Grundlegendes RDS-Programmiermodell
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 RDS werden Anwendungen, die in der folgenden Umgebung vorhanden sind: Eine Clientanwendung gibt ein Programm, das auf einem Server und die Parameter erforderlich, um die gewünschten Informationen zurückzugeben ausgeführt wird. Das Programm aufgerufen wird, auf dem Server verschafft sich Zugriff auf die angegebene Datenquelle, ruft die Informationen ab, optional verarbeitet die Daten, und klicken Sie dann die resultierende Informationen an die Clientanwendung in ein Formular, das einfach zu verwendenden zurückgegeben. RDS bietet das bedeutet, dass Sie die folgende Sequenz von Aktionen ausführen:  
  
-   Geben Sie das Programm auf dem Server aufgerufen werden, und rufen Sie eine Möglichkeit, die vom Client darauf verweisen. (Dieser Verweis bezeichnet ein *Proxy*. Es stellt das Programm Remoteservers dar. Die Clientanwendung wird "den Proxy aufrufen" als ob es ein lokales Programm wurden, aber tatsächlich er das Programm Remoteservers ruft.)  
  
-   Serverprogramm aufrufen. Übergeben Sie Parameter, um die Server-Anwendung, die die Datenquelle und den Befehl, um das Problem zu identifizieren. (Die Server-Anwendung verwendet ADO für den Zugriff auf die Datenquelle. ADO stellt eine Verbindung mit einer der angegebenen Parameter und gibt dann den Befehl in den anderen Parameter angegeben.)  
  
-   Das Serverprogramm erhält eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt aus der Datenquelle. Optional können die **Recordset** Objekt wird auf dem Server verarbeitet.  
  
-   Serverprogramm gibt zurück, die endgültige **Recordset** Objekt an die Clientanwendung.  
  
-   Auf dem Client die **Recordset** Objekt abgelegt eines Formulars, das leicht von visuellen Steuerelementen verwendet werden kann.  
  
-   Änderungen an der **Recordset** Objekt gesendet werden, an die Server-Anwendung, die sie zum Aktualisieren der Datenquelle verwendet.  
  
 Dieses Programmiermodell enthält bestimmte praktischen Features. Wenn ein komplexer Server-Programm den Zugriff auf die Datenquelle ist nicht erforderlich, und wenn Sie die erforderliche Verbindung und Befehlsparameter angeben, automatisch RDS wird werden rufen Sie die angegebenen Daten mit einer einfachen, Standardserverprogramm ab.  
  
 Wenn Sie eine komplexere Verarbeitung benötigen, können Sie Ihre eigenen benutzerdefinierten Serverprogramm angeben. Z. B. Da benutzerdefinierte Serverprogramm das volle Potenzial von ADO, bei denen hat, konnte eine Verbindung mit unterschiedlichen Datenquellen herstellen, ihre Daten auf komplexe Weise kombinieren und dann ein einfaches, verarbeitete Ergebnis zurück, an die Clientanwendung.  
  
 Schließlich, wenn Ihre Anforderungen irgendwo dazwischen befinden, unterstützt ADO jetzt Anpassen des Verhaltens des das Standardprogramm für den Server.  
  
## <a name="see-also"></a>Siehe auch  
 [RDS-Programmiermodell im Detail](../../../ado/guide/remote-data-service/rds-programming-model-in-detail.md)   
 [RDS-Architektur](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [RDS Tutorial](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Recordset Object (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Verwendung und Sicherheit von RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


