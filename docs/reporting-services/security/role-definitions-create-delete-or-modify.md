---
title: Erstellen, Löschen oder Ändern einer Rolle (Management Studio) | Microsoft-Dokumentation
ms.date: 05/07/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
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
ms.openlocfilehash: f079b7b16f485b92c60952d082281a1dba52d024
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "65570544"
---
# <a name="role-definitions---create-delete-or-modify"></a>Rollendefinitionen: Erstellen, Löschen oder Ändern

Reporting Services stellt vordefinierte Rollen bereit, die Zugriffsebenen für den Berichtsserver definieren. Jedem Benutzer oder jeder Gruppe, der bzw. die auf den Berichtsserver zugreifen müssen, wird eine Rolle mit zulässigen Aufgaben zugewiesen. Rollen werden für den gesamten Berichtsserver definiert. Achten Sie bei der Definition und Verwendung einer Rolle für alle Bereiche des Berichtsservers auf Konsistenz.

Mit [!INCLUDE[SQL Server Management Studio](../../includes/ssmanstudiofull-md.md)] können Sie Rollen erstellen, ändern oder löschen. Es können nur Rollen gelöscht werden, die nicht verwendet werden.

 Verwenden Sie das SSRS-Webportal, um Benutzer und Gruppen den von Ihnen erstellten Rollen zuzuweisen. Weitere Informationen finden Sie unter [Gewähren von Benutzerzugriff auf einen Berichtsserver](../../reporting-services/security/grant-user-access-to-a-report-server.md).

> [!NOTE]  
>Wenn ein Berichtsserver für die Ausführung im integrierten SharePoint-Modus konfiguriert wird und Sie eine Verbindung zur SharePoint-Website hergestellt haben, in die der Berichtsserver integriert ist, können Sie die Berechtigungsebenen zur Steuerung des Zugriffs auf Inhalt und Vorgänge des Berichtsservers anzeigen lassen und ändern.

## <a name="to-create-a-role-definition"></a>So erstellen Sie eine Rollendefinition

1. Erweitern Sie im Objekt-Explorer einen Berichtsserverknoten.

2. Erweitern Sie den Ordner Sicherheit.

3. Falls Sie eine Rollendefinition auf Elementebene erstellen, klicken Sie mit der rechten Maustaste auf **Rollen** > **Neue Rolle**.

    Falls Sie hingegen eine Rollendefinition auf Systemebene erstellen, klicken Sie mit der rechten Maustaste auf **Systemrollen** > **Neue Systemrolle**.

4. Geben Sie einen eindeutigen Namen für die Rolle ein. Der Name muss mindestens ein Zeichen enthalten. Es dürfen auch Leerzeichen und bestimmte Sonderzeichen enthalten sein, jedoch nicht die folgenden Zeichen: `[; : \ / @ & = + , $ / * < > | "]`.

5. Geben Sie optional eine Beschreibung ein. In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] wird diese Beschreibung nur auf dieser Seite angezeigt. Benutzern, denen das Element im Webportal angezeigt wird, können die Beschreibung in diesem Tool anzeigen.

6. Wählen Sie die Aufgaben aus, die Mitglieder dieser Rolle ausführen können.

7. Klicken Sie auf **OK**.

### <a name="to-delete-or-modify-a-role-definition"></a>So löschen oder ändern Sie eine Rollendefinition  

1. Erweitern Sie im Objekt-Explorer einen Berichtsserverknoten.

2. Erweitern Sie den Ordner Sicherheit.

3. Erweitern Sie den Ordner „Rollen“, um eine Rollendefinition auf Elementebene zu löschen oder zu ändern, und führen Sie anschließend eine der folgenden Aktionen aus:

    1. Klicken Sie zum Löschen einer Rollendefinition mit der rechten Maustaste auf das Element, und klicken Sie anschließend auf **Löschen**. Das Dialogfeld **Katalogelemente löschen** wird angezeigt. Klicken Sie auf **OK**, um die Rolle zu löschen.
  
    2. Klicken Sie zum Ändern einer Rollendefinition mit der rechten Maustaste auf das Element, und klicken Sie anschließend auf **Eigenschaften**. Die Seite Allgemein im Dialogfeld **Benutzerrolleneigenschaften** wird angezeigt.

         Wählen Sie die Aufgaben aus, die Mitglieder dieser Rolle ausführen können, und klicken Sie dann auf **OK**.
  
4. Erweitern Sie den Ordner **Systemrollen** , um eine Rollendefinition auf Systemebene zu löschen oder zu ändern. Führen Sie eine der folgenden Aktionen aus:

- Klicken Sie zum Löschen einer Rollendefinition auf Systemebene mit der rechten Maustaste auf das Element, und klicken Sie anschließend auf **Löschen**. Das Dialogfeld **Katalogelemente löschen** wird angezeigt. Klicken Sie auf **OK**, um die Rolle zu löschen.

- Klicken Sie zum Ändern einer Rollendefinition auf Systemebene mit der rechten Maustaste auf das Element, und klicken Sie anschließend auf **Eigenschaften**. Die Seite Allgemein im Dialogfeld **Systemrolleneigenschaften** wird angezeigt. Wählen Sie die Aufgaben aus, die Mitglieder dieser Rolle ausführen können. Klicken Sie dann auf **OK**, um die Änderungen zu übernehmen.

## <a name="see-also"></a>Weitere Informationen

 [Connect to a Report Server in Management Studio (Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio)](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)  
 [Erstellen und Verwalten von Rollenzuweisungen](../../reporting-services/security/create-and-manage-role-assignments.md)  
 [Reporting Services in SQL Server Management Studio (SSRS)](../../reporting-services/tools/reporting-services-in-sql-server-management-studio-ssrs.md)
