---
title: Sicherheitsrollen (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], roles
- Analysis Services objects, roles
- security [Analysis Services], roles
- roles [Analysis Services], about roles
- server roles [Analysis Services]
- database roles [Analysis Services]
- roles [Analysis Services]
- storing data [Analysis Services], roles
- access rights [Analysis Services], roles
ms.assetid: 5b7e9cef-ff68-4d8e-99bc-e0094ced1baa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2e63ef1a2463f65e108ade9a43b748e02831da57
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62725254"
---
# <a name="security-roles--analysis-services---multidimensional-data"></a>Sicherheitsrollen (Analysis Services – Mehrdimensionale Daten)
  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] werden zur Verwaltung der Sicherheit von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Objekten und -Daten Rollen verwendet. Im Allgemeinen wird eine Rolle der SIDs (Sicherheits-IDs) von Microsoft Windows-Benutzern bzw. Windows-Gruppen zugeordnet, für die bestimmte Zugriffsrechte und -berechtigungen auf von einer Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]verwalteten Objekte definiert sind. In [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]werden die folgenden zwei Arten von Rollen bereitgestellt:  
  
-   Die Serverrolle, bei der es sich um eine feste Rolle handelt, mit der der Administratorzugriff auf eine Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]bereitgestellt wird.  
  
-   Datenbankrollen, bei denen es sich um von Administratoren definierte Rollen handelt, mit denen der Zugriff auf Objekte und Daten für Benutzer ohne Administratorrechte gesteuert wird.  
  
 Sicherheit in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] wird mithilfe von Rollen und Berechtigungen verwaltet. Rollen sind Gruppen von Benutzern. Benutzer, auch als Elemente bezeichnet, können zu Rollen hinzugefügt oder aus diesen entfernt werden. Berechtigungen für Objekte werden mithilfe von Rollen festgelegt, und alle Mitglieder in einer Rolle können die Objekte verwenden, für die die Rolle die Berechtigungen besitzt. Alle Elemente in einer Rolle verfügen über die gleichen Berechtigungen für die Objekte. Berechtigungen gelten speziell für Objekte. Jedes Objekt verfügt über eine Berechtigungsauflistung, die die Berechtigungen für dieses Objekt enthält. Einem Objekt können unterschiedliche Berechtigungssätze zugeordnet werden. Jeder Berechtigung in der Berechtigungsauflistung des Objekts ist eine einzige Rolle zugeordnet.  
  
## <a name="role-and-role-member-objects"></a>Rollen und Rollenelementobjekte  
 Eine Rolle ist ein enthaltendes Objekt für eine Auflistung von Benutzern (Elementen). Eine Rollendefinition begründet die Mitgliedschaft der Benutzer in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Da Berechtigungen mithilfe von Rollen zugewiesen werden, muss ein Benutzer ein Element einer Rolle sein, bevor er Zugriff auf Objekte erhält.  
  
 Ein <xref:Microsoft.AnalysisServices.Role>-Objekt besteht aus den Parametern Name, ID und Elemente. Elemente sind eine Auflistung von Zeichenfolgen. Jedes Element enthält den Benutzernamen im Format "domäne\benutzername". "Name" ist eine Zeichenfolge, die den Namen der Rolle enthält. "ID" ist eine Zeichenfolge, die den eindeutigen Bezeichner der Rolle enthält.  
  
### <a name="server-role"></a>Serverrolle  
 Die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Serverrolle definiert den administrativen Zugriff von Windows-Benutzern und -Gruppen auf eine Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Mitglieder dieser Rolle haben Zugriff auf alle [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenbanken und -Objekte in einer Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Mit dieser Rolle können die folgenden Aufgaben ausgeführt werden:  
  
-   Durchführen von Administratorfunktionen auf Serverebene mit SQL Server Management Studio oder [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], einschließlich dem Erstellen von Datenbanken und Festlegen von Eigenschaften auf Serverebene.  
  
-   Programmgesteuertes Ausführen administrativer Funktionen mit Analysis Management Objects (AMO).  
  
-   Verwalten von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenbankrollen.  
  
-   Starten von Ablaufverfolgungen (außer für die Verarbeitung von Ereignissen verwendeten Ablaufverfolgungen, die mit einer Datenbankrolle mit Verarbeitungszugriff ausgeführt werden können).  
  
 Jede Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verfügt über eine Serverrolle, mit der die Benutzer definiert werden, die diese Instanz verwalten können. Der Name und die ID dieser Rolle lauten Administratoren. Im Gegensatz zu Datenbankrollen kann die Serverrolle weder gelöscht werden, noch ist es möglich, der Serverrolle Berechtigungen hinzuzufügen bzw. aus ihr zu entfernen. Mit anderen Worten: Abhängig davon, ob der jeweilige Benutzer in der Serverrolle für diese Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]eingeschlossen ist oder nicht, ist ein Benutzer ein Administrator bzw. kein Administrator einer Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
### <a name="database-roles"></a>Datenbankrollen  
 Eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenbankrolle definiert den Benutzerzugriff auf die in einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenbank enthaltenen Objekte und Daten. Eine Datenbankrolle wird in einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenbank als separates Objekt erstellt und gilt nur für die Datenbank, in der diese Rolle erstellt wurde. Der Administrator, der ebenfalls die Berechtigungen innerhalb der Rolle definiert, schließt die Windows-Benutzer und -Gruppen in die Rolle ein.  
  
 Neben den Zugriffsberechtigungen auf die Daten und Objekte innerhalb der Datenbank ermöglichen die Berechtigungen einer Rolle den Mitgliedern den Zugriff auf die Datenbank sowie deren Verwaltung. Jeder Berechtigung wird mindestens ein Zugriffsrecht zugeordnet, mit dem wiederum die Berechtigung für eine präzisere Steuerung des Zugriffs auf ein bestimmtes Objekt der Datenbank gewährt wird.  
  
## <a name="permission-objects"></a>Berechtigungsobjekte  
 Berechtigungen sind mit einem Objekt (Cube, Dimension, sonstige) für eine bestimmte Rolle verbunden. Berechtigungen geben an, welche Vorgänge das Element dieser Rolle mit diesem Objekt ausführen kann.  
  
 Die <xref:Microsoft.AnalysisServices.Permission>-Klasse ist eine abstrakte Klasse. Deshalb müssen Sie die abgeleiteten Klassen verwenden, um Berechtigungen für die entsprechenden Objekte zu definieren. Für jedes Objekt wird eine von der Berechtigung abgeleitete Klasse definiert.  
  
|Objekt|Class|  
|------------|-----------|  
|<xref:Microsoft.AnalysisServices.Database>|<xref:Microsoft.AnalysisServices.DatabasePermission>|  
|<xref:Microsoft.AnalysisServices.DataSource>|<xref:Microsoft.AnalysisServices.DataSourcePermission>|  
|<xref:Microsoft.AnalysisServices.Dimension>|<xref:Microsoft.AnalysisServices.DimensionPermission>|  
|<xref:Microsoft.AnalysisServices.Cube>|<xref:Microsoft.AnalysisServices.CubePermission>|  
|<xref:Microsoft.AnalysisServices.MiningStructure>|<xref:Microsoft.AnalysisServices.MiningStructurePermission>|  
|<xref:Microsoft.AnalysisServices.MiningModel>|<xref:Microsoft.AnalysisServices.MiningModelPermission>|  
  
 Folgende Aktionen werden durch Berechtigungen aktiviert:  
  
|Aktion|Werte|Erklärung|  
|------------|------------|-----------------|  
|Verarbeiten|{`true`, `false`}<br /><br /> Standard=`false`|Wenn `true` festgelegt wird, können Elemente das Objekt sowie alle in dem Objekt enthaltenen Objekte verarbeiten.<br /><br /> Prozessberechtigungen gelten nicht für Miningmodelle. <xref:Microsoft.AnalysisServices.MiningModel>-Berechtigungen werden immer von <xref:Microsoft.AnalysisServices.MiningStructure> geerbt.|  
|ReadDefinition|{`None`, `Basic`, `Allowed`}<br /><br /> Standard=`None`|Gibt an, ob Elemente die mit dem Objekt verbundenen Datendefinitionen (ASSL) lesen können.<br /><br /> Wenn `Allowed` festgelegt wird, können Elemente die mit dem Objekt verbundenen ASSL lesen.<br /><br /> `Basic` und `Allowed` werden von in dem Objekt enthaltenen Objekten geerbt. `Allowed` überschreibt `Basic` und `None`.<br /><br /> `Allowed` ist für DISCOVER_XML_METADATA auf einem Objekt erforderlich `Basic` ist erforderlich, um verknüpfte Objekte und lokale Cubes zu erstellen.|  
|Leseberechtigung|{`None`, `Allowed`}<br /><br /> Standard=`None` (außer für DimensionPermission, hier gilt Standard=`Allowed`)|Gibt an, ob Elemente über Lesezugriff auf Schemarowsets und Dateninhalt verfügen.<br /><br /> `Allowed` erteilt Lesezugriff auf eine Datenbank, die eine Datenbank ermitteln werden kann.<br /><br /> `Allowed` für einen Cube ermöglicht Lesezugriff auf Schemarowsets und Zugriff auf Cubeinhalte (wenn nicht eingeschränkt durch <xref:Microsoft.AnalysisServices.CellPermission> und <xref:Microsoft.AnalysisServices.CubeDimensionPermission>).<br /><br /> `Allowed` für eine Dimension gewährt diese Leseberechtigung für alle Attributen in der Dimension (wenn nicht eingeschränkt durch <xref:Microsoft.AnalysisServices.CubeDimensionPermission>). Die Leseberechtigung wird nur für die statische Vererbung an die <xref:Microsoft.AnalysisServices.CubeDimensionPermission> verwendet. Wenn `None` für eine Dimension festgelegt wird, wird die Dimension verborgen und Standardelemente erhalten nur Zugriff auf aggregierbare Attribute. Wenn die Dimension ein nicht aggregierbares Attribut enthält, wird ein Fehler ausgegeben.<br /><br /> Wenn `Allowed` für <xref:Microsoft.AnalysisServices.MiningModelPermission> festgelegt wird, werden Berechtigungen für das Anzeigen von Objekten in Schemarowsets und die Ausführung von vorhergesagten Joins erteilt.<br /><br /> **NoteAllowed** ist erforderlich, um das Lesen oder Schreiben auf ein beliebiges Objekt in der Datenbank.|  
|Schreiben|{`None`, `Allowed`}<br /><br /> Standard=`None`|Gibt an, ob Elemente über Schreibzugriff auf Daten des übergeordneten Objekts verfügen.<br /><br /> Der Zugriff gilt für <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.Cube> und <xref:Microsoft.AnalysisServices.MiningModel>-Unterklassen. Er gilt nicht für Datenbank-<xref:Microsoft.AnalysisServices.MiningStructure>-Unterklassen, die einen Überprüfungsfehler generieren.<br /><br /> Wenn `Allowed` für <xref:Microsoft.AnalysisServices.Dimension> festgelegt wird, werden Schreibberechtigungen für alle Attribute in der Dimension gewährt.<br /><br /> Wenn `Allowed` für <xref:Microsoft.AnalysisServices.Cube> festgelegt wird, werden Schreibberechtigungen für die Zellen des Cubes gewährt, für deren Partitionen der Typ=writeback definiert wurde.<br /><br /> Wenn `Allowed` für <xref:Microsoft.AnalysisServices.MiningModel> festgelegt wird, werden Berechtigungen für die Änderung des Modellinhalts gewährt.<br /><br /> Wenn `Allowed` für <xref:Microsoft.AnalysisServices.MiningStructure> festgelegt wird, besitzt dies in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] keine bestimmte Bedeutung. **Hinweis**:  Write kann nicht festgelegt werden, um `Allowed` , wenn Lesevorgänge auch festgelegt ist `Allowed`|  
|Verwalten von **beachten:**  Nur in Datenbankberechtigungen|{`true`, `false`}<br /><br /> Standard=`false`|Gibt an, ob Elemente eine Datenbank verwalten können.<br /><br /> `true` gewährt Elementen Zugriff auf alle Objekte in einer Datenbank.<br /><br /> Ein Element kann über Verwaltungsberechtigungen für eine bestimmte Datenbank verfügen, jedoch nicht für andere.|  
  
## <a name="see-also"></a>Siehe auch  
 [Autorisieren des Zugriffs auf Objekte und Vorgänge &#40;Analysis Services&#41;](../authorizing-access-to-objects-and-operations-analysis-services.md)  
  
  
