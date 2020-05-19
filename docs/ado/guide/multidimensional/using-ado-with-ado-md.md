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
author: rothja
ms.author: jroth
ms.openlocfilehash: 591a10e8c91aa22f939ff48f341b376bbd8ebe1b
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82748009"
---
# <a name="using-ado-with-ado-md"></a>Verwenden von ADO mit ADO MD
ADO und ADO MD sind miteinander verknüpft, aber getrennte Objekt Modelle. ADO stellt Objekte für das Herstellen einer Verbindung mit Datenquellen, das Ausführen von Befehlen, das Abrufen von Tabellendaten und Schema Metadaten in einem Tabellenformat und das Anzeigen von Anbieter Fehlerinformationen bereit. ADO MD stellt Objekte zum Abrufen mehrdimensionaler Daten und zum Anzeigen von mehrdimensionalen Schema Metadaten bereit.  
  
 Wenn Sie mit einem MDP arbeiten, können Sie sich für die Verwendung von ADO, ADO MD oder beides mit Ihrer Anwendung entscheiden. Wenn Sie auf beide Bibliotheken innerhalb Ihres Projekts verweisen, haben Sie vollständigen Zugriff auf die Funktionen, die von Ihrem MDP bereitgestellt werden.  
  
 Es ist häufig nützlich für Consumer, eine vereinfachte tabellarische Ansicht eines mehrdimensionalen Datasets zu erhalten. Hierfür können Sie das ADO- [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt verwenden. Geben Sie die Quelle für das [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) als ***Quell*** Parameter für die [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode eines **Recordsets**anstelle der Quelle für ein ADO MD **Cellsets**an.  
  
 Es kann auch hilfreich sein, die Schema Metadaten in einer tabellarischen Ansicht und nicht als eine Hierarchie von Objekten anzuzeigen. Die ADO [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) -Methode für das [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt ermöglicht dem Benutzer das Öffnen eines **Recordsets** , das Schema Informationen enthält. Der ***QueryType*** -Parameter der **OpenSchema** -Methode verfügt über mehrere [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md) -Werte, die sich speziell auf MDPs beziehen. Die Werte lauten wie folgt:  
  
-   **adschemacubes**  
  
-   **adschemadimensions**  
  
-   **adschemahierarchien**  
  
-   **adschemalevels**  
  
-   **adschemameasures**  
  
-   **"adschemamembers"**  
  
 Um ADO-Enumerationswerte mit ADO MD Eigenschaften oder Methoden zu verwenden, muss das Projekt auf die ADO-und ADO MD-Bibliotheken verweisen. Beispielsweise können Sie die ADO **adstate** -Enumerationswerte mit der ADO MD [State](../../../ado/reference/ado-md-api/state-property-ado-md.md) -Eigenschaft verwenden. Weitere Informationen zum Erstellen von Verweisen auf Bibliotheken finden Sie in der Dokumentation zu Ihrem Entwicklungs Tool.  
  
 Weitere Informationen zu den ADO-Objekten und-Methoden finden Sie in der [ADO-API-Referenz](../../../ado/reference/ado-api/ado-api-reference.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO MD-Objektmodell](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (mehrdimensional) (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Übersicht über mehrdimensionale Schemas und Daten](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [Programmieren mit ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Arbeiten mit mehrdimensionalen Daten](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
