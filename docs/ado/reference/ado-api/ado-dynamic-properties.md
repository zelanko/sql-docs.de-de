---
title: ADO – dynamische Eigenschaften | Microsoft-Dokumentation
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
manager: jroth
ms.openlocfilehash: 2ad6c2804b70011380a12b5b9e0cd1f52fd56398
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66696868"
---
# <a name="ado-dynamic-properties"></a>ADO – dynamische Eigenschaften
Dynamische Eigenschaften hinzugefügt werden können die [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Sammlungen von der [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md), [Befehl](../../../ado/reference/ado-api/command-object-ado.md), oder [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekte. Die Quelle für diese Eigenschaften ist entweder ein Datenanbieter, wie z. B. die [OLE DB-Anbieter für SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), oder ein Dienstanbieter, wie z. B. die [Microsoft Cursor Service für OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md). Finden Sie in der entsprechenden Datenanbieter oder die Dokumentation von Service Provider für Weitere Informationen zu einer bestimmten dynamische Eigenschaft.  
  
 Die [ADO dynamische Property-Index](../../../ado/reference/ado-api/ado-dynamic-property-index.md) stellt einen Querverweis zwischen den ADO und OLE DB-Namen für jede dynamische Eigenschaft der standard OLE DB-Anbieter bereit.  
  
 Die folgenden dynamischen Eigenschaften sind besonders interessant, und auch in den Quellen, die zuvor erwähnten dokumentiert sind. Spezielle Funktionen mit ADO ist in den ADO-Hilfethemen in der folgenden Liste dokumentiert.  
  
|||  
|-|-|  
|[Optimieren](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)|Gibt an, ob ein Index für dieses Feld erstellt werden soll.|  
|[Prompt](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)|Gibt an, ob der OLE DB-Anbieter, den Benutzer zur Initialisierung auffordert.|  
|[Reshape Name](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)|Gibt einen Namen für die **Recordset** Objekt.|  
|[Resync-Befehl](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)|Gibt an, ein benutzerdefinierten Befehl-Zeichenfolge, die **Resync** Probleme der Methode zum Aktualisieren der Daten in der Tabelle, die mit dem Namen in der **eindeutige Tabelle** dynamische Eigenschaft.|  
|[Unique Table, Unique Schema und Unique Catalog](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|**Eindeutige Tabelle** gibt den Namen der Basistabelle, auf denen Updates, einfügungen und löschungen zulässig sind.<br /><br /> **Eindeutiges Schema** gibt an, das Schema oder die Namen des Besitzers der Tabelle.<br /><br /> **Eindeutige Katalogressource** gibt an, den Katalog oder die Namen der Datenbank, die die Tabelle enthält.|  
|[Aktualisieren Sie die erneute Synchronisierung](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)|Gibt an, ob die **UpdateBatch** Methode einen impliziten folgt **Resync** Vorgangs-Methode, und wenn Ja, im Rahmen dieses Vorgangs.|  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-API-Referenz](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO-Collections](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO – Enumerationskonstanten](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Anhang B: ADO-Fehler](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO-Ereignisse](../../../ado/reference/ado-api/ado-events.md)   
 [ADO-Methoden](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO-Objektmodell](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO-Objekte und Schnittstellen](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [ADO-Eigenschaften](../../../ado/reference/ado-api/ado-properties.md)
