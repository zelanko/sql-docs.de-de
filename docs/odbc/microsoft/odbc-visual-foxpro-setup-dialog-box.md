---
title: ODBC-Visual FoxPro-einrichten (Dialogfeld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], installing
- FoxPro ODBC driver [ODBC], installing
ms.assetid: de020197-7f53-4643-9cbf-b7887ba88de9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 37ec2a9f033c124ab70db996f11179797877c09b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47686438"
---
# <a name="odbc-visual-foxpro-setup-dialog-box"></a>Einrichten von ODBC-Visual FoxPro (Dialogfeld)
Die **ODBC-Visual FoxPro-Setup** Dialogfeld können Sie zum Hinzufügen oder Ändern einer Visual FoxPro-Datenquelle.  
  
 Informationen zum Herunterladen des Treibers finden Sie unter [der Visual FoxPro-ODBC-Treiber-Download-Site](http://go.microsoft.com/fwlink/?LinkId=121318).  
  
## <a name="dialog-box-options"></a>Dialogfeld "Optionen"  
 **Datenquellenname**  
 Geben Sie den Namen, die, den Sie für die Datenquelle verwenden möchten.  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung für die Datenquelle an.  
  
 **Datenbanktyp**  
 Können Sie den Typ der Datenbank auswählen die Datenquelle für die Verbindung verwendet werden soll.  
  
 **Visual FoxPro-Datenbank (. EINER DATENBANK)**  
 Gibt an, dass die Datenquelle mit einer Visual FoxPro verbindet [Datenbank](../../odbc/microsoft/visual-foxpro-terminology.md) (DBC-Datei) und für alle Tabellen und lokalen Ansichten in der Datenbank.  
  
 **Freien Sie Verzeichnis der Tabelle**  
 Gibt an, dass die Datenquelle in einem Verzeichnis verbunden [kostenlose Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md). Alle [Datenbank](../../odbc/microsoft/visual-foxpro-terminology.md) werden Tabellen im gleichen Verzeichnis wie z. B. durch ODBC-Katalogfunktionen ignoriert [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) oder [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md). Datenbanktabellen können zugegriffen werden, indem Sie SQL SELECT-Anweisungen, die über gesendet [SQLExecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md) und [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
 **Pfad**  
 Zeigt den Pfad und Namen für die Datenbank oder das Verzeichnis der kostenlosen Tabellen, mit denen die Datenquelle verbunden wird.  
  
 **Durchsuchen**  
 Ermöglicht Ihnen die Suche Ihr System und das Netzwerk für die Datenbank oder das Verzeichnis, mit der Datenquelle hergestellt werden soll.  
  
 **Optionen**  
 Erweitert das Dialogfeld, sodass Sie Visual FoxPro-ODBC-Treiber festgelegt werden können.  
  
## <a name="driver"></a>Treiber  
 **Sortierreihenfolge**  
 Die Reihenfolge, in der Felder sortiert werden. Die Standard-Sequenzen wider, die Sequenzen, die von Ihrer Sprachversion des Betriebssystems unterstützt wird. Eine Liste der unterstützten sortierenden Sequenzen, finden Sie unter [festgelegt COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
 **Exclusive**  
 Wenn dieses Kontrollkästchen aktiviert ist, wird der Treiber die Visual FoxPro-Datenbank geöffnet, ausschließlich auf, wenn Sie Daten unter Verwendung der Datenquelle zugreifen. Andere Benutzer zugreifen nicht die Datenbank oder den Tabellen in der Datenbank, während die Datenbank exklusiv genutzt wird. Tabellen in der exklusiv geöffnete Datenbank werden als SHARED geöffnet. Um eine Tabelle ausschließlich zu öffnen, verwenden die [exklusiv festgelegt](../../odbc/microsoft/set-exclusive-command.md) Befehl. Ist dieses Kontrollkästchen deaktiviert, wenn **Datenbanktyp** nastaven NA hodnotu **freies**.  
  
 **NULL**  
 Bestimmt, ob Spalten mit ALTER TABLE und CREATE TABLE erstellt wurden null-Werte zulassen. Wenn Sie Null ON festlegen, fügt der INSERT-SQL einen null-Wert in jede Spalte, die nicht in einer INSERT-SQL enthalten... VALUE-Klausel. Wenn Null auf OFF festgelegt ist, wird ein Leerzeichen eingefügt. Außerdem können Sie steuern, diese Option aus, über eine übergebene Verbindungszeichenfolge wie im folgenden Code:  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;NULL=NO"  
```  
  
 **Gelöscht**  
 Bestimmt, ob als gelöscht markierte Zeilen zurückgegeben werden. Außerdem können Sie steuern, diese Option aus, über eine übergebene Verbindungszeichenfolge wie im folgenden Code:  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;  
DELETED=YES"  
```  
  
 **Abrufen der Daten im Hintergrund**  
 Bestimmt, ob Datensätze, im Hintergrund (progressive abrufen abgerufen werden) oder Ihre Anwendung wartet, bis alle Datensätze in das Resultset abgerufen werden.
