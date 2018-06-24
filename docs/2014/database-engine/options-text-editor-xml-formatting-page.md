---
title: Optionen (Seite Text-Editor - XML - Formatierung) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 97373178-d288-4127-af37-d9f5fe1b8607
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 5d77f7351d712f63e9cfc92c3ff03b131cb6d5d3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048119"
---
# <a name="options-text-editor---xml---formatting-page"></a>Optionen (Text-Editor – XML – Seite „Formatierung“)
  In diesem Dialogfeld können Sie die Formatierungseinstellungen für den XML-Editor festlegen. Sie können über das Menü **Extras** auf das Dialogfeld **Optionen** zugreifen.  
  
> [!NOTE]  
>  Zum Anzeigen dieser Einstellungen wählen Sie zunächst den Ordner **Text-Editor** und anschließend den Ordner **XML** aus. Wählen Sie dann im Dialogfeld **Optionen** die Option **Formatierung** aus.  
  
## <a name="attributes"></a>Attribute  
 **Manuelle attributformatierung beibehalten**  
 Nimmt keine Neuformatierung von Attributen vor. Dies ist die Standardeinstellung.  
  
> [!NOTE]  
>  Wenn die Attribute auf mehrere Zeilen verteilt sind, richtet der Editor jede Attributzeile am Einzug des jeweils übergeordneten Elements aus.  
  
 **Attribute jeweils in einer eigenen Zeile ausrichten**  
 Richtet das zweite und alle nachfolgenden Attribute vertikal am Einzug des ersten Attributs aus. Der folgende XML-Text verkörpert ein Beispiel für die Ausrichtung der Attribute.  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95"  
</item>  
```  
  
## <a name="auto-reformat"></a>Automatisch neu formatieren  
 **Bei einfügen aus der Zwischenablage.**  
 Formatiert den aus der Zwischenablage eingefügten XML-Text neu.  
  
 **Bei Komplettierung des Endtags**  
 Formatiert das Element nach Abschluss des Endtags neu.  
  
## <a name="mixed-content"></a>Gemischter Inhalt  
 **Standardformat: gemischten Inhalt.**  
 Versucht, gemischten Inhalt neu zu formatieren. Der Inhalt von `xml:space="preserve"`-Bereichen wird dabei jedoch nicht berücksichtigt. Dies ist die Standardeinstellung.  
  
 Wenn ein Element sowohl Text als auch Markup enthält, wird sein Inhalt wie gemischter Inhalt behandelt. Das folgende Beispiel zeigt ein Element mit gemischtem Inhalt.  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
```  
  
 \</dir >  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Editor &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md)  
  
  