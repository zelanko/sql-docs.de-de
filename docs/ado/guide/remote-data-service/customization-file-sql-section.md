---
title: SQL-Abschnitt der Anpassungs Datei | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: e65c2871-9986-44ff-b8b7-7f5eda91b3fa
author: rothja
ms.author: jroth
ms.openlocfilehash: 934b982004bf27e28a8daeed09061101886ce444
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82749878"
---
# <a name="customization-file-sql-section"></a>SQL-Abschnitt der Anpassungsdatei
Der **SQL** -Abschnitt kann eine neue SQL-Zeichenfolge enthalten, die die Client Befehls Zeichenfolge ersetzt. Wenn im Abschnitt keine SQL-Zeichenfolge vorhanden ist, wird der Abschnitt ignoriert.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 Die neue SQL-Zeichenfolge kann *parametrisiert*werden. Das heißt, Parameter in der SQL-Zeichenfolge des **SQL** -Abschnitts (festgelegt durch das Zeichen '? ') können durch entsprechende Argumente in einem *Bezeichner* in der Client Befehls Zeichenfolge ersetzt werden (angegeben durch eine durch Trennzeichen getrennte Liste in Klammern). Der Bezeichner und die Argumentliste Verhalten sich wie ein Funktions Aufruf.  
  
 Angenommen, die Client Befehls Zeichenfolge ist `"CustomerByID(4)"` , der SQL-Abschnitts Header ist `[SQL CustomerByID]` , und die neue SQL-Abschnitts Zeichenfolge ist `"SELECT * FROM Customers WHERE CustomerID = ?".` der Handler, der `"SELECT * FROM Customers WHERE CustomerID = 4"` diese Zeichenfolge generiert und zum Abfragen der Datenquelle verwendet.  
  
 Wenn die neue SQL-Anweisung die NULL-Zeichenfolge ("") ist, wird der Abschnitt ignoriert.  
  
 Wenn die neue SQL-Anweisungs Zeichenfolge ungültig ist, tritt bei der Ausführung der Anweisung ein Fehler auf. Der Client Parameter wird effektiv ignoriert. Sie können dies absichtlich tun, um alle SQL-Client Befehle zu deaktivieren, indem Sie Folgendes angeben:  
  
```console
[SQL default]   
SQL = " "  
```  
  
## <a name="syntax"></a>Syntax  
 Ein Ersatz-SQL-Zeichen folgen Eintrag hat folgendes Format:  
  
 **SQL =**   
 ***SqlString***  
  
|Teil|BESCHREIBUNG|  
|----------|-----------------|  
|**SQL**|Eine literale Zeichenfolge, die angibt, dass dies ein SQL-Abschnitts Eintrag ist.|  
|***SqlString***|Eine SQL-Zeichenfolge, die die Client Zeichenfolge ersetzt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereich für die Anpassungs Dateiverbindung](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Abschnitt "Anpassungs Datei Protokolle"](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Benutzer Listen Abschnitt "Anpassungs Datei"](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [DataFactory-Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Erforderliche Client Einstellungen](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Grundlegendes zur Anpassungs Datei](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Schreiben Ihres eigenen benutzerdefinierten Handlers](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


