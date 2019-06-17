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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62768024"
---
# <a name="choose-a-destination-sql-server-import-and-export-wizard"></a>Ziel auswählen (SQL Server-Import/Export-Assistent)
  Verwenden der **wählen Sie ein Ziel** Seite an das Ziel der Daten, die Sie kopieren möchten.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import / Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen zum Starten des Assistenten als auch die Berechtigungen erforderlich, um den Assistenten erfolgreich ausführen, finden Sie unter [führen Sie die SQL Server-Import / Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="static-options"></a>Statische Optionen  
 **Ziel**  
 Wählen Sie den Datenanbieter aus, dessen Datenspeicherformat mit dem des Zieles übereinstimmt. Möglicherweise sind für die Datenquelle mehrere Anbieter verfügbar. Z. B. mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, der .NET Framework-Datenanbieter für SQL Server oder Microsoft OLE DB-Anbieter für SQL Server.  
  
> [!NOTE]  
>  Wählen Sie zum Speichern von Daten in einem ODBC-Ziel den .NET Framework-Datenanbieter für ODBC aus.  
  
 Die **Datenquelle** Eigenschaft verfügt über eine Variable Anzahl von Optionen, mit denen sich je nach den auf dem Computer installierten Anbietern ändern. In den folgenden Tabellen sind die Optionen für einige häufig verwendete Ziele aufgeführt. Die Angaben zu anderen Anbietern finden Sie in den entsprechenden Dokumentationen zu den Anbietern.  
  
## <a name="dynamic-options"></a>Dynamische Optionen  
 In den folgenden Abschnitten sind die verfügbaren Optionen für mehrere Datenquellen aufgeführt. Nicht alle Ziele, die in der Dropdownliste der Ziele verfügbar sind, werden hier aufgeführt.  
  
### <a name="destination--sql-server-native-client-or-microsoft-ole-db-provider-for-sql-server"></a>Ziel = SQL Server Native Client oder Microsoft OLE DB-Anbieter für SQL Server  
 **Servername**  
 Geben Sie den Namen des Servers ein, der die Daten empfangen soll, oder wählen Sie einen Server aus der Liste aus.  
  
 **Windows-Authentifizierung verwenden**  
 Gibt an, ob das Paket die Microsoft Windows-Authentifizierung verwenden soll, um sich bei der Datenbank anzumelden. Im Sinne einer größeren Sicherheit wird die Windows-Authentifizierung empfohlen.  
  
 **SQL Server-Authentifizierung verwenden**  
 Gibt an, ob das Paket die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwenden soll, um sich bei der Datenbank anzumelden. Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwenden, müssen Sie einen Benutzernamen und ein Kennwort angeben.  
  
 **Benutzername**  
 Geben Sie einen Benutzernamen für die Datenbankverbindung an, wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwenden.  
  
 **Kennwort**  
 Geben Sie das Kennwort für die Datenbankverbindung ein, wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwenden.  
  
 **Datenbank**  
 Wählen Sie aus der Liste der Datenbanken für die angegebene Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], oder erstellen Sie eine neue Datenbank, indem Sie auf **neu**.  
  
 **Aktualisieren**  
 Klicken Sie auf **Aktualisieren**, um die Liste der verfügbaren Datenbanken zu aktualisieren.  
  
 **Neu**  
 Erstellen Sie eine neue Zieldatenbank mithilfe der **Create Database** Dialogfeld.  
  
### <a name="destination--flat-file-destination"></a>Ziel = Flatfileziel  
 **Dateiname**  
 Geben Sie den Pfad und den Dateinamen für die Datei an, in der die Daten gespeichert werden sollen. Klicken Sie alternativ auf **Durchsuchen**, um nach einer Datei zu suchen.  
  
 **Durchsuchen**  
 Suchen Sie nach einer Datei mithilfe des Dialogfelds **Öffnen**.  
  
 **Gebietsschema**  
 Geben Sie die Gebietsschema-ID (LCID) an, die die Sortierreihenfolge für Zeichen und das Datums- und Zeitformat definiert.  
  
 **Unicode**  
 Gibt an, ob Unicode verwendet werden soll. Wenn Sie Unicode verwenden, brauchen Sie keine Codepage anzugeben.  
  
 **Codepage**  
 Geben Sie die Codepage für die Sprache an, die Sie verwenden möchten.  
  
 **Format**  
 Gibt an, ob die Datei Formatierung mit Trennzeichen, fester Breite oder rechtem Flatterrand verwendet.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|Mit Trennzeichen|Als Trennzeichen für Spalten von einem Trennzeichen, angegeben auf der **Spalten** Seite.|  
|Feste Breite|Spalten haben eine feste Breite.|  
|Rechter Flatterrand|Bei Dateien mit rechtem Flatterrand weisen alle Spalten mit Ausnahme der letzten eine feste Breite auf. Die letzte Spalte wird durch das Zeilentrennzeichen begrenzt.|  
  
 **Textqualifizierer**  
 Geben Sie die zu verwendenden Textqualifizierer ein. Sie können z. B. angeben, dass jede Textspalte in Anführungszeichen eingeschlossen werden soll.  
  
 **Spaltennamen in der ersten Datenzeile**  
 Gibt an, ob die Spaltennamen in der ersten Datenzeile angezeigt werden.  
  
### <a name="destination--microsoft-excel"></a>Ziel = Microsoft Excel  
  
> [!NOTE]  
>  Wählen Sie **Microsoft Excel** nur dann, wenn die Verbindung mit einer Datenquelle, die Excel 2003 verwendet werden sollen oder früher. Um eine Verbindung mit einer Datenquelle herzustellen, die Excel 2007 verwendet, wählen Sie **Microsoft Office 12.0 Access Database Engine OLE DB Provider**, klicken Sie auf **Eigenschaften**, und klicken Sie dann auf die **alle** Registerkarte die **Datenlinkeigenschaften** im Dialogfeld für **erweiterte Eigenschaften**, geben Sie `Excel 12.0`.  
  
 **Excel-Dateipfad**  
 Geben Sie den Pfad und Namen für die Arbeitsmappe in der zum Speichern der Daten (z. B. C:\MyData.xls, \\\Sales\Database\Northwind.xls). Oder klicken Sie auf **Durchsuchen** um eine Arbeitsmappe zu suchen.  
  
 **Durchsuchen**  
 Suchen Sie nach einer Excel-Arbeitsmappe mithilfe der **öffnen** Dialogfeld.  
  
 **Excel-Version**  
 Wählen Sie die Version von Excel aus, die von der Zielarbeitsmappe verwendet wird.  
  
> [!NOTE]  
>  Wenn Sie Daten in ein [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]-Ziel exportieren, verwendet der Assistent die Excel-Zielkomponente von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Informationen zu einige Überlegungen zur Verwendung und bekannten Problemen finden Sie unter [Excel-Ziel](../data-flow/excel-destination.md).  
  
### <a name="destination--microsoft-access"></a>Ziel = Microsoft Access  
  
> [!NOTE]  
>  Wählen Sie **Microsoft Access** nur dann, wenn die Verbindung mit einer Datenbank, die Access 2003 verwendet werden sollen oder früher. Wählen Sie zum Herstellen einer datenbankverbindung, die Access 2007 verwendet, **Microsoft Office 12.0 Access Database Engine OLE DB Provider**.  
  
 **Dateiname**  
 Geben Sie den Pfad und Namen für die Datenbankdatei in der zum Speichern der Daten (z. B. C:\MyData.mdb, \\\Sales\Database\Northwind.mdb). Oder klicken Sie auf **Durchsuchen** um eine Datenbankdatei zu suchen.  
  
 **Durchsuchen**  
 Navigieren Sie zu der Datei mit den **öffnen** Dialogfeld.  
  
 **Benutzername**  
 Geben Sie einen gültigen Benutzernamen für die Datenbankverbindung an, wenn der Datenbank eine Informationsdatei für die Arbeitsgruppe zugeordnet ist.  
  
 **Kennwort**  
 Geben Sie das Kennwort des Benutzers für die Datenbankverbindung an, wenn der Datenbank eine Informationsdatei für die Arbeitsgruppe zugeordnet ist. Jedoch, wenn die Datenbank mit einem einzigen Kennwort für alle Benutzer geschützt ist, müssen Sie angeben dieses Werts in der **Datenlinkeigenschaften** Dialogfeld aus zugegriffen werden kann die **erweitert** Schaltfläche.  
  
 **Erweitert**  
 Mithilfe des Dialogfelds **Datenlinkeigenschaften** geben Sie erweiterte Optionen an, z.B. das Datenbankkennwort oder eine nicht standardmäßige Informationsdatei für Arbeitsgruppen. Weitere Informationen zu OLE DB-Anbieter-Eigenschaften, suchen Sie im Abschnitt "Datenzugriff" des der [MSDN-Bibliothek](https://go.microsoft.com/fwlink/?linkid=62553).  
  
  
