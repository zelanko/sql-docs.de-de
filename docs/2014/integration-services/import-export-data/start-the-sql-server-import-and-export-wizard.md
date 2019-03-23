---
title: Ausführen des SQLServer Import / Export-Assistenten | Microsoft-Dokumentation
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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 824642cf50923aa7ec879bfedbbb8f4ceaa6d9f3
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58384178"
---
# <a name="run-the-sql-server-import-and-export-wizard"></a>Ausführen des SQL Server-Import/Export-Assistenten
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Import/Export-Assistent stellt die einfachste Methode zum Kopieren von Daten zwischen Datenquellen und zum Erstellen von Basispaketen bereit. Weitere Informationen zum Assistenten finden Sie unter [SQL Server-Import / Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).  
  
 Ein Video, das veranschaulicht, wie die SQL Server-Import / Export-Assistenten zum Erstellen eines Pakets, die Daten aus einer SQL Server-Datenbank in eine Microsoft Excel-Kalkulationstabelle exportiert werden, finden Sie unter [Exportieren von SQL Server-Daten nach Excel (SQL Server-Video)](https://go.microsoft.com/fwlink/?LinkId=131024).  
  
### <a name="to-start-the-sql-server-import-and-export-wizard"></a>So starten Sie den SQL Server-Import/Export-Assistenten  
  
-   Auf der **starten** Startmenü **Programme**, zeigen Sie auf**Microsoft SQL Server** , und klicken Sie dann auf **importieren und Exportieren von Daten**.  
  
     -oder-  
  
     In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], mit der rechten Maustaste die **SSIS-Pakete** Ordner, und klicken Sie dann auf **SSISImport / Export-Assistenten**.  
  
     -oder-  
  
     In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]auf die **Projekt** Menü klicken Sie auf **SSISImport / Export-Assistenten**.  
  
     -oder-  
  
     In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], Herstellen einer Verbindung mit der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Servertyp aus, erweitern Sie Datenbanken, mit der rechten Maustaste in einer Datenbank, zeigen Sie auf **Aufgaben**, und klicken Sie dann auf **Importdaten** oder **Exportieren von Daten**.  
  
     -oder-  
  
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
        |Volltextindizierung verwenden|Wahr|  
  
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
  
     Falls der Assistent in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder an der Eingabeaufforderung gestartet wird, kann das Paket sofort ausgeführt werden. Optional können Sie das Paket zum Speichern der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Msdb** Datenbank oder im Dateisystem. Weitere Informationen zu den **Msdb** finden Sie unter [Paketverwaltung &#40;SSIS-Dienst&#41;](../service/package-management-ssis-service.md).  
  
     Beim Speichern des Pakets können Sie die Paketschutzebene festlegen und das Kennwort angeben, wenn für die Schutzebene ein Kennwort verwendet wird. Weitere Informationen zu paketschutzebenen finden Sie unter [Zugriffssteuerung für vertrauliche Daten in Paketen](../security/access-control-for-sensitive-data-in-packages.md).  
  
     Falls der Assistent in einem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Projekt in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] gestartet wird, kann das Paket nicht im Assistenten ausgeführt werden. Stattdessen wird das Paket dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Projekt hinzugefügt, in dem Sie den Assistenten gestartet haben. Sie können das Paket dann in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ausführen.  
  
    > [!NOTE]  
    >  In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], die Möglichkeit, das vom Assistenten erstellte Paket speichern ist nicht verfügbar.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Import/Export-Assistent](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)   
 [Erstellen von Paketen in SQL Server-Datentools](../create-packages-in-sql-server-data-tools.md)  
  
  
