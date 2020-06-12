---
title: Erteilen von Berechtigungen zum Lesen von Definitionen für Objekt Metadaten (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- metadata [Analysis Services]
- permissions [Analysis Services], read metadata
- read metadata permissions
ms.assetid: c857e48e-64b0-4ffe-900d-a0a3ddafcefb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 92edbbb45438622566b240d6c600428dff61ac96
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546622"
---
# <a name="grant-read-definition-permissions-on-object-metadata-analysis-services"></a>Erteilen von Berechtigungen zum Lesen von Definitionen für Objektmetadaten (Analysis Services)
  Die Berechtigung zum Lesen von Objektdefinitionen oder Metadaten für ausgewählte Objekte ermöglicht es einem Administrator, Benutzern die Berechtigung zum Anzeigen von Objektdefinitionen zu erteilen, ohne diesen Benutzern gleichzeitig auch die Berechtigung zum Ändern der Objektdefinition, der Objektstruktur oder der Ansicht der tatsächlichen Daten für das Objekt zu erteilen. `Read Definition`Berechtigungen können auf der Datenbank-, Datenquellen-, Dimensions-, Mining Struktur-und Mining Modell Ebene erteilt werden. Wenn Sie `Read Definition` Berechtigungen für einen Cube benötigen, müssen Sie `Read Definition` für die Datenbank aktivieren. Beachten Sie, dass die Berechtigungen Additiv sind. Eine Rolle kann beispielsweise einem Benutzer die Berechtigung zum Lesen eines Cubes erteilen, während eine andere Datenbankrolle demselben Benutzer die Berechtigung zum Lesen der Metadaten für eine Dimension erteilen kann. Die Berechtigungen aus den beiden unterschiedlichen Rollen werden kombiniert, um dem Benutzer die Berechtigung sowohl zum Lesen der Metadaten für den Cube als auch der Metadaten für die Dimension innerhalb dieser Datenbank zu erteilen.  
  
> [!NOTE]  
>  Die Berechtigung zum Lesen der Metadaten einer Datenbank ist die Mindestberechtigung, die zum Herstellen einer Verbindung mit einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank mithilfe von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oder [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]erforderlich ist. Ein Benutzer, der über die Berechtigung zum Lesen von Metadaten verfügt, kann auch das DISCOVER_XML_METADATA-Schemarowset für die Abfrage des Objekts und die Ansicht seiner Metadaten verwenden. Weitere Informationen finden Sie unter [DISCOVER_XML_METADATA-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset).  
  
## <a name="set-read-definition-permissions-on-a-database"></a>Festlegen von Berechtigungen zum Lesen von Definitionen in einer Datenbank  
 Wenn Sie die Berechtigung zum Lesen von Datenbankmetadaten gewähren, erteilen Sie auch die Berechtigung, die Metadaten aller Objekte in der Datenbank zu lesen.  
  
 Wir empfehlen, dass Sie die- `Read Definition` Berechtigung auf Datenbankebene einschließen, wenn Sie Rollen für die dedizierte Verarbeitung einrichten. `Read Definition`Ermöglicht es nicht-Administratoren, die Objekthierarchie eines Modells in anzuzeigen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] und für nachfolgende Verarbeitung zu einzelnen Objekten zu navigieren.  
  
1.  Stellen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Sie in eine Verbindung mit der Instanz von her [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , erweitern Sie in Objekt-Explorer **Rollen** für die entsprechende Datenbank, und klicken Sie dann auf eine Daten Bank Rolle (oder erstellen Sie eine neue Daten Bank Rolle).  
  
2.  Wählen Sie auf der Registerkarte **Allgemein** die `Read Definition` Option aus.  
  
3.  Geben Sie im **Mitgliedschaft** sbereich die Windows-Konten von Benutzern und Gruppen ein, die mit dieser Rolle eine Verbindung zu Analysis Services herstellen.  
  
4.  Klicken Sie auf **OK** , um die Erstellung der Rolle zu abzuschließen.  
  
## <a name="set-read-definition-permissions-on-individual-objects"></a>Festlegen von Berechtigungen zum Lesen von Definitionen individueller Objekte  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]her, öffnen Sie den Ordner **Datenbanken** , und wählen Sie eine Datenbank aus. Erweitern Sie im Objekt-Explorer das **Rollen** -Element für die entsprechende Datenbank, und klicken Sie dann auf eine Datenbankrolle (oder erstellen Sie eine neue Datenbankrolle).  
  
2.  Deaktivieren Sie im Bereich **Allgemein** die Daten Bank Berechtigung für `Read Definition` . Mit diesem Schritt entfernen Sie das Erben von Berechtigungen, sodass Sie Berechtigungen für individuelle Objekte festlegen können.  
  
3.  Wählen Sie das Objekt aus, für das Sie `Read Definition` Eigenschaften angeben:  
  
    -   Klicken Sie im Bereich **Datenquellen** auf das `Read Definition` Kontrollkästchen für diese Datenquelle. Rollenmitglieder können die Verbindungszeichenfolge zur Datenquelle anzeigen, einschließlich des Servernamens und möglicherweise des Benutzernamens. Diese Berechtigung ist verfügbar, wenn Sie Informationen zur Verbindungszeichenfolge bereitstellen möchten, ohne auch die Berechtigung zum Ändern der Verbindungszeichenfolge oder Anzeigen der Definitionen beliebiger anderer Objekte zu erteilen.  
  
    -   Aktivieren Sie im Bereich **Dimensionen** das `Read Definition` Kontrollkästchen für diese Dimension. Erfahrene Analysten und Entwickler müssen möglicherweise die Definition anzeigen, ohne sie zu ändern oder die Definitionen anderer Objekte (wie andere Dimensionen, Cubeobjekte oder Miningstrukturen oder-modelle) anzuzeigen.  
  
    -   Aktivieren Sie im Bereich Mining Strukturen das `Read Definition` Kontrollkästchen für Data Mining Strukturen oder Modelle. `Read Definition`ist zum Durchsuchen des Datenmodells erforderlich. Weitere Informationen finden Sie unter [Erteilen von Berechtigungen für Data Mining-Strukturen und -Modelle &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md).  
  
4.  Geben Sie im **Mitgliedschaft** sbereich die Windows-Konten von Benutzern und Gruppen ein, die mit dieser Rolle eine Verbindung zu Analysis Services herstellen.  
  
5.  Klicken Sie auf **OK** , um die Erstellung der Rolle zu abzuschließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erteilen von Daten Bank Berechtigungen &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md)   
 [Erteilen von Verarbeitungsberechtigungen &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md)  
  
  
