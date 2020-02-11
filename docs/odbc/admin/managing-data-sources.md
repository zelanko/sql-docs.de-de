---
title: Verwalten von Datenquellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- deleting data sources [ODBC], ODBC data source administrator
- data sources [ODBC], ODBC data source administrator
- adding data sources [ODBC], ODBC data source administrator
- removing data sources [ODBC], ODBC data source administrator
- ODBC data source administrator [ODBC], data source management
ms.assetid: 67cc4945-4850-4eb4-8da6-b835ddaeca4c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9dc741321894ae69a9ffb59738576a01d47628f5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67901657"
---
# <a name="managing-data-sources"></a>Verwalten von Datenquellen
Nachdem Sie einen ODBC-Treiber aus dem Setup Programm des Treibers installiert haben, können Sie eine oder mehrere Datenquellen dafür definieren. Der Datenquellen Name (Data Source Name, DSN) sollte eine eindeutige Beschreibung der Daten bereitstellen. z. b. *Abrechnung* oder Konten, die *bezahlt*werden. Die Benutzer-und Systemdaten Quellen, die für alle zurzeit installierten Treiber definiert sind, werden auf den Registerkarten **Benutzer-DSN** oder **System-DSN** des Dialog Felds **ODBC-Datenquellen-Administrator** aufgeführt. Die Datei Datenquellen in einem bestimmten Verzeichnis sind auf der Registerkarte **Datei-DSN** aufgeführt. das Verzeichnis, das angezeigt werden soll, wird in das Feld **Suchen in** auf der Registerkarte **Datei-DSN** eingegeben.  
  
> [!NOTE]  
>  Verwenden Sie c:\windows\syswow64\odbcad32.exe, um eine Datenquelle zu verwalten, die eine Verbindung mit einem 32-Bit-Treiber unter der 64-Bit-Plattform herstellt. Verwenden Sie c:\windows\system32\odbcad32.exe, um eine Datenquelle zu verwalten, die eine Verbindung mit einem 64-Bit-Treiber herstellt. In den **Verwaltungs Tools** auf einem 64-Bit-Windows 8-Betriebssystem gibt es Symbole für das Dialogfeld " **ODBC-Datenquellen-Administrator** " für 32-Bit und 64-Bit.  
  
 Wenn Sie das 64-Bit odbcad32. exe zum Konfigurieren oder Entfernen eines DSN verwenden, der eine Verbindung mit einem 32-Bit-Treiber herstellt, z.b. **Driver do Microsoft\*Access (MDB)**, wird die folgende Fehlermeldung angezeigt:  
  
```  
The specified DSN contains an architecture mismatch between the Driver and Application  
```  
  
 Um diesen Fehler zu beheben, verwenden Sie 32-Bit odbcad32. exe, um den DSN zu konfigurieren oder zu entfernen.  
  
 Eine Datenquelle verknüpft einen bestimmten ODBC-Treiber mit den Daten, auf die Sie über diesen Treiber zugreifen möchten. Beispielsweise können Sie eine Datenquelle erstellen, um den ODBC-dBase-Treiber für den Zugriff auf eine oder mehrere dBASE-Dateien zu verwenden, die sich in einem bestimmten Verzeichnis auf der Festplatte oder auf einem Netzwerklaufwerk befinden. Mit dem ODBC-Datenquellen-Administrator können Sie Datenquellen hinzufügen, ändern und löschen, wie in der folgenden Tabelle beschrieben.  
  
|Action|BESCHREIBUNG|  
|------------|-----------------|  
|Hinzufügen von Datenquellen|Es ist möglich, mehrere Datenquellen hinzuzufügen, von denen jeder einen Treiber mit einigen Daten verknüpft, auf die Sie mithilfe dieses Treibers zugreifen möchten. Weisen Sie jeder Datenquelle einen Namen zu, der diese Datenquelle eindeutig identifiziert. Wenn Sie z. b. eine Datenquelle für eine Gruppe von dBASE-Dateien erstellen, die Kundeninformationen enthalten, können Sie der Datenquelle den Namen "Customers" geben. Anwendungen zeigen in der Regel Datenquellen Namen an, aus denen Benutzer auswählen können.<br /><br /> Das Hinzufügen einer Datei Datenquelle unterscheidet sich geringfügig vom Hinzufügen von Benutzer-oder Systemdaten Quellen. Weitere Informationen finden Sie in der Hilfedatei für den ODBC-Datenquellen-Administrator.|  
|Ändern von Datenquellen|Abhängig von Ihren Anforderungen ist es möglicherweise erforderlich, Datenquellen neu zu konfigurieren. Sie können die Optionen zurücksetzen, indem Sie im Dialogfeld für die Treiber Einrichtung auf **Konfigurieren** klicken.|  
|Löschen von Datenquellen|Klicken Sie nach dem Auswählen einer Datenquelle auf **Entfernen** .|  
  
 Weitere Informationen zu Datei Datenquellen finden Sie unter [Herstellen einer Verbindung mithilfe von Datei Datenquellen](../../odbc/reference/develop-app/connecting-using-file-data-sources.md) oder der [SQLDriverConnect-Funktion](../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-Datenquellen-Administrator](../../odbc/admin/odbc-data-source-administrator.md)
