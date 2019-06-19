---
title: ADO-Objekte und Schnittstellen | Microsoft-Dokumentation
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
manager: jroth
ms.openlocfilehash: 48b1f3794828af7f60c1d00313506fa9f9c522c8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66696632"
---
# <a name="ado-objects-and-interfaces"></a>ADO-Objekte und -Schnittstellen
Die Beziehungen zwischen diesen Objekten werden dargestellt, der [ADO-Objektmodell](../../../ado/reference/ado-api/ado-object-model.md).  
  
 Jedes Objekt kann in der entsprechenden Auflistung enthalten sein. Z. B. eine [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt enthalten einer [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung. Weitere Informationen finden Sie unter [ADO-Collections](../../../ado/reference/ado-api/ado-collections.md) oder ein Thema der bestimmten Sammlung.  
  
|||  
|-|-|  
|[IADOCommandConstruction](https://msdn.microsoft.com/library/windows/desktop/aa965677.aspx)|Zum Abrufen der zugrunde liegenden OLE DB-Befehl von einem Objekt ADOCommand verwendet.|  
|[ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)|Erstellt ein ADO **Datensatz** Objekt von einem OLE DB **Zeile** Objekts in einer C/C++-Anwendung.|  
|[ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)|Erstellt ein ADO **Recordset** Objekt von einem OLE DB **Rowset** Objekts in einer C/C++-Anwendung.|  
|[ADOStreamConstruction-Schnittstelle](../../../ado/reference/ado-api/adostreamconstruction-interface.md)|Erstellt ein ADO **Stream** Objekt von einem OLE DB **IStream** Objekts in einer C/C++-Anwendung.|  
|[Befehl](../../../ado/reference/ado-api/command-object-ado.md)|Definiert einen bestimmten Befehl, den Sie für eine Datenquelle ausführen möchten.<br /><br /> Die **Befehl** Objekt ist nicht sicher für Skripting.|  
|[Verbindung](../../../ado/reference/ado-api/connection-object-ado.md)|Stellt eine offene Verbindung mit einer Datenquelle dar.<br /><br /> Die **Verbindung** Objekt für die Skripterstellung sicher ist.|  
|[IDSOShapeExtensions-Schnittstelle](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)|Ruft das zugrunde liegende Objekt für den OLE DB-Datenquelle für das SHAPE-Anbieter ab.|  
|[Fehler](../../../ado/reference/ado-api/error-object.md)|Enthält Details über den Datenzugriff, die auf einem einzigen Vorgang im Zusammenhang mit der Anbieter beziehen.<br /><br /> Die **Fehler** Objekt ist nicht sicher für Skripting.|  
|[Feld](../../../ado/reference/ado-api/field-object.md)|Stellt eine Spalte mit einem gemeinsamen Datentyp.|  
|[Parameter](../../../ado/reference/ado-api/parameter-object.md)|Stellt einen Parameter oder die zugeordnete Argument ein **Befehl** -Objekt auf Grundlage einer parametrisierten Abfrage oder gespeicherten Prozedur.<br /><br /> Die **Parameter** Objekt ist nicht sicher für Skripting.|  
|[Eigenschaft](../../../ado/reference/ado-api/property-object-ado.md)|Repräsentiert eine dynamische Eigenschaft eines ADO-Objekts, das vom Anbieter definiert ist.|  
|[Record](../../../ado/reference/ado-api/record-object-ado.md)|Stellt eine Zeile einer **Recordset**, oder ein Verzeichnis oder eine Datei in einem Dateisystem. Die **Datensatz** Objekt für die Skripterstellung sicher ist.|  
|[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)|Stellt die Gruppe von Datensätzen aus einer Basistabelle oder die Ergebnisse eines ausgeführten Befehls dar. Zu jedem Zeitpunkt den **Recordset** -Objekt verweist auf nur einen einzelnen Datensatz in der Gruppe als aktuellen Datensatz.<br /><br /> Die **Recordset** Objekt für die Skripterstellung sicher ist.|  
|[Stream](../../../ado/reference/ado-api/stream-object-ado.md)|Stellt einen binären Datenstrom dar.<br /><br /> Die **Stream** Objekt für die Skripterstellung sicher ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-API-Referenz](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO-Collections](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO – dynamische Eigenschaften](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [ADO – Enumerationskonstanten](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Anhang B: ADO-Fehler](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO-Ereignisse](../../../ado/reference/ado-api/ado-events.md)   
 [ADO-Methoden](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO-Objektmodell](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO-Eigenschaften](../../../ado/reference/ado-api/ado-properties.md)
