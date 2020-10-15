---
title: Konfigurieren von Editoren (SQL Server Management Studio)
description: In diesem Artikel erfahren Sie, wie Sie den Vorgang der SQL Server Management Studio-Editoren anpassen, indem Sie die Optionen im Dialogfeld „Optionen“ festlegen.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
ms.assetid: e7c7a8ef-f561-4258-a7b6-c445dba69f87
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7da0e6a9eff582e69fa37ccd4396039fe6ac1727
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039094"
---
# <a name="configure-editors-sql-server-management-studio"></a>Konfigurieren von Editoren (SQL Server Management Studio)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Sie können die Operation der [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Editoren anpassen, indem Sie die Optionen für jeden Editor konfigurieren.  
  
## <a name="setting-editor-options"></a>Festlegen der Editor-Optionen  
 Sie können die meisten Editoroptionen einrichten, indem Sie im Menü **Extras** den Eintrag **Optionen…** auswählen und so das Dialogfeld **Optionen** anzeigen. Öffnen Sie im Dialogfeld **Optionen** den Knoten **Text-Editor** im linken Bereich, um die Optionen für Code- und Textbearbeitung festzulegen. Die Knoten unter Text-Editor gelten für bestimmte Editoren:  
  
1.  **Alle Sprachen**: Mit diesem Knoten festgelegte Optionen gelten für alle [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]-Editoren. Sie können diese Einstellungen mithilfe der anderen Knoten überschreiben, um für einen bestimmten Editor andere Optionen festzulegen.  
  
2.  **Nur-Text**: Mit diesem Knoten festgelegte Optionen gelten für MDX-, DMX- und Text-Editoren.  
  
3.  **Transact-SQL**: Mit diesem Knoten festgelegte Optionen gelten für den Datenbank-Engine-Abfrage-Editor.  
  
4.  **XML**: Mit diesem Knoten festgelegte Optionen gelten für den XML for Analysis-Editor.  
  
 Öffnen Sie die Knoten **Abfrageausführung** oder **Abfrageergebnisse** , um die Ausführung von Abfragen und die Anzeige der Ergebnisse anzupassen.  
  
## <a name="editor-configuration-tasks"></a>Editorkonfigurationstasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt das Vorgehen für die Festlegung, dass ein Editor durch Doppelklicken auf eine Datei mit einer angegebenen Erweiterung in Windows-Explorer geöffnet werden soll.|[Zuordnen von Dateierweiterungen zu einem Code-Editor](./associate-file-extensions-to-a-code-editor.md)|  
|Beschreibt die Anpassung von Schriftarten für eine bessere Lesbarkeit von Code und Text.|[Ändern von Schriftfarbe, Schriftgrad und Schriftschnitt](./change-font-color-size-and-style.md)|  
|Beschreibt das Vorgehen zur Anzeige von Eigenschaften|[Verwenden des Eigenschaftenfensters in Management Studio](./use-the-properties-window-in-management-studio.md)|  
|Speicherort der F1-Hilfeseiten zu den Dialogfeldern für Editoroptionen.|[Abfrageoptionen (Seiten; F1-Hilfe)](../f1-help/f1-help-for-server-connections-sql-server-management-studio.md)|