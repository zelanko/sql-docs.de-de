---
description: 'Anhang A: Daten-und Dienstanbieter'
title: 'Anhang A: Anbieter | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data providers [ADO]
- providers [ADO]
- ADO, providers
- service providers [ADO]
- service components [ADO]
ms.assetid: e2581b47-b11e-4e1e-b96c-d39c77c5b48a
author: rothja
ms.author: jroth
ms.openlocfilehash: d14a3399eb771965d039126ebf3672a8ad3d5190
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88396406"
---
# <a name="appendix-a-data-and-service-providers"></a>Anhang A: Daten-und Dienstanbieter
In diesem Abschnitt werden drei Arten von Anbietern behandelt: Datenanbieter, Dienstanbieter und Dienst Komponenten. Anbieter lassen sich in zwei Kategorien unterteilen: solche, die Daten bereitstellen Ein *Datenanbieter* besitzt seine eigenen Daten und macht Sie in tabellarischer Form für Ihre Anwendung verfügbar. Ein *Dienstanbieter* kapselt einen Dienst, indem er Daten erzeugt und nutzt, um Features in Ihren ADO-Anwendungen zu erweitern. Ein Dienstanbieter kann auch weiter als *Dienst Komponente*definiert werden, die zusammen mit anderen Dienstanbietern oder Komponenten verwendet werden muss.

## <a name="data-providers"></a>Datenanbieter
 ADO ist leistungsstark und flexibel, da es eine Verbindung mit einem von mehreren unterschiedlichen Datenanbietern herstellen kann und immer noch dasselbe Programmiermodell verfügbar macht, unabhängig von den spezifischen Features eines beliebigen Anbieters.

 Da jeder Datenanbieter eindeutig ist, variiert die Interaktion der Anwendung mit ADO jedoch geringfügig vom Datenanbieter. Die Unterschiede lassen sich normalerweise in eine von drei Kategorien unterteilen:

-   Verbindungsparameter in der [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) -Eigenschaft.

-   Verwendung des [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekts.

-   Anbieter spezifisches [recordsetverhalten](../../../ado/reference/ado-api/recordset-object-ado.md) .

 Details zu jedem der derzeit von Microsoft verfügbaren Datenanbietern werden wie folgt aufgelistet.

|Bereich|Thema|
|----------|-----------|
|ODBC-Datenbanken|[Microsoft OLE DB-Anbieter für ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)|
|Microsoft-Indizierungs Dienst|[Microsoft OLE DB-Anbieter für Microsoft Indexdienst](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md)|
|Azure Active Directory|[Microsoft OLE DB-Anbieter für Microsoft Active Directory Service](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md)|
|Microsoft Jet-Datenbanken|[OLE DB Anbieter für Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)|
|Microsoft SQL Server|[Microsoft OLE DB-Anbieter für SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)|
|Oracle-Datenbanken|[Microsoft OLE DB-Anbieter für Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md)|
|Internet Publishing|[Microsoft OLE DB-Anbieter für die Internet Veröffentlichung](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)|
|Einfache Datenquellen|[Microsoft OLE DB Simple-Anbieter](../../../ado/guide/appendixes/microsoft-ole-db-simple-provider.md)|

## <a name="provider-specific-dynamic-properties"></a>Anbieterspezifische dynamische Eigenschaften
 Die [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistungen der [Connection](../../../ado/reference/ado-api/connection-object-ado.md)-, [Command](../../../ado/reference/ado-api/command-object-ado.md)-und [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekte enthalten dynamische Eigenschaften, die für den Anbieter spezifisch sind. Diese Eigenschaften enthalten Informationen zu den Funktionen, die für den Anbieter spezifisch sind, über die von ADO unterstützten integrierten Eigenschaften hinaus.

 Nachdem Sie die Verbindung hergestellt und diese Objekte erstellt haben, verwenden Sie die [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) -Methode für die **Properties** -Auflistung des-Objekts, um die anbieterspezifischen Eigenschaften abzurufen. Ausführliche Informationen zu diesen dynamischen Eigenschaften finden Sie in der Dokumentation des Anbieters und im [OLE DB Programmierer-Handbuch](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8) .

## <a name="service-providers"></a>Dienstanbieter
 Wenn Sie einen Dienstanbieter verwenden möchten, müssen Sie ein Schlüsselwort angeben. Sie sollten auch die anbieterspezifischen dynamischen Eigenschaften kennen, die den einzelnen Dienstanbietern zugeordnet sind. Anbieterspezifische Details werden für jeden Dienstanbieter aufgelistet, der zurzeit von Microsoft zur Verfügung gestellt wird:

-   [Microsoft Data Shaping Service für OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)

-   [Microsoft OLE DB-Persistenzanbieter](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)

-   [Microsoft OLE DB Remoting-Anbieter](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)

## <a name="service-components"></a>Dienstkomponenten
 Der [Cursor Dienst für OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) Dienst Komponente ergänzt die Cursor Unterstützungsfunktionen von Datenanbietern. Außerdem ist ein Schlüsselwort erforderlich, das über dynamische Eigenschaften verfügt.

 Weitere Informationen zu OLE DB Anbietern finden Sie unter [Microsoft OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx).

## <a name="provider-commands"></a>Anbieter Befehle
 Für jeden hier aufgeführten Anbieter müssen Sie, wenn Ihre Anwendungen Benutzern gestatten, SQL-Anweisungen als Anbieter Befehle einzugeben, immer die Benutzereingaben überprüfen und potenzielle Hackerangriffe mithilfe potenziell gefährlicher SQL-Anweisungen, wie z `DROP TABLE t1` . b. als Teil der Benutzereingabe, überprüfen.

## <a name="see-also"></a>Weitere Informationen
 [Command Object (ADO)](../../../ado/reference/ado-api/command-object-ado.md) [-Verbindungs Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md) [Microsoft OLE DB Provider für Microsoft Active Directory Service](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md) [Microsoft OLE DB Provider for Microsoft-Indizierungs Dienst](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md) [Microsoft OLE DB Provider für ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md) [Microsoft OLE DB-Anbieter für Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md) [Microsoft OLE DB Provider für SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) [Microsoft OLE DB Provider für Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) [Properties Collection (](../../../ado/reference/ado-api/properties-collection-ado.md) ADO) Refresh-Methode (ADO) Refresh- [Recordset Object (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [Methode (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)
