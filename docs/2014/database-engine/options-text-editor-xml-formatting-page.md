---
title: Optionen (Text-Editor-XML-Formatierungs Seite) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 97373178-d288-4127-af37-d9f5fe1b8607
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: f96625c9658c3bd9864f0928e738357b6e14311e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66089847"
---
# <a name="options-text-editor---xml---formatting-page"></a>Optionen (Text-Editor – XML – Seite „Formatierung“)

In diesem Dialogfeld können Sie die Formatierungseinstellungen für den XML-Editor festlegen. Sie können über das Menü **Extras** auf das Dialogfeld **Optionen** zugreifen.  
  
> [!NOTE]  
> Zum Anzeigen dieser Einstellungen wählen Sie zunächst den Ordner **Text-Editor** und anschließend den Ordner **XML** aus. Wählen Sie dann im Dialogfeld **Optionen** die Option **Formatierung** aus.  
  
## <a name="attributes"></a>Attribute  
 **Manuelle Attributformatierung beibehalten**  
 Nimmt keine Neuformatierung von Attributen vor. Dies ist die Standardoption.  
  
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
 **Bei Einfügen aus der Zwischenablage**  
 Formatiert den aus der Zwischenablage eingefügten XML-Text neu.  
  
 **Bei Komplettierung des Endtags**  
 Formatiert das Element nach Abschluss des Endtags neu.  
  
## <a name="mixed-content"></a>Gemischter Inhalt  
 **Standardformat: gemischter Inhalt**  
 Versucht, gemischten Inhalt neu zu formatieren. Der Inhalt von `xml:space="preserve"`-Bereichen wird dabei jedoch nicht berücksichtigt. Dies ist die Standardoption.  
  
 Wenn ein Element sowohl Text als auch Markup enthält, wird sein Inhalt wie gemischter Inhalt behandelt. Das folgende Beispiel zeigt ein Element mit gemischtem Inhalt.  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
```  
  
 \</dir>  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Editor &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md)  
