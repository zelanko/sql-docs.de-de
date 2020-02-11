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
ms.openlocfilehash: 6b322dacbf85ec24b58e315ecbbf9d547d1481f9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926482"
---
# <a name="using-ado-with-scripting-languages"></a>Verwenden von ADO mit Skriptsprachen
In einer Skript Umgebung können Sie mithilfe von ADO Daten mithilfe von serverseitiger Skripterstellung verfügbar machen. In diesem Szenario werden ADO, der zugrunde liegende OLE DB-Anbieter und alle anderen Komponenten, die für den Verweis auf einen bestimmten Datenspeicher erforderlich sind, auf einem Server installiert, auf dem Internetinformationsdienste (IIS) ausgeführt wird. Mithilfe von Active Server Pages (ASP) ist ADO eine Komponente, auf die in einem Skript verwiesen wird, das z. b. HTML generieren kann. Dieser HTML-Inhalt kann über HTTP an einen Client-Webbrowser übermittelt werden. Mithilfe der Skripterstellung kann die Webseite Aktionen an das serverseitige Skript zurücksenden, um bestimmte Daten zu aktualisieren, zu durchlaufen oder anzuzeigen.  
  
 Bevor Sie ein ActiveX-Objekt in einer Webseite verwenden, ist es wichtig zu wissen, ob das Objekt für die Skripterstellung sicher ist. Wenn ein Objekt als sicher für die Skripterstellung angesehen wird, bedeutet dies, dass das Steuerelement keine schädlichen Maßnahmen auf dem Computer des Benutzers durchführen kann und daher ausgeführt werden kann, ohne die Genehmigung des Benutzers anzufordern. In der folgenden Tabelle werden die ADO-Objekte aufgelistet und angegeben, ob Sie für die Skripterstellung sicher sind.  
  
|Object|Sicher für Skripterstellung?|  
|------------|-------------------------|  
|ADO-Verbindung|Ja|  
|ADO-Befehl|Nein|  
|ADO-Parameter|Nein|  
|ADO-Recordset|Ja|  
|ADO-Datensatz|Ja|  
|ADO-Stream|Ja|  
|ADO-Fehler|Nein|  
|ADOX-Katalog|Nein|  
|ADOX-CellSet|Nein|  
|RDS-DataControl|Ja|  
|RDS-DataSpace|Ja|  
|RDS-DataFactory|Nein|  
  
 In der folgenden Tabelle sind die in Windows DAC/MDAC enthaltenen Anbieter aufgelistet, und es wird angegeben, ob Sie für die Skripterstellung sicher sind.  
  
|Anbieter|Sicher für Skripterstellung?|  
|--------------|-------------------------|  
|Form|Ja|  
|Persist|Ja|  
|Remote|Ja|  
|OLE DB Anbieter für SQL Server (SQLOLEDB)|Nein|  
|OLE DB Anbieter für ODBC (MSDASQL)|Nein|  
  
## <a name="odbc-data-sources"></a>ODBC-Datenquellen  
 Ein wichtiger Unterschied zwischen der Skripterstellung und dem nicht-Skript-ADO-Code ist die ODBC-Datenquelle (sofern verwendet). Für nicht-Skript Anwendungen können Sie im ODBC-Datenquellen-Administrator einen Benutzer-DSN erstellen. Bei Skripts, die unter IIS ausgeführt werden, müssen Sie einen System-DSN erstellen. Andernfalls erkennen Ihre Skripts die von Ihnen erstellte Datenquelle nicht. Dies gilt für jede ADO-Skript Anwendung, die den Microsoft OLE DB-Anbieter für ODBC über Microsoft IIS verwendet.  
  
## <a name="referencing-the-ado-library"></a>Verweisen auf die ADO-Bibliothek  
 Gilt nicht für Skriptsprachen.  
  
## <a name="handling-events"></a>Behandeln von Ereignissen  
 Gilt nicht für Skriptsprachen.  
  
 Die folgenden Themen enthalten spezifischere Informationen zur Verwendung von ADO mit Skriptsprachen:  
  
-   [VBScript-ADO-Programmierung](../../../ado/guide/appendixes/vbscript-ado-programming.md)  
  
-   [JScript-ADO-Programmierung](../../../ado/guide/appendixes/jscript-ado-programming.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft ActiveX Data Objects (ADO)](../../../ado/microsoft-activex-data-objects-ado.md)   
 [Verwenden von ADO mit Microsoft Visual Basic](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-basic.md)   
 [Verwenden von ADO mit Microsoft Visual C++](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md)   
