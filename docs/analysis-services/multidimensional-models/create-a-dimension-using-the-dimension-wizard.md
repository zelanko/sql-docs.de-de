---
title: Erstellen einer Dimension mit dem Dimensions-Assistenten | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ba906ab17169b2e2faf6bef54137fcc4e6210660
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62866879"
---
# <a name="create-a-dimension-using-the-dimension-wizard"></a>Erstellen einer Dimension mit dem Dimensions-Assistenten
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Sie können eine neue Dimension erstellen, indem Sie den Dimensions-Assistenten von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]verwenden.  
  
### <a name="to-create-a-new-dimension"></a>So erstellen Sie eine neue Dimension  
  
1.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **Dimensionen**, und klicken Sie dann auf **Neue Dimension**.  
  
2.  Wählen Sie auf der Seite **Erstellungsmethode auswählen** des Dimensions-Assistenten die Option **Vorhandene Tabelle verwenden**aus, und klicken Sie dann auf **Weiter**.  
  
    > [!NOTE]  
    >  Möglicherweise müssen Sie gelegentlich eine Dimension ohne eine vorhandene Tabelle erstellen. Weitere Informationen finden Sie unter [Erstellen einer Dimension durch Generieren einer Nichtzeittabelle in der Datenquelle](../../analysis-services/multidimensional-models/create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md) und [Erstellen einer Zeitdimension durch Generieren einer Zeittabelle](../../analysis-services/multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md).  
  
3.  Führen Sie auf der Seite **Quellinformationen angeben** die folgenden Schritte aus:  
  
    1.  Wählen Sie in der Liste **Datenquellensicht** eine Datenquellensicht aus.  
  
    2.  Wählen Sie in der Liste **Haupttabelle** die Hauptdimensionstabelle aus.  
  
    3.  Überprüfen Sie in der Liste **Schlüsselspalten** die Schlüsselspalten, die der Assistent automatisch auf Basis des Primärschlüssels ausgewählt hat, der in der Hauptdimensionstabelle definiert ist. Um diese Standardeinstellung zu ändern, geben Sie die Schlüsselspalten an, die die Dimensionstabelle mit der Faktentabelle verknüpfen.  
  
    4.  Überprüfen Sie in der Dropdownliste **Namensspalte** die Namensspalte, die der Assistent automatisch ausgewählt hat.  
  
         Dieser Standardname ist angemessen, wenn die Spalte beschreibende Informationen enthält. Möglicherweise möchten Sie aber einen Namen angeben, der für den Endbenutzer mehr Aussagekraft besitzt. Falls von einem Produktkategorieattribut in einer &lt;localizedText&gt;Products&lt;/localizedText&gt;-Dimension z. B. die **ProductCategoryKey** -Spalte als Schlüsselspalte verwendet wird, können Sie die **ProductCategoryName** -Spalte als Namensspalte angeben.  
  
         Wenn die Liste **Schlüsselspalten** mehrere Schlüsselspalten enthält, müssen Sie eine Namensspalte angeben, die die Elementwerte für das Schlüsselattribut bereitstellt. Hierzu können Sie eine benannte Berechnung in der Datenquellensicht erstellen und diese als Namensspalte verwenden.  
  
    5.  Klicken Sie auf **Weiter**.  
  
4.  Wählen Sie auf der Seite **Verknüpfte Tabellen auswählen** die verknüpften Tabellen aus, die Sie in die Dimension einschließen möchten, und klicken Sie dann auf **Weiter**.  
  
    > [!NOTE]  
    >  Wenn die angegebene Hauptdimensionstabelle Beziehungen zu anderen Dimensionstabellen hat, wird die Seite **Verknüpfte Tabellen** auswählen angezeigt.  
  
5.  Wählen Sie auf der Seite **Dimensionsattribute auswählen** die Attribute aus, die Sie in die Dimension einschließen möchten, und klicken Sie dann auf **Weiter**.  
  
     Optional können Sie die Attributnamen ändern, das Durchsuchen aktivieren oder deaktivieren und den Attributtyp angeben.  
  
    > [!NOTE]  
    >  Um die Felder **Durchsuchen aktivieren** und **Attributtyp** eines Attributs zu aktivieren, muss das Attribut zum Einschließen in die Dimension ausgewählt sein.  
  
6.  Wählen Sie auf der Seite **Kontointelligenz definieren** in der Spalte **Integrierte Kontotypen** den Kontotyp aus, und klicken Sie dann auf **Weiter**.  
  
     Der Kontotyp muss dem Kontotyp der Quelltabelle entsprechen, der in der Spalte **Kontotypen der Quelltabelle** aufgeführt ist.  
  
    > [!NOTE]  
    >  Wenn Sie auf der Seite **Dimensionsattribute auswählen** des Assistenten ein **Kontotyp** -Dimensionsattribut ausgewählt haben, wird die Seite **Kontointelligenz definieren** angezeigt.  
  
7.  Geben Sie auf der Seite **Assistenten abschließen** einen Namen für die neue Dimension ein, und überprüfen Sie die Dimensionsstruktur. Wenn Sie Änderungen vornehmen möchten, klicken Sie auf **Zurück**, andernfalls auf **Fertig stellen**.  
  
    > [!NOTE]  
    >  Nach Abschluss des Dimensions-Assistenten können Sie den Dimensions-Designer zum Hinzufügen, Entfernen und Konfigurieren von Attributen und Hierarchien in der Dimension verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Dimension anhand einer vorhandenen Tabelle](../../analysis-services/multidimensional-models/create-a-dimension-by-using-an-existing-table.md)  
  
  
