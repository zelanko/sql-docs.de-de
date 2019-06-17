---
title: Erteilen von Berechtigungen für eine Dimension (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.dimensions.f1
helpviewer_keywords:
- dimensions [Analysis Services], security
- read/write permissions
- user access rights [Analysis Services], dimensions
- permissions [Analysis Services], dimensions
ms.assetid: be5b2746-0336-4b12-827e-131462bdf605
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3efce85f27db9d0695ea56e9940ab563ed40537a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66074961"
---
# <a name="grant-permissions-on-a-dimension-analysis-services"></a>Gewähren von Berechtigungen in einer Dimension (Analysis Services)
  Dimensionssicherheit wird verwendet, um Berechtigungen für ein Dimensionsobjekt festzulegen, nicht für dessen Daten. Meist ist das Gewähren oder Verweigern des Zugriffs auf Verarbeitungsvorgänge das Hauptziel bei der Festlegung von Berechtigungen in einer Dimension.  
  
 Unter Umständen möchten Sie jedoch vielleicht nicht die Verarbeitungsvorgänge steuern, sondern den Datenzugriff für eine Dimension oder die darin enthaltenen Attribute und Hierarchien. Ein Unternehmen mit regionalen Vertriebsabteilungen möchte beispielsweise Verkaufsdaten für Mitarbeiter außerhalb der Abteilung sperren. Sie können Berechtigungen für Dimensionsattribute und Dimensionsmitglieder festlegen, um Zugriff auf Teile der Dimensionsdaten für unterschiedliche Komponenten zu gewähren oder zu verweigern. Beachten Sie, dass Sie nicht den Zugriff auf ein bestimmtes Dimensionsobjekt selbst, sondern nur auf dessen Daten verweigern können. Wenn Sie vor allem den Zugriff für Mitglieder in einer Dimension gewähren oder verweigern möchten, einschließlich der Zugriffsrechte für individuelle Attributhierarchien, finden Sie Informationen hierzu unter [Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) .  
  
 Die restlichen Abschnitte dieses Themas behandeln Berechtigungen, die Sie direkt für das Dimensionsobjekt festlegen können, einschließlich:  
  
-   Leseberechtigungen oder Lese-/Schreibberechtigungen (Sie können nur Leseberechtigungen oder Lese-/Schreibberechtigungen wählen. "Keine" ist nicht möglich.) Da Sie ja den Zugriff auf Dimensionsdaten beschränken möchten, lesen Sie unter [Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) nach.  
  
-   Verarbeitungsberechtigungen (Verwenden Sie diese, wenn Szenarios eine Verarbeitungsstrategie benötigen, die individuelle Berechtigungen für einzelne Objekte erforderlich macht.)  
  
-   Berechtigungen für das Lesen von Definitionen (Dies wird meist verwendet, um interaktive Verarbeitung bei einem Tool zu unterstützen oder Transparenz in einem Modell zu gewährleisten. Die Leseberechtigung für Definitionen ermöglicht das Anzeigen der Struktur einer Dimension, ohne Zugriff auf deren Daten oder die Möglichkeit zur Änderung der Definition zu gewähren.)  
  
 Wenn Sie Rollen für eine Dimension definieren, variieren die verfügbaren Berechtigungen abhängig davon, ob es sich beim Objekt um eine eigenständige Datenbankdimension – innerhalb der Datenbank, jedoch außerhalb eines Cubes – oder eine Cubedimension handelt.  
  
> [!NOTE]  
>  Standardmäßig werden Berechtigungen in einer Datenbank von einer Cubedimension geerbt. Wenn Sie zum Beispiel **Lese-/Schreibzugriff** in einer Customer-Datenbankdimension aktivieren, erbt die Customer-Cubedimension den **Lese-/Schreibzugriff** im Kontext der aktuellen Rolle. Sie können geerbte Berechtigungen löschen, wenn Sie eine Berechtigungseinstellung überschreiben möchten.  
  
## <a name="set-permissions-on-a-database-dimension"></a>Erteilen von Berechtigungen für eine Datenbankdimension  
 Datenbankdimensionen sind eigenständige Objekte innerhalb einer Datenbank, mit denen Dimensionen innerhalb desselben Modells erneut verwendet werden können. Denken Sie hierbei an eine DATE-Datenbankdimension, die in einem Modell vielfach verwendet wird, wie die Cubedimensionen Order Date, Ship Date und Due Date. Da Cubes und Datenbankdimensionen in einer Datenbank Peer-Objekte sind, können Sie Verarbeitungsberechtigungen unabhängig für jedes Objekt festlegen.  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]her, erweitern Sie im Objekt-Explorer das **Rollen** -Element für die entsprechende Datenbank, und klicken Sie dann auf eine Datenbankrolle (oder erstellen Sie eine neue Datenbankrolle).  
  
2.  Im Bereich **Dimensionen** sollte für die Dimension **Alle Datenbankdimensionen**festgelegt sein.  
  
     Die Standardeinstellung für Berechtigungen ist **Lesen**.  
  
     Obwohl **Lese-/Schreibzugriff** verfügbar ist, wird empfohlen, diese Berechtigung nicht zu verwenden. **Lesen/Schreiben** wird für das Rückschreiben von Dimensionen verwendet, die veraltet sind. Finden Sie unter [als veraltet markierte Analysis Services-Funktionen in SQLServer 2014](../deprecated-analysis-services-features-in-sql-server-2014.md).  
  
     Optional können Sie die Berechtigungen **Definition lesen** und **Verarbeiten** für individuelle Objekte festlegen, solange diese Berechtigungen noch nicht auf Datenbankebene festgelegt wurden. Einzelheiten finden Sie unter [Erteilen von Berechtigungen zum Verarbeiten &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md) und [Erteilen von Berechtigungen zum Lesen von Definitionen für Objektmetadaten &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md).  
  
## <a name="set-permissions-on-a-cube-dimension"></a>Erteilen von Berechtigungen für eine Cubedimension  
 Cubedimensionen sind Datenbankdimensionen, die zu einem Cube hinzugefügt wurden. Als solche hängen sie strukturell von den zugehörigen Measuregruppen ab. Obwohl diese Objekte atomar verarbeitet werden können, ist es im Hinblick auf die Autorisierung sinnvoller, den Cube und die Cubedimensionen als einzelne Entität zu behandeln.  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]her, erweitern Sie im Objekt-Explorer das **Rollen** -Element für die entsprechende Datenbank, und klicken Sie dann auf eine Datenbankrolle (oder erstellen Sie eine neue Datenbankrolle).  
  
2.  In der **Dimensionen** Bereich, Änderung legen Sie die Dimension zu \<Cubename > **Cubedimensionen**.  
  
     Standardmäßig werden Berechtigungen von einer entsprechenden Datenbankdimension geerbt. Deaktivieren Sie das Kontrollkästchen **Erben** , um Berechtigungen von **Lesen** zu **Lesen/Schreiben**zu ändern. Lesen Sie zuerst den Hinweis im vorhergehenden Abschnitt, bevor Sie **Lesen/Schreiben**verwenden.  
  
> [!IMPORTANT]  
>  Wenn Sie mithilfe von AMO (Analysis Management Objects) Datenbankrollenberechtigungen konfigurieren, trennt jeder Verweis auf eine Cubedimension im DimensionPermission-Attribut eines Cubes die Berechtigungsvererbung aus dem DimensionPermission-Attribut der Datenbank. Weitere Informationen zu AMO finden Sie unter [Entwickeln mit Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).  
  
## <a name="see-also"></a>Siehe auch  
 [Rollen und Berechtigungen &#40;Analysis Services&#41;](roles-and-permissions-analysis-services.md)   
 [Erteilen von Cube- oder Modellberechtigungen &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md)   
 [Erteilen von Berechtigungen für Data Mining-Strukturen und -Modelle &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)   
 [Erteilen von benutzerdefiniertem Zugriff auf Dimensionsdaten &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md)   
 [Erteilen von benutzerdefiniertem Zugriff auf Zellendaten &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md)  
  
  
