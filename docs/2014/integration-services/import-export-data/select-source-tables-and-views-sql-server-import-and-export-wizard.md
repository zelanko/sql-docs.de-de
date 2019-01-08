---
title: Quelltabellen und -sichten auswählen (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.selectsourcetablesandviews.f1
ms.assetid: f60e1a19-2ea6-403c-89ab-3e60ac533ea0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 074fb9aff14a2d173658c0a8ed8e31740e957a37
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52760312"
---
# <a name="select-source-tables-and-views-sql-server-import-and-export-wizard"></a>Quelltabellen und -sichten auswählen (SQL Server-Import/Export-Assistent)
  Verwenden der **auswählen von Quelltabellen und-Sichten** Seite Geben Sie an, die Tabellen und Sichten aus der Datenquelle an das Ziel kopiert werden.  
  
> [!NOTE]  
>  Sie müssen nicht alle Spalten in einer Tabelle kopieren, wenn Sie die Option zum Kopieren von Tabellen auswählen. Klicken Sie auf Bearbeiten Zuordnungen angezeigt, nach dem Auswählen einer Zieltabelle, die **Spaltenzuordnungen** Dialogfeld. Wählen Sie  **\<ignorieren >** in die **Ziel** Spalte die **Spaltenzuordnungen** im Dialogfeld für Spalten, die übersprungen werden sollen.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import / Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Informationen zu den Optionen zum Starten des Assistenten sowie zu den Berechtigungen erforderlich, um den Assistenten erfolgreich ausführen, finden Sie unter [führen Sie die SQL Server-Import / Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem SQL Server-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Optionen  
  
### <a name="tables-and-views-list"></a>Liste 'Tabellen und Sichten'  
 **Quelle**  
 Wählen Sie mithilfe der Kontrollkästchen aus der Liste der verfügbaren Tabellen und Sichten die in das Ziel zu kopierenden Elemente aus. Wenn Sie eine Quelltabelle oder -sicht auswählen und keine weitere Aktion ausführen, werden das Schema und die Daten aus der Quelle ohne Änderungen kopiert.  
  
 **Ziel**  
 Wählen Sie aus der Liste für jede Quelltabelle eine Zieltabelle aus.  
  
> [!NOTE]  
>  Wenn Sie zu diesem Zeitpunkt den Assistenten anhalten, um eine Zieltabelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oder eines anderen Tools zu erstellen, ist die neue Tabelle in der Liste verfügbarer Zieltabellen nicht sofort sichtbar. Um die Liste der Zieltabellen zu aktualisieren, zwei Seiten zurück auf die **wählen Sie ein Ziel** Seite, wählen Sie die Zieldatenbank erneut aus, und dann wieder zur der **auswählen von Quelltabellen und-Sichten**.  
  
### <a name="other-options"></a>Weitere Optionen  
 **Zuordnungen bearbeiten**  
 Verwenden der **Spaltenzuordnungen** Dialogfeld Zielspalten zum Empfangen der Quelldaten angibt. Sie können nur eine Teilmenge der Spalten kopieren, indem Sie auswählen \<ignorieren > in der **Ziel** Spalte die **Spaltenzuordnungen** im Dialogfeld für Spalten, die übersprungen werden sollen.  
  
 **Vorschau**  
 Vorschau von Quelldaten in die **Vorschaudaten** Dialogfeld bestätigen es vor dem Importieren oder exportieren. Die **Vorschaudaten** im Dialogfeld angezeigt, bis zu 200 Zeilen mit Daten.  
  
 Nach der Vorschau der Daten können Sie die Optionen ändern, die Sie für die Datenquelle und das Ziel ausgewählt haben. Um diese Änderungen vorzunehmen, klicken Sie auf der Seite **Quelltabellen und -sichten auswählen** auf **Zurück** , um zu vorherigen Seiten zurückzukehren, auf denen Sie Ihre Auswahlen ändern können.  
  
  
