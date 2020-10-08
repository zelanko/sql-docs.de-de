---
title: Informationen zu OLE DB-Verbindungseigenschaften | Microsoft-Dokumentation
description: Im OLE DB-Treiber für SQL Server legen Consumer Eigenschaftswerte fest, um ein bestimmtes Objektverhalten anzufordern. Erfahren Sie mehr über das Festlegen von Eigenschaften.
ms.custom: ''
ms.date: 05/20/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, properties
- OLE DB Driver for SQL Server, properties
- properties [OLE DB]
- property values [OLE DB Driver for SQL Server]
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af733c202d9413cde25abf98974b7bce0ed8284a
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727222"
---
# <a name="about-ole-db-properties"></a>Informationen zu OLE DB-Eigenschaften
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

<!--
NOTE , GeneMi , 2020/May/20:
    This SQL 2016+ article is a nearly exact duplicate of another SQL 2016+ article.
    This article resides under docs/connect/oledb/ole-db-driver/.

    The other article resides under docs/relational-databases/native-client-ole-db-provider/.
    And, the other article has a SQL 2014 counterpart having its same GitHub directory path and filename, to support SQL 2014 OPS Versioning with SQL 2016+.

    This path-file name is:
'\sql-docs-pr\docs\connect\oledb\ole-db-driver\about-ole-db-properties.md'.

    The other path-file is named:
'\sql-docs-pr\docs\relational-databases\native-client-ole-db-provider\about-ole-db-properties.md'.

    Therefore, maybe this docs/connect/oledb/... file should be deleted?

1611957:  This NOTE relates to SEO content bug 1611957 about metadata 'title:' value duplication:
    https://mseng.visualstudio.com/TechnicalContent/_workitems/edit/1611957

PR 15068:  This HTML comment is being added by PR...
    https://github.com/MicrosoftDocs/sql-docs-pr/pull/15068
-->

  Consumer legen Eigenschaftswerte fest, um ein bestimmtes Objektverhalten anzufordern. Zum Beispiel verwenden Consumer Eigenschaften, um die Schnittstellen anzugeben, die von einem Rowset verfügbar gemacht werden sollen. Consumer rufen die Eigenschaftswerte ab, um die Fähigkeiten eines Objekts zu ermitteln, beispielsweise eines Rowsets, einer Sitzung oder eines Datenquellenobjekts.  
  
 Jede Eigenschaft verfügt über einen Wert, einen Typ, eine Beschreibung, ein Lese-/Schreibattribut. Rowset-Eigenschaften besitzen überdies einen Indikator, der angibt, ob die Eigenschaft auf einzelne Spalten des Rowsets angewendet werden kann.  
  
 Eine Eigenschaft wird durch eine GUID und eine ganze Zahl, welche die Eigenschaften-ID darstellt, identifiziert. Ein Eigenschaftensatz ist ein Satz aller Eigenschaften, die über die gleiche GUID verfügen. Neben den vordefinierten OLE DB-Eigenschaftensätzen implementiert der OLE DB-Treiber für SQL Server anbieterspezifische Eigenschaftensätze und die zugehörigen Eigenschaften. Jede Eigenschaft gehört zu einer oder mehreren Eigenschaftengruppen. Eine Eigenschaftengruppe ist die Gruppe aller Eigenschaften, die für ein bestimmtes Objekt gelten. Beispiele für Eigenschaftengruppen sind die Initialisierungseigenschaftengruppe, die Datenquellen-Eigenschaftengruppe, die Sitzungseigenschaftengruppe, die Rowseteigenschaftengruppe, die Tabelleneigenschaftengruppe und die Spalteneigenschaftengruppe. Jede dieser Eigenschaftengruppen enthält Eigenschaften.  
  
 Das Festlegen von Eigenschaftswerten beinhaltet Folgendes:  
  
1.  Bestimmen der Eigenschaften, deren Werte festgelegt werden sollen  
  
2.  Bestimmen der Eigenschaftensätze, die die identifizierten Eigenschaften enthalten  
  
3.  Zuordnen eines Arrays von DBPROPSET-Strukturen, wobei für jeden identifizierten Eigenschaftensatz eine Struktur angegeben werden muss  
  
4.  Zuordnen eines Arrays von DBPROP-Strukturen, wobei für jeden Eigenschaftensatz eine Struktur angegeben werden muss. Die Anzahl der Elemente in jedem Array entspricht der Anzahl der Eigenschaften (die in Schritt 1 identifiziert wurden), die zu diesem Eigenschaftensatz gehören.  
  
5.  Füllen der DBPROP-Struktur für jede Eigenschaft  
  
6.  Eintragen der Daten (Eigenschaftensatz-GUID, Zähler für die Anzahl der Elemente und ein Zeiger auf das zugehörige DBPROP-Array) in die DBPROPSET-Struktur für jeden Eigenschaftensatz  
  
7.  Aufrufen einer Methode, um Eigenschaften festzulegen und die Anzahl und das Array von DBPROPSET-Strukturen zu übergeben  
  
## <a name="see-also"></a>Weitere Informationen  
 [Creating an OLE DB Driver for SQL Server Application (Erstellen eines OLE DB-Treibers für eine SQL Server-Anwendung)](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)   
 [Eigenschaften (OLE DB)](/previous-versions/windows/desktop/ms722734(v=vs.85))  
  
