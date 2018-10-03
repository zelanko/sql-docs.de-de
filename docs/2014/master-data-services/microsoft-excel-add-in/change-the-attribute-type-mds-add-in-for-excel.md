---
title: Ändern des Attributtyps (MDS-Add-In für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: 9d3001d9-8d0f-4e4a-8e04-4f666bf0df69
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: ce5905026d2a64df3180828e5ee2983f88a5aa06
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48056080"
---
# <a name="change-the-attribute-type-mds-add-in-for-excel"></a>Ändern des Attributtyps (MDS-Add-in für Excel)
  Im [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]können Administratoren den Attributtyp ändern, wenn der Datentyp oder die Anzahl zulässiger Zeichen falsch ist.  
  
 Wenn Sie den Attributtyp ändern möchten, um eine eingeschränkte Liste (domänenbasiertes Attribut) zu erstellen, finden Sie weitere Informationen unter [Erstellen eines domänenbasierten Attributs &#40;MDS-Add-In für Excel&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md).  
  
> [!NOTE]  
>  Sie können den Typ oder die Länge der Spalten **Name** oder **Code** nicht aktualisieren.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf die Funktionsbereiche **Systemverwaltung** und **Explorer** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../administrators-master-data-services.md).  
  
-   Modell, Entität und Attribut müssen vorhanden sein.  
  
### <a name="to-change-the-attribute-type"></a>So ändern Sie den Attributtyp  
  
1.  Laden Sie in Excel die Entität, die die Spalte (Attribut) enthält, die Sie ändern möchten. Weitere Informationen finden Sie unter [Laden von Daten aus MDS in Excel](export-data-to-excel-from-master-data-services.md).  
  
2.  Klicken Sie in der Spalte, die Sie ändern möchten, auf eine beliebige Zelle.  
  
3.  Klicken Sie in der Gruppe **Modell erstellen** auf **Attributeigenschaften**.  
  
4.  Aktualisieren Sie im Dialogfeld **Attributeigenschaften** je nach Bedarf die Einstellungen.  
  
5.  Klicken Sie auf **OK**.  
  
## <a name="what-happens-when-you-change-the-attribute-type"></a>Was geschieht, wenn Sie den Attributtyp ändern?  
 Wenn eine Abhängigkeit von dem Attribut besteht, wenn eine MDS-Geschäftsregel beispielsweise auf das Attribut verweist oder das Attribut in einer Abonnementsicht enthalten ist, und Sie den Datentyp eines Attributs ändern, verfährt MDS wie folgt:  
  
-   Der Datentyp des Attributs wird geändert.  
  
-   Es wird eine Kopie des Attributs mit dem Suffix _old generiert, die keinen Wert enthält. Dies wird als bezeichnet ein **veraltet** Attribut.  
  
 Alle vorhandenen Abhängigkeiten vom ursprünglichen Attribut verweisen jedoch auf das veraltete Attribut und nicht auf das geänderte.  
  
 Dies impliziert Folgendes:  
  
-   Da die Logik aufgrund des neuen Datentyps des Attributs u. U. nicht identisch ist, müssen Sie die Geschäftsregeln aktualisieren, sodass diese auf das geänderte Attribut verweisen. Sie müssen jede betroffene Regel bearbeiten und dann die Ausdrücke ändern, um Verweise auf das veraltete Attribut (_old) zu entfernen, damit auf das aktualisierte Attribut verwiesen wird.  
  
-   Sie müssen alle Abonnementsichten unter der Auswahl Integrationsmanagement öffnen, wählen Sie die Zeile anzeigen, öffnen Sie sie für die Bearbeitung durch Klicken auf das Stiftsymbol und klicken Sie dann auf die **speichern Datenträger** Symbol, um die Sichtdefinition zu aktualisieren. Es sind keine weiteren Änderungen erforderlich, um die Sichtsyntax neu zu generieren.  
  
-   Stagingtabellen, die das Attribut enthalten, wird eine Spalte für das veraltete Attribut hinzugefügt. Das bedeutet, dass der Stagingcode betroffen ist. Um das veraltete Attribut zu entfernen, können Sie es löschen, nachdem Sie die Geschäftsregeln und Abonnementsichten aktualisiert haben.  
  
 **Löschen des veralteten Attributs**  
  
 Bevor Sie ein veraltetes Attribut löschen, müssen Sie alle Verweise auf das Attribut entfernen, indem Sie die Geschäftsregeln korrigieren und die Abonnementsichten wie oben beschrieben neu generieren. Andernfalls wird beim Versuch, das veraltete Attribut zu löschen, auf der Webseite für die Systemverwaltung in einer Fehlermeldung darauf hingewiesen, dass das Attribut nicht gelöscht werden kann, da ein Objekt darauf verweist.  
  
 Um ein Attribut zu löschen, finden Sie unter [Löschen eines Attributs &#40;Master Data Services&#41;](../delete-an-attribute-master-data-services.md)  
  
> [!TIP]  
>  Es ist aufwändig, Datentypen für MDS-Attribute zu ändern, die vorhandene Daten und zugehörige Entitäten aufweisen. Dies gilt insbesondere, wenn eine deklarierte Geschäftsregel oder Abonnementsicht von der Entität abhängt. Als bewährte Methode wird empfohlen, mit einem Datentyp zu beginnen, der flexibel genug ist, um die erforderlichen Werte aufzunehmen. Zeichenfolgen können anfangs kurz sein, müssen aber im Laufe der Zeit u. U. erweitert werden, sodass immer der ungünstigste Fall berücksichtigt werden sollte. Die zusätzliche Länge von Textzeichenfolgen kann Probleme verursachen (da sich breite Textfelder in der grafischen Benutzeroberfläche beispielsweise nur schwer in den Bildschirm einpassen lassen). Daher sollten Sie zu lange Zeichenfolgen vermeiden.  
  
## <a name="see-also"></a>Siehe auch  
 [Attribute &#40;Master Data Services&#41;](../attributes-master-data-services.md)   
 [Erstellen eines Modells &#40;MDS-Add-In für Excel&#41;](building-a-model-mds-add-in-for-excel.md)  
  
  
