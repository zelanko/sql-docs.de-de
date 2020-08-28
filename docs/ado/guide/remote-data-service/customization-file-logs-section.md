---
description: Logs-Abschnitt der Anpassungsdatei
title: Abschnitt "Anpassungs Datei Protokolle" | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- logs section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: a368e264-865c-41ee-be00-d9097255c2ea
author: rothja
ms.author: jroth
ms.openlocfilehash: 890ba32615cdd78d9b999958f3ce3cb1e0755b81
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88978241"
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
  
|Teil|Beschreibung|  
|----------|-----------------|  
|**irre**|Eine Literalzeichenfolge, die angibt, dass dies ein Protokolldatei Eintrag ist.|  
|*FileName*|Ein kompletter Pfad und Dateiname. Der typische Dateiname lautet **c:\msdfmap.log**.|  
  
 Die Protokolldatei enthält den Benutzernamen, das HRESULT, das Datum und die Uhrzeit der einzelnen Fehler.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereich für die Anpassungs Dateiverbindung](./customization-file-connect-section.md)   
 [SQL-Abschnitt der Anpassungs Datei](./customization-file-sql-section.md)   
 [Benutzer Listen Abschnitt "Anpassungs Datei"](./customization-file-userlist-section.md)   
 [DataFactory-Anpassung](./datafactory-customization.md)   
 [Erforderliche Client Einstellungen](./required-client-settings.md)   
 [Grundlegendes zur Anpassungs Datei](./understanding-the-customization-file.md)   
 [Schreiben Ihres eigenen benutzerdefinierten Handlers](./writing-your-own-customized-handler.md)