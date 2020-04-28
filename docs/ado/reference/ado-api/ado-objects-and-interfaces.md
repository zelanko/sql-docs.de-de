---
title: ADO-Objekte und-Schnittstellen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, objects and interfaces
- objects [ADO]
ms.assetid: d0b7e254-c89f-4406-b846-a060ef038c30
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e5ecc6de67defb2366bf208c38bd2de5bff643e4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67920906"
---
# <a name="ado-objects-and-interfaces"></a>ADO-Objekte und -Schnittstellen
Die Beziehungen zwischen diesen Objekten werden im ADO- [Objektmodell](../../../ado/reference/ado-api/ado-object-model.md)dargestellt.  
  
 Jedes-Objekt kann in der entsprechenden-Auflistung enthalten sein. Ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt kann z. b. in einer [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung enthalten sein. Weitere Informationen finden Sie unter [ADO Collections](../../../ado/reference/ado-api/ado-collections.md) or a specific Collection Topic.  
  
|||  
|-|-|  
|[Iadocommandconstruction](https://msdn.microsoft.com/library/windows/desktop/aa965677.aspx)|Wird verwendet, um den zugrunde liegenden OLEDB-Befehl aus einem ADOCommand-Objekt abzurufen.|  
|[Adorecordconstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)|Erstellt ein ADO- **Daten Satz** Objekt aus einem OLE DB **Row** -Objekt in einer C/C++-Anwendung.|  
|[Adorecordsetconstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)|Erstellt ein ADO- **Recordset** -Objekt aus einem OLE DB Rowsetobjekt in einer C/C++-Anwendung. **Rowset**|  
|[ADOStreamConstruction-Schnittstelle](../../../ado/reference/ado-api/adostreamconstruction-interface.md)|Erstellt ein ADO- **Streamobjekt** aus einem OLE DB **IStream** -Objekt in einer C/C++-Anwendung.|  
|[Befehl](../../../ado/reference/ado-api/command-object-ado.md)|Definiert einen bestimmten Befehl, den Sie für eine Datenquelle ausführen möchten.<br /><br /> Das **Command** -Objekt ist für die Skripterstellung nicht sicher.|  
|[Connection](../../../ado/reference/ado-api/connection-object-ado.md)|Stellt eine offene Verbindung mit einer Datenquelle dar.<br /><br /> Das **Verbindungs** Objekt ist für die Skripterstellung sicher.|  
|[IDSOShapeExtensions-Schnittstelle](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)|Ruft das zugrunde liegende OLEDB-Datenquellen Objekt für den Shape-Anbieter ab.|  
|[Fehler](../../../ado/reference/ado-api/error-object.md)|Enthält Details zu Datenzugriffs Fehlern, die sich auf einen einzelnen Vorgang beziehen, der den Anbieter einbezieht.<br /><br /> Das **Fehler** Objekt ist für die Skripterstellung nicht sicher.|  
|[Feld](../../../ado/reference/ado-api/field-object.md)|Stellt eine Datenspalte mit einem gemeinsamen Datentyp dar.|  
|[Parameter](../../../ado/reference/ado-api/parameter-object.md)|Stellt einen Parameter oder ein Argument dar, der einem **Befehls** Objekt auf Grundlage einer parametrisierten Abfrage oder gespeicherten Prozedur zugeordnet ist.<br /><br /> Das **Parameter** Objekt ist für die Skripterstellung nicht sicher.|  
|[Eigenschaft](../../../ado/reference/ado-api/property-object-ado.md)|Stellt eine dynamische Eigenschaft eines ADO-Objekts dar, das vom Anbieter definiert wird.|  
|[Aufnahme](../../../ado/reference/ado-api/record-object-ado.md)|Stellt eine Zeile eines **Recordsets**oder ein Verzeichnis oder eine Datei in einem Dateisystem dar. Das **Daten Satz** Objekt ist für die Skripterstellung sicher.|  
|[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)|Stellt den Satz von Datensätzen aus einer Basistabelle oder die Ergebnisse eines ausgeführten Befehls dar. Das **Recordset** -Objekt bezieht sich jederzeit auf einen einzelnen Datensatz innerhalb des Satzes als aktuellen Datensatz.<br /><br /> Das **Recordset** -Objekt ist für die Skripterstellung sicher.|  
|[Stream](../../../ado/reference/ado-api/stream-object-ado.md)|Stellt einen binären Datenstrom dar.<br /><br /> Das **Stream** -Objekt ist für die Skripterstellung sicher.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-API-Referenz](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO-Sammlungen](../../../ado/reference/ado-api/ado-collections.md)   
 [Dynamische ADO-Eigenschaften](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [ADO-Enumerationskonstanten](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Anhang B: ADO-Fehler](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO-Ereignisse](../../../ado/reference/ado-api/ado-events.md)   
 [ADO-Methoden](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO-Objektmodell](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO-Eigenschaften](../../../ado/reference/ado-api/ado-properties.md)
