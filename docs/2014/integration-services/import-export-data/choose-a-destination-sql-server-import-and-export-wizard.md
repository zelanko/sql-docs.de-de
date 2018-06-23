---
title: Ziel auswählen (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.impexpwizard.chooseadestination.f1
ms.assetid: 1898be15-3e69-42d3-8ecb-3733c9f6c8e3
caps.latest.revision: 54
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6f0bfcc4ed838cccd0088cbf0011f6e630ee1fc5
ms.sourcegitcommit: d463f543e8db4a768f8e9736ff28fedb3fb17b9f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2018
ms.locfileid: "36324624"
---
# <a name="choose-a-destination-sql-server-import-and-export-wizard"></a>Ziel auswählen (SQL Server-Import/Export-Assistent)
  Verwenden der **wählen Sie ein Ziel** Seite, um das Ziel der Daten anzugeben, die Sie kopieren möchten.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import / Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen zum Starten des Assistenten als auch die Berechtigungen erforderlich, um den Assistenten erfolgreich ausführen finden Sie unter [führen Sie die SQL Server-Import / Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Der Zweck der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import / Export-Assistenten zum Kopieren von Daten aus einer Quelle in ein Ziel ist. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="static-options"></a>Statische Optionen  
 **Ziel**  
 Wählen Sie den Datenanbieter aus, dessen Datenspeicherformat mit dem des Zieles übereinstimmt. Möglicherweise sind für die Datenquelle mehrere Anbieter verfügbar. Z. B. mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, der .NET Framework-Datenanbieter für SQL Server oder Microsoft OLE DB-Anbieter für SQL Server.  
  
> [!NOTE]  
>  Wählen Sie zum Speichern von Daten in einem ODBC-Ziel den .NET Framework-Datenanbieter für ODBC aus.  
  
 Die **Datenquelle** Eigenschaft verfügt über eine Variable Anzahl von Optionen, die abhängig von den auf dem Computer installierten Anbietern ändern. In den folgenden Tabellen sind die Optionen für einige häufig verwendete Ziele aufgeführt. Die Angaben zu anderen Anbietern finden Sie in den entsprechenden Dokumentationen zu den Anbietern.  
  
## <a name="dynamic-options"></a>Dynamische Optionen  
 In den folgenden Abschnitten sind die verfügbaren Optionen für mehrere Datenquellen aufgeführt. Nicht alle Ziele, die in der Dropdownliste der Ziele verfügbar sind, werden hier aufgeführt.  
  
### <a name="destination--sql-server-native-client-or-microsoft-ole-db-provider-for-sql-server"></a>Ziel = SQL Server Native Client oder Microsoft OLE DB-Anbieter für SQL Server  
 **Servername**  
 Geben Sie den Namen des Servers ein, der die Daten empfangen soll, oder wählen Sie einen Server aus der Liste aus.  
  
 **Windows-Authentifizierung verwenden**  
 Gibt an, ob das Paket die Microsoft Windows-Authentifizierung verwenden soll, um sich bei der Datenbank anzumelden. Im Sinne einer größeren Sicherheit wird die Windows-Authentifizierung empfohlen.  
  
 **SQL Server-Authentifizierung verwenden**  
 Gibt an, ob das Paket verwenden soll [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung für die Anmeldung an der Datenbank. Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwenden, müssen Sie einen Benutzernamen und ein Kennwort angeben.  
  
 **Benutzername**  
 Geben Sie einen Benutzernamen für die Verbindung mit der Datenbank, bei der Verwendung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.  
  
 **Kennwort**  
 Geben Sie das Kennwort für die Datenbankverbindung ein, wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwenden.  
  
 **Datenbank**  
 Wählen Sie aus der Liste der Datenbanken für die angegebene Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], oder erstellen Sie eine neue Datenbank, indem Sie auf **neu**.  
  
 **Aktualisieren**  
 Klicken Sie auf **Aktualisieren**, um die Liste der verfügbaren Datenbanken zu aktualisieren.  
  
 **Neu**  
 Erstellen Sie eine neue Zieldatenbank mithilfe der **Create Database** (Dialogfeld).  
  
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
  
|value|Description|  
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
>  Wählen Sie **Microsoft Excel** nur, wenn eine Verbindung mit einer Datenquelle herstellen, die Excel 2003 verwendet werden sollen oder früher. Um eine Verbindung mit einer Datenquelle herzustellen, die Excel 2007 verwendet, wählen Sie **Microsoft Office 12.0 Access Database Engine OLE DB Provider**, klicken Sie auf **Eigenschaften**, und klicken Sie dann auf die **alle** auf der Registerkarte die **Datenlinkeigenschaften** im Dialogfeld für **erweiterte Eigenschaften**, geben Sie `Excel 12.0`.  
  
 **Excel-Dateipfad**  
 Geben Sie den Pfad und Namen für die Arbeitsmappe in der zum Speichern der Daten (z. B. C:\MyData.xls, \\\Sales\Database\Northwind.xls). Oder klicken Sie auf **Durchsuchen** um eine Arbeitsmappe zu suchen.  
  
 **Durchsuchen**  
 Suchen Sie nach einer Excel-Arbeitsmappe mithilfe der **öffnen** (Dialogfeld).  
  
 **Excel-Version**  
 Wählen Sie die Version von Excel aus, die von der Zielarbeitsmappe verwendet wird.  
  
> [!NOTE]  
>  Beim Exportieren von Daten in einem [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] Ziel, die der Assistent verwendet die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel-Zielkomponente. Informationen über einige Überlegungen zur Verwendung und bekannte Probleme finden Sie unter [Excel-Ziel](../data-flow/excel-destination.md).  
  
### <a name="destination--microsoft-access"></a>Ziel = Microsoft Access  
  
> [!NOTE]  
>  Wählen Sie **Microsoft Access** nur, wenn eine Datenbank herstellen, für die Access 2003 verwendet werden sollen oder früher. Wählen Sie zum Herstellen einer Datenbank, die Access 2007 verwendet, **Microsoft Office 12.0 Access Database Engine OLE DB Provider**.  
  
 **Dateiname**  
 Geben Sie den Pfad und Namen für die Datenbankdatei in der zum Speichern der Daten (z. B. C:\MyData.mdb, \\\Sales\Database\Northwind.mdb). Oder klicken Sie auf **Durchsuchen** um eine Datei zu suchen.  
  
 **Durchsuchen**  
 Navigieren Sie zu der Datei mit den **öffnen** (Dialogfeld).  
  
 **Benutzername**  
 Geben Sie einen gültigen Benutzernamen für die Datenbankverbindung an, wenn der Datenbank eine Informationsdatei für die Arbeitsgruppe zugeordnet ist.  
  
 **Kennwort**  
 Geben Sie das Kennwort des Benutzers für die Datenbankverbindung an, wenn der Datenbank eine Informationsdatei für die Arbeitsgruppe zugeordnet ist. Jedoch, wenn die Datenbank mit einem einzigen Kennwort für alle Benutzer geschützt ist, müssen Sie angeben dieser Wert in der **Datenlinkeigenschaften** im Dialogfeld aus erfolgt die **erweitert** Schaltfläche.  
  
 **Erweitert:**  
 Mithilfe des Dialogfelds **Datenlinkeigenschaften** geben Sie erweiterte Optionen an, z.B. das Datenbankkennwort oder eine nicht standardmäßige Informationsdatei für Arbeitsgruppen. Weitere Informationen zu OLE DB-Anbietereigenschaften, suchen Sie im Abschnitt "Datenzugriff" des der [MSDN Library](http://go.microsoft.com/fwlink/?linkid=62553).  
  
  