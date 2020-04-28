---
title: Abschnitt "Anpassungs Datei Protokolle" | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- logs section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: a368e264-865c-41ee-be00-d9097255c2ea
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 14c5436478444e525c7a9753cf3e4e5cddb92f5d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922788"
---
# <a name="customization-file-logs-section"></a>Logs-Abschnitt der Anpassungsdatei
Der Abschnitt " **Logs** " enthält einen Eintrag für die Protokolldatei, der den Namen einer Datei angibt, die Fehler während des Vorgangs des **DataFactory**aufzeichnet.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
 Ein Protokolldatei Eintrag hat folgendes Format:  
  
```console
  
err=  
FileName  
  
```  
  
## <a name="remarks"></a>Bemerkungen  
  
|Teil|BESCHREIBUNG|  
|----------|-----------------|  
|**irre**|Eine Literalzeichenfolge, die angibt, dass dies ein Protokolldatei Eintrag ist.|  
|*FileName*|Ein kompletter Pfad und Dateiname. Der typische Dateiname lautet **c:\msdfmap.log**.|  
  
 Die Protokolldatei enthält den Benutzernamen, das HRESULT, das Datum und die Uhrzeit der einzelnen Fehler.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereich für die Anpassungs Dateiverbindung](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [SQL-Abschnitt der Anpassungs Datei](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Benutzer Listen Abschnitt "Anpassungs Datei"](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [DataFactory-Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Erforderliche Client Einstellungen](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Grundlegendes zur Anpassungs Datei](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Schreiben Ihres eigenen benutzerdefinierten Handlers](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


