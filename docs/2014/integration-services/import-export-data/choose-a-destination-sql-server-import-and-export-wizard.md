---
title: Ziel auswählen (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.chooseadestination.f1
ms.assetid: 1898be15-3e69-42d3-8ecb-3733c9f6c8e3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 746aed7f49b0db51f46a32fdf040eb5b9e968dd2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62768024"
---
# <a name="choose-a-destination-sql-server-import-and-export-wizard"></a>Ziel auswählen (SQL Server-Import/Export-Assistent)
  Verwenden Sie die Seite **Ziel auswählen** , um das Ziel der Daten anzugeben, die Sie kopieren möchten.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import/Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen für das Starten des Assistenten sowie zu den Berechtigungen, die zum erfolgreichen Ausführen des Assistenten erforderlich sind, finden Sie unter [Ausführen des SQL Server-Import/Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="static-options"></a>Statische Optionen  
 **Ziel**  
 Wählen Sie den Datenanbieter aus, dessen Datenspeicherformat mit dem des Zieles übereinstimmt. Möglicherweise sind für die Datenquelle mehrere Anbieter verfügbar. Mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können Sie z. b. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, den .NET Framework Datenanbieter für SQL Server oder den Microsoft OLE DB-Anbieter für SQL Server verwenden.  
  
> [!NOTE]  
>  Wählen Sie zum Speichern von Daten in einem ODBC-Ziel den .NET Framework-Datenanbieter für ODBC aus.  
  
 Die **Datenquellen** Eigenschaft verfügt über eine Variable Anzahl von Optionen, die sich abhängig von den auf dem Computer installierten Anbietern ändern. In den folgenden Tabellen sind die Optionen für einige häufig verwendete Ziele aufgeführt. Die Angaben zu anderen Anbietern finden Sie in den entsprechenden Dokumentationen zu den Anbietern.  
  
## <a name="dynamic-options"></a>Dynamische Optionen  
 In den folgenden Abschnitten sind die verfügbaren Optionen für mehrere Datenquellen aufgeführt. Nicht alle Ziele, die in der Dropdownliste der Ziele verfügbar sind, werden hier aufgeführt.  
  
### <a name="destination--sql-server-native-client-or-microsoft-ole-db-provider-for-sql-server"></a>Ziel = SQL Server Native Client oder Microsoft OLE DB-Anbieter für SQL Server  
 **Servername**  
 Geben Sie den Namen des Servers ein, der die Daten empfangen soll, oder wählen Sie einen Server aus der Liste aus.  
  
 **Windows-Authentifizierung verwenden**  
 Gibt an, ob das Paket die Microsoft Windows-Authentifizierung verwenden soll, um sich bei der Datenbank anzumelden. Im Sinne einer größeren Sicherheit wird die Windows-Authentifizierung empfohlen.  
  
 **SQL Server Authentifizierung verwenden**  
 Gibt an, ob das Paket die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwenden soll, um sich bei der Datenbank anzumelden. Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwenden, müssen Sie einen Benutzernamen und ein Kennwort angeben.  
  
 **Benutzername**  
 Geben Sie einen Benutzernamen für die Datenbankverbindung an, wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwenden.  
  
 **Kennwort**  
 Geben Sie das Kennwort für die Datenbankverbindung ein, wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwenden.  
  
 **Datenbank**  
 Wählen Sie aus der Liste der Datenbanken auf der angegebenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Instanz von aus, oder erstellen Sie eine neue Datenbank, indem Sie auf **neu**klicken.  
  
 **Aktualisieren**  
 Klicken Sie auf **Aktualisieren**, um die Liste der verfügbaren Datenbanken zu aktualisieren.  
  
 **Neu**  
 Erstellen Sie eine neue Zieldatenbank mithilfe des Dialog Felds **Datenbank erstellen** .  
  
### <a name="destination--flat-file-destination"></a>Ziel = Flatfileziel  
 **Dateiname**  
 Geben Sie den Pfad und den Dateinamen für die Datei an, in der die Daten gespeichert werden sollen. Klicken Sie alternativ auf **Durchsuchen**, um nach einer Datei zu suchen.  
  
 **Durchsuchen**  
 Suchen Sie nach einer Datei mithilfe des Dialogfelds **Öffnen**.  
  
 **Gebietsschema**  
 Geben Sie die Gebietsschema-ID (LCID) an, die die Sortierreihenfolge für Zeichen und das Datums- und Zeitformat definiert.  
  
 **Unicode-**  
 Gibt an, ob Unicode verwendet werden soll. Wenn Sie Unicode verwenden, brauchen Sie keine Codepage anzugeben.  
  
 **Codepage**  
 Geben Sie die Codepage für die Sprache an, die Sie verwenden möchten.  
  
 **Ges**  
 Gibt an, ob die Datei Formatierung mit Trennzeichen, fester Breite oder rechtem Flatterrand verwendet.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|Durch Trennzeichen getrennt|Spalten werden durch ein Trennzeichen getrennt, das auf der Seite **Spalten** angegeben wird.|  
|Feste Breite|Spalten haben eine feste Breite.|  
|Rechter Flatterrand|Bei Dateien mit rechtem Flatterrand weisen alle Spalten mit Ausnahme der letzten eine feste Breite auf. Die letzte Spalte wird durch das Zeilentrennzeichen begrenzt.|  
  
 **Textqualifizierer**  
 Geben Sie die zu verwendenden Textqualifizierer ein. Sie können z. B. angeben, dass jede Textspalte in Anführungszeichen eingeschlossen werden soll.  
  
 **Spaltennamen in der ersten Daten Zeile**  
 Gibt an, ob die Spaltennamen in der ersten Datenzeile angezeigt werden.  
  
### <a name="destination--microsoft-excel"></a>Ziel = Microsoft Excel  
  
> [!NOTE]  
>  Wählen Sie **Microsoft Excel** nur aus, wenn Sie eine Verbindung mit einer Datenquelle herstellen möchten, für die Excel 2003 oder früher verwendet wird. Zum Herstellen einer Verbindung mit einer Datenquelle, die Excel 2007 verwendet, wählen Sie **Microsoft Office 12,0 Access Datenbank-Engine OLE DB Provider**aus, klicken Sie auf **Eigenschaften**, und geben `Excel 12.0`Sie dann im Dialogfeld Daten Verknüpfungs **Eigenschaften** auf der Registerkarte **alle** für **Erweiterte Eigenschaften**ein.  
  
 **Excel-Dateipfad**  
 Geben Sie den Pfad und den Dateinamen für die Arbeitsmappe an, in der die Daten gespeichert werden sollen (z. b. c:\mydata.xls, \\\sales\database\northwind.xls). Oder klicken Sie auf **Durchsuchen** , um eine Arbeitsmappe zu suchen.  
  
 **Durchsuchen**  
 Suchen Sie mithilfe des Dialog Felds **Öffnen** eine Excel-Arbeitsmappe.  
  
 **Excel-Version**  
 Wählen Sie die Version von Excel aus, die von der Zielarbeitsmappe verwendet wird.  
  
> [!NOTE]  
>  Wenn Sie Daten in ein [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]-Ziel exportieren, verwendet der Assistent die Excel-Zielkomponente von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Weitere Informationen zu Überlegungen zur Verwendung und zu bekannten Problemen finden Sie unter [Excel Destination](../data-flow/excel-destination.md).  
  
### <a name="destination--microsoft-access"></a>Ziel = Microsoft Access  
  
> [!NOTE]  
>  Wählen Sie **Microsoft Access** nur aus, wenn Sie eine Verbindung mit einer Datenbank herstellen möchten, die Access 2003 oder früher verwendet. Zum Herstellen einer Verbindung mit einer Datenbank, die Access 2007 verwendet, wählen Sie **Microsoft Office 12,0 Access Datenbank-Engine OLE DB Provider**aus.  
  
 **Dateiname**  
 Geben Sie den Pfad und den Dateinamen für die Datenbankdatei an, in der die Daten gespeichert werden sollen (z. b. c:\mydata.mdb, \\\sales\database\northwind.mdb). Oder klicken Sie auf **Durchsuchen** , um eine Datenbankdatei zu suchen.  
  
 **Durchsuchen**  
 Navigieren Sie im Dialogfeld **Öffnen** zu der Datenbankdatei.  
  
 **Benutzername**  
 Geben Sie einen gültigen Benutzernamen für die Datenbankverbindung an, wenn der Datenbank eine Informationsdatei für die Arbeitsgruppe zugeordnet ist.  
  
 **Kennwort**  
 Geben Sie das Kennwort des Benutzers für die Datenbankverbindung an, wenn der Datenbank eine Informationsdatei für die Arbeitsgruppe zugeordnet ist. Wenn die Datenbank jedoch mit einem einzigen Kennwort für alle Benutzer geschützt ist, müssen Sie diesen Wert im Dialogfeld **Daten** Verknüpfungs Eigenschaften angeben, auf das über die Schaltfläche **erweitert** zugegriffen wird.  
  
 **Erweitert**  
 Mithilfe des Dialogfelds **Datenlinkeigenschaften** geben Sie erweiterte Optionen an, z.B. das Datenbankkennwort oder eine nicht standardmäßige Informationsdatei für Arbeitsgruppen. Weitere Informationen zu OLE DB Anbieter Eigenschaften finden Sie im Abschnitt Datenzugriff der [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553).  
  
  
