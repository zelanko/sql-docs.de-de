---
title: DQS-Bereinigungstransformation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data correction
- correct data
ms.assetid: d2ec1b1a-c745-4741-b57c-6fdb524a154c
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 696dce12d347fe8da679c5d029b9f9d78bafc19c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283716"
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
  
-   Artikel [Bereinigung komplexer Daten unter Verwendung von Verbunddomänen](http://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx)auf social.technet.microsoft.com.  
  
  
