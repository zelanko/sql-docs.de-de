---
title: Verwenden von ADO mit ADO MD | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, using with ADO MD
ms.assetid: cfae435e-2ac3-4312-8c1e-9ca4a74cd875
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 69707e5026497a1f98ab168d71b4e6b286520fbe
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47790420"
---
# <a name="using-ado-with-ado-md"></a>Verwenden von ADO mit ADO MD
Sind ADO und ADO MD verwandten, separaten Object-Modelle. ADO stellt Objekte für eine Verbindung mit Datenquellen, Ausführen von Befehlen, Abrufen von Tabellendaten und Schemametadaten in einem tabellarischen Format und Anzeigen von Fehlerinformationen des Anbieters bereit. ADO MD bietet Objekte zum Abrufen von mehrdimensionalen Daten und Anzeigen von Metadaten von mehrdimensionalen Schema.  
  
 Wenn Sie mit einem MDP arbeiten, können Sie ADO, ADO MD oder beides mit Ihrer Anwendung verwenden. Durch Verweisen auf die beiden Bibliotheken in Ihrem Projekt, müssen Sie vollständigen Zugriff auf die Funktionalität Ihrer MDP.  
  
 Es ist häufig nützlich, Benutzern eine vereinfachte, tabellarische Ansicht eines mehrdimensionalen Datasets zu erhalten. Sie erreichen dies, indem Sie das ADO [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt. Geben Sie die Quelle für Ihre [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) als die ***Quelle*** -Parameter für die [öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode der ein **Recordset**, und nicht als Quelle für eine ADO MD **Cellset**.  
  
 Es kann auch zum Anzeigen der Schemametadaten in einer tabellarischen Ansicht nicht als eine Hierarchie von Objekten nützlich sein. Das ADO [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) Methode für die [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) -Objekt können Sie den Benutzer aus, öffnen Sie eine **Recordset** , die die Schemainformationen enthält. Die ***QueryType*** Parameter, der die **OpenSchema** Methode verfügt über mehrere [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md) Werte, die speziell auf MDPs beziehen. Die Werte lauten wie folgt:  
  
-   **adSchemaCubes**  
  
-   **adSchemaDimensions**  
  
-   **adSchemaHierarchies**  
  
-   **adSchemaLevels**  
  
-   **adSchemaMeasures**  
  
-   **adSchemaMembers**  
  
 Um Enumerationswerte von ADO mit ADO MD-Eigenschaften oder Methoden verwenden zu können, muss Ihr Projekt sowohl ADO und ADO MD-Bibliotheken verweisen. Sie können z. B. das ADO **AdState** Enumerationswerte, die mit der ADO MD [Zustand](../../../ado/reference/ado-md-api/state-property-ado-md.md) Eigenschaft. Weitere Informationen dazu, wie Verweise auf Bibliotheken herstellen finden Sie in der Dokumentation zu Ihrem Entwicklungstool.  
  
 Weitere Informationen zu den ADO-Objekte und Methoden finden Sie unter den [ADO-API-Referenz](../../../ado/reference/ado-api/ado-api-reference.md).  
  
## <a name="see-also"></a>Siehe auch  
 [ADO MD-Objektmodell](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (mehrdimensional) (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Übersicht über multidimensionale Schemas und Daten](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [Programmieren mit ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Arbeiten mit mehrdimensionalen Daten](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
