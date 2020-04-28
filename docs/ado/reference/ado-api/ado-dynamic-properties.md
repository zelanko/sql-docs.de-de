---
title: Dynamische ADO-Eigenschaften | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- dynamic properties [ADO]
- properties [ADO], dynamic
ms.assetid: d7b06d72-f792-4328-93a2-5006b9e2c581
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 71396a071a42d7dd40a6537a2834541aab2b6bad
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67921093"
---
# <a name="ado-dynamic-properties"></a>ADO – dynamische Eigenschaften
Dynamische Eigenschaften können den [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistungen der [Connection](../../../ado/reference/ado-api/connection-object-ado.md)-, [Command](../../../ado/reference/ado-api/command-object-ado.md)-oder [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekte hinzugefügt werden. Die Quelle für diese Eigenschaften ist entweder ein Datenanbieter, z. b. der [OLE DB Anbieter für SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), oder ein Dienstanbieter, z. b. der [Microsoft-Cursor Dienst für OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md). Weitere Informationen zu einer bestimmten dynamischen Eigenschaft finden Sie in der entsprechenden Datenanbieter-oder Dienstanbieter Dokumentation.  
  
 Der [dynamische ADO-Eigenschafts Index](../../../ado/reference/ado-api/ado-dynamic-property-index.md) stellt einen Querverweis zwischen den ADO-und OLE DB Namen für jede dynamische Eigenschaft des Standard OLE DB Anbieters bereit.  
  
 Die folgenden dynamischen Eigenschaften sind besonders interessant und auch in den zuvor erwähnten Quellen dokumentiert. Spezielle Funktionen mit ADO sind in den ADO-Hilfe Themen in der folgenden Liste dokumentiert.  
  
|||  
|-|-|  
|[Optimieren](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)|Gibt an, ob für dieses Feld ein Index erstellt werden soll.|  
|[prompt](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)|Gibt an, ob der OLE DB Anbieter den Benutzer zur Eingabe von Initialisierungs Informationen auffordern soll.|  
|[Name der erneuten Form](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)|Gibt einen Namen für das **Recordset** -Objekt an.|  
|[Befehl zum erneuten Synchronisieren](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)|Gibt eine vom Benutzer bereitgestellte Befehls Zeichenfolge an, mit der die Methode für die **erneute Synchronisierung** die Daten in der in der dynamischen Eigenschaft **Unique Table** genannten Tabelle aktualisiert.|  
|[Unique Table, Unique Schema, Unique Catalog](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|**Eindeutige Tabelle** Gibt den Namen der Basistabelle an, auf der Updates, Einfügungen und Löschungen zulässig sind.<br /><br /> Eindeutiges **Schema** Gibt das Schema oder den Namen des Besitzers der Tabelle an.<br /><br /> Eindeutiger **Katalog** Gibt den Katalog oder den Namen der Datenbank an, in der die Tabelle enthalten ist.|  
|[Neusynchronisierung aktualisieren](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)|Gibt an, ob auf die **UpdateBatch** -Methode ein impliziter Vorgang zum **erneuten Synchronisieren** der Methode folgt, und wenn ja, der Gültigkeitsbereich dieses Vorgangs.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-API-Referenz](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO-Sammlungen](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO-Enumerationskonstanten](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Anhang B: ADO-Fehler](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO-Ereignisse](../../../ado/reference/ado-api/ado-events.md)   
 [ADO-Methoden](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO-Objektmodell](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO-Objekte und-Schnittstellen](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [ADO-Eigenschaften](../../../ado/reference/ado-api/ado-properties.md)
