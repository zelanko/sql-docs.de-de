---
title: Rollenzuweisungen | Microsoft-Dokumentation
ms.date: 05/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- users [Reporting Services]
- roles [Reporting Services]
- role-based security [Reporting Services], role assignments
- groups [Reporting Services]
- security [Reporting Services], role assignments
ms.assetid: 600e112c-1897-48a6-93c0-6e9f3f12dc01
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a6fe3c0cd82d8ee8b92948d76d4f7cdb5fa4cf73
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65570568"
---
# <a name="role-assignments"></a>Rollenzuweisungen

In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]bestimmen *Rollenzuweisungen* den Zugriff auf gespeicherte Elemente und auf den Berichtsserver selbst. Eine Rollenzuweisung besteht aus den folgenden Teilen:  
  
- Einem sicherungsfähigen Element, für das Sie den Zugriff steuern möchten. Beispiele für sicherungsfähige Elemente sind Ordner, Berichte und Ressourcen.  
  
- Einem Benutzer- oder Gruppenkonto, das mit der Windows-Sicherheit oder einem sonstigen Authentifizierungsmechanismus authentifiziert werden kann.  
  
- Rollendefinitionen definieren zulässige Aufgaben und enthalten folgende Komponenten:
  - **Browser**
  - **Inhalts-Manager**
  - **Meine Berichte**
  - **Verleger**
  - **Report Builder (Berichts-Generator)**
  - **Systemadministrator**
  - **Systembenutzer**

 Rollenzuweisungen werden innerhalb der Ordnerhierarchie vererbt und automatisch von folgenden enthaltenen Komponenten geerbt:

- **Berichte**
- **Freigegebene Datenquellen**
- **Ressourcen**
- **Unterordner**

Sie können die geerbte Sicherheit überschreiben, indem Sie Rollenzuweisungen für einzelne Elemente definieren. Alle Teile der Ordnerhierarchie müssen durch mindestens eine Rollenzuweisung gesichert werden. Es ist nicht möglich, ein nicht gesichertes Element zu erstellen oder Einstellungen derart zu ändern, dass dadurch ein nicht gesichertes Element entsteht.  
  
 Das folgende Diagramm veranschaulicht eine Rollenzuweisung, die einer Gruppe und einem bestimmten Benutzer die **Verleger** -Rolle für den Ordner B zuordnet.  
  
 ![Rollenzuweisungsdiagramm](../../reporting-services/security/media/report-securityarch.gif "Role assignments diagram")  
Rollenzuweisungsdiagramm  
  
## <a name="system-level-and-item-level-role-assignments"></a>Rollenzuweisungen auf System- und Elementebene

 Die rollenbasierte Sicherheit in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] wird anhand der folgenden Ebenen organisiert:

- Rollenzuweisung auf Elementebene steuern den Zugriff auf Elemente in der Ordnerhierarchie des Berichtsservers, z B.:
  - Berichte
  - Ordner
  - Berichtsmodelle
  - Freigegebene Datenquellen
  - Andere Ressourcen

- Rollenzuweisungen auf Elementebene werden definiert, wenn eine Rollenzuweisung für ein bestimmtes Element oder den Stammordner erstellt wird.

- Systemrollenzuweisungen autorisieren Vorgänge, die auf dem gesamten Server ausgeführt werden. Beispielsweise ist die Fähigkeit, Aufträge zu verwalten, ein Vorgang auf Systemebene. Eine Systemrollenzuweisung entspricht nicht einem Systemadministrator. Mit der Rollenzuweisung werden keine erweiterten Berechtigungen übertragen, die die vollständige Steuerung eines Berichtsservers ermöglichen.

Eine Systemrollenzuweisung gewährt nicht den Zugriff auf Elemente in der Ordnerhierarchie. System- und Elementsicherheit schließen sich gegenseitig aus. In bestimmten Fällen kann es notwendig sein, Rollenzuweisungen sowohl auf System- als auch auf Elementebene zu erstellen, um den Zugriff für einen Benutzer oder eine Gruppe in ausreichendem Maße zu ermöglichen.

## <a name="users-and-groups-in-role-assignments"></a>Benutzer und Gruppen in Rollenzuweisungen

 Bei den Benutzer- oder Gruppenkonten, die Sie in Rollenzuweisungen angeben, handelt es sich um Domänenkonten. Der Berichtsserver erstellt oder verwaltet zwar keine Benutzer und Gruppen aus einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Domäne (oder einem anderen Sicherheitsmodell, falls Sie eine benutzerdefinierte Sicherheitserweiterung verwenden), aber er verweist auf diese.

Rollenzuweisungen für ein bestimmtes Element dürfen nicht für dasselbe Benutzer- oder Gruppenkonto angegeben werden. Falls ein Benutzerkonto auch Mitglied eines Gruppenkontos ist und für beide Rollenzuweisungen vorhanden sind, stehen die Aufgaben der beiden Rollenzuweisungen dem Benutzer zur Verfügung.

Wenn Sie einer Gruppe, die bereits über eine Rollenzuweisung verfügt, einen Benutzer hinzufügen, müssen Sie IIS zurücksetzen, damit die neue Rollenzuweisung wirksam wird.

## <a name="predefined-role-assignments"></a>Vordefinierte Rollenzuweisungen

 Standardmäßig werden vordefinierte Rollenzuweisungen implementiert, die lokalen Administratoren die Verwaltung des Berichtsservers ermöglichen. Sie können weitere Rollenzuweisungen hinzufügen, um anderen Benutzern den Zugriff zu gewähren.

 Weitere Informationen zu den vordefinierten Rollenzuweisungen, die Standardsicherheit bereitstellen, finden Sie unter [Vordefinierte Rollen](../../reporting-services/security/role-definitions-predefined-roles.md).  

## <a name="see-also"></a>Weitere Informationen

 [Erstellen, Löschen oder Ändern einer Rolle &#40;Management Studio&#41;](../../reporting-services/security/role-definitions-create-delete-or-modify.md)

 [Rollenzuweisungen: Ändern oder Löschen](../../reporting-services/security/role-assignments-modify-or-delete.md)

 [Festlegen von Berechtigungen für Berichtsserverelemente auf einer SharePoint-Website &#40;Reporting Services im integrierten SharePoint-Modus&#41;](../../reporting-services/security/set-permissions-for-report-server-items-on-a-sharepoint-site.md)

 [Granting Permissions on a Native Mode Report Server (Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus)](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
