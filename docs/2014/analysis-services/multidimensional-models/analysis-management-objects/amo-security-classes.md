---
title: AMO-Sicherheitsklassen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- Analysis Management Objects, security
- security [AMO]
- AMO, security
ms.assetid: e3d5012a-8121-40de-9244-1fc824228693
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f8ce9352890b4e1113278148a92c4802074f0d25
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48047830"
---
# <a name="amo-security-classes"></a>AMO-Sicherheitsklassen
  
 Die folgende Abbildung zeigt die Beziehung der in diesem Thema erläuterten Klassen.  
  
 ![AMO-Sicherheitsklassen, die in diesem Thema behandelten](../../../analysis-services/dev-guide/media/amo-securityclasses.gif "AMO-Sicherheitsklassen in diesem Thema behandelt.")  
  
##  <a name="RolesMembers"></a> Rollen und RoleMember-Objekte  
 Ein <xref:Microsoft.AnalysisServices.Role>-Objekt wird erstellt, indem es der Rollenauflistung der Datenbank hinzugefügt und das <xref:Microsoft.AnalysisServices.Role>-Objekt auf dem Server mithilfe der Update-Methode aktualisiert wird. Ein <xref:Microsoft.AnalysisServices.Role> Objekt muss aktualisiert werden, bevor sie verwendet werden kann.  
  
 So entfernen Sie eine <xref:Microsoft.AnalysisServices.Role> Objekt muss gelöscht werden, indem Sie mit der Drop-Methode, der die <xref:Microsoft.AnalysisServices.Role> Objekt. Die Remove-Methode aus der Rollenauflistung verhindert lediglich die Anzeige der Rolle in Ihrer Anwendung, Sie entfernt jedoch die Rolle nicht vom Server. Ein <xref:Microsoft.AnalysisServices.Role>-Objekt kann nicht gelöscht werden, wenn diesem Berechtigungen zugeordnet sind.  
  
 Ein <xref:Microsoft.AnalysisServices.RoleMember> objekterstellung wird von der Members-Auflistung der Rolle einen Benutzer hinzufügen und Aktualisieren der <xref:Microsoft.AnalysisServices.Role> -Objekt auf dem Server mithilfe der Update-Methode. Nur Serveradministratoren und Datenbankadministratoren sind berechtigt, Rollen zu erstellen. Ein <xref:Microsoft.AnalysisServices.Role> Objekt auf dem Server aktualisiert werden muss, bevor eines seiner Member ist zulässig, die Objekte verwenden, die der Benutzer Berechtigungen erhalten hat.  
  
 Um ein <xref:Microsoft.AnalysisServices.RoleMember>-Objekt zu entfernen, muss es mithilfe der Remove-Methode der Auflistung aus der Auflistung entfernt werden, und anschließend muss die Rolle mithilfe der Update-Methode aktualisiert werden.  
  
 Weitere Informationen zu den Methoden und Eigenschaften für diese Objekte zur Verfügung stehen, finden Sie unter <xref:Microsoft.AnalysisServices.Role> und <xref:Microsoft.AnalysisServices.RoleMember> in die <xref:Microsoft.AnalysisServices>.  
  
##  <a name="Permissions"></a> Berechtigungsobjekte  
 Ein <xref:Microsoft.AnalysisServices.Permission> Objekt wird erstellt, indem es der berechtigungsauflistung des Objekts hinzugefügt und aktualisiert die <xref:Microsoft.AnalysisServices.Permission> -Objekt auf dem Server mithilfe der Update-Methode.  
  
 So entfernen Sie eine <xref:Microsoft.AnalysisServices.Permission> Objekt, mit der Drop-Methode des Objekts gelöscht werden muss. Die Remove-Methode aus der Berechtigungsauflistung verhindert lediglich die Anzeige der Berechtigungen in Ihrer Anwendung, Sie entfernt jedoch das <xref:Microsoft.AnalysisServices.Permission>-Objekt nicht vom Server. Eine Rolle kann nicht gelöscht werden, wenn ihr eine Berechtigung zugeordnet ist.  
  
 Weitere Informationen zu den Methoden und Eigenschaften zur Verfügung stehen, finden Sie unter <xref:Microsoft.AnalysisServices.Permission> in <xref:Microsoft.AnalysisServices>.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.AnalysisServices>   
 [Programmieren von AMO-Sicherheitsobjekten](programming-amo-security-objects.md)   
 [Berechtigungen und Zugriffsrechte &#40;Analysis Services – mehrdimensionale Daten&#41;](https://msdn.microsoft.com/library/ms174786(v=sql.120).aspx)   
 [Einführung in AMO-Klassen](amo-classes-introduction.md)   
 [Logische Architektur &#40;Analysis Services – mehrdimensionale Daten&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Datenbankobjekte &#40;Analysis Services – mehrdimensionale Daten&#41;](../olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
