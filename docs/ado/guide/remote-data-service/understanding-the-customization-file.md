---
description: Grundlegendes zur Anpassungsdatei
title: Grundlegendes zur Anpassungs Datei | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- customization file in RDS [ADO]
ms.assetid: 136f74bf-8d86-4a41-be66-c86cbcf81548
author: rothja
ms.author: jroth
ms.openlocfilehash: 9b097d54015d9f48140aafb6feb360b8013edeaf
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88977391"
---
# <a name="understanding-the-customization-file"></a>Grundlegendes zur Anpassungsdatei
Jeder Abschnitts Header in der Anpassungs Datei besteht aus eckigen Klammern (**[]**), die einen Typ und einen Parameter enthalten. Die vier Abschnitts Typen werden durch die Literalzeichenfolgen **Connect**, **SQL**, **userlist**oder **Logs**angegeben. Der-Parameter ist die Literalzeichenfolge, der Standardwert, ein vom Benutzer angegebener Bezeichner oder Nothing.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 Daher wird jeder Abschnitt mit einem der folgenden Abschnitts Header gekennzeichnet:  
  
```console
  
[ connect default ] [ connect    
identifier   
] [ sql  default ] [ sql    
identifier   
] [ userlist    
identifier   
] [ logs ]  
  
```  
  
 Die Abschnitts Header haben die folgenden Teile.  
  
|Teil|Beschreibung|  
|----------|-----------------|  
|**connect**|Eine Literalzeichenfolge, die eine Verbindungs Zeichenfolge ändert.|  
|**SQL**|Eine Literalzeichenfolge, die eine Befehls Zeichenfolge ändert.|  
|**UserList**|Eine Literalzeichenfolge, die die Zugriffsrechte eines bestimmten Benutzers ändert.|  
|**logs**|Eine Literalzeichenfolge, die eine Protokolldatei zum Aufzeichnen von Betriebsfehlern angibt.|  
|**default**|Eine Literalzeichenfolge, die verwendet wird, wenn kein Bezeichner angegeben oder gefunden wird.|  
|*identifier*|Eine Zeichenfolge, die einer Zeichenfolge in der **Connect** -oder **Befehls** Zeichenfolge entspricht.<br /><br /> -Verwenden Sie diesen Abschnitt, wenn der Abschnitts Header **Connect** enthält und die Bezeichnerzeichenfolge in der Verbindungs Zeichenfolge gefunden wird.<br />-Verwenden Sie diesen Abschnitt, wenn der Abschnitts Header **SQL** enthält und die Bezeichnerzeichenfolge in der Befehls Zeichenfolge gefunden wird.<br />-Verwenden Sie diesen Abschnitt, wenn der Abschnitts Header **userlist** enthält und die Bezeichnerzeichenfolge mit einem **Verbindungs** Abschnitts Bezeichner übereinstimmt.|  
  
 Das **DataFactory** Ruft den-Handler auf und übergibt Client Parameter. Der Handler sucht in den Client Parametern nach ganzen Zeichen folgen, die mit bezeichtern in den entsprechenden Abschnitts Headern zu vergleichen sind. Wenn eine Entsprechung gefunden wird, wird der Inhalt dieses Abschnitts auf den Client Parameter angewendet.  
  
 Ein bestimmter Abschnitt wird unter den folgenden Umständen verwendet:  
  
-   Ein **Connect** -Abschnitt wird verwendet, wenn der Wert Teil des Client Verbindungs Zeichenfolgen-Schlüssel Worts "**Data Source =**_value_" mit dem Bezeichner des **Verbindungs** Abschnitts übereinstimmt. 
  
-   Ein **SQL** -Abschnitt wird verwendet, wenn die Client Befehls Zeichenfolge eine Zeichenfolge enthält, die einem **SQL** -Abschnitts Bezeichner entspricht.  
  
-   Wenn kein entsprechender Bezeichner vorhanden ist, wird ein **Connect** -oder **SQL** -Abschnitt mit einem Standardparameter verwendet.  
  
-   Ein **userlist** -Abschnitt wird verwendet, wenn der **userlist** -Abschnitts Bezeichner mit einem **Verbindungs** Abschnitts Bezeichner übereinstimmt. Wenn eine Entsprechung vorliegt, wird der Inhalt des Abschnitts " **userlist** " auf die Verbindung angewendet, die durch den Abschnitt " **Connect** " gesteuert wird.  
  
-   Wenn die Zeichenfolge in einer Verbindung oder Befehls Zeichenfolge nicht mit dem Bezeichner in einem **Connect** -oder **SQL** -Abschnitts Header identisch ist und kein **Connect** -oder **SQL** -Abschnitts Header mit einem Default-Parameter vorhanden ist, wird die Client Zeichenfolge unverändert verwendet.  
  
-   Der Abschnitt **Logs** wird immer dann verwendet, wenn das **DataFactory** in Betrieb ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereich für die Anpassungs Dateiverbindung](./customization-file-connect-section.md)   
 [Abschnitt "Anpassungs Datei Protokolle"](./customization-file-logs-section.md)   
 [SQL-Abschnitt der Anpassungs Datei](./customization-file-sql-section.md)   
 [Benutzer Listen Abschnitt "Anpassungs Datei"](./customization-file-userlist-section.md)   
 [DataFactory-Anpassung](./datafactory-customization.md)   
 [Erforderliche Client Einstellungen](./required-client-settings.md)   
 [Schreiben Ihres eigenen benutzerdefinierten Handlers](./writing-your-own-customized-handler.md)