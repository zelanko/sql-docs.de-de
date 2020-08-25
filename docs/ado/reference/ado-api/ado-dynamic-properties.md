---
description: ADO – dynamische Eigenschaften
title: Dynamische ADO-Eigenschaften | Microsoft-Dokumentation
ms.prod: sql
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- dynamic properties [ADO]
- properties [ADO], dynamic
ms.assetid: d7b06d72-f792-4328-93a2-5006b9e2c581
author: rothja
ms.author: jroth
ms.openlocfilehash: 83ab2320d3400c5be066af246b50daccaf468462
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88771759"
---
# <a name="ado-dynamic-properties"></a>ADO – dynamische Eigenschaften
Dynamische Eigenschaften können den [Properties](./properties-collection-ado.md) -Auflistungen der [Connection](./connection-object-ado.md)-, [Command](./command-object-ado.md)-oder [Recordset](./recordset-object-ado.md) -Objekte hinzugefügt werden. Die Quelle für diese Eigenschaften ist entweder ein Datenanbieter, z. b. der [OLE DB Anbieter für SQL Server](../../guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), oder ein Dienstanbieter, z. b. der [Microsoft-Cursor Dienst für OLE DB](../../guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md). Weitere Informationen zu einer bestimmten dynamischen Eigenschaft finden Sie in der entsprechenden Datenanbieter-oder Dienstanbieter Dokumentation.  
  
 Der [dynamische ADO-Eigenschafts Index](./ado-dynamic-property-index.md) stellt einen Querverweis zwischen den ADO-und OLE DB Namen für jede dynamische Eigenschaft des Standard OLE DB Anbieters bereit.  
  
 Die folgenden dynamischen Eigenschaften sind besonders interessant und auch in den zuvor erwähnten Quellen dokumentiert. Spezielle Funktionen mit ADO sind in den ADO-Hilfe Themen in der folgenden Liste dokumentiert.  
  
|Dynamic-Eigenschaft|Beschreibung|  
|-|-|  
|[Optimieren](./optimize-property-dynamic-ado.md)|Gibt an, ob für dieses Feld ein Index erstellt werden soll.|  
|[Eingabeaufforderung](./prompt-property-dynamic-ado.md)|Gibt an, ob der OLE DB Anbieter den Benutzer zur Eingabe von Initialisierungs Informationen auffordern soll.|  
|[Name der erneuten Form](./reshape-name-property-dynamic-ado.md)|Gibt einen Namen für das **Recordset** -Objekt an.|  
|[Befehl zum erneuten Synchronisieren](./resync-command-property-dynamic-ado.md)|Gibt eine vom Benutzer bereitgestellte Befehls Zeichenfolge an, mit der die Methode für die **erneute Synchronisierung** die Daten in der in der dynamischen Eigenschaft **Unique Table** genannten Tabelle aktualisiert.|  
|[Unique Table, Unique Schema, Unique Catalog](./unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|**Eindeutige Tabelle** Gibt den Namen der Basistabelle an, auf der Updates, Einfügungen und Löschungen zulässig sind.<br /><br /> Eindeutiges **Schema** Gibt das Schema oder den Namen des Besitzers der Tabelle an.<br /><br /> Eindeutiger **Katalog** Gibt den Katalog oder den Namen der Datenbank an, in der die Tabelle enthalten ist.|  
|[Neusynchronisierung aktualisieren](./update-resync-property-dynamic-ado.md)|Gibt an, ob auf die **UpdateBatch** -Methode ein impliziter Vorgang zum **erneuten Synchronisieren** der Methode folgt, und wenn ja, der Gültigkeitsbereich dieses Vorgangs.|
| &nbsp; | &nbsp; |

## <a name="see-also"></a>Weitere Informationen  
 [ADO-API-Referenz](./ado-api-reference.md)   
 [ADO-Sammlungen](./ado-collections.md)   
 [ADO-Enumerationskonstanten](./ado-enumerated-constants.md)   
 [Anhang B: ADO-Fehler](../../guide/appendixes/appendix-b-ado-errors.md)   
 [ADO-Ereignisse](./ado-events.md)   
 [ADO-Methoden](./ado-methods.md)   
 [ADO-Objektmodell](./ado-object-model.md)   
 [ADO-Objekte und-Schnittstellen](./ado-objects-and-interfaces.md)   
 [ADO-Eigenschaften](./ado-properties.md)