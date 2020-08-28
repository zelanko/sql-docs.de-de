---
description: ADO-Objekte und -Schnittstellen
title: ADO-Objekte und-Schnittstellen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, objects and interfaces
- objects [ADO]
ms.assetid: d0b7e254-c89f-4406-b846-a060ef038c30
author: rothja
ms.author: jroth
ms.openlocfilehash: 80391605a0480d8967afb1e0240168a393f09363
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88976311"
---
# <a name="ado-objects-and-interfaces"></a>ADO-Objekte und -Schnittstellen
Die Beziehungen zwischen diesen Objekten werden im ADO- [Objektmodell](./ado-object-model.md)dargestellt.  
  
 Jedes-Objekt kann in der entsprechenden-Auflistung enthalten sein. Ein [Fehler](./error-object.md) Objekt kann z. b. in einer [Fehler](./errors-collection-ado.md) Auflistung enthalten sein. Weitere Informationen finden Sie unter [ADO Collections](./ado-collections.md) or a specific Collection Topic.  
  
|Objekt oder Schnittstelle|Beschreibung|  
|-|-|  
|[Iadocommandconstruction](/previous-versions/windows/desktop/aa965677(v=vs.85))|Wird verwendet, um den zugrunde liegenden OLEDB-Befehl aus einem ADOCommand-Objekt abzurufen.|  
|[Adorecordconstruction](./adorecordconstruction-interface.md)|Erstellt ein ADO- **Daten Satz** Objekt aus einem OLE DB **Row** -Objekt in einer C/C++-Anwendung.|  
|[Adorecordsetconstruction](./adorecordsetconstruction-interface.md)|Erstellt ein ADO- **Recordset** -Objekt aus einem OLE DB Rowsetobjekt in einer C/C++-Anwendung. **Rowset**|  
|[ADOStreamConstruction-Schnittstelle](./adostreamconstruction-interface.md)|Erstellt ein ADO- **Streamobjekt** aus einem OLE DB **IStream** -Objekt in einer C/C++-Anwendung.|  
|[Befehl](./command-object-ado.md)|Definiert einen bestimmten Befehl, den Sie für eine Datenquelle ausführen möchten.<br /><br /> Das **Command** -Objekt ist für die Skripterstellung nicht sicher.|  
|[Connection](./connection-object-ado.md)|Stellt eine offene Verbindung mit einer Datenquelle dar.<br /><br /> Das **Verbindungs** Objekt ist für die Skripterstellung sicher.|  
|[IDSOShapeExtensions-Schnittstelle](./idsoshapeextensions-interface.md)|Ruft das zugrunde liegende OLEDB-Datenquellen Objekt für den Shape-Anbieter ab.|  
|[Fehler](./error-object.md)|Enthält Details zu Datenzugriffs Fehlern, die sich auf einen einzelnen Vorgang beziehen, der den Anbieter einbezieht.<br /><br /> Das **Fehler** Objekt ist für die Skripterstellung nicht sicher.|  
|[Feld](./field-object.md)|Stellt eine Datenspalte mit einem gemeinsamen Datentyp dar.|  
|[Parameter](./parameter-object.md)|Stellt einen Parameter oder ein Argument dar, der einem **Befehls** Objekt auf Grundlage einer parametrisierten Abfrage oder gespeicherten Prozedur zugeordnet ist.<br /><br /> Das **Parameter** Objekt ist für die Skripterstellung nicht sicher.|  
|[Eigenschaft](./property-object-ado.md)|Stellt eine dynamische Eigenschaft eines ADO-Objekts dar, das vom Anbieter definiert wird.|  
|[Datensatz](./record-object-ado.md)|Stellt eine Zeile eines **Recordsets**oder ein Verzeichnis oder eine Datei in einem Dateisystem dar. Das **Daten Satz** Objekt ist für die Skripterstellung sicher.|  
|[Recordset](./recordset-object-ado.md)|Stellt den Satz von Datensätzen aus einer Basistabelle oder die Ergebnisse eines ausgeführten Befehls dar. Das **Recordset** -Objekt bezieht sich jederzeit auf einen einzelnen Datensatz innerhalb des Satzes als aktuellen Datensatz.<br /><br /> Das **Recordset** -Objekt ist für die Skripterstellung sicher.|  
|[Stream](./stream-object-ado.md)|Stellt einen binären Datenstrom dar.<br /><br /> Das **Stream** -Objekt ist für die Skripterstellung sicher.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-API-Referenz](./ado-api-reference.md)   
 [ADO-Sammlungen](./ado-collections.md)   
 [Dynamische ADO-Eigenschaften](./ado-dynamic-properties.md)   
 [ADO-Enumerationskonstanten](./ado-enumerated-constants.md)   
 [Anhang B: ADO-Fehler](../../guide/appendixes/appendix-b-ado-errors.md)   
 [ADO-Ereignisse](./ado-events.md)   
 [ADO-Methoden](./ado-methods.md)   
 [ADO-Objektmodell](./ado-object-model.md)   
 [ADO-Eigenschaften](./ado-properties.md)