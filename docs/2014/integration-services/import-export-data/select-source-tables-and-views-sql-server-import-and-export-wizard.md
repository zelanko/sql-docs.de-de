---
title: Quelltabellen und -sichten auswählen (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
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
- sql12.dts.impexpwizard.selectsourcetablesandviews.f1
ms.assetid: f60e1a19-2ea6-403c-89ab-3e60ac533ea0
caps.latest.revision: 47
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f785bac221acd45892a2a75a28682b2173e29e37
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061187"
---
# <a name="select-source-tables-and-views-sql-server-import-and-export-wizard"></a>Quelltabellen und -sichten auswählen (SQL Server-Import/Export-Assistent)
  Verwenden der **wählen Quelltabellen und-Sichten** Seite Geben Sie die Tabellen und Sichten aus der Datenquelle an das Ziel kopiert werden.  
  
> [!NOTE]  
>  Sie müssen nicht alle Spalten in einer Tabelle kopieren, wenn Sie die Option zum Kopieren von Tabellen auswählen. Klicken Sie auf Zuordnungen bearbeiten, um anzuzeigen, nach dem Auswählen einer Zieltabelle, die **Spaltenzuordnungen** (Dialogfeld). Wählen Sie  **\<ignorieren >** in der **Ziel** Spalte die **Spaltenzuordnungen** (Dialogfeld) für Spalten, die übersprungen werden sollen.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import / Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen zum Starten des Assistenten sowie zu den Berechtigungen erforderlich, um den Assistenten erfolgreich ausführen, finden Sie unter [führen Sie die SQL Server-Import / Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem SQL Server-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Tastatur  
  
### <a name="tables-and-views-list"></a>Liste 'Tabellen und Sichten'  
 **Quelle**  
 Wählen Sie mithilfe der Kontrollkästchen aus der Liste der verfügbaren Tabellen und Sichten die in das Ziel zu kopierenden Elemente aus. Wenn Sie eine Quelltabelle oder -sicht auswählen und keine weitere Aktion ausführen, werden das Schema und die Daten aus der Quelle ohne Änderungen kopiert.  
  
 **Ziel**  
 Wählen Sie aus der Liste für jede Quelltabelle eine Zieltabelle aus.  
  
> [!NOTE]  
>  Wenn Sie zu diesem Zeitpunkt im Assistenten zum Erstellen einer Zieltabelle in anhalten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oder ein anderes Tool, auf die neue Tabelle ist nicht in der Liste verfügbarer Zieltabellen sofort sichtbar. Zum Aktualisieren der Liste der Zieltabellen Schritt zwei Seiten zurück zur der **wählen Sie ein Ziel** Seite, wählen Sie die Zieldatenbank erneut aus, und gehen Sie erneut mit der **wählen Quelltabellen und-Sichten**.  
  
### <a name="other-options"></a>Weitere Optionen  
 **Zuordnungen bearbeiten**  
 Verwenden der **Spaltenzuordnungen** Dialogfeld Zielspalten zum Empfangen der Quelldaten angeben. Sie können nur eine Teilmenge der Spalten kopieren, indem Sie die Auswahl \<ignorieren > in der **Ziel** Spalte der **Spaltenzuordnungen** (Dialogfeld) für Spalten, die übersprungen werden sollen.  
  
 **Vorschau**  
 Vorschau von Quelldaten in der **Vorschaudaten** (Dialogfeld), überprüfen sie vor dem Importieren oder exportieren. Die **Vorschaudaten** im Dialogfeld werden bis zu 200 Datenzeilen angezeigt.  
  
 Nach der Vorschau der Daten können Sie die Optionen ändern, die Sie für die Datenquelle und das Ziel ausgewählt haben. Um diese Änderungen vorzunehmen, klicken Sie auf der Seite **Quelltabellen und -sichten auswählen** auf **Zurück** , um zu vorherigen Seiten zurückzukehren, auf denen Sie Ihre Auswahlen ändern können.  
  
  