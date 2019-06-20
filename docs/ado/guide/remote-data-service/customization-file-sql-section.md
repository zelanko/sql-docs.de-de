---
title: SQL-Abschnitt der Anpassungsdatei | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ba0d8c7ab1294400c19456abf164c6ad6be0dd2e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704307"
---
# <a name="customization-file-sql-section"></a>SQL-Abschnitt der Anpassungsdatei
Die **Sql** Abschnitt kann eine neue SQL-Zeichenfolge, die die Clientbefehlszeichenfolge ersetzt enthalten. Wenn keine SQL-Zeichenfolge in den Abschnitt vorhanden ist, wird der Abschnitt ignoriert.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Die neue SQL-Zeichenfolge möglicherweise *parametrisierte*. Das heißt, Parameter in der **Sql** Abschnitt der SQL-Zeichenfolge (vom angegebenen der "?" Zeichen) kann durch den entsprechenden Argumenten in ersetzt werden ein *Bezeichner* in der Clientbefehlszeichenfolge (vom angegebenen eine durch Trennzeichen getrennte Liste in Klammern angegeben). Verhalten sich wie ein Funktionsaufruf, der Bezeichner und einer Argumentliste aus.  
  
 Nehmen wir beispielsweise an, die Client-Befehlszeichenfolge ist `"CustomerByID(4)"`, ist der Überschrift des Abschnitts SQL `[SQL CustomerByID]`, und die neue SQL-Zeichenfolge im Abschnitt `"SELECT * FROM Customers WHERE CustomerID = ?".` der Ereignishandler generiert `"SELECT * FROM Customers WHERE CustomerID = 4"` und verwenden Sie diese Zeichenfolge zum Abfragen der Datenquelle.  
  
 Wenn die neue SQL-Anweisung, die null-Zeichenfolge ist (""), und klicken Sie dann im Abschnitt ignoriert wird.  
  
 Wenn die neue Zeichenfolge der SQL-Anweisung nicht gültig ist, misslingt die Ausführung der Anweisung. Die Clientparameter wird ignoriert. Sie erreichen dies absichtlich, um "alle Client-SQL-Befehle durch Angabe deaktivieren":  
  
```console
[SQL default]   
SQL = " "  
```  
  
## <a name="syntax"></a>Syntax  
 Ein Ersatz-SQL-Zeichenfolge-Eintrag hat folgendes Format:  
  
 **SQL=**    
 ***sqlString***  
  
|Teil|Beschreibung|  
|----------|-----------------|  
|**SQL**|Eine Literalzeichenfolge, die Hiermit ist ein SQL-Abschnitt-Eintrag.|  
|***sqlString***|Eine SQL-Zeichenfolge, die die Clientzeichenfolge ersetzt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Connect-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Logs-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [UserList-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [DataFactory-Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Erforderliche Clienteinstellungen](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Grundlegendes zu der Anpassungsdatei](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Schreiben Ihres eigenen benutzerdefinierten Handlers](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


