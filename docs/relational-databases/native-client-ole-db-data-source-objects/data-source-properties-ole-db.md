---
title: Datenquelleneigenschaften (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 6e14fefc-4e0b-4847-a833-4cf0abe65d50
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c05c16a608081e33a06007830416560f3ef30b9c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297302"
---
# <a name="data-source-properties-ole-db"></a>Datenquelleneigenschaften (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter implementiert Datenquelleneigenschaften wie folgt.  
  
|Eigenschafts-ID|Beschreibung|  
|-----------------|-----------------|  
|DBPROP_CURRENTCATALOG|R/W: Lesen/Schreiben; Standardwert: Keiner<br /><br /> Beschreibung: Der Wert von DBPROP_CURRENTCATALOG meldet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die aktuelle Datenbank für eine native Client-OLE-DB-Anbietersitzung. Das Festlegen des Eigenschaftswerts hat dieselbe Auswirkung wie das Festlegen der aktuellen Datenbank mithilfe der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung *USE* database.<br /><br /> Ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] gibt DBPROP_CURRENTCATALOG den Datenbanknamen in Kleinbuchstaben zurück, wenn Sie [sp_defaultdb](../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md) aufrufen und den Datenbanknamen in Kleinbuchstaben angeben, auch wenn die Datenbank ursprünglich mit einem Namen in Groß- und Kleinbuchstaben erstellt wurde. In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt DBPROP_CURRENTCATALOG den erwarteten Namen mit Groß- und Kleinbuchstaben zurück.|  
|DBPROP_MULTIPLECONNECTIONS|R/W: Lesen/Schreiben; Standardwert: VARIANT_FALSE<br /><br /> Beschreibung: Wenn während der Verbindung ein Befehl ausgeführt wird, der kein Rowset produziert, oder der ein Rowset produziert, das kein Servercursor ist, und Sie einen anderen Befehl ausführen, wird eine neue Verbindung erstellt, um den neuen Befehl auszuführen, wenn für DBPROP_MULTIPLECONNECTIONS VARIANT_TRUE festgelegt ist.<br /><br /> Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter erstellt keine weitere Verbindung, wenn DBPROP_MULTIPLECONNECTION VARIANT_FALSE ist oder wenn eine Transaktion für die Verbindung aktiv ist. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter gibt DB_E_OBJECTOPEN zurück, wenn DBPROP_MULTIPLECONNECTIONS VARIANT_FALSE ist, und gibt E_FAIL zurück, wenn eine aktive Transaktion vorhanden ist. Transaktionen und Sperren werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf Verbindungsbasis verwaltet. Wenn eine zweite Verbindung hergestellt wird, nutzen die Befehle auf den anderen Verbindungen Sperren nicht gemeinsam. Um zu gewährleisten, dass ein Befehl einen anderen nicht blockiert, halten Sie Zeilen gesperrt, die von dem anderen Befehl angefordert werden. Dies gilt auch beim Erstellen mehrerer Sitzungen.<br /><br /> Jede Sitzung verfügt über eine separate Verbindung.|  
  
 Im anbieterspezifischen Eigenschaftensatz DBPROPSET_SQLSERVERDATASOURCE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definiert der native Client-OLE-DB-Anbieter die folgenden zusätzlichen Datenquelleneigenschaften.  
  
|Eigenschafts-ID|Beschreibung|  
|-----------------|-----------------|  
|SSPROP_ENABLEFASTLOAD|R/W: Lesen/Schreiben; Standardwert: VARIANT_FALSE<br /><br /> Beschreibung: Um Massenkopiervorgänge aus dem Speicher zu aktivieren, sollte die SSPROP_ENABLEFASTLOAD-Eigenschaft auf VARIANT_TRUE festgelegt werden. Wenn diese Eigenschaft für die Datenquelle festgelegt wurde, lässt die neu erstellte Sitzung den Consumerzugriff auf die [IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)-Schnittstelle zu.<br /><br /> Wenn die Eigenschaft auf VARIANT_TRUE festgelegt ist, ist die **IRowsetFastLoad**-Schnittstelle über **IOpenRowset::OpenRowset** verfügbar, indem die **IID_IRowsetFastLoad**-Schnittstelle angefordert oder** SSPROP_IRowsetFastLoad** auf VARIANT_TRUE festgelegt wird.|  
|SSPROP_ENABLEBULKCOPY|R/W: Lesen/Schreiben; Standardwert: VARIANT_FALSE<br /><br /> Beschreibung: Um Massenkopiervorgänge aus Dateien zu aktivieren, sollte die SSPROP_ENABLEBULKCOPY-Eigenschaft auf VARIANT_TRUE festgelegt werden. Wenn diese Eigenschaft für die Datenquelle festgelegt wurde, ist der Consumerzugriff auf die IBCPSession-Schnittstelle auf derselben Ebene verfügbar wie Sessions.<br /><br /> Auch SSPROP_IRowsetFastLoad muss auf VARIANT_TRUE festgelegt werden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenquellenobjekte &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
