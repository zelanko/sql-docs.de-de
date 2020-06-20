---
title: Schema Optionen für die Themenbereichs Datenbank (Schemagenerierungs-Assistent) (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.schemagenwizard.subjectareaschemaopts.f1
ms.assetid: 4c109bb8-e19d-412b-908f-bfdd7f872439
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7edc1fc89e9463c7482b47866aa3d12e1bc231a7
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84940241"
---
# <a name="subject-area-database-schema-options-schema-generation-wizard-analysis-services---multidimensional-data"></a>Schemaoptionen für die Themenbereichsdatenbank (Schemagenerierungs-Assistent) (Analysis Services – Mehrdimensionale Daten)
  Mithilfe der Seite **Schemaoptionen für die Themenbereichsdatenbank** können Sie die Generierung des Schemas steuern und definieren, wie Daten erhalten bleiben.  
  
## <a name="options"></a>Tastatur  
 **Besitzendes Schema**  
 Gibt den Namen des Schemas innerhalb der neuen Themenbereichsdatenbank an.  
  
 **Primärschlüssel für Dimensionstabellen erstellen**  
 Erstellt Primärschlüssel für die Dimensionstabellen im generierten Schema. Wenn Sie diese Option nicht auswählen, wird kein Index erstellt.  
  
> [!NOTE]  
>  Wenn Sie diese Option nicht auswählen, wird die referenzielle Integrität erzwungen.  
  
 **Erstellen von Indizes**  
 Erstellt Indizes für Fremdschlüsselspalten im generierten Schema.  
  
 **Referenzielle Integrität erzwingen**  
 Erzwingt die referenzielle Integrität innerhalb des generierten Schemas. Wenn Sie diese Option nicht auswählen, werden Beziehungen erstellt, aber nicht erzwungen.  
  
 **Daten bei erneuter Generierung beibehalten**  
 Behält die Daten in der Themenbereichsdatenbank bei Abschluss des Assistenten bei. Wenn Sie diese Option nicht auswählen, werden möglicherweise alle Daten in der Themenbereichsdatenbank ohne Warnung gelöscht.  
  
 **Zeittabelle(n) auffüllen**  
 Gibt an, wie der Assistent die Zeittabellen auffüllt. Die folgende Tabelle beschreibt die möglichen Werte für diese Option.  
  
> [!NOTE]  
>  Diese Option ist nur aktiviert, wenn der Schemagenerierungs-Assistent von einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt aus mithilfe von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] im Projektmodus aufgerufen wird.  
  
|Value|Beschreibung|  
|-----------|-----------------|  
|Auffüllen|Die Themenbereichs-Zeittabellen werden aufgefüllt.|  
|Nicht auffüllen|Die Themenbereichs-Zeittabellen werden nicht aufgefüllt.|  
|Nur auffüllen, wenn leer|Die Themenbereichs-Zeittabellen werden nur aufgefüllt, wenn sie leer sind.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schemagenerierungs-Assistent F1-Hilfe &#40;Analysis Services-mehrdimensionalen Daten&#41;](schema-generation-wizard-f1-help-analysis-services-multidimensional-data.md)  
  
  
