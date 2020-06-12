---
title: Grant (Daten Bank Berechtigungen) (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Analysis Services], full control
- full control permissions [Analysis Services]
ms.assetid: be7e5f64-af43-47d6-84a5-c5c1c277d644
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b4e5ac88a81728d6e29d32b0d330ba8fd408633
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546682"
---
# <a name="grant-database-permissions-analysis-services"></a>Erteilen von Datenbankberechtigungen (Analysis Services)
  Wenn Sie Datenbanken mit Analysis Services verwalten und bereits über Kenntnisse zu relationalen Datenbanken verfügen, müssen Sie zuerst verstehen, dass in Bezug auf Datenzugriff die Datenbank nicht das primäre sicherungsfähige Objekt in Analysis Services ist.

 Die primäre Abfragestruktur in Analysis Services ist ein Cube (oder ein tabellarisches Modell), mit Benutzerberechtigungen, die für diese bestimmten Objekte festgelegt sind. Im Gegensatz zur relationalen Datenbank-Engine, bei dem Datenbankanmeldenamen und Benutzerberechtigungen (oft `db_datareader`) für die Datenbank selbst festgelegt sind, ist eine Analysis Services-Datenbank hauptsächlich ein Container für die Hauptabfrageobjekte in einem Datenmodell. Wenn Sie hauptsächlich den Datenzugriff für einen Cube oder ein tabellarisches Modell aktivieren möchten, können Sie zunächst die Datenbankberechtigungen umgehen und sich direkt diesem Thema zuwenden: [Erteilen von Cube- oder Modellberechtigungen &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md).

 Datenbankberechtigungen in Analysis Services ermöglichen administrative Funktionen. Weitgefasst gilt dies, wie es der Fall bei der Datenbankberechtigung Vollzugriff ist, oder granularer, wenn Sie die Verarbeitung von Vorgängen delegieren. Berechtigungsebenen für eine Analysis Services-Datenbank können Sie im Bereich **Allgemein** mit dem Dialogfeld **Rolle erstellen** festlegen. Dies wird in der folgenden Grafik gezeigt und nachstehend beschrieben.

 Es gibt in Analysis Services keine Anmeldenamen. Sie erstellen einfach Rollen und weisen im Bereich **Mitgliedschaft** Windows-Konten zu. Alle Benutzer, einschließlich der Administratoren, stellen die Verbindung zu Analysis Services über ein Windows-Konto her.

 ![Dialogfeld "Rolle erstellen" mit Datenbankberechtigungen](../media/ssas-permsdbrole.png "Dialogfeld "Rolle erstellen" mit Datenbankberechtigungen")

 Auf Datenbankebene gibt es drei Berechtigungstypen.

 **Vollzugriff (Administrator)** ─ Vollzugriff ist eine globale Berechtigung, die viele Zugriffsmöglichkeiten in einer Analysis Services-Datenbank mit sich bringt, z.B. die Fähigkeit, jedes Objekt in der Datenbank abzufragen oder zu verarbeiten und die Rollensicherheit zu verwalten. Vollzugriff entspricht dem Datenbankadministratorstatus. Wenn Sie `Full Control` auswählen, werden die Berechtigungen `Process Database` und `Read Definition` ebenfalls ausgewählt und können nicht entfernt werden.

> [!NOTE]
>  Serveradministratoren (Mitglieder der Serveradministratorrolle) besitzen ebenfalls impliziten Vollzugriff auf jede Datenbank auf dem Server.

 `Process Database`; Diese Berechtigung wird verwendet, um die Verarbeitung auf Datenbankebene zu delegieren. Als Administrator können Sie diesen Task auslagern, indem Sie eine Rolle erstellen, mit der eine andere Person oder ein Dienst Verarbeitungsvorgänge für ein beliebiges Objekt in der Datenbank aufrufen kann. Alternativ können Sie auch Rollen für die Verarbeitung bestimmter Objekte erstellen. Weitere Informationen finden Sie unter [Erteilen von Verarbeitungsberechtigungen &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md) .

 `Read Definition`: Diese Berechtigung gewährt die Möglichkeit, Objekt Metadaten zu lesen, abzüglich der Möglichkeit, zugeordnete Daten anzuzeigen. Meist wird diese Berechtigung für Rollen verwendet, die für die dedizierte Verarbeitung erstellt wurden. Dadurch können dann Tools wie [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] oder [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] für die interaktive Verarbeitung einer Datenbank verwendet werden. Ohne `Read Definition` ist die Berechtigung `Process Database` nur in Skriptszenarios effektiv. Wenn Sie die Verarbeitung automatisieren möchten, zum Beispiel durch SSIS oder ein anderes Zeitplanungsmodul, sollten Sie eine Rolle erstellen, die über `Process Database`, jedoch nicht über `Read Definition` verfügt. Erwägen Sie andernfalls, die beiden Eigenschaften in derselben Rolle zu kombinieren, um unbeaufsichtigte und interaktive Verarbeitung mit SQL Server-Tools zu unterstützen, die das Datenmodell auf einer Benutzeroberfläche grafisch darstellen.

## <a name="full-control-administrator-permissions"></a>Berechtigung Vollzugriff (Administrator)
 In [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]ist jede Windows-Benutzeridentität, die einer Rolle mit Berechtigung Vollzugriff (Administrator) zugewiesen ist, ein Datenbankadministrator. Ein Datenbankadministrator kann jeden Task innerhalb der Datenbank ausführen, einschließlich:

-   Verarbeiten von Objekten

-   Lesen von Daten und Metadaten für alle Objekte in der Datenbank, einschließlich Cubes, Dimensionen, Measure-Gruppen, Perspektiven und Data Mining-Modelle

-   Erstellen oder Anpassen von Datenbankrollen durch Hinzufügen von Benutzern oder Berechtigungen, einschließlich Hinzufügen von Benutzern zu Rollen mit der Berechtigung Vollzugriff

-   Löschen von Datenbankrollen oder Rollenmitgliedschaften

-   Registrieren von Assemblys (oder gespeicherten Prozeduren) für die Datenbank

 Beachten Sie, dass Datenbankadministratoren keine Datenbanken auf dem Server hinzufügen oder löschen und für andere Datenbanken auf demselben Server auch keine Administratorrechte gewähren können. Diese Berechtigung besitzen nur Serveradministratoren. Weitere Informationen zu dieser Berechtigungsebene finden Sie unter [Erteilen von Server Administrator Berechtigungen &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md) .

 Da alle Rollen über den Benutzer definiert werden, wird empfohlen, dass Sie für diesen Zweck eine Rolle erstellen (zum Beispiel mit dem Namen "dbadmin") und dann Windows-Konten von Benutzern und Gruppen entsprechend zuweisen.

#### <a name="create-roles-in-ssms"></a>Erstellen von Rollen in SSMS

1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]eine Verbindung mit der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz her, öffnen Sie den Ordner **Datenbanken** , wählen Sie eine Datenbank aus, klicken Sie mit der rechten Maustaste auf **Rollen** | **Neue Rolle**.

2.  Geben Sie im Bereich **Allgemein** einen Namen ein, zum Beispiel DBAdmin.

3.  Aktivieren Sie das Kontrollkästchen **Vollzugriff (Administrator)** für den Cube. Beachten Sie, dass `Process Database` und `Read Definition` automatisch ausgewählt werden. Diese beiden Berechtigungen sind immer in Rollen enthalten, die `Full Control` besitzen.

4.  Geben Sie im **Mitgliedschaft** sbereich die Windows-Konten von Benutzern und Gruppen ein, die mit dieser Rolle eine Verbindung zu Analysis Services herstellen.

5.  Klicken Sie auf **OK** , um die Erstellung der Rolle zu abzuschließen.

## <a name="process-database"></a>Datenbank verarbeiten
 Wenn Sie eine Rolle definieren, die Daten Bank Berechtigungen gewährt, können Sie nur überspringen `Full Control` und auswählen `Process Database` . Diese Berechtigung ermöglicht auf Datenbankebene die Verarbeitung aller Objekte innerhalb der Datenbank. Weitere Informationen finden Sie unter [Erteilen von Verarbeitungsberechtigungen &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md)

## <a name="read-definition"></a>Read Definition
 Ebenso `Process Database` `Read Definition` hat das Festlegen von Berechtigungen auf Datenbankebene einen kaskadierenden Effekt auf andere Objekte innerhalb der Datenbank. Wenn Sie Berechtigungen für das Lesen von Definitionen mit feinerer Granularität festlegen möchten, müssen Sie Im Bereich "Allgemein" "Definition lesen" als Datenbankeigenschaft entfernen. Weitere Informationen finden Sie unter [Erteilen von Berechtigungen zum Lesen von Definitionen für Objektmetadaten &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md).

## <a name="see-also"></a>Weitere Informationen
 [Erteilen Sie Server Administrator Berechtigungen &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md) [Erteilen von Prozess Berechtigungen &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md)


