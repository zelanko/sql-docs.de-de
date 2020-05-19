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
author: rothja
ms.author: jroth
ms.openlocfilehash: 441d3f9f2de12e269839c3561dd0d202121018be
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82750189"
---
# <a name="basic-rds-programming-model"></a>Grundlegendes RDS-Programmiermodell
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 RDS adressiert Anwendungen, die in der folgenden Umgebung vorhanden sind: eine Client Anwendung gibt ein Programm an, das auf einem Server ausgeführt wird, und die Parameter, die zum Zurückgeben der gewünschten Informationen erforderlich sind. Das auf dem Server aufgerufene Programm erhält Zugriff auf die angegebene Datenquelle, ruft die Informationen ab, verarbeitet optional die Daten und gibt die resultierenden Informationen an die Client Anwendung in einem Formular zurück, das leicht verwendet werden kann. RDS bietet Ihnen die Möglichkeit, die folgende Aktions Sequenz auszuführen:  
  
-   Geben Sie das Programm an, das auf dem Server aufgerufen werden soll, und erhalten Sie eine Möglichkeit, vom Client darauf zu verweisen. (Dieser Verweis wird manchmal als *Proxy*bezeichnet. Es stellt das Remote Serverprogramm dar. Die Client Anwendung wird den Proxy so aufrufen, als ob es sich um ein lokales Programm handelt, aber tatsächlich das Remote Serverprogramm aufruft.)  
  
-   Rufen Sie das Serverprogramm auf. Übergeben Sie Parameter an das Serverprogramm, mit dem die Datenquelle und der auszugebende Befehl identifiziert werden. (Das Serverprogramm verwendet ADO, um Zugriff auf die Datenquelle zu erhalten. ADO stellt eine Verbindung mit einem der angegebenen Parameter her und gibt dann den im anderen Parameter angegebenen Befehl aus.)  
  
-   Das Serverprogramm Ruft ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt aus der Datenquelle ab. Optional wird das **Recordset** -Objekt auf dem Server verarbeitet.  
  
-   Das Serverprogramm gibt das endgültige **Recordset** -Objekt an die Client Anwendung zurück.  
  
-   Auf dem Client wird das **Recordset** -Objekt in ein Formular eingefügt, das leicht von visuellen Steuerelementen verwendet werden kann.  
  
-   Alle Änderungen am **Recordset** -Objekt werden zurück an das Serverprogramm gesendet, das Sie zum Aktualisieren der Datenquelle verwendet.  
  
 Dieses Programmiermodell enthält bestimmte praktische Features. Wenn Sie kein komplexes Serverprogramm für den Zugriff auf die Datenquelle benötigen und die erforderlichen Verbindungs-und Befehlsparameter bereitstellen, ruft RDS die angegebenen Daten automatisch mit einem einfachen Standard Serverprogramm ab.  
  
 Wenn Sie eine komplexere Verarbeitung benötigen, können Sie Ihr eigenes benutzerdefiniertes Serverprogramm angeben. Da ein benutzerdefiniertes Serverprogramm z. b. die volle Leistungsfähigkeit von ADO hat, könnte es eine Verbindung mit mehreren verschiedenen Datenquellen herstellen, die Daten auf komplexe Weise kombinieren und dann ein einfaches, verarbeitetes Ergebnis an die Client Anwendung zurückgeben.  
  
 Wenn Ihre Bedürfnisse zwischen den Anforderungen liegen, unterstützt ADO nun das Anpassen des Verhaltens des standardmäßigen Server Programms.  
  
## <a name="see-also"></a>Weitere Informationen  
 [RDS-Programmiermodell im Detail](../../../ado/guide/remote-data-service/rds-programming-model-in-detail.md)   
 [RDS-Szenario](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [RDS-Tutorial](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Verwendung und Sicherheit von RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


