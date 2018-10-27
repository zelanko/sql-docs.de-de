---
title: Sicherheit in tabellarischen Modellen auf Objektebene | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 54384e050f4e45ad5d89d66111ecdcc851076d76
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50148205"
---
# <a name="object-level-security"></a>Sicherheit auf Objektebene
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Modell datensicherheit beginnt bei der Implementierung von effektiv [Rollen](../../analysis-services/tabular-models/roles-ssas-tabular.md) und Zeilenebene Filtern zum Definieren von Benutzerberechtigungen auf Daten von modellobjekten und Daten. Beginnen mit tabellarischen 1400-Modellen, können Sie auch definieren auf Objektebene Sicherheit, einschließlich Sicherheit auf Zeilenebene Tabelle und Sicherheit auf Zeilenebene Spalte in der [Roles-Objekt](https://docs.microsoft.com/bi-reference/tmsl/roles-object-tmsl).

## <a name="table-level-security"></a>Sicherheit auf Tabellenebene

Klicken Sie mit der Sicherheit auf Tabellenebene können Sie nicht nur den Zugriff auf Tabellendaten, aber auch vertrauliche Tabellennamen unterstützen, verhindern, dass böswillige Benutzer erkennen können, ob eine Tabelle vorhanden ist. 

 Sicherheit auf Zeilenebene Tabelle festgelegt ist, in den JSON-basierten Metadaten in den Model.bim [Tabular Model Scripting Language (TMSL)](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference), oder [Tabular Object Model (TOM)](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo). Festlegen der **MetadataPermission** Eigenschaft der **TablePermissions** -Klasse in der [Roles-Objekt](https://docs.microsoft.com/bi-reference/tmsl/roles-object-tmsl) zu **keine**.

In diesem Beispiel wird die MetadataPermission-Eigenschaft der TablePermissions-Klasse für die Product-Tabelle auf "None" festgelegt:

```
"roles": [
  {
    "name": "Users",
    "description": "All allowed users to query the model",
    "modelPermission": "read",
    "tablePermissions": [
      {
        "name": "Product",
        "metadataPermission": "none"
      }
    ]
  }
```

## <a name="column-level-security"></a>Sicherheit auf Zeilenebene Spalte

Ähnlich wie Sicherheit auf Tabellenebene mit Sicherheit auf Spaltenebene können Sie nicht nur Zugriff auf Spaltendaten, sondern auch vertrauliche Spaltennamen, beschränken hilft zu verhindern, dass böswillige Benutzer aus eine Spalte zu ermitteln.

 Sicherheit auf Zeilenebene Spalte festgelegt ist, in den JSON-basierten Metadaten in den Model.bim [Tabular Model Scripting Language (TMSL)](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference), oder [Tabular Object Model (TOM)](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo). Festlegen der **MetadataPermission** Eigenschaft der **Spaltenberechtigungen** -Klasse in der [Roles-Objekt](https://docs.microsoft.com/bi-reference/tmsl/roles-object-tmsl) zu **keine**.

In diesem Beispiel wird die MetadataPermission-Eigenschaft der Klasse Spaltenberechtigungen für die Basistarif-Spalte in der Employees-Tabelle auf "None" festgelegt:

```
"roles": [
  {
    "name": "Users",
    "description": "All allowed users to query the model",
    "modelPermission": "read",
    "tablePermissions": [
      {
        "name": "Employee",
        "columnPermissions": [
          {
            "name": "Base Rate",
            "metadataPermission": "none"
          }
        ]
      }
    ]
  }
```

## <a name="restrictions"></a>Restrictions

*  Sicherheit auf Zeilenebene Tabelle kann nicht für ein Modell festgelegt werden, wenn es sich um eine beziehungskette stoppt. Ein Fehler wird zur Entwurfszeit generiert.
 Z. B. wenn Beziehungen zwischen Tabellen A und B und B und C vorhanden sind, können nicht Sie Tabelle b sichern Wenn Tabelle B geschützt ist, kann keine Abfrage in Tabelle A die Beziehungen zwischen Tabellen A und B und B und C. übertragen. In diesem Fall konnte eine separate Beziehung zwischen Tabellen A und b konfiguriert werden

    ![Sicherheit auf Tabellenebene](../../analysis-services/tabular-models/media/ssas-ols.png)  


*  Sicherheit auf Zeilenebene und Sicherheit auf Zeilenebene Objekt können nicht aus unterschiedlichen Rollen kombiniert werden, da sie unerwünschten Zugriff auf gesicherte Daten führen kann. Zum Zeitpunkt der Abfrage für Benutzer, die Mitglieder dieser Kombination von Rollen sind, wird ein Fehler generiert.

*  Dynamische Berechnungen (Measures, KPIs, DetailRows) sind automatisch eingeschränkt, wenn sie eine gesicherte Tabelle oder Spalte verweisen. Zwar gibt es keinen Mechanismus, um ein Measure explizit zu schützen, ist es möglich, implizit ein Measure zu sichern, indem Sie die Aktualisierung des Ausdrucks, der auf einer gesicherten Tabelle oder Spalte verweisen.

*  Beziehungen, die eine gesicherte Spalte verweisen, funktionieren, sofern die Tabelle, der in die Spalte ist nicht sicher ist.




## <a name="see-also"></a>Siehe auch  
[Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
[Roles-Objekt (TMSL)](https://docs.microsoft.com/bi-reference/tmsl/roles-object-tmsl)  
[Tabular Model Scripting Language (TMSL) (Skriptsprache für tabellarische Modelle (TMSL))](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference)  
[Tabellenobjektmodell (TOM)](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).

  
