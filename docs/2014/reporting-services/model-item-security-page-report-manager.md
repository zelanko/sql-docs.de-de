---
title: Modellelementsicherheit (Seite) (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.modelproperties.modelitemsecurity.f1
ms.assetid: 8c5b29ae-1f17-41f2-ab59-97899b8fb4fc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 10aa1c7132126dd705986a55d5dc02d78a5263ef
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188431"
---
# <a name="model-item-security-page-report-manager"></a>Modellelementsicherheit (Seite) (Berichts-Manager)
  Verwenden Sie diese Seite, um Teile eines Modells zu sichern, indem Sie schreibgeschützte Berechtigungen für bestimmte Elemente erteilen oder aufheben. Die Modellelementsicherheit hat Auswirkungen auf die Ad-hoc-Durchsuchung von Daten zur Laufzeit und die Möglichkeit, Teile eines veröffentlichten Modells bei der Erstellung von Berichten im Berichts-Generator zu verwenden. Sie müssen über Inhalts-Manager-Berechtigungen verfügen, um diese Funktion zu verwenden.  
  
 Die Modellelementsicherheit wird auf ein auf dem Berichtsserver verarbeitetes Modell angewendet und wirkt sich nicht auf SMDL-Dateien aus, die Sie im Modell-Designer bearbeiten oder im Berichts-Designer verwenden. Darüber hinaus hat sie keine Auswirkungen auf Benutzer, die über die Berechtigung zum Ändern einer Modelldefinition verfügen. Benutzer mit Inhalts-Manager- oder Verlegerberechtigungen für ein Modell können sämtliche Teile dieses Modells anzeigen, unabhängig davon, ob Sie Modellelementsicherheit anwenden.  
  
> [!NOTE]  
>  Modellelemente können mithilfe von Sicherheitsfiltern zusätzlich gesichert werden.  
  
 Sie können Modellelementsicherheit für Entitäten, Ordner und einzelne Feldern innerhalb eines Modells definieren. Da ein Modell eine breite Vielfalt sicherungsfähiger Elemente umfasst, wurde Berechtigungsvererbung in das Modell integriert, wodurch Sie eine große Zahl von Elementen mittels einer kleinen Anzahl von Rollenzuweisungen sichern können. Die Berechtigungsvererbung basiert auf folgenden Elementen:  
  
-   Model  
  
-   Stammknoten  
  
-   Ordner oder Entitäten  
  
-   Felder  
  
 Anfangs wird die Zugriffsberechtigung für Elemente des Modells durch die Rollenzuweisungen vererbt, die für das Modell selbst festgelegt wurden. Ein Benutzer mit der Berechtigung, ein Modell in einem Ordner im Berichts-Manager anzuzeigen, kann alle Elemente im Modell anzeigen.  
  
 Wenn Sie Modellelementsicherheit anwenden, müssen Sie zumindest eine Rollenzuweisung für den Stammknoten erstellen. Diese erste Rollenzuweisung für den Stammknoten wird zur Quelle vererbter Berechtigungen. Die Rollenzuweisung für den Stammknoten wird automatisch allen Elementen in der Modellhierarchie vererbt.  
  
 Um die Berechtigungen für das Durchsuchen von Daten noch weiter anzupassen, können Sie Berechtigungen für Ordner und Entitäten ändern. Abschließend können Sie Berechtigungen für einzelne Felder festlegen.  
  
 Damit Rollenzuweisungen einfacher zu verwalten sind, sollten Sie Berechtigungen nur für Ordner oder Entitäten festlegen und nicht für einzelne Felder. Sie können nicht nach den Rollenzuweisungen suchen, die Sie erstellen. Wenn Sie also Sicherheitseinstellungen für bestimmte Felder festlegen und diese Einstellungen zu einem späteren Zeitpunkt aktualisieren möchten, müssen Sie durch das gesamte Modellnamespace klicken, um diese Felder wiederzufinden.  
  
 Erstellen Sie anfangs eine Rollenzuweisung für den Stammknoten und dann zusätzliche Rollenzuweisungen für Ordner und Entitäten. Deaktivieren Sie das Kontrollkästchen **Einzelne Modellelemente für dieses Modell unabhängig voneinander sichern**, um die Modellelementsicherheit zu deaktivieren. Wenn Sie das Kontrollkästchen deaktivieren, werden die ursprünglichen Berechtigungen wiederhergestellt, die vom Modell geerbt wurden.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-general-properties-page-for-a-report"></a>So öffnen Sie die Seite Allgemeine Eigenschaften für einen Bericht  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie das Modell, für das Sie Modellelementsicherheit konfigurieren möchten.  
  
2.  Zeigen Sie auf das Modell, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Dadurch wird die Seite Allgemeine Eigenschaften für das Modell geöffnet.  
  
4.  Wählen Sie die Registerkarte **Modellelementsicherheit** aus.  
  
## <a name="options"></a>Optionen  
 **Einzelne Modellelemente für dieses Modell unabhängig voneinander sichern**  
 Aktivieren Sie dieses Kontrollkästchen, um die Modellelementsicherheit zu aktivieren.  
  
 **Geben Sie die Sicherheit für einzelne Modellelemente im Modus**  
 Zeigt alle Elemente eines Modells. Sie können im Modellnamespace navigieren, um das mit Sicherheitseinstellungen zu versehende Element auszuwählen. Sie können jeweils nur ein Element auswählen. Stellen Sie sicher, dass Sie die erste Rollenzuweisung für den Stammknoten erstellt haben, bevor Sie mit anderen Ordnern und Entitäten fortfahren.  
  
 **Berechtigungen vom übergeordneten Element erben**  
 Aktivieren Sie diese Option, wenn das Element die Sicherheitseinstellungen des übergeordneten Elements erben soll.  
  
 **Weisen Sie die Leseberechtigung für die folgenden Benutzer und Gruppen (durch Semikolons getrennt)**  
 Aktivieren Sie diese Option, um das Benutzer- bzw. Gruppenkonto anzugeben, für das Sie den Zugriff definieren. Wenn Sie die Standardsicherheitseinstellungen verwenden, handelt es sich bei den Benutzer- bzw. Gruppenkonten um Windows-Domänenkonten. Geben Sie die Konten im folgenden Format:  *\<Domäne >\\< Konto\>*.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichtsserver im Management Studio (F1-Hilfe)](tools/report-server-in-management-studio-f1-help.md)  
  
  
