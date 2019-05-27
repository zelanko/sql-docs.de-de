---
title: Erteilen von Berechtigungen von Definitionen für Objektmetadaten (Analysis Services) zum Lesen | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: e03e55451c2340b5f0773e2873127c3551a82aab
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66074897"
---
# <a name="grant-read-definition-permissions-on-object-metadata-analysis-services"></a>Erteilen von Berechtigungen zum Lesen von Definitionen für Objektmetadaten (Analysis Services)
  Die Berechtigung zum Lesen von Objektdefinitionen oder Metadaten für ausgewählte Objekte ermöglicht es einem Administrator, Benutzern die Berechtigung zum Anzeigen von Objektdefinitionen zu erteilen, ohne diesen Benutzern gleichzeitig auch die Berechtigung zum Ändern der Objektdefinition, der Objektstruktur oder der Ansicht der tatsächlichen Daten für das Objekt zu erteilen. `Read Definition` Berechtigungen können auf die Datenbank, die Datenquelle, Dimension, Mining-Struktur und Miningmodellebene erteilt werden. Wenn Sie benötigen `Read Definition` Berechtigungen für einen Cube, die Sie aktivieren müssen `Read Definition` für die Datenbank. Beachten Sie, dass die Berechtigungen sind additiv. Eine Rolle kann beispielsweise einem Benutzer die Berechtigung zum Lesen eines Cubes erteilen, während eine andere Datenbankrolle demselben Benutzer die Berechtigung zum Lesen der Metadaten für eine Dimension erteilen kann. Die Berechtigungen aus den beiden unterschiedlichen Rollen werden kombiniert, um dem Benutzer die Berechtigung sowohl zum Lesen der Metadaten für den Cube als auch der Metadaten für die Dimension innerhalb dieser Datenbank zu erteilen.  
  
> [!NOTE]  
>  Die Berechtigung zum Lesen der Metadaten einer Datenbank ist die Mindestberechtigung, die zum Herstellen einer Verbindung mit einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank mithilfe von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oder [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]erforderlich ist. Ein Benutzer, der über die Berechtigung zum Lesen von Metadaten verfügt, kann auch das DISCOVER_XML_METADATA-Schemarowset für die Abfrage des Objekts und die Ansicht seiner Metadaten verwenden. Weitere Informationen finden Sie unter [DISCOVER_XML_METADATA-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset).  
  
## <a name="set-read-definition-permissions-on-a-database"></a>Festlegen von Berechtigungen zum Lesen von Definitionen in einer Datenbank  
 Wenn Sie die Berechtigung zum Lesen von Datenbankmetadaten gewähren, erteilen Sie auch die Berechtigung, die Metadaten aller Objekte in der Datenbank zu lesen.  
  
 Es wird empfohlen, dass Sie die `Read Definition` Berechtigung auf Datenbankebene integrieren, wenn Sie Rollen für die dedizierte Verarbeitung. Mit `Read Definition` können nicht-Administratoren, zeigen Sie die Objekthierarchie eines Modells, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] und für nachfolgende Verarbeitungsvorgänge zu individuellen Objekten zu navigieren.  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]her, erweitern Sie im Objekt-Explorer das **Rollen** -Element für die entsprechende Datenbank, und klicken Sie dann auf eine Datenbankrolle (oder erstellen Sie eine neue Datenbankrolle).  
  
2.  Auf der **allgemeine** Registerkarte die `Read Definition` Option.  
  
3.  Geben Sie im **Mitgliedschaft** sbereich die Windows-Konten von Benutzern und Gruppen ein, die mit dieser Rolle eine Verbindung zu Analysis Services herstellen.  
  
4.  Klicken Sie auf **OK** , um die Erstellung der Rolle zu abzuschließen.  
  
## <a name="set-read-definition-permissions-on-individual-objects"></a>Festlegen von Berechtigungen zum Lesen von Definitionen individueller Objekte  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]her, öffnen Sie den Ordner **Datenbanken** , und wählen Sie eine Datenbank aus. Erweitern Sie im Objekt-Explorer das **Rollen** -Element für die entsprechende Datenbank, und klicken Sie dann auf eine Datenbankrolle (oder erstellen Sie eine neue Datenbankrolle).  
  
2.  In der **allgemeine** Bereich, deaktivieren Sie die Datenbankberechtigung für `Read Definition`. Mit diesem Schritt entfernen Sie das Erben von Berechtigungen, sodass Sie Berechtigungen für individuelle Objekte festlegen können.  
  
3.  Wählen Sie das Objekt, das für die Sie angeben `Read Definition` Eigenschaften:  
  
    -   In der **Datenquellen** Bereich, klicken Sie auf die `Read Definition` für diese Datenquelle das Kontrollkästchen. Rollenmitglieder können die Verbindungszeichenfolge zur Datenquelle anzeigen, einschließlich des Servernamens und möglicherweise des Benutzernamens. Diese Berechtigung ist verfügbar, wenn Sie Informationen zur Verbindungszeichenfolge bereitstellen möchten, ohne auch die Berechtigung zum Ändern der Verbindungszeichenfolge oder Anzeigen der Definitionen beliebiger anderer Objekte zu erteilen.  
  
    -   In der **Dimensionen** Bereich, klicken Sie auf die `Read Definition` für diese Dimension das Kontrollkästchen. Erfahrene Analysten und Entwickler müssen möglicherweise die Definition anzeigen, ohne sie zu ändern oder die Definitionen anderer Objekte (wie andere Dimensionen, Cubeobjekte oder Miningstrukturen oder-modelle) anzuzeigen.  
  
    -   Klicken Sie im Bereich Mining-Strukturen auf die `Read Definition` für Datamining-Strukturen oder Modelle das Kontrollkästchen. `Read Definition` ist für das Durchsuchen des Datenmodells erforderlich. Weitere Informationen finden Sie unter [Erteilen von Berechtigungen für Data Mining-Strukturen und -Modelle &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md).  
  
4.  Geben Sie im **Mitgliedschaft** sbereich die Windows-Konten von Benutzern und Gruppen ein, die mit dieser Rolle eine Verbindung zu Analysis Services herstellen.  
  
5.  Klicken Sie auf **OK** , um die Erstellung der Rolle zu abzuschließen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erteilen von Datenbankberechtigungen &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md)   
 [Erteilen von Verarbeitungsberechtigungen &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md)  
  
  
