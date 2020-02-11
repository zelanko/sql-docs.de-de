---
title: Benannte Mengen erstellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculations [Analysis Services], named sets
- named sets [Analysis Services]
- members [Analysis Services], named sets
ms.assetid: 03cf97a4-1a18-45f3-acb0-35123bd619be
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c1fc4ab5d778535fdc4e2186c5bc88741b4367f5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66076143"
---
# <a name="create-named-sets"></a>Erstellen von benannten Mengen
  Eine benannte Menge ist eine Menge von Dimensionselementen oder ein Mengenausdruck, der zur Wiederverwendung, z. B. in MDX-Abfragen (Multidimensional Expressions), erstellt wird. Sie können benannte Mengen durch Kombinieren von Cubedaten, arithmetischen Operatoren, Zahlen und Funktionen erstellen. Sie können beispielsweise eine benannte Menge mit dem Namen Top Ten Factories erstellen, die die zehn Elemente der Factories-Dimension mit den höchsten Werten des Production-Measures enthält. Top Ten Factories kann dann von Endbenutzern in Abfragen verwendet werden. Ein Endbenutzer kann Top Ten Factories z. B. auf eine Achse und die Measures-Dimension, einschließlich Production, auf eine andere Achse platzieren. Weitere Informationen finden Sie unter [Berechnungen in mehrdimensionalen Modellen](calculations-in-multidimensional-models.md) und [Erstellen von benannten Mengen in MDX &#40;MDX&#41;](mdx/mdx-named-sets-building-named-sets.md).  
  
 Mithilfe des Befehls **Neue benannte Menge** auf der Registerkarte **Berechnungen** des Cube-Designers können Sie eine benannte Menge erstellen. Dieser Befehl kann im Menü **Cube** auf der Symbolleiste der Registerkarte **Berechnungen** aufgerufen werden. Mit diesem Befehl wird ein Formular zum Angeben der folgenden Optionen für die benannte Menge angezeigt:  
  
 **Name**  
 Wählt den Namen der benannten Menge aus. Dieser Name wird Endbenutzern angezeigt, wenn sie den Cube durchsuchen.  
  
 **Ausdruck**  
 Gibt den Ausdruck an, der die benannte Menge erzeugt. Dieser Ausdruck kann in MDX geschrieben werden. Der Ausdruck kann Folgendes enthalten:  
  
-   Datenausdrücke, die für Cubekomponenten wie Dimensionen, Ebenen, Measures usw. stehen.  
  
-   Arithmetische Operatoren.  
  
-   Zahlen.  
  
-   Funktionen  
  
 Sie können Cubekomponenten von der Registerkarte **Metadaten** des Bereichs **Berechnungstools** in das Feld **Ausdruck** im Bereich des Formular-Editors für benannte Mengen **** kopieren oder ziehen. Sie können Funktionen von der Registerkarte **Funktionen** des Bereichs **Berechnungstools** in das Feld **Ausdruck** im Bereich des Formular-Editors für benannte Mengen **** kopieren oder ziehen.  
  
> [!IMPORTANT]  
>  Wenn Sie den Mengen Ausdruck durch explizites benennen der Elemente in der Menge erstellen, schließen Sie die Liste der Elemente in ein Paar geschweifter Klammern ({}) ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berechnungen in mehrdimensionalen Modellen](calculations-in-multidimensional-models.md)  
  
  
