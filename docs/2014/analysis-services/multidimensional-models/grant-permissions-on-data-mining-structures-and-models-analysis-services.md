---
title: Erteilen von Berechtigungen für Data Mining Strukturen und Modelle (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.miningmodels.f1
helpviewer_keywords:
- data mining [Analysis Services], security
- permissions [Analysis Services], mining models
- mining models [Analysis Services], security
- mining structures [Analysis Services], security
- permissions [Analysis Services], mining structures
- user access rights [Analysis Services], mining structures
- user access rights [Analysis Services], mining models
ms.assetid: a0008004-e2b7-47db-acad-5fe7e12b130f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 25eb8fe00c523d4a94b7f6f0325bfd2c1f55e7be
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66074943"
---
# <a name="grant-permissions-on-data-mining-structures-and-models-analysis-services"></a>Erteilen von Berechtigungen für Data Mining-Strukturen und -Modellen (Analysis Services)
  Standardmäßig besitzt nur ein Analysis Services-Serveradministrator Berechtigungen zum Anzeigen von Data Mining-Strukturen oder Miningmodellen in der Datenbank. Befolgen Sie die Anweisungen unten, um Berechtigungen für Benutzer, die keine Administratoren sind, zu vergeben.  
  
## <a name="set-permissions-to-access-a-mining-structure"></a>Festlegen von Berechtigungen für den Zugriff auf eine Miningstruktur  
  
1.  Verbinden Sie sich in SSMS mit Analysis Services. Falls Sie Hilfe bei den Schritten brauchen, gehen Sie unter [Herstellen einer Verbindung von Clientanwendungen &#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md).  
  
2.  Öffnen Sie den Ordner **Datenbanken** in Objekt-Explorer, und wählen Sie eine Datenbank aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Rollen** , und wählen Sie **Neue Rolle**aus.  
  
4.  Geben Sie auf der Seite "Allgemein" einen Namen und optional eine Beschreibung ein. Diese Seite enthält auch mehrere Datenbankberechtigungen wie beispielsweise "Vollzugriff", "Datenbank verarbeiten" und "Definition lesen". Für den Data Mining-Zugriff ist keine dieser Berechtigungen erforderlich. Weitere Informationen zu Datenbankberechtigungen finden Sie unter [Erteilen von Datenbankberechtigungen &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md).  
  
5.  Wählen Sie im Bereich **Miningstruktur** entweder **Lesen** oder **Lesen/Schreiben**  für jede Data Mining-Struktur aus.  
  
6.  Geben Sie im **Mitgliedschaft** sbereich die Windows-Konten von Benutzern und Gruppen ein, die mit dieser Rolle eine Verbindung zu Analysis Services herstellen.  
  
7.  Klicken Sie auf **OK** , um die Erstellung der Rolle zu abzuschließen.  
  
## <a name="set-permissions-to-access-a-mining-model"></a>Festlegen von Berechtigungen für den Zugriff auf ein Miningmodell  
 Für ein Data Mining-Modell kann eine Rolle entweder über **Lesen** - oder **Lesen/Schreiben** -Berechtigungen verfügen sowie über die Berechtigungen **Drillthrough** und **Definition lesen** , die das Anzeigen und Durchsuchen der zugrunde liegenden Daten ermöglichen.  
  
 **Hinweis** Wenn Sie Drillthrough sowohl für die Miningstruktur als auch für das Miningmodell aktivieren, kann jeder Benutzer, der Mitglied einer Rolle mit Drillthroughberechtigungen für das Miningmodell und die Miningstruktur ist, auch Spalten in der Miningstruktur einsehen, selbst wenn diese Spalten nicht Teil des Miningmodells sind. Deswegen sollten Sie zum Schutz sensibler Informationen die Datenquellensicht so einrichten, dass persönliche Informationen verborgen sind, und Drillthroughzugriff auf die Miningstruktur nur zulassen, wenn es wirklich erforderlich ist.  
  
 Um einer Datenbankrolle Lese-/Schreibberechtigungen zu erteilen, muss der Benutzer Mitglied der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Serverrolle oder ein Mitglied einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbankrolle sein, die über die Berechtigung Vollzugriff (Administrator) verfügt.  
  
1.  Stellen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Sie in eine Verbindung mit der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]Instanz von her, erweitern Sie in Objekt-Explorer **Rollen** für die entsprechende Datenbank, und klicken Sie dann auf eine Daten Bank Rolle (oder erstellen Sie eine neue Daten Bank Rolle).  
  
2.  Suchen Sie im Bereich **Miningstuktur** das Miningmodell in der Liste **Miningmodelle** , und wählen Sie anschließend für dieses Miningmodell die Option **Lesen**, **Lesen/Schreiben**, **Drillthrough**oder **Durchsuchen** aus.  
  
3.  Geben Sie im **Mitgliedschaft** sbereich die Windows-Konten von Benutzern und Gruppen ein, die mit dieser Rolle eine Verbindung zu Analysis Services herstellen.  
  
4.  Klicken Sie auf **OK** , um die Erstellung der Rolle zu abzuschließen.  
  
 Wenn Sie eine Datenquelle in einer Drillthroughabfrage verwenden möchten, die die OPENQUERY-Klausel der Data Mining-Erweiterungen (DMX) verwendet, muss die Datenbankrolle auch über Lese-/Schreibberechtigungen für das entsprechende Datenquellenobjekt verfügen. Weitere Informationen finden Sie unter [Erteilen von Berechtigungen für ein Datenquellenobjekt &#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md) und [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery).  
  
> [!NOTE]  
>  Standardmäßig ist die Einreichung von DMX-Abfragen über OPENROWSET deaktiviert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erteilen von Server Administrator Berechtigungen &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md)   
 [Erteilen von Cube-oder Modell Berechtigungen &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md)   
 [Gewähren von benutzerdefiniertem Zugriff auf Dimensions Daten &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md)   
 [Erteilen von benutzerdefiniertem Zugriff auf Zellendaten &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md)  
  
  
