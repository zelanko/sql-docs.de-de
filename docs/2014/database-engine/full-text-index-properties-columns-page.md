---
title: Voll Text Index-Eigenschaften (Seite ' Spalten ') | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62778855"
---
# <a name="full-text-index-properties-columns-page"></a>Volltextindex-Eigenschaften (Seite "Spalten")
  **So zeigen Sie die Eigenschaften eines Volltextindexes an oder ändern diese**  
  
-   [Verwalten von Volltextindizes](../relational-databases/indexes/indexes.md)  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Eindeutiger Index**  
 Wählen Sie einen Index aus der Dropdownliste aus. Der Index muss genau eine Schlüsselspalte haben, muss eindeutig sein und darf keine NULL-Werte zulassen.  
  
 **Geeignete Spalten für die Volltextindizierung auswählen**  
 Im Raster werden die Tabellenspalten angezeigt, die für diesen Volltextindex verfügbar sind. Derezit volltextindizierte Spalten sind markiert. Optional können Sie weitere Spalten markieren, die volltextindiziert werden sollen.  
  
> [!IMPORTANT]  
>  Stellen Sie sicher, dass mindestens eine Spalte markiert ist, und klicken Sie dann auf OK.  
  
|||  
|-|-|  
|**Verfügbare Spalten**|Der Spaltenname.|  
|**Sprache für die Wörter Trennung**|Die Sprache, deren Wörtertrennung und Wortstammerkennung eine linguistische Analyse aller volltextindizierten Daten ausführen.<br /><br /> Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Wörter Trennungen und Wort](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md) Stamm Erkennungen für die Suche und [Auswählen einer Sprache beim Erstellen eines voll Text Indexes](../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md).|  
|**Typ**|Der Name der Tabellenspalte, die den Dokumenttyp der ausgewählten Spalte enthält. Dies ist eine schreibgeschützte Eigenschaft.|  
|**Statistische Semantik**|Wählen Sie aus, ob die semantische Indizierung für die ausgewählte Spalte aktiviert werden soll. Weitere Informationen finden Sie unter [Semantische Suche &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md).<br /><br /> Wenn Sie eine **Sprache** vor der Option **Statistische Semantik**auswählen und die ausgewählte Sprache über kein zugeordnetes semantisches Sprachmodell verfügt, ist das Kontrollkästchen **Statistische Semantik** deaktiviert. Wenn Sie **Statistische Semantik** vor einer **Sprache**auswählen, werden im Dropdown-Kombinationsfeld nur die Sprachen angezeigt, für die das semantische Sprachmodell unterstützt wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Auffüllen von Volltextindizes](../relational-databases/search/populate-full-text-indexes.md)  
  
  
