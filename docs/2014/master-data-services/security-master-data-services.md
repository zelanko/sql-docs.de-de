---
title: Sicherheit (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56bc41ea-de28-4184-aa7e-99111ae55af5
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: bbb9817ac5e9ef4c779dd8a283223622b28c9119
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060738"
---
# <a name="security-master-data-services"></a>Sicherheit (Master Data Services)
  Verwenden Sie die Sicherheitseinstellungen in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], um dafür zu sorgen, dass Benutzer auf die speziellen Masterdaten zugreifen können, die sie für ihre Arbeit benötigen, nicht jedoch auf Daten, für die sie nicht zuständig sind.  
  
 Mithilfe der Sicherheit können Sie auch einem Administrator für ein bestimmtes Modell und einen Funktionsbereich bestimmen. Sie können es z. B. jemandem ermöglichen, Versionen des Kundenmodells zu erstellen oder Sicherheitsberechtigungen festzulegen.  
  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Sicherheit basiert auf lokalen oder Active Directory-Domänenbenutzern und -gruppen. Beim Bestimmen der Daten, auf die ein Benutzer zugreifen kann, können Sie mithilfe der MDS-Sicherheit eine präzise Detailebene verwenden. Aufgrund der hohen Detailgenauigkeit kann die Sicherheit leicht kompliziert werden. Gehen Sie deshalb bei der Verwendung sich überschneidender Benutzer und Gruppen vorsichtig vor. Weitere Informationen finden Sie unter [Überlappende Benutzer- und Gruppenberechtigungen &#40;Master Data Services&#41;](overlapping-user-and-group-permissions-master-data-services.md).  
  
 Sie können den Sicherheitszugriff im Funktionsbereich **Benutzer- und Gruppenberechtigungen** der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung oder mit dem Webdienst zuweisen.  
  
## <a name="types-of-users"></a>Arten von Benutzern  
 Es gibt zwei Arten von Benutzern in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]:  
  
-   Benutzer, die auf Daten in den Funktionsbereich **Explorer** zugreifen.  
  
-   Benutzer, die die Fähigkeit haben, administrative Tasks in anderen Bereichen als **Explorer**auszuführen. Diese Benutzer heißen [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
## <a name="how-to-set-security"></a>Festlegen der Sicherheit  
 Sie müssen Folgendes zuweisen, um einem Benutzer oder einer Gruppe die Berechtigung für den Zugriff zu erteilen:  
  
-   [Zugriff auf Funktionsbereiche](../../2014/master-data-services/functional-area-permissions-master-data-services.md). Damit wird bestimmt, auf welche der fünf Funktionsbereiche der Benutzeroberfläche ein Benutzer zugreifen kann.  
  
-   [Modellobjektberechtigungen](../../2014/master-data-services/model-object-permissions-master-data-services.md), welche die Attribute, die ein Benutzer zugreifen kann und der Zugriffstyp (Lesen oder aktualisieren), die der Benutzer für diese Attribute besitzt.  
  
-   Optional, [hierarchieelementberechtigungen](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md), welche bestimmen die Elemente, die ein Benutzer zugreifen kann und Zugriffstyp (Lesen oder aktualisieren) der Benutzer hat auf diesen Member.  
  
 Wenn Sie Attributen und Elementen Berechtigungen zuweisen, überschneiden sich die Berechtigungen. Dabei bestimmen Regeln, welche Berechtigung Vorrang hat. Weitere Informationen finden Sie unter [How Permissions Are Determined &#40;Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md).  
  
 Zum Implementieren der Sicherheit auf Datensatzebene erstellen Sie eine Hierarchie für eine Entität, und weisen Sie Elementen der Hierarchie Benutzerberechtigungen zu. Elemente sind Datensätze.  Berechtigungen für Hierarchieelemente sollten nur verwendet werden, wenn ein Benutzer beschränkten Zugriff auf bestimmte Elemente erhalten soll.  
  
 Die folgende Abbildung zeigt die abgeleitete Hierarchie für die Stilentität und Berechtigungen für Stilelemente für einen ausgewählten Benutzer. Aktualisierungsberechtigungen sind den Elementen „M {Männer}“ und „U {Unisex}“ zugewiesen, und Leseberechtigungen dem Element „Styles für Frauen“. Dies bedeutet, dass der Benutzer die Datensätze für die Männer- und Unisexprodukte aktualisieren und die Produkte im Bereich „Styles für Frauen“ nur lesen kann.  
  
 ![Formatieren Sie die abgeleitete Hierarchie und Member Berechtigungen](../../2014/master-data-services/media/style-derived-hierarchy-mds.png "Stil abgeleitete Hierarchie auch Elementberechtigungen")  
  
 Informationen zum Erstellen einer Hierarchie finden Sie unter [Erstellen einer expliziten Hierarchie &#40;Master Data Services&#41; ](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) und [erstellen Sie eine abgeleitete Hierarchie &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md).  
  
 Informationen zu Elementen Berechtigungen zuweisen, finden Sie unter [Hierarchieelementberechtigungen zuweisen &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
## <a name="security-in-the-add-in-for-excel"></a>Sicherheit im Add-In für Excel  
 Die in der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung festgelegten Sicherheitseinstellungen werden auch auf das [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]angewendet. Benutzer können nur die Daten anzeigen und verarbeiten, für die sie über Berechtigungen verfügen. Administratoren können administrative Tasks ausführen.  
  
 Es muss allerdings berücksichtigt werden, dass alle in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] festgelegten Sicherheitseinstellungen in Excel erst nach 20 Minuten wirksam werden. Das Intervall wird durch die Einstellung *MdsMaximumUserInformationCacheInterval* in der Datei web.config definiert. Um das Intervall zu ändern, können Sie die Einstellung ändern und IIS neu starten.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Erstellen Sie einen Benutzer, der über die Vollberechtigung für ein Modell verfügt.|[Erstellen eines Modelladministrators &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-administrator-master-data-services.md)|  
|Fügen Sie [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]eine Active Directory-Gruppe hinzu; dies ist der erste Schritt darin, einer Gruppe die Berechtigung für den Zugriff auf Daten in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Webanwendung zu erteilen.|[Hinzufügen einer Gruppe &#40;Master Data Services&#41;](../../2014/master-data-services/add-a-group-master-data-services.md)|  
|Weisen Sie die Berechtigung einem Funktionsbereich der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Webanwendung zu.|[Zuweisen von Berechtigungen für Funktionsbereiche &#40;Master Data Services&#41;](../../2014/master-data-services/assign-functional-area-permissions-master-data-services.md)|  
|Weisen Sie die Berechtigung Attributwerten zu, indem Sie die Berechtigung zum Modellieren von Objekten zuweisen.|[Zuweisen von Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)|  
|Weisen Sie die Berechtigung Elementwerten zu, indem Sie die Berechtigung Hierarchieknoten zuweisen.|[Zuweisen von Berechtigungen für Hierarchieelemente &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Administratoren &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)   
 [Benutzer und Gruppen &#40;Master Data Services&#41;](../../2014/master-data-services/users-and-groups-master-data-services.md)   
 [Berechtigungen für Funktionsbereiche &#40;Master Data Services&#41;](../../2014/master-data-services/functional-area-permissions-master-data-services.md)   
 [Modellobjektberechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Berechtigungen für Hierarchieelemente &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Wie Berechtigungen bestimmt &#40;Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  