---
title: Aktualisieren des Schemas in einer Datenquellen Sicht (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data source views [Analysis Services], schema updates
- refreshing data source views
- data source views [Analysis Services], refreshing
ms.assetid: 634b0504-1437-43e7-8ac7-3248ac7989a3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5d11ac65a565df23332f24eef8a3e4ddb4e476a5
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78175707"
---
# <a name="refresh-the-schema-in-a-data-source-view-analysis-services"></a>Aktualisieren des Schemas in einer Datenquellensicht (Analysis Services)
  Nachdem eine Datenquellensicht (data source view; DSV) in einem Projekt oder einer Datenbank von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] definiert wurde, kann sich das Schema in einer zugrunde liegenden Datenquelle ändern. In einem Entwicklungsprojekt werden diese Änderungen nicht automatisch erkannt oder aktualisiert. Wenn Sie das Projekt auf einem Server bereitgestellt haben, werden darüber hinaus Verarbeitungsfehler auftreten, wenn Analysis Services keine Verbindung mehr mit der externen Datenquelle herstellen kann.

 Um die Datenquellensicht zu aktualisieren, sodass sie mit der externen Datenquelle übereinstimmt, können Sie die Datenquellensicht in Business Intelligence Development Studio (BIDS) aktualisieren. Beim Aktualisieren der Datenquellensicht werden Änderungen an den externen Datenquellen erkannt, auf denen die Datenquellensicht basiert, sowie eine Änderungsliste erstellt, in der Hinzufügungen oder Löschungen in Bezug auf die externe Datenquelle aufgeführt sind. Anschießend können Sie den Satz von Änderungen auf die Datenquellensicht anwenden, die eine erneute Ausrichtung mit der zugrunde liegenden Datenbank vornimmt. Beachten Sie, dass die Aktualisierung der Cubes und Dimensionen im Projekt, von denen die Datenquellensicht verwendet wird, häufig mit zusätzlicher Arbeit verbunden ist.

 Dieses Thema enthält die folgenden Abschnitte:

 [Bei der Aktualisierung unterstützte Änderungen](#bkmk_changlist)

 [Aktualisieren einer DSV in SQL Server Data Tools](#bkmk_DSVrefresh)

##  <a name="bkmk_changlist"></a>Bei der Aktualisierung unterstützte Änderungen
 Die Aktualisierung der Datenquellensicht kann folgende Aktionen umfassen:

-   Löschen von Tabellen, Spalten und Beziehungen

-   Hinzufügen von Spalten und Beziehungen in der Form, wie sie bereits in der Datenquellensicht enthalten sind

-   Hinzufügen neuer eindeutiger Einschränkungen. Wenn für eine Tabelle in der Datenquellensicht ein logischer Primärschlüssel vorhanden ist und der Tabelle in der Datenquelle ein physischer Schlüssel hinzugefügt wird, wird der logische Schlüssel entfernt und durch den physischen Schlüssel ersetzt.

 Bei der Aktualisierung werden einer Datenquellensicht nie neue Tabellen hinzugefügt. Wenn Sie eine neue Tabelle hinzufügen möchten, muss dieser Schritt manuell erfolgen. Weitere Informationen finden Sie unter [Hinzufügen oder Entfernen von Tabellen oder Sichten in einer Datenquellensicht &#40;Analysis Services&#41;](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)aus.

##  <a name="bkmk_DSVrefresh"></a>Aktualisieren einer DSV in SQL Server Data Tools
 Doppelklicken Sie zum Aktualisieren einer Datenquellensicht im Projektmappen-Explorer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]auf die Datenquellensicht, und klicken Sie anschließend auf die Schaltfläche „Datenquellensicht aktualisieren“, oder wählen Sie im Menü „Datenquellensicht“ die Option **Aktualisieren** aus.

 Während einer Aktualisierung fragt [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] alle zugrunde liegenden relationalen Datenquellen ab, um zu ermitteln, ob Änderungen in Tabellen/Sichten vorliegen, die in der Datenquellensicht enthalten sind. Falls mit den zugrunde liegenden Datenquellen keine Verbindungen hergestellt werden können und Änderungen vorgenommen wurden, können diese im Dialogfenster **Datenquellensicht aktualisieren** angezeigt werden.

 ![Datenquellen Sicht aktualisieren (Dialogfeld)](../media/ssas-olapdsv-refresh.gif "Datenquellensicht aktualisieren (Dialogfeld)")

 Im Dialogfeld sind Tabellen, Spalten, Einschränkungen und Beziehungen aufgelistet, die in der Datenquellensicht gelöscht oder hinzugefügt werden. Darüber hinaus werden in diesem Bericht alle benannten Abfragen oder Berechnungen aufgeführt, die nicht erfolgreich vorbereitet werden können. Die betroffenen Objekte werden in einer Strukturansicht aufgelistet. Dabei werden Spalten und Beziehungen unterhalb der Tabellen geschachtelt dargestellt, und die Art der Änderung (Löschung oder Hinzufügung) wird für jedes Objekt angezeigt. Die Objektsymbole der Standard-Datenquellensicht zeigen an, welcher Objekttyp betroffen ist.

 Das Aktualisieren basiert vollständig auf den Namen der zugrunde liegenden Objekte. Wenn ein zugrunde liegendes Objekt in der Datenquelle umbenannt wird, behandelt der Datenquellen Sicht-Designer deshalb das umbenannte Objekt als zwei separate Vorgänge: einen Löschvorgang und eine Addition. In diesem Fall müssen Sie die umbenannten Objekte bei Bedarf manuell wieder in die Datenquellensicht einfügen. Möglicherweise müssen auch Beziehungen oder logische Primärschlüssel neu erstellt werden.

> [!IMPORTANT]
>  Wenn Sie wissen, dass eine Tabelle in einer Datenquelle umbenannt wurde, können Sie den Befehl **Tabelle ersetzen** verwenden, um die Tabelle durch die umbenannte Tabelle zu ersetzen, bevor Sie die Datenquellensicht aktualisieren. Weitere Informationen finden Sie unter [Ersetzen einer Tabelle oder einer benannten Abfrage in einer Datenquellensicht &#40;Analysis Services&#41;](replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services.md).

 Nachdem Sie den Bericht geprüft haben, können Sie die Änderungen entweder annehmen oder das Update abbrechen und alle Änderungen ablehnen. Alle Änderungen müssen zusammen akzeptiert oder abgelehnt werden. Einzelne Elemente können nicht aus der Liste ausgewählt werden. Sie können die Änderungen auch in einem Bericht speichern.

## <a name="see-also"></a>Weitere Informationen
 [Datenquellensichten in mehrdimensionalen Modellen](data-source-views-in-multidimensional-models.md)


