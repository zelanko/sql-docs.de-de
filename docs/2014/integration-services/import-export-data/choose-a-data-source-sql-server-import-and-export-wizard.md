---
title: Auswählen einer Datenquelle (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.chooseadatasource.f1
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b6e399cf6c145f36febd9b32ae7a84c54741bb43
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62893595"
---
# <a name="choose-a-data-source-sql-server-import-and-export-wizard"></a>Datenquelle auswählen (SQL Server-Import/Export-Assistent)
  Verwenden Sie die Seite **Datenquelle auswählen** , um die Quelle der Daten anzugeben, die Sie kopieren möchten.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import/Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen für das Starten des Assistenten sowie zu den Berechtigungen, die zum erfolgreichen Ausführen des Assistenten erforderlich sind, finden Sie unter [Ausführen des SQL Server-Import/Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Tastatur  
 **Data Source**  
 Wählen Sie den Datenanbieter aus, dessen Datenspeicherformat mit dem der Quelle übereinstimmt. Möglicherweise sind für die Datenquelle mehrere Anbieter verfügbar. Mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können Sie z. b. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, den .NET Framework Datenanbieter für SQL Server oder den Microsoft OLE DB-Anbieter für SQL Server verwenden.  
  
 Die **Datenquellen** Eigenschaft verfügt über eine Variable Anzahl von Optionen, die von den auf dem Computer installierten Anbietern abhängig sind. In den folgenden Tabellen werden die Optionen für einige häufig verwendete Ziele aufgeführt. Die Angaben zu anderen Anbietern finden Sie in den entsprechenden Dokumentationen zu den Anbietern.  
  
## <a name="dynamic-options"></a>Dynamische Optionen  
 In den folgenden Abschnitten sind die verfügbaren Optionen für mehrere Datenquellen aufgeführt. Allerdings sind nicht alle Datenquellen sind hier aufgeführt, die in der Dropdownliste Datenquellen verfügbar sind.  
  
### <a name="data-source--sql-server-native-client-and-microsoft-ole-db-provider-for-sql-server"></a>Datenquelle = SQL Server Native Client und Microsoft OLE DB-Anbieter für SQL Server  
 **Servername**  
 Geben Sie den Namen des Servers ein, der die Daten enthält, oder wählen Sie einen Server aus der Liste aus.  
  
 **Windows-Authentifizierung verwenden**  
 Gibt an, ob das Paket die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung verwenden soll, um sich bei der Datenbank anzumelden. Im Sinne einer größeren Sicherheit wird die Windows-Authentifizierung empfohlen.  
  
 **SQL Server Authentifizierung verwenden**  
 Gibt an, ob das Paket die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwenden soll, um sich bei der Datenbank anzumelden. Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwenden, müssen Sie einen Benutzernamen und ein Kennwort angeben.  
  
 **Benutzername**  
 Geben Sie einen Benutzernamen für die Datenbankverbindung an, wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwenden.  
  
 **Kennwort**  
 Geben Sie das Kennwort für die Datenbankverbindung ein, wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwenden.  
  
 **Datenbank**  
 Wählen Sie eine Datenbank aus der Liste der Datenbanken für die angegebene Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus.  
  
 **Aktualisieren**  
 Klicken Sie auf **Aktualisieren**, um die Liste der verfügbaren Datenbanken zu aktualisieren.  
  
### <a name="data-source--net-framework-data-provider-for-sql-server"></a>Datenquelle = .NET Framework-Datenanbieter für SQL Server  
 Auf dieser Seite wird eine alphabetische Liste von Optionen für den [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Datenanbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angezeigt. Die wichtigsten Optionen sind in der folgenden Tabelle aufgeführt.  
  
 **Data Source**  
 Geben Sie den Namen des Servers ein, der die Daten enthält, oder wählen Sie einen Server aus der Liste aus.  
  
 **Anfangskatalog**  
 Geben Sie den Namen der Quelldatenbank ein.  
  
 **Integrierte Sicherheit**  
 Geben Sie `True` an, um eine Verbindung mithilfe der integrierten Windows-Authentifizierung herzustellen, oder `False`, um mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung eine Verbindung herzustellen. Wenn Sie `False` angeben, müssen Sie eine Benutzer-ID und ein Kennwort eingeben. Standardwert: `False`.  
  
 **Benutzer-ID**  
 Geben Sie einen Benutzernamen für die Datenbankverbindung an, wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwenden.  
  
 **Kennwort**  
 Geben Sie das Kennwort für die Datenbankverbindung ein, wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwenden.  
  
 Die zusätzlichen Optionen, die beim Auswählen dieses Anbieters aufgeführt werden, sind nicht erforderlich, um erfolgreich eine Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle herzustellen. Eine Beschreibung dieser zusätzlichen Optionen finden Sie in der Dokumentation zum [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Datenanbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK (Software Development Kit).  
  
### <a name="data-source--microsoft-excel"></a>Datenquelle = Microsoft Excel  
  
> [!NOTE]  
>  Wählen Sie **Microsoft Excel** nur aus, wenn Sie eine Verbindung mit einer Datenquelle herstellen möchten, für die Excel 2003 oder früher verwendet wird. Zum Herstellen einer Verbindung mit einer Datenquelle, die Excel 2007 verwendet, wählen Sie **Microsoft Office 12,0 Access Datenbank-Engine OLE DB Provider**aus, klicken Sie auf **Eigenschaften**, und geben `Excel 12.0` Sie dann auf der Registerkarte **alle** des Dialog Felds **Daten Link Eigenschaften** als Wert für **Erweiterte Eigenschaften**ein.  
  
 **Excel-Dateipfad**  
 Geben Sie den Pfad und den Dateinamen für die Kalkulationstabelle an, aus der die Daten importiert werden sollen. Beispiel: **c:\mydata.xls, \\\sales\database\northwind.xls**. Oder klicken Sie auf **Durchsuchen**.  
  
 **Durchsuchen**  
 Suchen Sie die Kalkulationstabelle mithilfe des Dialogfelds **Öffnen**.  
  
 **Excel-Version**  
 Wählen Sie die Version von Excel aus, in der die Quelldaten gespeichert sind.  
  
> [!NOTE]  
>  Wenn Sie Daten aus einer [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]-Quelle importieren, verwendet der Assistent die Excel-Quellkomponente von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Informationen zu Überlegungen zur Verwendung und zu bekannten Problemen finden Sie unter [Excel-Quelle](../data-flow/excel-source.md).  
  
### <a name="data-source--microsoft-access"></a>Datenquelle = Microsoft Access  
  
> [!NOTE]  
>  Wählen Sie **Microsoft Access** nur aus, wenn Sie eine Verbindung mit einer Datenbank herstellen möchten, die Access 2003 oder früher verwendet. Um eine Verbindung mit einer Datenbank herzustellen, die Access 2007 verwendet, wählen Sie stattdessen **Microsoft Office 12,0 Access Datenbank-Engine OLE DB-Anbieters** aus.  
  
 **Dateiname**  
 Geben Sie den Pfad und den Dateinamen für die Datenbankdatei an, aus der die Daten importiert werden sollen. Beispiel: **C:\MyData.mdb, \\\Sales\Database\Northwind.mdb**. Oder klicken Sie auf **Durchsuchen**.  
  
 **Durchsuchen**  
 Suchen Sie die Datenbankdatei mithilfe des Dialogfelds **Öffnen**.  
  
 **Benutzername**  
 Geben Sie einen gültigen Benutzernamen für die Datenbankverbindung an, wenn der Datenbank eine Informationsdatei für die Arbeitsgruppe zugeordnet ist.  
  
 **Kennwort**  
 Geben Sie das Kennwort des Benutzers für die Datenbankverbindung an, wenn der Datenbank eine Informationsdatei für die Arbeitsgruppe zugeordnet ist. Wenn die Datenbank jedoch mit einem einzigen Kennwort für alle Benutzer geschützt ist, müssen Sie diesen Wert im Dialogfeld **Daten** Verknüpfungs Eigenschaften angeben, auf das Sie durch Klicken auf **erweitert**zugreifen können.  
  
 **Erweitert**  
 Mithilfe des Dialog Felds **Daten Link Eigenschaften** können Sie erweiterte Optionen wie das Daten Bank Kennwort oder eine nicht standardmäßige Arbeitsgruppen-Informationsdatei angeben. Weitere Informationen zu OLE DB Anbieter Eigenschaften finden Sie im Abschnitt Datenzugriff der [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553).  
  
### <a name="data-source--flat-file-source"></a>Datenquelle = Flatfilequelle  
 Unter den folgenden Themen finden Sie Informationen zu den Optionen für eine Flatfile-Datenquelle.  
  
 [Verbindungs-Manager-Editor für Flatfiles &#40;Seite Allgemein&#41;](../general-page-of-integration-services-designers-options.md)  
  
 [Verbindungs-Manager-Editor für Flatfiles &#40;Seite Spalten&#41;](../flat-file-connection-manager-editor-columns-page.md)  
  
 [Verbindungs-Manager-Editor für Flatfiles &#40;Seite Erweiterte Seite&#41;](../flat-file-connection-manager-editor-advanced-page.md)  
  
 [Verbindungs-Manager-Editor für Flatfiles &#40;Vorschau Seite&#41;](../flat-file-connection-manager-editor-preview-page.md)  
  
  
