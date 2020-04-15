---
title: Tabellenwertparameter (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, table-valued parameters
- table-valued parameters (OLE DB)
ms.assetid: 4298b73d-615b-4d28-9843-03b4d5fc489e
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 15055f582d7add6194753e2743d63b5e082318b5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300230"
---
# <a name="table-valued-parameters-ole-db"></a>Tabellenwertparameter (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In diesem Abschnitt wird die Unterstützung für Tabellenwertparameter in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter beschrieben. Weitere Übersichtsinformationen finden Sie unter [Tabellenwertparameter &#40;SQL Server Native Client&#41;](../../relational-databases/native-client/features/table-valued-parameters-sql-server-native-client.md). Ein Beispiel finden Sie unter [Verwenden von Tabellenwertparametern (OLE DB)](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md).  
  
## <a name="remarks"></a>Bemerkungen  
 Derzeit können Sie mehrzeilige Daten an den Server als Parameter an eine Prozedur mit Parametersätzen senden (der DBPARAMS-Parameter in **ICommand::Execute**). Bei Parametersätzen muss jedes Element des Satzes in einer separaten Remoteprozeduranforderung (Remote Procedure Call, RPC) an den Server gesendet werden. Tabellenwertparameter stellen eine ähnliche Funktionalität bereit, bieten jedoch eine bessere Integration mit dem Server. Dadurch werden die Anzahl von RPC-Anforderungen reduziert und setbasierte Vorgänge auf dem Server aktiviert.  
  
 Tabellenwertparameter werden in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider als OLE DB **Rowset-Objekte** unterstützt. Jedes **Rowset-Objekt** kann vom Consumer (d. h. der Clientanwendung, die den nativen Client-OLE-DB-Anbieter verwendet) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Platzhalter für Parameterparameter mit Tabellenwert bereitgestellt werden. Tabellenwertparameter werden wie andere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Parametertypen behandelt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt Erstellungs-, Ermittlungs-, Spezifizierungs-, Bindungs- und Schemaschnittstellen zur Verfügung.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Tabellenwertparameter-Rowseterstellung](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)  
  
-   [Tabellenwertparameter-Typermittlung](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md)  
  
-   [Ausführen von Befehlen, die Tabellenwertparameter enthalten](../../relational-databases/native-client-ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md)  
  
-   [Einfügen von Daten in Tabellenwertparameter](../../relational-databases/native-client-ole-db-table-valued-parameters/inserting-data-into-table-valued-parameters.md)  
  
-   [Schemarowsets für OLE DB-Tabellenwertparameter geändert](../../relational-databases/native-client-ole-db-table-valued-parameters/schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [OLE DB-Typunterstützung für Tabellenwertparameter](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)  
  
-   [OLE DB-Unterstützung für Tabellenwertparameter-Typen &#40;Methoden&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [OLE DB-Unterstützung für Tabellenwertparameter-Typen &#40;Eigenschaften&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
