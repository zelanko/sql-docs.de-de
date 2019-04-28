---
title: DQS-Bereinigungstransformation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data correction
- correct data
ms.assetid: d2ec1b1a-c745-4741-b57c-6fdb524a154c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0c06abe4d6adb3916028b3501c16b68d2491af47
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900397"
---
# <a name="dqs-cleansing-transformation"></a>DQS-Bereinigungstransformation
  Die DQS-Bereinigungstransformation korrigiert Daten aus einer verbundenen Datenquelle mithilfe von Data Quality Services (DQS), indem sie genehmigte Regeln anwendet, die für die verbundene Datenquelle oder eine ähnliche Datenquelle erstellt wurden. Weitere Informationen zu Datenkorrekturregeln finden Sie unter [DQS Knowledge Bases and Domains](../../../data-quality-services/dqs-knowledge-bases-and-domains.md). Weitere Informationen zu DQS finden Sie unter [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md).  
  
 Die DQS-Bereinigungstransformation bestimmt, ob die Daten korrigiert werden müssen, indem sie die Daten in einer Eingabespalte verarbeitet. Dabei gelten folgende Bedingungen:  
  
-   Die Spalte ist für die Datenkorrektur ausgewählt.  
  
-   Der Datentyp der Spalte wird in der Datenkorrektur unterstützt.  
  
-   Der Spalte ist eine Domäne mit einem kompatiblen Datentyp zugeordnet.  
  
 Die Transformation umfasst auch eine Fehlerausgabe, die Sie zur Behandlung von Fehlern auf Zeilenebene konfigurieren können. Die Fehlerausgabe wird mit dem **Transformations-Editor für die DQS-Bereinigung**konfiguriert.  
  
 Sie können die [Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) in den Datenfluss einschließen, um Zeilen mit Daten zu ermitteln, bei denen es sich wahrscheinlich um Duplikate handelt.  
  
## <a name="data-quality-projects-and-values"></a>Data Quality-Projekte und -Werte  
 Wenn Sie Daten mit der DQS-Bereinigungstransformation verarbeiten, wird ein Bereinigungsprojekt auf dem Data Quality-Server erstellt. Das Projekt wird mit dem Data Quality Client verwaltet. Mit dem Data Quality Client können Sie außerdem die Projektwerte in eine DQS-Wissensdatenbankdomäne importieren. Sie können die Werte nur in eine Domäne (oder verknüpfte Domäne) importieren, für deren Verwendung die DQS-Bereinigungstransformation konfiguriert wurde.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Öffnen von Integration Services-Projekten im Data Quality-Client](../../../data-quality-services/open-integration-services-projects-in-data-quality-client.md)  
  
-   [Importieren von Bereinigungsprojektwerten in eine Domäne](../../../data-quality-services/import-cleansing-project-values-into-a-domain.md)  
  
-   [Anwenden von Datenqualitätsregeln auf eine Datenquelle](apply-data-quality-rules-to-data-source.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Verwalten von &#40;öffnen, entsperren, umbenennen und Löschen von&#41; Data Quality-Projekten](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)  
  
-   Artikel [Bereinigung komplexer Daten unter Verwendung von Verbunddomänen](https://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx)auf social.technet.microsoft.com.  
  
  
