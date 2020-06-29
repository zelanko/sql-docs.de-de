---
title: Ausführen des SQL Server-Import/Export-Assistenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Import and Export Wizard
- starting SQL Server Import and Export Wizard
- Import and Export Wizard
- starting Import and Export Wizard
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b1803dd3357d2a725f2196e2c692f7470e27a03f
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436857"
---
# <a name="run-the-sql-server-import-and-export-wizard"></a>Ausführen des SQL Server-Import/Export-Assistenten
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Import/Export-Assistent stellt die einfachste Methode zum Kopieren von Daten zwischen Datenquellen und zum Erstellen von Basispaketen bereit. Weitere Informationen zum Assistenten finden Sie unter [SQL Server-Import/Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).  
  
 Ein Video, das veranschaulicht, wie der SQL Server-Import/Export-Assistent zum Erstellen eines Pakets verwendet wird, das Daten aus einer SQL Server Datenbank in ein Microsoft Excel-Arbeitsblatt exportiert, finden Sie unter [Exportieren von SQL Server Daten nach Excel (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131024).  
  
### <a name="to-start-the-sql-server-import-and-export-wizard"></a>So starten Sie den SQL Server-Import/Export-Assistenten  
  
-   Zeigen Sie im Menü **Start** auf **Alle Programme**, zeigen Sie auf**Microsoft SQL Server** , und klicken Sie dann auf **Daten importieren und exportieren**.  
  
     - oder -  
  
     [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Klicken Sie in mit der rechten Maustaste auf den Ordner **SSIS-Pakete** , und klicken Sie dann auf **ssisimport und Export-Assistent**.  
  
     - oder -  
  
     [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Klicken Sie in im Menü **Projekt** auf **ssisimport und Export-Assistent**.  
  
     - oder -  
  
     Stellen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Sie in eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)] Servertyp her, erweitern Sie Datenbanken, klicken Sie mit der rechten Maustaste auf eine Datenbank, **Export data**zeigen Sie auf **Tasks**, und klicken Sie dann auf **Daten importieren** bzw  
  
     - oder -  
  
     Führen Sie in einem Eingabeaufforderungsfenster DTSWizard.exe aus. Diese Datei ist im Verzeichnis C:\Programme\Microsoft SQL Server\100\DTS\Binn gespeichert.  
  
    > [!NOTE]  
    >  Auf einem 64-Bit-Computer installiert [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] die 64-Bit-Version des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Import/Export-Assistenten (DTSWizard.exe). Jedoch verfügen einige Datenquellen, wie Access oder Excel, nur über einen 32-Bit-Anbieter. Damit Sie diese Datenquellen verwenden können, müssen Sie möglicherweise die 32-Bit-Version des Assistenten installieren und ausführen. Wählen Sie zum Installieren der 32-Bit-Version des Assistenten während des Setups entweder Clienttools oder [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
### <a name="to-import-or-export-data-by-using-the-sql-server-import-and-export-wizard"></a>So importieren oder exportieren Sie Daten mit dem SQL Server-Import/Export-Assistenten  
  
1.  Starten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Import/Export-Assistenten.  
  
2.  Wählen Sie auf den entsprechenden Assistentenseiten eine Datenquelle und ein Datenziel aus.  
  
     Zu den verfügbaren Datenquellen zählen [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Datenanbieter, OLE DB-Anbieter, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Anbieter, [!INCLUDE[vstecado](../../includes/vstecado-md.md)]-Anbieter, Microsoft Office Excel, Microsoft Office Access und die Flatfilequelle. In Abhängigkeit von der Quelle legen Sie Optionen fest, wie z. B. den Authentifizierungsmodus, den Servernamen, den Datenbanknamen und das Dateiformat.  
  
    > [!NOTE]  
    >  Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB-Anbieter für Oracle unterstützt die folgenden Oracle-Datentypen nicht: BLOB, CLOB, NCLOB, BFILE und UROWID. Deshalb kann die OLE DB-Quelle keine Daten aus Tabellen herausziehen, die Spalten mit diesen Datentypen enthalten.  
  
     Zu den verfügbaren Datenzielen zählen [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Datenanbieter, OLE DB-Anbieter, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, Excel, Access und das Flatfileziel.  
  
3.  Legen Sie die Optionen für den Zieltyp fest, den Sie ausgewählt haben.  
  
     Wenn es sich bei dem Ziel um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank handelt, können Sie Folgendes angeben:  
  
    -   Geben Sie an, ob eine neue Datenbank erstellt werden soll, und legen Sie die Datenbankeigenschaften fest. Die folgenden Eigenschaften können nicht konfiguriert werden, und der Assistent verwendet die angegebenen Standardwerte:  
  
        |Eigenschaft|Wert|  
        |--------------|-----------|  
        |Sortierung|Latin1_General_CS_AS_KS_WS|  
        |Wiederherstellungsmodell|Vollständig|  
        |Volltextindizierung verwenden|True|  
  
    -   Wählen Sie aus, ob Daten aus Tabellen oder Sichten kopiert werden sollen oder ob Abfrageergebnisse kopiert werden sollen.  
  
         Wenn Sie die Quelldaten abfragen und die Ergebnisse kopieren möchten, können Sie eine Transact-SQL-Abfrage erstellen. Sie können die Transact-SQL-Abfrage manuell eingeben oder eine als Datei gespeicherte Abfrage verwenden. Der Assistent enthält eine Suchfunktion, um nach der Datei zu suchen. Der Assistent öffnet die Datei automatisch und fügt deren Inhalt auf der Assistentenseite ein, wenn Sie die Datei auswählen.  
  
         Wenn es sich bei der Quelle um einen [!INCLUDE[vstecado](../../includes/vstecado-md.md)]-Anbieter handelt, können Sie auch die Option zum Kopieren von Abfrageergebnissen verwenden, wobei Sie die DBCommand-Zeichenfolge als Abfrage bereitstellen.  
  
         Wenn als Quelldaten eine Sicht vorhanden ist, konvertiert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Import/Export-Assistent die Sicht im Ziel automatisch in eine Tabelle.  
  
    -   Geben Sie an, ob die Zieltabelle gelöscht und anschließend neu erstellt wird und ob IDENTITY_INSERT aktiviert werden soll.  
  
    -   Geben Sie an, ob Zeilen in einer vorhandenen Zieltabelle gelöscht oder angefügt werden sollen. Falls die Tabelle nicht vorhanden ist, wird sie automatisch vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Import/Export-Assistenten erstellt.  
  
     Wenn es sich bei dem Ziel um ein Flatfileziel handelt, können Sie Folgendes angeben:  
  
    -   Geben Sie das Zeilentrennzeichen in der Zieldatei an.  
  
    -   Geben Sie das Spaltentrennzeichen in der Zieldatei an.  
  
4.  (Optional) Wählen Sie eine Tabelle aus, und ändern Sie die Zuordnungen zwischen Quell- und Zielspalten, oder ändern Sie die Metadaten von Zielspalten:  
  
    -   Ordnen Sie Quellspalten verschiedenen Zielspalten zu.  
  
    -   Ändern Sie den Datentyp in der Zielspalte.  
  
    -   Legen Sie die Länge von Spalten mit Zeichendatentypen fest.  
  
    -   Legen Sie die Genauigkeit und die Dezimalstellen von Spalten mit numerischen Datentypen fest.  
  
    -   Geben Sie an, ob für die Spalte NULL-Werte zulässig sind.  
  
5.  (Optional) Wählen Sie mehrere Tabellen aus, und aktualisieren Sie die Metadaten und Optionen, die auf jene Tabellen angewendet werden sollen:  
  
    -   Wählen Sie ein vorhandenes Zielschema aus, oder geben Sie ein neues Schema an, dem Tabellen zugewiesen werden sollen.  
  
    -   Geben Sie an, ob IDENTITY_INSERT in Zieltabellen aktiviert werden soll.  
  
    -   Geben Sie an, ob Zieltabellen gelöscht und neu erstellt werden sollen.  
  
    -   Geben Sie an, ob vorhandene Zieltabellen abgeschnitten werden sollen.  
  
6.  Speichern Sie ein Paket, und führen Sie es aus.  
  
     Falls der Assistent in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder an der Eingabeaufforderung gestartet wird, kann das Paket sofort ausgeführt werden. Optional können Sie das Paket in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** -Datenbank oder im Dateisystem speichern. Weitere Informationen zur **msdb** -Datenbank finden Sie unter [Paketverwaltung &#40;SSIS-Dienst&#41;](../service/package-management-ssis-service.md).  
  
     Beim Speichern des Pakets können Sie die Paketschutzebene festlegen und das Kennwort angeben, wenn für die Schutzebene ein Kennwort verwendet wird. Weitere Informationen zu Paket Schutz Ebenen finden Sie unter [Access Control für sensible Daten in-Paketen](../security/access-control-for-sensitive-data-in-packages.md).  
  
     Falls der Assistent in einem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Projekt in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] gestartet wird, kann das Paket nicht im Assistenten ausgeführt werden. Stattdessen wird das Paket dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Projekt hinzugefügt, in dem Sie den Assistenten gestartet haben. Sie können das Paket dann in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ausführen.  
  
    > [!NOTE]  
    >  In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] ist die Option zum Speichern des vom Assistenten erstellten Pakets nicht verfügbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Import/Export-Assistent](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)   
 [Erstellen von Paketen in SQL Server-Datentools](../create-packages-in-sql-server-data-tools.md)  
  
  
