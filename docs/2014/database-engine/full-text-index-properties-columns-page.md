---
title: Volltextindex-Eigenschaften (Spaltenseite) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.columns.f1
ms.assetid: 75e52edb-0d07-4393-9345-8b5af4561e35
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 67b7e72e0c4b248e8951667561eaf7548bfba1b5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141640"
---
# <a name="full-text-index-properties-columns-page"></a>Volltextindex-Eigenschaften (Seite "Spalten")
  **Zum Anzeigen oder ändern die Eigenschaften einer Volltext-Indexes**  
  
-   [Verwalten von Volltextindizes](../relational-databases/indexes/indexes.md)  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Eindeutiger index**  
 Wählen Sie einen Index aus der Dropdownliste aus. Der Index muss genau eine Schlüsselspalte haben, muss eindeutig sein und darf keine NULL-Werte zulassen.  
  
 **Wählen Sie die geeigneten Spalten, die volltextindiziert werden**  
 Im Raster werden die Tabellenspalten angezeigt, die für diesen Volltextindex verfügbar sind. Derezit volltextindizierte Spalten sind markiert. Optional können Sie weitere Spalten markieren, die volltextindiziert werden sollen.  
  
> [!IMPORTANT]  
>  Stellen Sie sicher, dass mindestens eine Spalte markiert ist, und klicken Sie dann auf OK.  
  
|||  
|-|-|  
|**Verfügbare Spalten**|Der Spaltenname.|  
|**Sprache für die Wörtertrennung**|Die Sprache, deren Wörtertrennung und Wortstammerkennung eine linguistische Analyse aller volltextindizierten Daten ausführen.<br /><br /> Weitere Informationen finden Sie unter [konfigurieren und Verwalten von Wörtertrennungen und Wortstammerkennungen für die Suche](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md) und [Wählen einer Sprache beim Erstellen einer Volltextindex](../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md).|  
|**Typ**|Der Name der Tabellenspalte, die den Dokumenttyp der ausgewählten Spalte enthält. Dies ist eine schreibgeschützte Eigenschaft.|  
|**Statistische Semantik**|Wählen Sie aus, ob die semantische Indizierung für die ausgewählte Spalte aktiviert werden soll. Weitere Informationen finden Sie unter [Semantische Suche &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md).<br /><br /> Wenn Sie eine **Sprache** vor der Option **Statistische Semantik**auswählen und die ausgewählte Sprache über kein zugeordnetes semantisches Sprachmodell verfügt, ist das Kontrollkästchen **Statistische Semantik** deaktiviert. Wenn Sie **Statistische Semantik** vor einer **Sprache**auswählen, werden im Dropdown-Kombinationsfeld nur die Sprachen angezeigt, für die das semantische Sprachmodell unterstützt wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [Auffüllen von Volltextindizes](../relational-databases/search/populate-full-text-indexes.md)  
  
  
