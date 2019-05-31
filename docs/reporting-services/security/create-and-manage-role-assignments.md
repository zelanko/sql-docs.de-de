---
title: Erstellen und Verwalten von Rollenzuweisungen | Microsoft-Dokumentation
ms.date: 05/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- roles [Reporting Services], assignments
- security [Reporting Services], role assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 086d0987-b43c-4834-8372-e08fb4b432f8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 863904e2d82fc97045305dd2430241a91e333f11
ms.sourcegitcommit: 553ecea0427e4d2118ea1ee810f4a73275b40741
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65619602"
---
# <a name="create-and-manage-role-assignments"></a>Erstellen und Verwalten von Rollenzuweisungen

Bei einer *Rollenzuweisung* handelt es sich um eine Sicherheitsrichtlinie, über die die Berechtigungen eines Benutzers oder einer Gruppe festgelegt werden. Anhand von Berechtigungen wird entschieden, ob der Benutzer oder die Gruppe auf ein bestimmtes Berichtsserverelement zugreifen oder eine Aufgabe durchführen kann. Eine Rollenzuweisung besteht aus einem einzelnen Benutzer- oder Gruppenkontonamen und mindestens einer Rollendefinition.

Rollenzuweisungen gelten auf *Elementebene* oder *Systemebene*.

- Rollenzuweisungen auf Elementebene werden im Kontext eines bestimmten Elements oder Branches in der Ordnerhierarchie des Berichtsservers erstellt. Sie navigieren zu einem bestimmten Ordner oder Element, um eine Rollenzuweisung dafür zu erstellen.

- Mit Rollenzuweisungen auf Systemebene können ausgewählte Benutzer Aufgaben ausführen, die den gesamten Berichtsserverstandort betreffen. Zu diesen Aufgaben zählt Folgendes:
  - Erstellen von freigegebenen Zeitplänen
  - Verwalten von Aufträgen
  - Verarbeiten von Berichten
  - Festlegen von Eigenschaften

Die Sicherheit auf Systemebene betrifft den Zugriff auf Elemente in der Ordnerhierarchie des Berichtsservers nicht.

## <a name="creating-an-item-level-role-assignment"></a>So erstellen Sie eine Rollenzuweisung auf Elementebene

Sie können für jedes Benutzer- oder Gruppenkonto, das auf den Berichtsserver zugreifen können muss, eine eigene Rollenzuweisung erstellen. Befindet sich das Konto nicht in der Domäne, in der der Berichtsserver enthalten ist, geben Sie den Domänennamen an. Nachdem Sie ein Konto angegeben haben, können Sie eine oder mehrere Rollendefinitionen auswählen. Die Rollendefinitionen sind kumulativ. Die kombinierten Aufgaben aus allen Definitionen werden in der Zuweisung für einen bestimmten Benutzer oder eine bestimmte Gruppe unterstützt.

Wählen Sie ein Element aus, das weit oben in der Ordnerhierarchie angeordnet ist (z. B. den Stammknoten „Stamm“). Anschließend können Sie Rollenzuweisungen erstellen, um bestimmte Bereiche der Ordnerhierarchie zu sperren.

Sie müssen Mitglied der lokalen Gruppe Administratoren auf dem Berichtsserver-Computer sein, um eine Rollenzuweisung erstellen zu können. Sie können diese Aufgabe delegieren, indem Sie andere Benutzer der Rolle **Inhalts-Manager** zuweisen.

Zum Erstellen oder Verwalten von rollenzuweisungen oder Weitere Informationen finden Sie unter [Gewähren von Benutzerzugriff auf einen Berichtsserver](../../reporting-services/security/grant-user-access-to-a-report-server.md)
  
## <a name="creating-a-system-level-role-assignment"></a>Erstellen einer Rollenzuweisung auf Systemebene

Rollenzuweisungen auf System- und Elementebene ergänzen sich. Sie müssen allen Benutzern oder Gruppen, die über eine Rollenzuweisung auf Elementebene verfügen, auch eine Rolle auf Systemebene zuweisen.

Rollenzuweisungen auf Systemebene umfassen eine Vielzahl von Berechtigungen, jedoch keine Berechtigungen, die Teil einer Rollenzuweisung auf Elementebene sind.

Im Gegensatz zu den Systemberechtigungen auf einem Computer umfassen die Systemrollen in Berichtsservern keine übergreifenden Berechtigungen, die alle möglichen Aufgaben umfassen. Bei Rollenzuweisungen auf Systemebene handelt es sich einfach um eine Menge von Tasks, die die Berichtsserversite betreffen. Anhand von Systemrollenzuweisungen wird bestimmt, ob Benutzer Anwendungseigenschaften (beispielsweise als Bild oder Titel der Homepage) anzeigen, freigegebene Zeitpläne anzeigen oder verwalten oder den Berichts-Generator ausführen können.

Erstellen und Verwalten von rollenzuweisung auf Systemebene oder für Weitere Informationen finden Sie unter [Gewähren von Benutzerzugriff auf einen Berichtsserver](../../reporting-services/security/grant-user-access-to-a-report-server.md) und [vordefinierte Rollen](../../reporting-services/security/role-definitions-predefined-roles.md).  

## <a name="modifying-a-role-assignment"></a>Ändern einer Rollenzuweisung

Eine Rollenzuweisung kann jederzeit geändert werden. Die Änderungen werden wirksam, wenn Sie die Rollenzuweisung speichern. Benutzersitzungen sind von Rollenzuweisungsänderungen nicht betroffen. Wenn ein Benutzer einen Bericht geöffnet hat und Sie eine Rollenzuweisung ändern, um den Zugriff darauf zu sperren, kann der Benutzer den Bericht weiterhin in der aktuellen Sitzung verwenden.

Wenn Sie ein Benutzerkonto einer Gruppe hinzufügen, die bereits Teil einer Rollenzuweisung ist, kann das Benutzerkonto erst nach einer kurzen Verzögerung auf die Elemente zugreifen. Diese Verzögerung wird durch das Zwischenspeichern von Authentifizierungstokens durch Internetinformationsdienste (Internet Information Services, IIS) verursacht. Sie können entweder warten, bis die Tokens aktualisiert werden (normalerweise 15 Minuten), oder Sie können IIS zurücksetzen, damit der Cache sofort aktualisiert wird.

Es kann immer nur eine Rollenzuweisung geändert werden. Sie können keine globalen Such- und Ersetzungsvorgänge durchführen, um die Namen oder Einstellungen von Rollendefinitionen zu ändern oder um alle Rollenzuweisungen mit einem bestimmten Benutzer oder einer bestimmten Gruppe zu suchen.

## <a name="deleting-a-role-assignment"></a>Löschen einer Rollenzuweisung

Zum Löschen von Rollenzuweisungen aktivieren Sie das Kontrollkästchen neben den Rollenzuweisungen, die Sie löschen möchten, und klicken Sie dann auf **Löschen**. Zum Löschen von Rollenzuweisungen können Sie auch auf die Schaltfläche **Zur übergeordneten Sicherheit zurückkehren**klicken. Wenn Sie auf diese Schaltfläche klicken, werden die vorhandenen Rollenzuweisungen für das Element gelöscht und durch die Zuweisungen ersetzt, die vom übergeordneten Element geerbt werden.

## <a name="see-also"></a>Weitere Informationen

[Grant User Access to a Report Server (Gewähren von Benutzerzugriff auf einen Berichtsserver)](../../reporting-services/security/grant-user-access-to-a-report-server.md)  
[Role Assignments (Rollenzuweisungen)](../../reporting-services/security/role-assignments.md)  
[Rollendefinitionen](../../reporting-services/security/role-definitions.md)  
[Vordefinierte Rollen](../../reporting-services/security/role-definitions-predefined-roles.md)  
[Granting Permissions on a Native Mode Report Server (Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus)](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)
