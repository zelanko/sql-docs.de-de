---
title: Erstellen, Löschen oder Ändern einer Rolle (Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- deleting roles
- removing roles
- roles [Reporting Services], definitions
- modifying roles
- roles [Reporting Services], deleting
- roles [Reporting Services], modifying
ms.assetid: 3d1d56e6-a283-44a7-8417-36cb4d2c74d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 066c69298126cbc635d388d75659b98dcff95917
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66101809"
---
# <a name="create-delete-or-modify-a-role-management-studio"></a>Erstellen, Löschen oder Ändern einer Rolle (Management Studio)
  Reporting Services stellt vordefinierte Rollen, die eine Zugriffsebene für einen Berichtsserver definieren, zur Verfügung. Jeder Benutzer bzw. jede Benutzergruppe, die auf den Berichtsserver zugreifen möchte, benötigt hierfür eine Rolle, mit der die ausführbaren Aufgaben beschrieben werden. Rollen werden für den gesamten Berichtsserver definiert. Sie können eine Rollendefinition nicht für bestimmte Bereiche des Berichtsservers abändern oder angeben, dass eine Rolle je nach Zusammenhängen unterschiedlich verwendet werden soll.  
  
 Verwenden Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], um Rollen zu erstellen, zu ändern oder zu löschen. Sie können nur Rollen löschen, die nicht verwendet werden.  
  
 Sie können die Zuweisungen von Benutzern und Gruppen zu von Ihnen erstellten Rollen mit dem Berichts-Manager vornehmen: Weitere Informationen finden Sie unter [Gewähren von Benutzer Zugriff auf einen Berichts Server &#40;Berichts-Manager&#41;](grant-user-access-to-a-report-server.md).  
  
> [!NOTE]  
>  Wenn ein Berichtsserver für die Ausführung im integrierten SharePoint-Modus konfiguriert wird und Sie eine Verbindung zur SharePoint-Website hergestellt haben, in die der Berichtsserver integriert ist, können Sie die Berechtigungsebenen zur Steuerung des Zugriffs auf Inhalt und Vorgänge des Berichtsservers anzeigen lassen und ändern.  
  
### <a name="to-create-a-role-definition"></a>So erstellen Sie eine Rollendefinition  
  
1.  Erweitern Sie im Objekt-Explorer einen Berichtsserverknoten.  
  
2.  Erweitern Sie den Ordner Sicherheit.  
  
3.  Falls Sie eine Rollendefinition auf Elementebene erstellen, klicken Sie mit der rechten Maustaste auf **Rollen**, und zeigen Sie anschließend auf **Neue Rolle**.  
  
     Falls Sie eine Rollendefinition auf Systemebene erstellen, können Sie mit der rechten Maustaste auf **Systemrollen**klicken und anschließend auf **Neue Systemrolle**zeigen.  
  
4.  Geben Sie einen eindeutigen Namen für die Rolle ein. Der Name muss mindestens ein Zeichen enthalten. Er kann auch Leerzeichen und Sonderzeichen enthalten, er darf jedoch folgende Zeichen nicht enthalten: ; ? : \@ & = +, $/* \< > | "oder/.  
  
5.  Geben Sie optional eine Beschreibung ein. In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] wird diese Beschreibung nur auf dieser Seite angezeigt. Benutzer, die dieses Element im Berichts-Manager anzeigen, können diese Beschreibung in diesem Tool anzeigen.  
  
6.  Wählen Sie die Aufgaben aus, die Mitglieder dieser Rolle ausführen können.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-or-modify-a-role-definition"></a>So löschen oder ändern Sie eine Rollendefinition  
  
1.  Erweitern Sie im Objekt-Explorer einen Berichtsserverknoten.  
  
2.  Erweitern Sie den Ordner Sicherheit.  
  
3.  Erweitern Sie den Ordner Rollen, um eine Rollendefinition auf Elementebene zu löschen oder zu ändern. Führen Sie einen der folgenden Schritte aus:  
  
    1.  Klicken Sie zum Löschen einer Rollendefinition mit der rechten Maustaste auf das Element, und klicken Sie anschließend auf **Löschen**. Das Dialogfeld **Objekt löschen** wird angezeigt. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    2.  Klicken Sie zum Ändern einer Rollendefinition mit der rechten Maustaste auf das Element, und klicken Sie anschließend auf **Eigenschaften**. Die Seite Allgemein im Dialogfeld **Benutzerrolleneigenschaften** wird angezeigt.  
  
         Wählen Sie die Aufgaben aus, die Mitglieder dieser Rolle ausführen können, und klicken Sie dann auf **OK**.  
  
4.  Erweitern Sie den Ordner **Systemrollen** , um eine Rollendefinition auf Systemebene zu löschen oder zu ändern. Führen Sie einen der folgenden Schritte aus:  
  
    1.  Klicken Sie zum Löschen einer Systemrollendefinition auf Systemebene mit der rechten Maustaste auf das Element, und klicken Sie anschließend auf **Löschen**. Das Dialogfeld **Objekt löschen** wird angezeigt. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    2.  Klicken Sie zum Ändern einer Systemrollendefinition auf Systemebene mit der rechten Maustaste auf das Element, und klicken Sie anschließend auf **Eigenschaften**. Die Seite Allgemein im Dialogfeld **Systemrolleneigenschaften** wird angezeigt.  
  
         Wählen Sie die Aufgaben aus, die Mitglieder dieser Rolle ausführen können, und klicken Sie dann auf **OK** , um die Änderungen zu übernehmen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](../tools/connect-to-a-report-server-in-management-studio.md)   
 (Create-and-manage-role-assignments.MD)   
 [Reporting Services in SQL Server Management Studio &#40;SSRS&#41;](../tools/reporting-services-in-sql-server-management-studio-ssrs.md)  
  
  
