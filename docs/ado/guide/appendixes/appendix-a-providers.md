---
title: 'Anhang A: Anbieter | Microsoft-Dokumentation'
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4ffecfc87ec23fc4d62174dae31220511c9f72d4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67926970"
---
# <a name="appendix-a-data-and-service-providers"></a>Anhang A: Daten und Dienstanbieter
In diesem Abschnitt werden drei Arten von Anbietern: Datenanbieter, Dienstanbietern und Dienstkomponenten. Anbieter können in zwei Kategorien unterteilt: die Bereitstellung von Daten und die Dienste bereitstellen. Ein *Datenanbieter* besitzt seine eigenen Daten und macht Sie sie in tabellarischer Form für Ihre Anwendung verfügbar. Ein *Dienstanbieter* kapselt einen Dienst starten, indem Sie erzeugen und Nutzen von Daten, die Funktionen in den ADO-Anwendungen zu erweitern. Ein Dienstanbieter sind als auch noch weiter definiert eine *Dienstkomponente*, die zusammen mit anderen Dienstanbietern oder Komponenten funktionieren müssen.

## <a name="data-providers"></a>Datenanbieter
 ADO ist leistungsfähiger und flexibler, da immer noch verfügbar das gleiche Programmiermodell, unabhängig davon, welche Funktionen für alle angegebenen Anbieter machen und mit jedem der mehrere verschiedene Datenanbieter verbinden können.

 Da jede Datenanbieter eindeutig ist, variiert wie die Anwendung mit ADO interagiert etwas vom Datenanbieter jedoch. Die Unterschiede werden in der Regel in einer von drei Kategorien:

-   Verbindungsparameter in die ["ConnectionString"](../../../ado/reference/ado-api/connectionstring-property-ado.md) Eigenschaft.

-   [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Nutzung Objekt.

-   Anbieterspezifische [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Verhalten.

 Details für jede der derzeit verfügbaren von Microsoft-Datenanbieter werden wie folgt aufgeführt.

|Bereich|Thema|
|----------|-----------|
|ODBC-Datenbanken|[Microsoft OLE DB-Anbieter für ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)|
|Microsoft Indexdienst|[Microsoft OLE DB-Anbieter für Microsoft Indexdienst](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md)|
|Active Directory-Dienst|[Microsoft OLE DB-Anbieter für Microsoft Active Directory-Dienst](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md)|
|Microsoft Jet-Datenbanken|[OLE DB-Anbieter für Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)|
|Microsoft SQL Server|[Microsoft OLE DB-Anbieter für SQLServer](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)|
|Oracle-Datenbanken|[Microsoft OLE DB-Anbieter für Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md)|
|Internet-Publishing|[Microsoft OLE DB-Anbieter für Internet-Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)|
|Einfache Datenquellen|[Einfache Microsoft OLE DB-Anbieter](../../../ado/guide/appendixes/microsoft-ole-db-simple-provider.md)|

## <a name="provider-specific-dynamic-properties"></a>Dynamische Eigenschaften der anbieterspezifischen
 Die [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Sammlungen von der [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md), [Befehl](../../../ado/reference/ado-api/command-object-ado.md), und [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekte enthalten die dynamische Eigenschaften, die spezifisch für die Anbieter. Diese Eigenschaften enthalten Informationen zu Funktionen, die spezifisch für den Anbieter über die integrierte Eigenschaften, die ADO unterstützt.

 Verwenden Sie nach dem Herstellen der Verbindung, und Erstellen dieser Objekte, die [aktualisieren](../../../ado/reference/ado-api/refresh-method-ado.md) Methode für die **Eigenschaften** Auflistung des Objekts, das die anbieterspezifischen Eigenschaften zu erhalten. Finden Sie in der Dokumentation des Anbieters und der [OLE DB Programmer's Guide](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8) ausführliche Informationen über diese dynamischen Eigenschaften.

## <a name="service-providers"></a>Dienstanbieter
 Um einen Dienstanbieter verwenden zu können, müssen Sie ein Schlüsselwort angeben. Sie sollten auch die anbieterspezifische dynamische Eigenschaften mit jedem Dienstanbieter kennen. Anbieterspezifische Informationen sind für jeden Dienstanbieter aufgeführt, die derzeit von Microsoft verfügbar ist:

-   [Microsoft Data Shaping Service für OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)

-   [Microsoft OLE DB-Persistenz-Provider](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)

-   [Microsoft OLE DB-Anbieter für Remoting](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)

## <a name="service-components"></a>Dienstkomponenten
 Die [Cursor Service für OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) Dienstkomponente ergänzt die Cursorfunktionen der Unterstützung von Datenanbietern. Außerdem müssen ein Schlüsselwort und dynamische Eigenschaften hat.

 Weitere Informationen zu OLE DB-Anbieter, finden Sie unter [Microsoft OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx).

## <a name="provider-commands"></a>Anbieterbefehle
 Für jeden Anbieter hier aufgeführt, wenn Ihre Anwendungen zulassen, dass die Benutzer zur Eingabe von SQL-Anweisungen wie die Anbieterbefehle, müssen Sie immer die Benutzereingabe überprüft und mögliche Hacker-Angriffe, die potenziell gefährliche SQL-Anweisungen, wie z. B. mit aufmerksam sein `DROP TABLE t1`, als Teil der Benutzereingabe.

## <a name="see-also"></a>Siehe auch
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md) [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md) [Microsoft OLE DB-Anbieter für Microsoft Active Directory-Dienst ](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md) [Microsoft OLE DB-Anbieter für Microsoft Indexdienst](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md) [Microsoft OLE DB-Anbieter für ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md) [Microsoft OLE DB-Anbieter für Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md) [Microsoft OLE DB-Anbieter für SQLServer](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) [Microsoft OLE DB-Anbieter für Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [ Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [Refresh-Methode (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)
