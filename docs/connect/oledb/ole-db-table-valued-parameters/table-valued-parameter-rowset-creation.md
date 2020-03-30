---
title: Tabellenwertparameter für die Rowseterstellung | Microsoft-Dokumentation
description: Statische und dynamische Tabellenwertparameter für die Rowseterstellung
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
ms.openlocfilehash: c771d8bde657b464b29a109dadd7a4d6fa33fbdb
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67994109"
---
# <a name="table-valued-parameter-rowset-creation"></a>Tabellenwertparameter-Rowseterstellung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Consumer können zwar ein beliebiges Rowsetobjekt für Tabellenwertparameter bereitstellen, typische Rowsetobjekte werden jedoch mit Back-End-Datenspeichern implementiert und bieten somit nur eine eingeschränkte Leistung. Der OLE DB-Treiber für SQL Server ermöglicht es somit Consumern, ein spezielles Rowset-Objekt auf speicherinternen Daten zu erstellen. Dieses besondere Rowsetobjekt im Arbeitsspeicher ist ein neues COM-Objekt, das als Tabellenwertparameter für Rowsets bezeichnet wird. Es bietet ähnliche Funktionen wie Parametersätze.  
  
 Tabellenwertparameter-Rowsetobjekte werden explizit vom Consumer für Eingabeparameter durch mehrere Schnittstellen auf Sitzungsebene erstellt. Es steht eine Instanz des Tabellenwertparameter-Rowsetobjekts pro Tabellenwertparameter zur Verfügung. Der Consumer kann die Tabellenwertparameter-Rowsetobjekte entweder durch Bereitstellen der Metadateninformationen, die bereits bekannt sind (statisches Szenario), oder durch Ermitteln über Anbieterschnittstellen (dynamisches Szenario) erstellen. In den folgenden Abschnitten werden diese beiden Szenarien beschrieben.  
  
## <a name="static-scenario"></a>Statisches Szenario  
 Wenn die Typinformationen bekannt sind, verwendet der Consumer ITableDefinitionWithConstraints::CreateTableWithConstraints, um einen Tabellenwertparameter für Rowsetobjekte zu instanziieren, die einem Tabellenwertparameter entsprechen.  
  
 Das *guid*-Feld (*pTableID*-Parameter) enthält die besondere GUID (CLSID_ROWSET_TVP). Das Element *pwszName* enthält den Namen des Tabellenwertparameter-Typs, den der Consumer instanziieren möchte. Das Feld *eKin* wird auf DBKIND_GUID_NAME festgelegt. Der Name ist erforderlich, wenn es sich um eine Ad-hoc-SQL-Anweisung handelt; bei einem Prozeduraufruf ist die Angabe des Namens optional.  
  
 Bei der Aggregation übergibt der Consumer den *pUnkOuter*-Parameter mit dem kontrollierenden IUnknown-Element.  
  
 Die Eigenschaften des Tabellenwertparameter-Rowsetobjekts sind schreibgeschützt, sodass der Consumer keine Eigenschaften in *rgPropertySets* festlegen muss.  
  
 Für das Element *rgPropertySets* jeder DBCOLUMNDESC-Struktur kann der Consumer zusätzliche Eigenschaften für jede Spalte angeben. Diese Eigenschaften gehören zum DBPROPSET_SQLSERVERCOLUMN-Eigenschaftensatz. Sie ermöglichen es Ihnen, berechnete und standardmäßige Einstellungen für jede Spalte anzugeben. Sie unterstützen auch vorhandene Spalteneigenschaften, z. B. NULL-Zulässigkeit und Identität.  
  
 Um entsprechende Informationen aus einem Tabellenwertparameter-Rowsetobjekt abzurufen, verwendet der Consumer IRowsetInfo::GetProperties.  
  
 Der Consumer kann IColumnsRowset::GetColumnsRowset oder IColumnsInfo::GetColumnInfo verwenden, um Informationen über die Statusangaben „NULL“, „Eindeutig“, „Berechnet“ und „Update“ für die einzelnen Spalten abzurufen. Diese Methoden stellen ausführliche Informationen über jede Tabellenwertparameter-Rowsetspalte bereit.  
  
 Der Consumer gibt den Typ jeder Spalte des Tabellenwertparameters an. Dies ähnelt der Angabe von Spalten, wenn in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eine Tabelle erstellt wird. Der Consumer erhält vom OLE DB-Treiber für SQL Server über den *ppRowset*-Ausgabeparameter ein Rowsetobjekt für Tabellenwertparameter.  
  
## <a name="dynamic-scenario"></a>Dynamisches Szenario  
 Wenn der Consumer keine Typinformationen hat, sollte IOpenRowset::OpenRowset zum Instanziieren von Rowsetobjekten für Tabellenwertparameter verwendet werden. Der Consumer muss dem Anbieter somit nur den Typnamen zur Verfügung stellen.  
  
 In diesem Szenario erhält der Anbieter im Namen des Consumers Typinformationen zu einem Tabellenwertparameter-Rowsetobjekt vom Server.  
  
 Die Parameter *pTableID* und *pUnkOuter* sollten wie im statischen Szenario festgelegt werden. Der OLE DB-Treiber für SQL Server erhält dann die Typinformationen (Spalteninformationen und Einschränkungen) vom Server und gibt über den Parameter *ppRowset* ein Tabellenwertparameter-Rowsetobjekt zurück. Für diesen Vorgang ist eine Kommunikation mit dem Server notwendig, sodass die Leistung nicht so gut ist wie beim statischen Szenario. Das dynamische Szenario funktioniert nur mit parametrisierten Prozeduraufrufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenwertparameter &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
