---
title: Erteilen von Berechtigungen für ein Datenquellen Objekt (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.datasources.f1
helpviewer_keywords:
- read/write permissions
- user access rights [Analysis Services], data sources
- security [Analysis Services], data sources
- connection strings [Analysis Services]
- data sources [Analysis Services], security
ms.assetid: b4e302d3-c93b-4383-aa4a-37d15c129830
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0a7de676f5863187c2c137e056392a605af474f
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546672"
---
# <a name="grant-permissions-on-a-data-source-object-analysis-services"></a>Erteilen von Berechtigungen für ein Datenquellenobjekt (Analysis Services)
  Im Normalfall benötigen die meisten Benutzer von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] keinen Zugriff auf die Datenquellen, die einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt zugrunde liegen. Sie fragen die Daten in der Regel nur in einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank ab. Allerdings muss ein Benutzer im Zusammenhang mit dem Data Mining, z. B. beim Ausführen von Vorhersagen auf der Basis eines Miningmodells, die aus einem Miningmodell abgeleiteten Daten mit den vom Benutzer bereitgestellten Daten verknüpfen. Um eine Verbindung mit der Datenquelle, in der sich die vom Benutzer bereitgestellten Daten befinden, herstellen zu können, verwendet der Benutzer eine DMX-Abfrage (Data Mining-Erweiterungen), die sowohl die [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery)-Klausel als auch die [OPENROWSET &#40;DMX&#41;](/sql/dmx/source-data-query-openrowset)-Klausel enthält.  
  
 Zum Ausführen einer DMX-Abfrage, die eine Verbindung mit einer Datenquelle herstellt, muss der Benutzer Zugriff auf das Datenquellenobjekt innerhalb der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank haben. Standardmäßig haben nur Server- oder Datenbankadministratoren Zugriff auf Datenquellenobjekte. Dies bedeutet, dass ein Benutzer nur dann auf ein Datenquellenobjekt zugreifen kann, wenn er von einem Administrator entsprechende Berechtigungen erhält.  
  
> [!IMPORTANT]  
>  Aus Sicherheitsgründen ist das Übermitteln von DMX-Abfragen mithilfe einer offenen Verbindungszeichenfolge in der OPENROWSET-Klausel deaktiviert.  
  
## <a name="set-read-permissions-to-a-data-source"></a>Festlegen von Leseberechtigungen für eine Datenquelle  
 Einer Datenbankrolle können entweder keine Zugriffsberechtigungen für ein Datenquellenobjekt oder Leseberechtigungen erteilt werden.  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]her, erweitern Sie im Objekt-Explorer das **Rollen** -Element für die entsprechende Datenbank, und klicken Sie dann auf eine Datenbankrolle (oder erstellen Sie eine neue Datenbankrolle).  
  
2.  Suchen Sie im Bereich **Datenquellenzugriff** das Datenquellenobjekt in der Liste **Datenquelle** , und wählen Sie dann in der Liste **Zugriff** für die Datenquelle die Option **Lesen** aus. Wenn diese Option nicht verfügbar ist, überprüfen Sie im Bereich **Allgemein** , ob "Vollzugriff" ausgewählt ist. Vollzugriff enthält bereits Berechtigungen. Sie können die Berechtigungen für die Datenquelle nicht überschreiben.  
  
## <a name="working-with-the-connection-string-used-by-a-data-source-object"></a>Arbeiten mit der Verbindungszeichenfolge, die von einem Datenquellenobjekt verwendet wird  
 Das Datenquellenobjekt enthält die Verbindungszeichenfolge, die zum Verbindungsaufbau mit der zugrunde liegenden Datenquelle verwendet wird. Diese Verbindungszeichenfolge kann die folgenden Angaben enthalten:  
  
-   **Angabe eines Benutzernamens und eines Kennworts**  
  
     Wenn die von einem Datenquellenobjekt verwendete Verbindungszeichenfolge einen Benutzernamen und ein Kennwort angibt, kann es sinnvoll sein, mehrere Datenquellenobjekte zu erstellen, von denen jedes unterschiedliche Benutzerkonten hat. Durch das Erstellen mehrerer Datenquellenobjekte können Benutzer auf bestimmte Datenquellenobjekte zugreifen, während der Zugriff auf andere Datenquellenobjekte verhindert wird. Diese anderen Datenquellenobjekte können von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] selbst zum Verarbeiten von Objekten wie z. B. Cubes und Miningmodellen verwendet werden.  
  
-   **Angabe der Windows-Authentifizierung**  
  
     Wenn die von einem Datenquellenobjekt verwendete Verbindungszeichenfolge die Windows-Authentifizierung angibt, muss [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in der Lage sein, die Identität des Clients anzunehmen. Wenn sich die Datenquelle auf einem Remotecomputer befindet, müssen die beiden Computer mithilfe der Kerberos-Authentifizierung als vertrauenswürdig für den Identitätswechsel eingestuft werden, weil ansonsten die Abfrage zumeist fehlschlägt. Weitere Informationen finden Sie unter [Configure Analysis Services for Kerberos constrained delegation](../instances/configure-analysis-services-for-kerberos-constrained-delegation.md) .  
  
     Wenn der Client den Identitätswechsel nicht zulässt (durch die Identitätswechselebene-Eigenschaft in OLE DB und anderen Clientkomponenten), versucht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , eine anonyme Verbindung mit der zugrunde liegenden Datenquelle herzustellen. Anonyme Verbindungen auf Remotedatenquellen sind selten erfolgreich, da die meisten Datenquellen keine anonymen Verbindungen akzeptieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenquellen in mehrdimensionalen Modellen](data-sources-in-multidimensional-models.md)   
 [Eigenschaften der Verbindungs Zeichenfolge &#40;Analysis Services&#41;](../instances/connection-string-properties-analysis-services.md)   
 [Von Analysis Services unterstützte Authentifizierungsmethoden](../instances/authentication-methodologies-supported-by-analysis-services.md)   
 [Gewähren von benutzerdefiniertem Zugriff auf Dimensions Daten &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md)   
 [Erteilen von Cube-oder Modell Berechtigungen &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md)   
 [Erteilen von benutzerdefiniertem Zugriff auf Zellendaten &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md)  
  
  
