---
title: Grundlegendes zu der Anpassungsdatei | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- customization file in RDS [ADO]
ms.assetid: 136f74bf-8d86-4a41-be66-c86cbcf81548
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d58edcfae92c94cfc635d3539f81faf834e382c7
ms.sourcegitcommit: d9c5b9ab3c282775ed61712892eeb3e150ccc808
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2019
ms.locfileid: "67597569"
---
# <a name="understanding-the-customization-file"></a>Grundlegendes zur Anpassungsdatei
Jeder Überschrift des Abschnitts in der Anpassungsdatei besteht aus eckige Klammern ( **[]** ), die einen Typ und die Parameter enthält. Die vier Abschnitt sind gekennzeichnet durch die Literalzeichenfolgen **verbinden**, **Sql**, **Userlist**, oder **Protokolle**. Der Parameter ist der literalen Zeichenfolge, die Standardeinstellung, eine vom Benutzer angegebenen Bezeichner oder "nothing".  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Aus diesem Grund wird jedem Abschnitt mit einem der folgenden Abschnittsheader gekennzeichnet:  
  
```console
  
[ connect default ] [ connect    
identifier   
] [ sql  default ] [ sql    
identifier   
] [ userlist    
identifier   
] [ logs ]  
  
```  
  
 Die Abschnittsheader haben die folgenden Teile.  
  
|Teil|Description|  
|----------|-----------------|  
|**connect**|Eine Literalzeichenfolge, die eine Verbindungszeichenfolge zu ändern.|  
|**sql**|Eine Literalzeichenfolge, die eine Befehlszeichenfolge ändert.|  
|**userlist**|Eine Literalzeichenfolge, die die Zugriffsrechte für einen bestimmten Benutzer ändert.|  
|**logs**|Ein Zeichenfolgenliteral, das eine Aufzeichnung ablauffehler Protokolldatei angibt.|  
|**default**|Eine Literalzeichenfolge, die verwendet wird, wenn kein Bezeichner angegeben wird oder wurde gefunden.|  
|*identifier*|Eine Zeichenfolge, die eine Zeichenfolge in entspricht der **verbinden** oder **Befehl** Zeichenfolge.<br /><br /> -Verwenden Sie diesen Abschnitt aus, wenn der Überschrift des Abschnitts enthält **verbinden** und die ID-Zeichenfolge in der Verbindungszeichenfolge gefunden wird.<br />-Verwenden Sie diesen Abschnitt aus, wenn der Überschrift des Abschnitts enthält **Sql** und die ID-Zeichenfolge in der Befehlszeichenfolge gefunden wird.<br />-Verwenden Sie diesen Abschnitt aus, wenn der Überschrift des Abschnitts enthält **Userlist** und die ID-Zeichenfolge entspricht einer **verbinden** Abschnitt Bezeichner.|  
  
 Die **DataFactory** ruft der Handler auf, und die Client-Parameter übergeben. Der Handler sucht nach ganzen Zeichenfolgen in die Clientparameter, die Bezeichner in den entsprechenden Abschnittsheadern entsprechen. Wenn eine Übereinstimmung gefunden wird, werden die Inhalte des Abschnitts an den Clientparameter angewendet.  
  
 Ein bestimmter Abschnitt wird in den folgenden Situationen verwendet:  
  
-   Ein **verbinden** Abschnitt wird verwendet, wenn der Wertteil des Clients verbunden sind, Schlüsselwort "**Datenquelle =** _Wert_", entspricht einer **verbinden** Abschnitt-Bezeichner. 
  
-   Ein **Sql** Abschnitt wird verwendet, wenn die Client-Befehlszeichenfolge eine Zeichenfolge enthält, die entspricht einer **Sql** Abschnitt Bezeichner.  
  
-   Ein **verbinden** oder **Sql** Abschnitt mit einem Standardparameter wird verwendet, wenn kein übereinstimmender Bezeichner vorhanden ist.  
  
-   Ein **Userlist** Abschnitt wird verwendet, wenn die **Userlist** Bezeichner entspricht Abschnitt eine **verbinden** Abschnitt Bezeichner. Wenn eine Übereinstimmung, den Inhalt des vorliegt der **Userlist** -Abschnitt angewendet werden, für die Verbindung, unterliegt die **verbinden** Abschnitt.  
  
-   Wenn die Zeichenfolge in eine Verbindung oder eines Befehl Zeichenfolge nicht den Bezeichner in einem übereinstimmt **verbinden** oder **Sql** Abschnitt Header, und es gibt keine **verbinden** oder **Sql**  Abschnitt Header mit einem Standardparameter, die Clientzeichenfolge ohne Änderungen verwendet wird.  
  
-   Die **Protokolle** Abschnitt wird verwendet, wenn die **DataFactory** durchgeführt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Connect-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Logs-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [SQL-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [UserList-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [DataFactory-Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Erforderliche Clienteinstellungen](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Schreiben Ihres eigenen benutzerdefinierten Handlers](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)

