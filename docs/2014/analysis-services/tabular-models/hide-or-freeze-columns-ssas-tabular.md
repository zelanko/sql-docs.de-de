---
title: Ausblenden oder Einfrieren von Spalten (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.hideunhidecolumnsdb.f1
ms.assetid: 5407aee5-6a07-4559-a2ba-2ca00a242f02
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d3277c722652e67036d0c0bfe2a904797f327a4d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37214050"
---
# <a name="hide-or-freeze-columns-ssas-tabular"></a>Ausblenden oder Einfrieren von Spalten (SSAS – tabellarisch)
  Wenn es im Modell-Designer Spalten gibt, die Sie nicht in einer Tabelle anzeigen möchten, können Sie diese zeitweise ausblenden. Durch das Ausblenden einer Spalte erhalten Sie mehr Platz auf dem Bildschirm, um neue Spalten hinzuzufügen oder nur mit relevanten Datenspalten zu arbeiten. Sie können Spalten über das Menüband **Spalte** im Modell-Designer und über das Kontextmenü der einzelnen Spaltenüberschriften aus- und einblenden. Um einen Bereich eines Modells sichtbar zu halten, während Sie einen Bildlauf zu einem anderen Bereich des Modells ausführen, können Sie bestimmte Spalten in einem Bereich sperren, indem Sie sie fixieren.  
  
> [!IMPORTANT]  
>  Die Möglichkeit, Spalten auszublenden, dient nicht der Datensicherheit, sondern nur zur Vereinfachung und Kürzung der Spaltenliste im Modell-Designer oder in Berichten. Um Daten zu sichern, können Sie Sicherheitsrollen definieren. Durch Rollen können die anzeigbaren Metadaten und Daten auf die in der Rolle definierten Objekte eingeschränkt werden. Weitere Informationen finden Sie unter [Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).  
  
 Wenn Sie mit ausgeblendeten Spalten arbeiten, haben Sie die Möglichkeit, eine Spalte auszublenden, während Sie im Modell-Designer oder in Berichten arbeiten. Wenn Sie alle Spalten ausblenden, wird die gesamte Tabelle im Modell-Designer leer angezeigt.  
  
> [!NOTE]  
>  Wenn Sie viele Spalten ausblenden müssen, können Sie eine Perspektive erstellen, statt Spalten aus- und einzublenden. Eine Perspektive ist eine benutzerdefinierte Sicht der Daten, die das Arbeiten mit Teilmengen verknüpfter Daten erleichtert. Weitere Informationen finden Sie unter [Erstellen und Verwalten von Perspektiven &#40;SSAS – tabellarisch&#41;](perspectives-ssas-tabular.md).  
  
### <a name="to-hide-an-individual-column"></a>So blenden Sie eine einzelne Spalte aus  
  
1.  Wählen Sie im Modell-Designer die Tabelle aus, die die auszublendende Spalte enthält.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Spalte, und klicken Sie dann auf **Spalten ausblenden**und auf **Aus Designer und aus Berichten**, **Aus Berichten**oder **Aus Designer**.  
  
### <a name="to-hide-multiple-columns"></a>So blenden Sie mehrere Spalten aus  
  
1.  Wählen Sie im Modell-Designer die Tabelle aus, die die auszublendenden Spalten enthält.  
  
2.  Klicken Sie auf das Menü **Spalten** , und klicken Sie dann auf **Aus- und einblenden**.  
  
3.  Suchen Sie im Dialogfeld **Spalten aus- und einblenden** diejenigen Spalten, die Sie ausblenden möchten, und deaktivieren Sie dann **In Designer** bzw. **In Berichten**.  
  
4.  Klicken Sie auf **OK**.  
  
### <a name="to-freeze-columns"></a>So fixieren Sie Spalten  
  
1.  Wählen Sie im Modell-Designer die Tabelle aus, die die zu fixierenden Spalten enthält.  
  
2.  Wählen Sie eine oder mehrere Spalten zum Fixieren aus.  
  
3.  Klicken Sie auf das Menü **Spalten** , und klicken Sie dann auf **Fixieren**.  
  
    > [!NOTE]  
    >  Wenn Spalten fixiert sind, werden Sie im Designer in der Tabelle nach links (bzw. nach vorne) verschoben. Wenn Sie die Fixierung der Spalte aufheben, wird diese nicht an ihre ursprüngliche Position zurückverschoben.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellen und Spalten &#40;SSAS – tabellarisch&#41;](tables-and-columns-ssas-tabular.md)   
 [Perspektiven &#40;SSAS – tabellarisch&#41;](perspectives-ssas-tabular.md)   
 [Rollen &#40;SSAS – tabellarisch&#41;](roles-ssas-tabular.md)  
  
  
