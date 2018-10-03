---
title: Tabellenwertparameter-Rowseterstellung | Microsoft-Dokumentation
description: Statische und dynamische Tabellenwertparameter-rowseterstellung
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, rowset creation
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 2b8e85b4ebfa679dda4e980df54cd11a06b1946d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47805398"
---
# <a name="table-valued-parameter-rowset-creation"></a>Tabellenwertparameter-Rowseterstellung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Consumer können zwar ein beliebiges Rowsetobjekt für Tabellenwertparameter bereitstellen, typische Rowsetobjekte werden jedoch mit Back-End-Datenspeichern implementiert und bieten somit nur eine eingeschränkte Leistung. Der OLE DB-Treiber für SQL Server ermöglicht es somit Consumern, ein spezielles Rowset-Objekt auf speicherinternen Daten zu erstellen. Diese spezielle, in-Memory-Rowset-Objekt ist ein neues COM-Objekt, das Namen eines Tabellenwertparameter-Rowsets. Es bietet ähnliche Funktionen wie Parametersätze.  
  
 Tabellenwertparameter-Rowsetobjekte werden explizit vom Consumer für Eingabeparameter durch mehrere Schnittstellen auf Sitzungsebene erstellt. Es steht eine Instanz des Tabellenwertparameter-Rowsetobjekts pro Tabellenwertparameter zur Verfügung. Der Consumer kann die Tabellenwertparameter-Rowsetobjekte entweder durch Bereitstellen der Metadateninformationen, die bereits bekannt sind (statisches Szenario), oder durch Ermitteln über Anbieterschnittstellen (dynamisches Szenario) erstellen. In den folgenden Abschnitten werden diese beiden Szenarien beschrieben.  
  
## <a name="static-scenario"></a>Statisches Szenario  
 Wenn die Typinformationen bekannt ist, verwendet der Consumer ITableDefinitionWithConstraints::CreateTableWithConstraints einem Tabellenwertparameter-Rowset-Objekt zu instanziieren, das einem Tabellenwertparameter entspricht.  
  
 Die *Guid* Feld (*pTableID* Parameter) enthält die besondere GUID (CLSID_ROWSET_TVP). Das Element *pwszName* enthält den Namen des Tabellenwertparameter-Typs, den der Consumer instanziieren möchte. Das Feld *eKin* wird auf DBKIND_GUID_NAME festgelegt. Der Name ist erforderlich, wenn es sich um eine Ad-hoc-SQL-Anweisung handelt; bei einem Prozeduraufruf ist die Angabe des Namens optional.  
  
 Bei der Aggregation übergibt der Consumer die *pUnkOuter* Parameter steuernden IUnknown.  
  
 Die Eigenschaften des Tabellenwertparameter-Rowsetobjekts sind schreibgeschützt, sodass der Consumer keine Eigenschaften in *rgPropertySets* festlegen muss.  
  
 Für das Element *rgPropertySets* jeder DBCOLUMNDESC-Struktur kann der Consumer zusätzliche Eigenschaften für jede Spalte angeben. Diese Eigenschaften gehören zum DBPROPSET_SQLSERVERCOLUMN-Eigenschaftensatz. Sie ermöglichen es Ihnen, berechnete und standardmäßige Einstellungen für jede Spalte anzugeben. Sie unterstützen auch vorhandene Spalteneigenschaften, z. B. NULL-Zulässigkeit und Identität.  
  
 Um entsprechende Informationen aus einem Tabellenwertparameter-Rowsetobjekt abzurufen, verwendet der Consumer IRowsetInfo::GetProperties.  
  
 Zum Abrufen von Informationen zu den Null, eindeutig ist, berechnet, und Aktualisieren des Status der einzelnen Spalten, kann der Consumer IColumnsRowset:: GetColumnsRowset oder IColumnsInfo:: GetColumnInfo verwenden. Diese Methoden stellen ausführliche Informationen über jede Tabellenwertparameter-Rowsetspalte bereit.  
  
 Der Consumer gibt den Typ jeder Spalte des Tabellenwertparameters an. Dies ähnelt der Angabe von Spalten, wenn in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eine Tabelle erstellt wird. Der Consumer erhält ein Tabellenwertparameter-Rowsetobjekt aus der OLE DB-Treiber für SQL Server über die *PpRowset* output-Parameter.  
  
## <a name="dynamic-scenario"></a>Dynamisches Szenario  
 Wenn der Consumer keine Typinformationen besitzt, sollte IOpenRowset:: OPENROWSET zum Instanziieren von Tabellenwertparameter-Rowsetobjekte verwendet werden. Der Consumer muss dem Anbieter somit nur den Typnamen zur Verfügung stellen.  
  
 In diesem Szenario erhält der Anbieter im Namen des Consumers Typinformationen zu einem Tabellenwertparameter-Rowsetobjekt vom Server.  
  
 Die *pTableID* und *pUnkOuter* Parameter wie beim statischen Szenario festgelegt werden. Der OLE DB-Treiber für SQL Server erhält dann die Typinformationen (Spalteninformationen und Einschränkungen) vom Server und gibt über den Parameter *ppRowset* ein Tabellenwertparameter-Rowsetobjekt zurück. Für diesen Vorgang ist eine Kommunikation mit dem Server notwendig, sodass die Leistung nicht so gut ist wie beim statischen Szenario. Das dynamische Szenario funktioniert nur mit parametrisierten Prozeduraufrufen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Tabellenwertparameter &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
