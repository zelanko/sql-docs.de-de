---
title: Konfigurieren von DataFactory für den sicheren bzw. uneingeschränkten Modus | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0ee24eb54db193aa16f15f550de66b92cf9b896c
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66699785"
---
# <a name="configuring-datafactory-for-safe-or-unrestricted-modes"></a>Konfigurieren von DataFactory für den sicheren oder den uneingeschränkten Modus
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Standardmäßig wird die ADO mit einer "sicheren" installiert [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) Konfiguration. Im Abgesicherter Modus für RDS-Server-Komponenten bedeutet, dass Folgendes zutrifft:  
  
1.  Handler, die mit der RDSServer.DataFactory (Dies wird durch eine registrierungsschlüsseleinstellung vorgeschrieben) erforderlich ist.  
  
2.  Der Standardhandler, msdfmap.handler, wird registriert, als Standardhandler markiert und in der Liste sicherer Handler vorhanden.  
  
3.  Datei "Msdfmap.ini" wird im Windows-Verzeichnis installiert. Bevor Sie RDS in 3-Tier-Modus verwenden, müssen Sie diese Datei gemäß Ihren Anforderungen entspricht, konfigurieren.  
  
 Optional können Sie einem uneingeschränkten konfigurieren **DataFactory** Installation. **DataFactory** direkt ohne benutzerdefinierten Handlers verwendet werden kann. Benutzer können einen benutzerdefinierten Handler weiterhin verwenden, indem Sie die Verbindungszeichenfolgen ändern, aber es ist nicht erforderlich. Weitere Informationen zu den Auswirkungen der Verwendung der **RDSServer.DataFactory** Objekt, finden Sie unter [Sichern von RDS-Anwendungen](../../../ado/guide/remote-data-service/securing-rds-applications.md).  
  
 Die Registrierung Datei handsafe.reg wurde bereitgestellt, um die Handler-Registrierungseinträge für eine sichere Konfiguration einzurichten. Führen Sie zum Ausführen im abgesicherten Modus handsafe.reg.  
  
 Nach der Ausführung handsafe.reg, müssen Sie beenden und starten Sie den WWW-Publishingdienst auf dem Webserver neu, indem Sie die folgenden Befehle in einem Eingabeaufforderungsfenster eingeben: "NET STOP W3SVC" und "NET START W3SVC".  
  
## <a name="see-also"></a>Siehe auch  
 [DataFactory-Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)



