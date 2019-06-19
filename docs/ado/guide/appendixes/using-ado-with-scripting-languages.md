---
title: Verwenden von ADO mit Skriptsprachen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- scripting languages [ADO]
- ADO, scripting languages
ms.assetid: 76fc4d00-0c9f-422b-af5c-af6ed8fb29d8
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d41d5a0239f11882c135c27fd4af8e817e83b799
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702762"
---
# <a name="using-ado-with-scripting-languages"></a>Verwenden von ADO mit Skriptsprachen
Innerhalb einer skriptumgebung kann ADO Daten über die serverseitige Skripts verfügbar zu machen. In diesem Szenario ADO zugrunde liegenden OLE DB-Anbieter, die sie verwendet und alle anderen Komponenten erforderlich, um einen bestimmten Datenspeicher verweisen auf einem Server mit Internetinformationsdienste (Internet Information Services, IIS) installiert sind. ADO ist mit Active Server Pages (ASP) ist eine Komponente, die auf die verwiesen wird in einem Skript, die HTML-Code, z. B. generieren kann. Diese HTML-Inhalt kann über HTTP auf einen Webbrowser für den Client übergeben werden. Mithilfe von Skripts können die Webseite Aktionen senden, an die serverseitigen Skript, sodass Sie aktualisieren, durchlaufen oder bestimmte Daten anzeigen.  
  
 Bevor Sie ein ActiveX-Objekt auf einer Webseite verwenden, ist es wichtig zu wissen, ob das Objekt für die Skripterstellung sicher ist. Wenn ein Objekt als "sicher für Skripting" eingestuft wird, bedeutet dies, dass das Steuerelement keine schädliche Aktionen auf dem Computer des Benutzers durchführen und daher ausgeführt werden, kann ohne die Zustimmung des Benutzers angefordert. Die folgende Tabelle listet die ADO-Objekte und gibt an, ob sie für die Skripterstellung sicher sind.  
  
|Objekt|Für Scripting sicher sind?|  
|------------|-------------------------|  
|ADO-Verbindung|Ja|  
|ADO-Befehl|Nein|  
|ADO-Parameter|Nein|  
|ADO-Recordset|Ja|  
|ADO Record|Ja|  
|ADO-Stream|Ja|  
|ADO-Fehler|Nein|  
|ADOX-Katalog|Nein|  
|ADOX-CellSet|Nein|  
|RDS-DataControl|Ja|  
|RDS-Datenspeicher|Ja|  
|RDS Data Factory|Nein|  
  
 Die folgende Tabelle listet die mit Windows DAC/MDAC enthaltenen Anbieter, und gibt an, ob sie für die Skripterstellung sicher sind.  
  
|Anbieter|Für Scripting sicher sind?|  
|--------------|-------------------------|  
|Form|Ja|  
|Beibehalten|Ja|  
|Remote|Ja|  
|OLE DB-Anbieter für SQLServer (SQLOLEDB)|Nein|  
|OLE DB-Anbieter für ODBC (MSDASQL)|Nein|  
  
## <a name="odbc-data-sources"></a>ODBC-Datenquellen  
 Ein deutlicher Unterschied zwischen Skript und nicht zur skriptprogrammierung ADO-Code ist der ODBC-Datenquelle verwendet. Für Anwendungen nicht zur skriptprogrammierung können Sie in der ODBC-Datenquellen-Administrator einen Benutzer-DSN erstellen. Für Skripts, die unter IIS ausgeführt werden, müssen Sie einen System-DSN erstellen; Andernfalls werden die Skripts die Datenquelle, die Sie erstellt haben, nicht erkannt. Dies gilt für alle Skripts ADO-Anwendung mithilfe von Microsoft OLE DB-Anbieter für ODBC über Microsoft IIS.  
  
## <a name="referencing-the-ado-library"></a>Verweis auf die ADO-Bibliothek  
 Nicht zutreffend mit Skriptsprachen.  
  
## <a name="handling-events"></a>Behandeln von Ereignissen  
 Nicht zutreffend mit Skriptsprachen.  
  
 Die folgenden Themen enthalten spezifischere Informationen zum Verwenden von ADO mit Skriptsprachen an:  
  
-   [VBScript-ADO-Programmierung](../../../ado/guide/appendixes/vbscript-ado-programming.md)  
  
-   [JScript-ADO-Programmierung](../../../ado/guide/appendixes/jscript-ado-programming.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft ActiveX Data Objects (ADO)](../../../ado/microsoft-activex-data-objects-ado.md)   
 [Verwenden von ADO mit Microsoft Visual Basic](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-basic.md)   
 [Verwenden von ADO mit Microsoft Visual C++](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md)   
