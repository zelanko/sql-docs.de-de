---
title: Tabellenwertparameter-Rowseterstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, rowset creation
ms.assetid: ffe213ca-cc0e-465e-b31c-a8272324c4fe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de130ef821551383ada1a6df3574404cd3518e88
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153670"
---
# <a name="table-valued-parameter-rowset-creation"></a>Tabellenwertparameter-Rowseterstellung
  Consumer können zwar ein beliebiges Rowsetobjekt für Tabellenwertparameter bereitstellen, typische Rowsetobjekte werden jedoch mit Back-End-Datenspeichern implementiert und bieten somit nur eine eingeschränkte Leistung. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ermöglicht es somit Consumern, ein spezielles Rowsetobjekt auf speicherinternen Daten zu erstellen. Diese spezielle, in-Memory-Rowset-Objekt ist ein neues COM-Objekt, das Namen eines Tabellenwertparameter-Rowsets. Es bietet ähnliche Funktionen wie Parametersätze.  
  
 Tabellenwertparameter-Rowsetobjekte werden explizit vom Consumer für Eingabeparameter durch mehrere Schnittstellen auf Sitzungsebene erstellt. Es steht eine Instanz des Tabellenwertparameter-Rowsetobjekts pro Tabellenwertparameter zur Verfügung. Der Consumer kann die Tabellenwertparameter-Rowsetobjekte entweder durch Bereitstellen der Metadateninformationen, die bereits bekannt sind (statisches Szenario), oder durch Ermitteln über Anbieterschnittstellen (dynamisches Szenario) erstellen. In den folgenden Abschnitten werden diese beiden Szenarien beschrieben.  
  
## <a name="static-scenario"></a>Statisches Szenario  
 Wenn die Typinformationen bekannt ist, verwendet der Consumer ITableDefinitionWithConstraints::CreateTableWithConstraints einem Tabellenwertparameter-Rowset-Objekt zu instanziieren, das einem Tabellenwertparameter entspricht.  
  
 Die *Guid* Feld (*pTableID* Parameter) enthält die besondere GUID (CLSID_ROWSET_TVP). Das Element *pwszName* enthält den Namen des Tabellenwertparameter-Typs, den der Consumer instanziieren möchte. Das Feld *eKin* wird auf DBKIND_GUID_NAME festgelegt. Der Name ist erforderlich, wenn es sich um eine Ad-hoc-SQL-Anweisung handelt; bei einem Prozeduraufruf ist die Angabe des Namens optional.  
  
 Bei der Aggregation übergibt der Consumer die *pUnkOuter* Parameter steuernden IUnknown.  
  
 Die Eigenschaften des Tabellenwertparameter-Rowset-Objekts sind schreibgeschützt, sodass der Consumer nicht erwartet wird, um die Eigenschaften festgelegt werden, *RgPropertySets*.  
  
 Für das Element *rgPropertySets* jeder DBCOLUMNDESC-Struktur kann der Consumer zusätzliche Eigenschaften für jede Spalte angeben. Diese Eigenschaften gehören zum DBPROPSET_SQLSERVERCOLUMN-Eigenschaftensatz. Sie ermöglichen es Ihnen, berechnete und standardmäßige Einstellungen für jede Spalte anzugeben. Sie unterstützen auch vorhandene Spalteneigenschaften, z. B. NULL-Zulässigkeit und Identität.  
  
 Um entsprechende Informationen aus einem Tabellenwertparameter-Rowsetobjekt abzurufen, verwendet der Consumer IRowsetInfo::GetProperties.  
  
 Zum Abrufen von Informationen zu den Null, eindeutig ist, berechnet, und Aktualisieren des Status der einzelnen Spalten, IColumnsRowset:: GetColumnsRowset oder IColumnsInfo:: GetColumnInfo der Consumer verwenden. Diese Methoden stellen ausführliche Informationen über jede Tabellenwertparameter-Rowsetspalte bereit.  
  
 Der Consumer gibt den Typ jeder Spalte des Tabellenwertparameters an. Dies ähnelt der Angabe von Spalten, wenn in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Tabelle erstellt wird. Der Consumer erhält ein Tabellenwertparameter-Rowset-Objekt aus der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter über die *PpRowset* output-Parameter.  
  
## <a name="dynamic-scenario"></a>Dynamisches Szenario  
 Wenn der Consumer keine Typinformationen, sollte IOpenRowset:: OPENROWSET zum Instanziieren von Tabellenwertparameter-Rowsetobjekte verwendet werden. Der Consumer muss dem Anbieter somit nur den Typnamen zur Verfügung stellen.  
  
 In diesem Szenario erhält der Anbieter im Namen des Consumers Typinformationen zu einem Tabellenwertparameter-Rowsetobjekt vom Server.  
  
 Die *pTableID* und *pUnkOuter* Parameter wie beim statischen Szenario festgelegt werden. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erhält dann die Typinformationen (Spalteninformationen und Einschränkungen) vom Server, und ein Tabellenwertparameter-Rowsetobjekt durch Zurückgeben der *PpRowset* Parameter. Für diesen Vorgang ist eine Kommunikation mit dem Server notwendig, sodass die Leistung nicht so gut ist wie beim statischen Szenario. Das dynamische Szenario funktioniert nur mit parametrisierten Prozeduraufrufen.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenwertparameter &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
