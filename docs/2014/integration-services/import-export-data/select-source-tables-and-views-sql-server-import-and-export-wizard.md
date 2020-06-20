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
author: janinezhang
ms.author: janinez
ms.openlocfilehash: aee638291a4aee2c4ea5d60a69fc206af613e15d
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965550"
---
# <a name="select-source-tables-and-views-sql-server-import-and-export-wizard"></a>Quelltabellen und -sichten auswählen (SQL Server-Import/Export-Assistent)
  Verwenden Sie die Seite **Quell Tabellen und-Sichten auswählen** , um die Tabellen und Sichten anzugeben, die aus der Datenquelle in das Ziel kopiert werden sollen.  
  
> [!NOTE]  
>  Sie müssen nicht alle Spalten in einer Tabelle kopieren, wenn Sie die Option zum Kopieren von Tabellen auswählen. Nachdem Sie eine Ziel Tabelle ausgewählt haben, klicken Sie auf Zuordnungen bearbeiten, um das Dialogfeld **Spalten** Zuordnungen anzuzeigen. Wählen Sie in der Spalte **\<ignore>** **Ziel** im Dialogfeld **Spalten** Zuordnungen die Spalten aus, die Sie überspringen möchten.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import/Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen für das Starten des Assistenten sowie zu den Berechtigungen, die zum erfolgreichen Ausführen des Assistenten erforderlich sind, finden Sie unter [Ausführen des SQL Server-Import/Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem SQL Server-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Tastatur  
  
### <a name="tables-and-views-list"></a>Liste 'Tabellen und Sichten'  
 **Quelle**  
 Wählen Sie mithilfe der Kontrollkästchen aus der Liste der verfügbaren Tabellen und Sichten die in das Ziel zu kopierenden Elemente aus. Wenn Sie eine Quelltabelle oder -sicht auswählen und keine weitere Aktion ausführen, werden das Schema und die Daten aus der Quelle ohne Änderungen kopiert.  
  
 **Ziel**  
 Wählen Sie aus der Liste für jede Quelltabelle eine Zieltabelle aus.  
  
> [!NOTE]  
>  Wenn Sie zu diesem Zeitpunkt den Assistenten anhalten, um eine Zieltabelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oder eines anderen Tools zu erstellen, ist die neue Tabelle in der Liste verfügbarer Zieltabellen nicht sofort sichtbar. Um die Liste der Ziel Tabellen zu aktualisieren, führen Sie zwei Seiten auf die Seite **Ziel auswählen** zurück, wählen Sie die Zieldatenbank erneut aus, und führen Sie dann erneut die Option **Quell Tabellen und-Sichten auswählen**aus.  
  
### <a name="other-options"></a>Weitere Optionen  
 **Zuordnungen bearbeiten**  
 Im Dialogfeld **Spalten** Zuordnungen können Sie Ziel Spalten angeben, um die Quelldaten zu empfangen. Sie können nur eine Teilmenge von Spalten kopieren, indem Sie \<ignore> in der Spalte **Ziel** des Dialog Felds **Spalten** Zuordnungen für Spalten auswählen, die Sie überspringen möchten.  
  
 **Vorschau**  
 Stellen Sie im Dialogfeld **Vorschau Daten** eine Vorschau der Quelldaten zur Überprüfung vor dem Importieren oder exportieren vor. Im Dialogfeld **Vorschau Daten** werden bis zu 200 Daten Zeilen angezeigt.  
  
 Nach der Vorschau der Daten können Sie die Optionen ändern, die Sie für die Datenquelle und das Ziel ausgewählt haben. Um diese Änderungen vorzunehmen, klicken Sie auf der Seite **Quelltabellen und -sichten auswählen** auf **Zurück** , um zu vorherigen Seiten zurückzukehren, auf denen Sie Ihre Auswahlen ändern können.  
  
  
