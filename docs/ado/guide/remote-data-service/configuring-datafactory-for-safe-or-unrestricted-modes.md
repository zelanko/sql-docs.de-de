---
description: Konfigurieren von DataFactory für den sicheren oder den uneingeschränkten Modus
title: Konfigurieren von datafactory für den sicheren oder uneingeschränkten Modus | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory configuration in RDS [ADO]
ms.assetid: 8ff24805-dc7a-42ae-b600-5bad0e3f51b8
author: rothja
ms.author: jroth
ms.openlocfilehash: ffd9c1b82225a131722cdaf384c4bd5662b5322f
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88758390"
---
# <a name="configuring-datafactory-for-safe-or-unrestricted-modes"></a>Konfigurieren von DataFactory für den sicheren oder den uneingeschränkten Modus
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 ADO wird standardmäßig mit einer "sicheren" [RDSServer. DataFactory](../../reference/rds-api/datafactory-object-rdsserver.md) -Konfiguration installiert. Der abgesicherte Modus für RDS-Server Komponenten bedeutet, dass Folgendes zutrifft:  
  
1.  Der Handler ist mit dem RDSServer. DataFactory erforderlich (Dies wird durch eine Registrierungsschlüssel Einstellung vorgeschrieben).  
  
2.  Der Standard Handler, msdfmap. Handler, ist registriert, in der Liste der Safe-Handler vorhanden und als Standard Handler gekennzeichnet.  
  
3.  Msdfmap.ini Datei wird im Windows-Verzeichnis installiert. Sie müssen diese Datei gemäß Ihren Anforderungen konfigurieren, bevor Sie RDS im Modus mit drei Ebenen verwenden.  
  
 Optional können Sie eine unbeschränkte **DataFactory** -Installation konfigurieren. **DataFactory** kann direkt ohne den benutzerdefinierten Handler verwendet werden. Benutzer können weiterhin einen benutzerdefinierten Handler verwenden, indem Sie die Verbindungs Zeichenfolgen ändern, dies ist jedoch nicht erforderlich. Weitere Informationen zu den Auswirkungen der Verwendung des **RDSServer. DataFactory** -Objekts finden Sie unter [Sichern von RDS-Anwendungen](./securing-rds-applications.md).  
  
 Die Registrierungsdatei handsafe. reg wurde bereitgestellt, um die Handler-Registrierungseinträge für eine sichere Konfiguration einzurichten. Wenn Sie im abgesicherten Modus ausführen möchten, führen Sie handsafe. reg aus.  
  
 Nach dem Ausführen von handsafe. reg müssen Sie den World Wide Web Publishing Dienst auf dem Webserver abbrechen und neu starten, indem Sie die folgenden Befehle in einem Eingabe Aufforderungs Fenster eingeben: "NET-W3SVC" und "net start W3SVC".  
  
## <a name="see-also"></a>Weitere Informationen  
 [DataFactory-Anpassung](./datafactory-customization.md)   
 [Grundlegendes zu RDS](./rds-fundamentals.md)