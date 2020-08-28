---
description: Verwenden von ADO mit ADO MD
title: Verwenden von ADO mit ADO MD | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, using with ADO MD
ms.assetid: cfae435e-2ac3-4312-8c1e-9ca4a74cd875
author: rothja
ms.author: jroth
ms.openlocfilehash: 17d4094959c72389bf1cef71e6547394e676f78f
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88978581"
---
# <a name="using-ado-with-ado-md"></a>Verwenden von ADO mit ADO MD
ADO und ADO MD sind miteinander verknüpft, aber getrennte Objekt Modelle. ADO stellt Objekte für das Herstellen einer Verbindung mit Datenquellen, das Ausführen von Befehlen, das Abrufen von Tabellendaten und Schema Metadaten in einem Tabellenformat und das Anzeigen von Anbieter Fehlerinformationen bereit. ADO MD stellt Objekte zum Abrufen mehrdimensionaler Daten und zum Anzeigen von mehrdimensionalen Schema Metadaten bereit.  
  
 Wenn Sie mit einem MDP arbeiten, können Sie sich für die Verwendung von ADO, ADO MD oder beides mit Ihrer Anwendung entscheiden. Wenn Sie auf beide Bibliotheken innerhalb Ihres Projekts verweisen, haben Sie vollständigen Zugriff auf die Funktionen, die von Ihrem MDP bereitgestellt werden.  
  
 Es ist häufig nützlich für Consumer, eine vereinfachte tabellarische Ansicht eines mehrdimensionalen Datasets zu erhalten. Hierfür können Sie das ADO- [Recordset](../../reference/ado-api/recordset-object-ado.md) -Objekt verwenden. Geben Sie die Quelle für das [Cellset](../../reference/ado-md-api/cellset-object-ado-md.md) als ***Quell*** Parameter für die [Open](../../reference/ado-api/open-method-ado-recordset.md) -Methode eines **Recordsets**anstelle der Quelle für ein ADO MD **Cellsets**an.  
  
 Es kann auch hilfreich sein, die Schema Metadaten in einer tabellarischen Ansicht und nicht als eine Hierarchie von Objekten anzuzeigen. Die ADO [OpenSchema](../../reference/ado-api/openschema-method.md) -Methode für das [Verbindungs](../../reference/ado-api/connection-object-ado.md) Objekt ermöglicht dem Benutzer das Öffnen eines **Recordsets** , das Schema Informationen enthält. Der ***QueryType*** -Parameter der **OpenSchema** -Methode verfügt über mehrere [SchemaEnum](../../reference/ado-api/schemaenum.md) -Werte, die sich speziell auf MDPs beziehen. Die Werte lauten wie folgt:  
  
-   **adschemacubes**  
  
-   **adschemadimensions**  
  
-   **adschemahierarchien**  
  
-   **adschemalevels**  
  
-   **adschemameasures**  
  
-   **"adschemamembers"**  
  
 Um ADO-Enumerationswerte mit ADO MD Eigenschaften oder Methoden zu verwenden, muss das Projekt auf die ADO-und ADO MD-Bibliotheken verweisen. Beispielsweise können Sie die ADO **adstate** -Enumerationswerte mit der ADO MD [State](../../reference/ado-md-api/state-property-ado-md.md) -Eigenschaft verwenden. Weitere Informationen zum Erstellen von Verweisen auf Bibliotheken finden Sie in der Dokumentation zu Ihrem Entwicklungs Tool.  
  
 Weitere Informationen zu den ADO-Objekten und-Methoden finden Sie in der [ADO-API-Referenz](../../reference/ado-api/ado-api-reference.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO MD-Objektmodell](../../reference/ado-md-api/ado-md-object-model.md)   
 [ADO (mehrdimensional) (ADO MD)](./ado-multidimensional-ado-md.md)   
 [Übersicht über mehrdimensionale Schemas und Daten](./overview-of-multidimensional-schemas-and-data.md)   
 [Programmieren mit ADO MD](./programming-with-ado-md.md)   
 [Arbeiten mit mehrdimensionalen Daten](./working-with-multidimensional-data.md)