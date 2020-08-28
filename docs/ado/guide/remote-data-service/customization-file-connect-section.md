---
description: Connect-Abschnitt der Anpassungsdatei
title: Connect-Abschnitt der Anpassungs Datei | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connect section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: d50eb3cc-a822-486f-b80b-65bb50547ecd
author: rothja
ms.author: jroth
ms.openlocfilehash: 19dfe6f81293234d3615d0c3acaae83c50febc1d
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88978271"
---
# <a name="customization-file-connect-section"></a>Connect-Abschnitt der Anpassungsdatei
Das Standardverhalten des Handlers besteht darin, alle Verbindungen abzulehnen. Der Abschnitt " **Connect** " gibt Ausnahmen für dieses Verhalten an. Wenn z. b. alle **Connect** -Abschnitte nicht vorhanden oder leer waren, können standardmäßig keine Verbindungen hergestellt werden.  
  
 Der Abschnitt " **Connect** " kann Folgendes enthalten:  
  
-   Ein Standard Zugriffs Eintrag, der die für diese Verbindung zulässigen Standard Lese-und Schreibvorgänge angibt. Wenn im Abschnitt kein Standard Zugriffs Eintrag vorhanden ist, wird der Abschnitt ignoriert.  
  
-   Eine neue Verbindungs Zeichenfolge, die die Client Verbindungs Zeichenfolge ersetzt.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
 Ein Standard Zugriffs Eintrag hat folgendes Format:  
  
```console
  
Access=  
accessRight  
  
```  
  
 Der Eintrag der Verbindungs Zeichenfolge für die Ersetzung hat folgendes Format:  
  
```console
  
Connect=  
connectionString  
  
```  
  
## <a name="remarks"></a>Bemerkungen  
  
|Teil|Beschreibung|  
|----------|-----------------|  
|**Herstellen einer Verbindung**|Eine Literalzeichenfolge, die angibt, dass dies ein Verbindungs Zeichen folgen Eintrag ist|  
|**_connectionString_**|Eine Zeichenfolge, die die gesamte Client Verbindungs Zeichenfolge ersetzt.|  
|**zugreifen**|Eine Literalzeichenfolge, die angibt, dass dies ein Zugriffs Eintrag ist|  
|**_accessright_**|Eine der folgenden Zugriffsrechte:<br /><br /> -   **NoAccess** : der Benutzer kann nicht auf die Datenquelle zugreifen.<br />-   Schreib **geschützt: der** Benutzer kann die Datenquelle lesen.<br />-   " **Lesewrite** ": der Benutzer kann die Datenquelle lesen oder in diese schreiben.|  
  
 Wenn Sie eine beliebige Verbindung zulassen möchten (damit das Standardverhalten des Handlers deaktiviert wird), legen Sie den Zugriffs Eintrag im Abschnitt **Connect default** auf fest `Access=ReadWrite` , und löschen Sie alle anderen **Verbindungs** _identifier_ -ID-Abschnitte, oder kommentieren Sie Sie aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abschnitt "Anpassungs Datei Protokolle"](./customization-file-logs-section.md)   
 [SQL-Abschnitt der Anpassungs Datei](./customization-file-sql-section.md)   
 [Benutzer Listen Abschnitt "Anpassungs Datei"](./customization-file-userlist-section.md)   
 [DataFactory-Anpassung](./datafactory-customization.md)   
 [Erforderliche Client Einstellungen](./required-client-settings.md)   
 [Grundlegendes zur Anpassungs Datei](./understanding-the-customization-file.md)   
 [Schreiben Ihres eigenen benutzerdefinierten Handlers](./writing-your-own-customized-handler.md)