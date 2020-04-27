---
title: Umbenennen einer Tabelle oder Spalte (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.renametableorcolumn.f1
ms.assetid: 88061a39-c5aa-403d-a52b-7fdb365fc235
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d9d9f11b8713ea26cd79e95b9edc3f36c0bf3564
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66066689"
---
# <a name="rename-a-table-or-column-ssas-tabular"></a>Umbenennen einer Tabelle oder Spalte (SSAS – tabellarisch)
  Sie können während des Importvorgangs den Namen einer Tabelle ändern, indem Sie im **Tabellenimport-Assistenten** auf der Seite **Tabellen und Sichten auswählen** einen **Anzeigenamen**eingeben. Sie können während des Datenimports auch Tabellen- und Spaltennamen ändern, indem Sie im **Tabellenimport-Assistenten** auf der Seite **SQL-Abfrage angeben**eine Abfrage angeben.  
  
 Nachdem dem Modell die Daten hinzugefügt wurden, wird der Name (oder Titel) einer Tabelle auf der Tabellenregisterkarte im unteren Bereich des Modell-Designers angezeigt. Sie können den Namen einer Tabelle ändern, um ihr einen geeigneteren Namen zu geben. Sie können eine Spalte auch umbenennen, nachdem die Daten dem Modell hinzugefügt wurden. Diese Option ist insbesondere dann wichtig, wenn Sie Daten aus mehreren Quellen importiert haben und sicherstellen möchten, dass Spalten in anderen Tabellen Namen haben, die leicht zu unterscheiden sind.  
  
### <a name="to-rename-a-table"></a>So benennen Sie eine Tabelle um  
  
1.  Klicken Sie im Modell-Designer mit der rechten Maustaste auf die Registerkarte der Tabelle, die Sie umbenennen möchten, und klicken Sie auf **Umbenennen**.  
  
2.  Geben Sie den neuen Namen ein.  
  
    > [!NOTE]  
    >  Sie können mit dem Dialogfeld **Tabelleneigenschaften bearbeiten** andere Eigenschaften einer Tabelle bearbeiten, einschließlich der Verbindungsinformationen und Spaltenzuordnungen. Den Namen können Sie in diesem Dialogfeld jedoch nicht ändern.  
  
### <a name="to-rename-a-column"></a>So benennen Sie eine Spalte um  
  
1.  Doppelklicken Sie im Modell-Designer auf die Kopfzeile der Spalte, die Sie umbenennen möchten, oder klicken Sie mit der rechten Maustaste auf die Kopfzeile, und wählen Sie im Kontextmenü **Spalte umbenennen** aus.  
  
2.  Geben Sie den neuen Namen ein.  
  
## <a name="naming-requirements-for-columns-and-tables"></a>Anforderungen für die Benennung von Spalten und Tabellen  
 Die folgenden Wörter und Zeichen können nicht im Namen einer Tabelle oder einer Spalte verwendet werden:  
  
-   Führende oder nachfolgende Leerzeichen  
  
-   Steuerzeichen  
  
-   Die folgenden Zeichen (die in den Namen von Analysis Services-Objekten nicht gültig sind):.,; ':/ \\*|? &% $! + = () []{}<>  
  
-   Von Analysis Services reservierte Schlüsselwörter, einschließlich Funktionsnamen und Operatoren von Multidimensional Expressions (MDX) und Data Mining Extensions (DMX)  
  
## <a name="effect-of-renaming-on-existing-tables-columns-and-calculations"></a>Auswirkung des Umbenennungsvorgangs auf vorhandene Tabellen, Spalten und Berechnungen  
 Jedes Mal, wenn Sie den Namen einer Tabelle ändern, ändern Sie den Namen des zugrunde liegenden Tabellenobjekts, der möglicherweise mehrere Spalten oder Measures enthält. Daher müssen alle Spalten in der Tabelle und alle Beziehungen, die diese Tabelle verwenden, aktualisiert werden, um den neuen Namen in ihren Definitionen zu verwenden. Dieses Update wird in einigen Fällen automatisch durchgeführt. Measures werden nicht automatisch aktualisiert.  
  
 Darüber hinaus müssen alle Berechnungen, die die umbenannte Tabelle oder Spalten in der umbenannten Tabelle verwenden, ebenfalls aktualisiert werden, und die von diesen Berechnungen abgeleiteten Daten müssen aktualisiert und neu berechnet werden. Je nach Anzahl der betroffenen Tabellen und Berechnungen kann dies einige Zeit in Anspruch nehmen. Der beste Zeitpunkt zum Umbenennen von Tabellen ist daher entweder während des Importvorgangs oder bevor Sie komplexe Beziehungen und Berechnungen erstellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellen und Spalten &#40;tabellarischen SSAS-&#41;](tables-and-columns-ssas-tabular.md)   
 [Aus Power Pivot &#40;tabellarischen SSAS-&#41;importieren](import-from-power-pivot-ssas-tabular.md)   
 [Importieren aus Analysis Services &#40;SSAS – tabellarisch&#41;](import-from-analysis-services-ssas-tabular.md)  
  
  
